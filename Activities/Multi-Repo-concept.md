Yes — in that case, you can make the **`ADO-Pipeline-Templates-Repo` the central pipeline repository** and keep **Sales/Service repos only for Salesforce source code**.

### Recommended structure

```text
Salesforce-Sales-Repo
 ├── force-app/
 └── sfdx-project.json

Salesforce-Service-Repo
 ├── force-app/
 └── sfdx-project.json

ADO-Pipeline-Templates-Repo
 └── templates/
      ├── validate.yml
      ├── deploy.yml
      └── salesforce-ci-cd.yml
```

**No `azure-pipelines.yml` in Sales or Service repos.**

---

## 1. `salesforce-ci-cd.yml`

This is the **main pipeline**.

```yaml
parameters:

- name: application
  type: string

- name: sourceRepo
  type: string

- name: environment
  type: string
  default: DEV

- name: orgAlias
  type: string


trigger: none

resources:
  repositories:
  - repository: app
    type: git
    name: ${{ parameters.sourceRepo }}
    ref: refs/heads/main


stages:

- stage: Validate
  displayName: '${{ parameters.application }} Validation'

  jobs:
  - job: Validate

    steps:

    - checkout: app

    - template: validate.yml
      parameters:
        orgAlias: ${{ parameters.orgAlias }}


- stage: Deploy
  displayName: '${{ parameters.application }} Deploy'

  dependsOn: Validate

  jobs:
  - job: Deploy

    steps:

    - checkout: app

    - template: deploy.yml
      parameters:
        environment: ${{ parameters.environment }}
        orgAlias: ${{ parameters.orgAlias }}
```

---

## 2. `validate.yml`

```yaml
parameters:

- name: orgAlias
  type: string


steps:

- bash: |
    echo "Validating Salesforce metadata..."

    sf project deploy start \
      --source-dir force-app \
      --target-org ${{ parameters.orgAlias }} \
      --dry-run

  displayName: Salesforce Validation
```

---

## 3. `deploy.yml`

```yaml
parameters:

- name: environment
  type: string

- name: orgAlias
  type: string


steps:

- bash: |
    echo "Deploying to ${{ parameters.environment }}"

    sf project deploy start \
      --source-dir force-app \
      --target-org ${{ parameters.orgAlias }}

  displayName: Salesforce Deployment
```

---

# How do Sales and Service get triggered?

You create **two Azure DevOps pipelines**, but both point to the **same `salesforce-ci-cd.yml`** in the central repo.

### Sales Pipeline

Pipeline configuration:

```text
Pipeline Name: Salesforce-Sales-CI-CD

YAML:
ADO-Pipeline-Templates-Repo
        │
        └── templates/salesforce-ci-cd.yml

Parameters:
application = Sales
sourceRepo  = Salesforce-Sales-Repo
environment = UAT
orgAlias    = SALES-UAT
```

### Service Pipeline

```text
Pipeline Name: Salesforce-Service-CI-CD

YAML:
ADO-Pipeline-Templates-Repo
        │
        └── templates/salesforce-ci-cd.yml

Parameters:
application = Service
sourceRepo  = Salesforce-Service-Repo
environment = UAT
orgAlias    = SERVICE-UAT
```

### Overall architecture

```text
                    ADO
                     │
        ┌────────────┴────────────┐
        │                         │
Sales Pipeline              Service Pipeline
        │                         │
        └────────────┬────────────┘
                     │
                     ▼
       ADO-Pipeline-Templates-Repo
                     │
                     ▼
          salesforce-ci-cd.yml
              │            │
              ▼            ▼
         validate.yml   deploy.yml
              │            │
              └─────┬──────┘
                    │
          ┌─────────┴─────────┐
          ▼                   ▼
Salesforce-Sales-Repo   Salesforce-Service-Repo
          │                   │
          ▼                   ▼
       Sales App           Service App
```

### 🎯 Interview answer

> **“I don't keep pipeline YAML files in each application repository. I centralize the CI/CD implementation in a dedicated ADO Pipeline Templates repository. Sales and Service are separate Salesforce source repositories, while their ADO pipelines point to the same reusable `salesforce-ci-cd.yml`. Using parameters, I pass the application name, source repository, environment and target Salesforce org. The common template then calls validation and deployment templates. This gives centralized pipeline management with reusable logic and avoids duplicating YAML across application repositories.”**

**One important distinction:** the Sales and Service repos contain **source code only**; the ADO project contains the **pipeline definitions/templates and environment configuration**.

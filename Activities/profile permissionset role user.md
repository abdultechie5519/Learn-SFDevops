Below are 5 practical Salesforce Admin homework exercises using only standard objects and English names. These can be performed in a Salesforce Developer (Free) Org.

---

Practical Exercise 1: Create Users, Profiles, and Roles

Objective

Learn how to create users and assign Profiles and Roles.

Tasks

1. Create the following Roles:

   * Sales Manager
   * Sales Representative

2. Create the following Users:

   * John Smith
   * Emma Johnson

3. Assign:

   * John Smith → Sales Manager Role
   * Emma Johnson → Sales Representative Role

4. Assign the Standard User profile to both users.

5. Login as Emma (Login As) and verify that she can access standard Salesforce tabs.

Expected Outcome

* Two users are created.
* Both have the Standard User profile.
* Roles are assigned correctly.

---

Practical Exercise 2: Permission Set

Objective

Grant additional permissions without changing the Profile.

Tasks

1. Create a Permission Set named:

   * Contact Edit Access

2. Grant:

   * Read
   * Create
   * Edit
     permissions on the Contact object.

3. Assign the Permission Set to Emma Johnson.

4. Verify the Permission Set assignment under the User record.

Expected Outcome

* Emma receives additional Contact permissions through the Permission Set.

---

Practical Exercise 3: Permission Set Group

Objective

Combine multiple Permission Sets into one group.

Tasks

1. Create two Permission Sets:

   * Account Access
   * Opportunity Access

2. Grant:

   * Account Access → Read & Edit on Account
   * Opportunity Access → Read & Create on Opportunity

3. Create a Permission Set Group:

   * Sales Team Access

4. Add both Permission Sets to the group.

5. Assign the Permission Set Group to John Smith.

Expected Outcome

* John receives permissions from both Permission Sets through one Permission Set Group.

---

Practical Exercise 4: Profile vs Permission Set

Objective

Understand the difference between Profiles and Permission Sets.

Tasks

1. Create one new user:

   * David Wilson

2. Assign:

   * Standard User Profile

3. Create a Permission Set:

   * Lead Access

4. Grant Create and Edit permissions on the Lead object.

5. Assign the Permission Set to David.

6. Compare:

   * Profile permissions
   * Permission Set permissions

Questions

* Which permission comes from the Profile?
* Which permission comes from the Permission Set?
* Can one user have multiple Permission Sets?

Expected Outcome

Students understand that Profiles provide the base access, while Permission Sets add extra access.

---

Practical Exercise 5: Roles and Record Visibility

Objective

Understand how Roles affect record access.

Tasks

1. Create two Roles:

   * Sales Manager
   * Sales Executive

2. Create two Users:

   * Alice Brown (Sales Manager)
   * Michael Davis (Sales Executive)

3. Login as Michael and create:

   * 1 Account
   * 1 Contact
   * 1 Opportunity

4. Login as Alice (Manager).

5. Check whether Alice can view Michael's records.

6. Observe the Role Hierarchy.

Questions

* Who owns the records?
* Who can view the records?
* Does the Role affect object permissions?
* What is the difference between a Role and a Profile?

Expected Outcome

Students understand that:

* Roles control record visibility.
* Profiles control object and feature permissions.
* Permission Sets provide additional access without changing the Profile.

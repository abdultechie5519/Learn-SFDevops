Salesforce Relationships – Practical Exercises (Free Salesforce Org)

Title: Salesforce Relationships Hands-on Exercises

Exercise 1: Student & Course (Lookup Relationship)

Objective:
Learn how to create and use a Lookup Relationship.

Scenario:
A student can exist without joining a course. If a course is deleted, the student record should remain.

Tasks:

* Create Custom Object: Student

  * Student Name
  * Email
* Create Custom Object: Course

  * Course Name
  * Duration
* Create a Lookup Relationship from Student → Course.
* Create:

  * 3 Courses
  * 5 Students
* Leave at least one student without selecting a course.
* Delete one Course record.
* Verify that Student records are still available and the Course lookup becomes blank.
* Explain why Lookup Relationship allows orphan child records.

---

Exercise 2: Department & Employee (Master-Detail Relationship)

Objective:
Understand Master-Detail Relationship behavior.

Scenario:
An employee must always belong to a department.

Tasks:

* Create Custom Object: Department

  * Department Name
* Create Custom Object: Employee

  * Employee Name
  * Salary
* Create a Master-Detail Relationship:

  * Employee (Child)
  * Department (Master)
* Create:

  * 2 Departments
  * 5 Employees
* Try creating an Employee without selecting a Department.
* Delete one Department.
* Verify all related Employee records are automatically deleted.
* Explain why child records cannot exist without the parent.

---

Exercise 3: Student & Club (Many-to-Many / Junction Object)

Objective:
Implement a Many-to-Many Relationship using a Junction Object.

Scenario:
A student can join multiple clubs, and each club can have multiple students.

Tasks:

* Create Custom Object: Student
* Create Custom Object: Club
* Create Junction Object: Student Club Membership
* Add two Master-Detail Relationships:

  * Student Club Membership → Student
  * Student Club Membership → Club
* Create:

  * 3 Students
  * 3 Clubs
* Enroll students into multiple clubs.
* Verify one student can belong to multiple clubs and one club contains multiple students.
* Explain why Junction Objects require two Master-Detail relationships.

---

Exercise 4: Account, Contact & Opportunity (Standard Objects)

Objective:
Understand relationships using standard Salesforce objects.

Scenario:
A company has contacts and sales opportunities.

Tasks:

* Create:

  * 2 Accounts
  * 4 Contacts
  * 3 Opportunities
* Associate Contacts with Accounts.
* Associate Opportunities with Accounts.
* Delete one Account (only if no restrictions prevent deletion).
* Observe what happens to related records.
* Identify:

  * Account → Contact relationship type.
  * Account → Opportunity relationship type.
* Explain the relationship behavior between these standard objects.

---

Exercise 5: Relationship Comparison & Knowledge Validation

Objective:
Compare Lookup, Master-Detail, and Junction Relationships.

Tasks:
Create the following:

* Lookup:

  * Vendor → Product
* Master-Detail:

  * Project → Task
* Junction:

  * Doctor ↔ Patient using Appointment

Perform these activities:

* Create sample records.
* Delete parent records and observe child record behavior.
* Check whether child records can exist without parents.
* Identify which relationships support Roll-Up Summary fields.
* Compare record ownership and sharing behavior.
* Document your observations in a table.

Knowledge Questions:

1. What is the difference between Lookup and Master-Detail Relationship?
2. What happens when a parent record is deleted in both relationship types?
3. Why is a Junction Object required for Many-to-Many relationships?
4. Can Roll-Up Summary fields be created on Lookup Relationships?
5. Can a child record exist without its parent in a Master-Detail Relationship?
6. Give one real-time example of each relationship type.
7. Which relationship automatically inherits security from the parent?
8. Why are Junction Objects created with two Master-Detail Relationships?

These five exercises cover the complete practical understanding of:

* Lookup Relationship
* Master-Detail Relationship
* Parent-Child behavior
* Cascade Delete
* Roll-Up Summary concepts
* Record Ownership
* Security Inheritance
* Many-to-Many Relationship using Junction Objects
* Standard and Custom Object relationship scenarios in a Salesforce Free Developer Org.

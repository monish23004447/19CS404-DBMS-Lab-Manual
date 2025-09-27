[# Experiment 1: Entity-Relationship (ER) Diagram

## 🎯 Objective:
To understand and apply the concepts of ER modeling by creating an ER diagram for a real-world application.

## 📚 Purpose:
The purpose of this workshop is to gain hands-on experience in designing ER diagrams that visually represent the structure of a database including entities, relationships, attributes, and constraints.

---

## 🧪 Choose One Scenario:

### 🔹 Scenario 1: University Database
Design a database to manage students, instructors, programs, courses, and student enrollments. Include prerequisites for courses.

**User Requirements:**
- Academic programs grouped under departments.
- Students have admission number, name, DOB, contact info.
- Instructors with staff number, contact info, etc.
- Courses have number, name, credits.
- Track course enrollments by students and enrollment date.
- Add support for prerequisites (some courses require others).

---

### 🔹 Scenario 2: Hospital Database
Design a database for patient management, appointments, medical records, and billing.

**User Requirements:**
- Patient details including contact and insurance.
- Doctors and their departments, contact info, specialization.
- Appointments with reason, time, patient-doctor link.
- Medical records with treatments, diagnosis, test results.
- Billing and payment details for each appointment.

---

## 📝 Tasks:
1. Identify entities, relationships, and attributes.
2. Draw the ER diagram using any tool (draw.io, dbdiagram.io, hand-drawn and scanned).
3. Include:
   - Cardinality & participation constraints
   - Prerequisites for University OR Billing for Hospital
4. Explain:
   - Why you chose the entities and relationships.
   - How you modeled prerequisites or billing.

# ER Diagram Submission - Monishkumar.v - 212223040116

## Scenario Chosen:
 Hospital 

## ER Diagram:
![image](https://github.com/user-attachments/assets/d9dffd63-c38a-4af5-aa1c-c76d650ac6a6)


## Entities and Attributes:
...
- DEPARTMENT: dept_id, dept_name, dept_head

- DOCTOR: doctor_id, name, specialization, phone_no, email_id, work_schedule

- PATIENT: patient_id, name, dob, gender, phone_no, email

- APPOINTMENT: appointment_id, appointment_time&date, reason_for_visit

- MEDICAL RECORDS: medical_record_id, diagnosis, treatment, result
...

## Relationships and Constraints:
...
- DEPARTMENT–DOCTOR (have):

- Cardinality: One-to-Many (One department has many doctors)

- Participation: Total on Doctor (Each doctor belongs to a department)

- DOCTOR–APPOINTMENT (have):

- Cardinality: One-to-Many (One doctor can have many appointments)

- Participation: Partial on Doctor

- PATIENT–APPOINTMENT (have):

- Cardinality: One-to-Many (One patient can book multiple appointments)

- Participation: Total on Appointment

- APPOINTMENT–MEDICAL RECORDS (have):

- Cardinality: One-to-One (Each appointment has one medical record)

- Participation: Total on both
...

## Extension (Prerequisite / Billing):
...
- Prerequisite: Not explicitly modeled in the diagram. Could be included as an attribute in APPOINTMENT or a separate entity linking PATIENT to required preliminary checks or documentation.
- Billing: Also not modeled. Could be an additional entity (e.g., BILL) related to APPOINTMENT or MEDICAL RECORDS with attributes like billing_id, cost, payment_status.
...

## Design Choices:
- Entity separation: Each core component (Doctor, Patient, Department, etc.) is represented as a distinct entity for clarity and normalization.

- One-to-many relationships: Realistically mirrors how healthcare systems function (e.g., one doctor having many appointments).

- Total participation constraints: Applied where involvement is mandatory (e.g., each appointment must link to a patient and doctor).

- Normalization: Avoids data redundancy, separating work schedule, treatment details, and appointment metadata into respective entities or attributes.

## RESULT
The ER diagram organizes healthcare data to efficiently manage doctors, patients, appointments, and medical records with clear relationships.

](https://github.com/monish23004447/19CS404-DBMS-Lab-Manual/blob/main/Experiment1_ER_Diagram/problem_statement.md)

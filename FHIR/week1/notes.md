# FHIR Week1 – Patient / Observation / MedicationRequest

https://hl7.org/fhir/

## 1. Overview of FHIR
- **Purpose**: Enable interoperability of healthcare data across systems.
- **Resource**: The fundamental unit of FHIR data (e.g., Patient, Observation, Medication).
- **REST API**: Standard way to access resources via HTTP methods (GET, POST, PUT, DELETE).
- **Reference**: A link from one resource to another (e.g., Observation.subject → Patient).

## 2. Key Fields – Patient Resource
- id: Unique identifier for the patient resource.
- identifier[]: IDs such as national ID or hospital number.
- name[]: Patient’s name (given and family name).
- gender: Gender of the patient.
- birthDate: Date of birth.

📄 [FHIR Patient Documentation](https://hl7.org/fhir/patient.html)

## 3. Key Fields – Observation Resource
- id: Unique identifier for the observation.
- code: What was measured (LOINC code recommended).
- value[x]: The value of the observation (numeric, string, etc.).
- effectiveDateTime: Date/time when the observation was taken.
- subject: Reference to the Patient.

📄 [FHIR Observation Documentation](https://hl7.org/fhir/observation.html)

## 4. Key Fields – MedicationRequest Resource
- id: Unique identifier for the medication request.
- medication[x]: Information about the prescribed medication (code or reference to Medication).
- subject: Reference to the Patient.
- authoredOn: Date the prescription was created.
- dosageInstruction[]: How the medication should be taken.

📄 [FHIR MedicationRequest Documentation](https://hl7.org/fhir/medicationrequest.html)

## 5. Relationship Diagram

![FHIR Relationship Diagram](fhir_diagram.png)

## 6. Sample JSON Files
- [patient.json](patient.json)
- [observation.json](observation.json)
- [medicationrequest.json](medicationrequest.json)


## References
https://www.youtube.com/watch?v=fv2xTR_0QnA&list=PLp4xNHWZ7IQkqH6bHsYVFkh1tX0P1_2VF&index=2

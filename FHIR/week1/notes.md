# FHIR Week1 – Patient / Observation / MedicationRequest

## 1. Overview of FHIR
 **FHIR (Fast Healthcare Interoperability Resources)** is an international standard developed by HL7 to enable interoperability of healthcare data.
- Based on JSON, XML, and REST API for data exchange.
- Organizes information into standardized data units called **Resources**.
- Ensures consistent data structures across different systems for seamless compatibility.
- Uses **References** to define relationships between resources (e.g., `Observation.subject` → `Patient`).


## 2. Key Fields – Patient Resource
- id
- identifier[]
- name[]
- gender
- birthDate

## 3. Key Fields – Observation Resource
- id
- code
- value[x]
- effectiveDateTime
- subject (Reference to Patient)

## 4. Key Fields – MedicationRequest Resource
- id
- medication[x]
- subject (Reference to Patient)
- authoredOn
- dosageInstruction[]

## 5. Relationship Diagram
(Image to be inserted)

## 6. Sample JSON Files
- [patient.json](patient.json)
- [observation.json](observation.json)
- [medicationrequest.json](medicationrequest.json)

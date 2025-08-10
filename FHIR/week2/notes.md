Got it 👍
Here’s your **`notes.md`** for Week 2 in English, ready to drop into your GitHub repo.

---

````markdown
# Week 2 – FHIR JSON & REST API (Patient Resource)

## 1. Learning Objectives
- Understand the **FHIR data format (JSON)** structure
- Learn how to use **REST API** requests and search parameters
- Retrieve **Patient** data from the public HAPI FHIR server using Python
- Implement JSON saving, CSV conversion, and summary output

---

## 2. Understanding FHIR JSON Structure
- `resourceType`: Type of resource (e.g., `Patient`)
- `id`: Unique identifier of the resource
- `name`: Array of patient names (`given`, `family`)
- `gender`: Patient gender
- `birthDate`: Date of birth
- `meta.lastUpdated`: Last updated timestamp

Example (retrieved with `_count=1` from HAPI server):
```json
{
  "resourceType": "Patient",
  "id": "12345",
  "name": [
    {
      "family": "Moore",
      "given": ["Jenny"]
    }
  ],
  "gender": "female",
  "birthDate": "1982-04-07",
  "meta": {
    "lastUpdated": "2025-08-10T12:00:00+00:00"
  }
}
````

---

## 3. REST API Structure

* General format:

  ```
  GET [base_url]/[ResourceType]?[search_parameters]
  ```
* HAPI FHIR R4 server example:

  ```
  https://hapi.fhir.org/baseR4/Patient?_count=5
  ```
* Key search parameters:

  * `_count`: Limit number of results
  * `_sort`: Sorting criteria (`-_lastUpdated` → newest first)
  * `name`, `family`, `given`: Name search
  * `birthdate`: Date of birth filter (`geYYYY-MM-DD`, `leYYYY-MM-DD` supported)

---

## 4. Python Implementation

### 4.1 How to Run (Terminal)

```bash
# Latest 5 records
python week2_fhir_patient_tool.py

# Search by name + birthdate
python week2_fhir_patient_tool.py --name Jenny --birthdate 1982-04-07 --count 5

# Patients with family name "Kim", 3 records, save to CSV
python week2_fhir_patient_tool.py --family Kim --count 3 --out csv
```

### 4.2 Main Features

* API request (`search_patients`)
* Convert JSON to summary list (`bundle_to_rows`)
* Save raw JSON / save CSV
* Flexible search parameters for filtering

---

## 5. Example Output

**Command:**

```bash
python week2_fhir_patient_tool.py --name Jenny --birthdate 1982-04-07 --count 5
```

**Output:**

```
id | Name        | Gender | BirthDate   | LastUpdated
-----------------------------------------------------
12345 | Jenny Moore | female | 1982-04-07 | 2025-08-10T12:00:00+00:00
67890 | Jenny Smith | female | 1982-04-07 | 2025-08-09T08:15:23+00:00
...
```

**Files Generated:**

* `patient_api.json`
* `patient_api.csv` (if CSV option selected)

---

## 6. Key Takeaways

* FHIR JSON is organized by resource type (`resourceType`)
* RESTful API search parameters allow for precise data filtering
* Python can automate the process from API call → data transformation → file saving

---

## 7. References

* HL7 FHIR Official Documentation: [https://www.hl7.org/fhir/patient.html](https://www.hl7.org/fhir/patient.html)
* HAPI FHIR Server: [https://hapi.fhir.org](https://hapi.fhir.org)
* fhirclient GitHub: [https://github.com/smart-on-fhir/client-py](https://github.com/smart-on-fhir/client-py)

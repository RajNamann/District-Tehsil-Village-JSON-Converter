# 🏛️ Excel → JSON District–Tehsil–Village Converter

This tool converts government *District–Tehsil–Village* data from Excel spreadsheets into structured JSON format.

Designed specifically for:
- Land Record Digitization Projects
- OBPAS / EDCR / GIS Systems
- Revenue Department Workflows
- Panchayat / Block / Tehsil Master Data Automation

No installation required.  
**Runs entirely in the browser.**  
Just **Upload → Convert → Download JSON**.

---

## 🧠 Problem This Solves

Government-issued district master Excel files frequently follow this pattern:

District | Tehsil | Village | | Tehsil | Village | | Tehsil | Village | ...
Mau | Ghosi | V1 | | Madhuban | V1 | | Kopaganj| V1 |
(Village Rows Continue…)
Mau | Muhammadabad | V1 | ...


Tehsils repeat **horizontally** in groups of 3 columns and villages list **vertically**.

This tool:
✅ Detects district boundaries  
✅ Detects every tehsil in a row  
✅ Collects all villages below each tehsil  
✅ Outputs clean JSON

---

## 🧾 Input Format Requirement

Your Excel sheet must look like this:

| District | Tehsil | Village |   | Tehsil | Village |   | Tehsil | Village |
|----------|--------|---------|---|--------|---------|---|--------|---------|
| Mau      | Ghosi  | Village1|   | Madhuban | Village1|   | Kopaganj | Village1 |
| (blank)  | (blank)| Village2|   | (blank) | Village2|   | (blank) | Village2 |
| (blank)  | (blank)| Village3|   | (blank) | Village3|   | (blank) | Village3 |
| Mau      | Muhammadabad | Village1 | ...

**Pattern rule:**  
Tehsil blocks repeat every **3 columns** →  
**[Tehsil Name] [Villages] [Spacer]**

District changes when column A becomes non-empty again.

---

## 🎯 Output JSON Structure

```json
[
  {
    "District": "Mau",
    "tehsils": [
      {
        "tehsilName": "Ghosi",
        "villages": ["Adampur", "Ahemadpur Asana", "Ahirani Buzurg", "..."]
      },
      {
        "tehsilName": "Madhuban",
        "villages": ["Ali Nagar", "Alipur", "Allipur", "..."]
      }
    ]
  }
]

This JSON is ready for:

APIs

SQL Import

GIS Mapping

Government Portal Master Data

📝 License

This project is licensed under the MIT License.
You may use it in commercial, government, or private systems freely.

👤 Maintainer
Naman Raj Srivastava
Email: namanrajsrivastava@gmail.com
# Dynamic eConsent Framework in REDCap

This project implements a **Dynamic Consent Form System** using REDCap's **e-Consent Framework** and **repeating instruments**. The system allows multiple consent forms to be managed and signed from a **single instrument**, avoiding the need for duplicative consent variables and making reconsenting easier and cleaner.

---

## 📋 Overview

Traditional REDCap projects often require a separate instrument or set of fields for each consent form, which can quickly become unwieldy when:
- Participants must sign multiple study sub-consents
- Consent forms are updated and require re-signatures from existing participants

This project introduces a **dynamic, single-form solution** using:
- A repeating e-Consent instrument
- Dynamic field display logic based on the selected consent form
- Built-in version control and flexible update capabilities

---

## 💡 Key Features

- ✅ **One instrument for all consents**: Select which consent form to show from a dropdown.
- 🧠 **Smart logic**: Dynamically displays only the relevant language, signature, and date fields.
- 🔁 **Repeating**: Allows multiple consents per participant (e.g., initial + updated version).
- 📂 **Version tracking**: Easily track which version was signed.
- 📈 **Scalable**: Simplifies reporting and analysis across consent waves.
- 🔧 **Easily updatable**: Modify language or add new versions with minimal reconfiguration.

---

## 📁 Repository Contents

- `dynamic_consent_instrument_v1.zip`: REDCap instrument file to import into your project
- `dynamic_consent_instrument_v2.zip`: Example updated version
- `field_dictionary.xlsx`: Field map and documentation for consent logic, versioning, and display behavior
- `README.md`: Project documentation

---

## 🛠️ Setup Instructions

1. **Import the Instrument**  
   In your REDCap project, navigate to **Project Setup > Online Designer** and **Import** the provided `.zip` instrument.

2. **Enable Repeating Instruments**  
   Go to **Project Setup > Enable optional modules and customizations**, and enable *Repeating Instruments* for the consent form.

3. **Enable e-Consent Framework**  
   From **Project Setup > e-Consent Framework**, enable the framework for your dynamic consent instrument.

4. **Customize Consent Options**  
   In the imported instrument:
   - Locate the field `consent_type` (dropdown)
   - Update choices to reflect your study’s consent forms
   - Review associated branching logic for each consent language block and signature section

5. **Manage Consent Versions**  
   - Use the field `consent_version` to distinguish between form versions
   - Archive old consent versions within the form using branching logic
   - Deploy new versions without modifying core structure

---

## 🔄 Updating Consent Forms

When a consent form is updated and the full cohort must be reconsented:

- **Do not create a new form**  
- Instead, update the relevant `consent_type` content and increment the `consent_version`
- Existing records remain accessible for historical versions
- The repeating nature of the instrument captures multiple signatures from the same participant over time

This allows a single query to retrieve all consent records for a given form across all versions, avoiding the need to merge multiple variables.

---

## 🧪 Use Case Example

Participant signs:
1. `Biorepository Consent v1` — May 2023
2. `Biorepository Consent v2` — July 2025

All records are stored under the same repeating consent form, tagged by `consent_type` and `consent_version`, and can be filtered or exported easily.

---

## 📊 Benefits

- **Streamlined data structure**
- **Reduced variable clutter**
- **Improved compliance tracking**
- **Historical version retention**
- **Simplified data pulls and reporting**

---

## 📩 Questions or Contributions

For questions, contributions, or instrument submissions, contact:

**Mesulam Center Data Management Core**  
Maintainer: [Debby Zemlock](mailto:your.email@northwestern.edu)

---

## 🏷️ License

Internal use only — Northwestern University  
Not licensed for public distribution or reuse without written permission.

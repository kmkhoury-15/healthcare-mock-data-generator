# Synthetic Healthcare Data Generator

A GitHub Pages-ready, single-page web app for generating **synthetic mock healthcare data** from a data dictionary.

The app is designed for public health teams, healthcare administrators, healthcare researchers, medical professionals, analysts, students, and developers who need realistic-looking test data for dashboards, demos, ETL testing, QA workflows, schema validation, and training.

> **Important:** This app generates synthetic data only. Do not upload real patient data, protected health information (PHI), production extracts, or confidential business data.

## What the app does

- Uploads a data dictionary in CSV, JSON, XLS, or XLSX format.
- Reads common dictionary columns such as `name`, `field_name`, `column_name`, `comment`, `description`, `type`, and `data_type`.
- Infers mock-data generation rules from each field's name, comment, and data type.
- Supports healthcare-specific generation profiles:
  - Healthcare administration / operations
  - Clinical research
  - Clinical care / medical professional
  - Public health surveillance
  - Mixed healthcare dataset
- Lets users manually edit the inferred rule for every field.
- Generates synthetic data directly in the browser.
- Exports generated records as CSV, JSON, or XLSX.

## Example generated field types

The inference engine can generate realistic synthetic values for fields such as:

- Patient IDs, MRNs, encounter IDs, claim IDs, provider IDs, facility IDs
- Names, contact fields, address fields, county, state, ZIP code
- Age, date of birth, sex, gender, race, ethnicity, preferred language
- Facility, department, unit, service line, provider name, provider specialty
- ICD-10-like diagnosis codes and diagnosis descriptions
- CPT-like procedure codes and procedure descriptions
- Medication names, medication classes, RxNorm-like codes, NDC-like codes
- Lab test names, LOINC-like codes, lab values, lab units, result flags
- Vital sign values, triage acuity, admission date, discharge date, length of stay
- Payer, plan type, claim status, authorization status, appointment status
- Charges, allowed amounts, payments, quality measures, readmission flags
- Study ID, participant ID, consent status, study arm, eligibility status
- Adverse events, adverse event grade, protocol deviations, IRB status
- Public health case ID, pathogen, reportable disease, case status, specimen type
- Test result, vaccination status, outbreak ID, public health action

## Project structure

```text
healthcare-mock-data-generator/
├── index.html
├── README.md
├── LICENSE
├── CHANGELOG.md
├── SECURITY.md
├── .gitignore
├── .nojekyll
├── .github/
│   └── workflows/
│       └── deploy-pages.yml
└── sample_dictionaries/
    ├── healthcare_admin_dictionary.csv
    ├── clinical_research_dictionary.csv
    ├── medical_professional_dictionary.csv
    ├── public_health_surveillance_dictionary.csv
    └── README.md
```

## Data dictionary format

Your data dictionary should contain at least one field-name column. The app recognizes names such as:

- `name`
- `field`
- `field_name`
- `column`
- `column_name`
- `variable`
- `variable_name`

Optional but recommended columns:

- `comment`
- `description`
- `definition`
- `type`
- `data_type`
- `allowed_values`
- `options`
- `choices`
- `enum`

Example:

```csv
name,type,comment
patient_id,string,Synthetic patient identifier
encounter_id,string,Visit or encounter identifier
admission_date,date,Hospital admission date
diagnosis_code,string,ICD-10 diagnosis code
total_charges,decimal,Total charges in US dollars
readmission_30d_flag,boolean,Yes/no flag for 30-day readmission
```

## Running locally

Because this is a static app, you can open `index.html` directly in a browser.

For a local web server, run:

```bash
python3 -m http.server 8000
```

Then open:

```text
http://localhost:8000
```

## Deploying to GitHub Pages

### Option 1: Repository settings

1. Create a new GitHub repository.
2. Upload all files from this folder to the repository root.
3. Make sure the main app file is named `index.html` and remains in the root folder.
4. Go to **Settings → Pages**.
5. Under **Build and deployment**, choose **Deploy from a branch**.
6. Select your main branch and the root folder `/`.
7. Save the setting and wait for GitHub Pages to publish the site.

### Option 2: GitHub Actions workflow

This repo also includes `.github/workflows/deploy-pages.yml`, which can publish the static site using GitHub Actions.

To use it:

1. Push this project to GitHub.
2. Go to **Settings → Pages**.
3. Set the source to **GitHub Actions**.
4. Push to `main`, or manually run the workflow from the **Actions** tab.

## Privacy and security notes

- The app is static HTML, CSS, and JavaScript.
- Dictionary files are read in the browser.
- Generated output is created in browser memory and downloaded locally.
- The app loads SheetJS from a CDN to support XLS/XLSX parsing and export.
- This app is not a HIPAA compliance tool and does not provide legal compliance guarantees.
- Do not upload real patient data, PHI, production extracts, proprietary data, or restricted datasets.

## Development notes

There is no build step, package manager, or backend service required.

The app intentionally keeps all code in `index.html` so it can be deployed directly to GitHub Pages with minimal setup.

## License

MIT License. See `LICENSE` for details.

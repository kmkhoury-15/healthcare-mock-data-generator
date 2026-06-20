# Security and privacy policy

This project is intended for synthetic mock-data generation only.

## Do not upload sensitive data

Do not upload:

- Protected health information (PHI)
- Real patient records
- Production extracts
- Confidential business records
- Identifiable research participant data
- Restricted or regulated datasets

## Browser-only processing

The app is a static client-side tool. Uploaded dictionaries are read by the browser and generated records are created in browser memory.

However, this project uses the SheetJS browser library from a CDN for XLS/XLSX support. Loading a CDN script creates a network request for that script. Uploaded dictionary content is not intentionally sent to any backend by this app.

## Compliance disclaimer

This app is not a HIPAA compliance product and does not provide legal, regulatory, privacy, or security compliance guarantees.

Use only with synthetic schemas, public sample dictionaries, and non-sensitive development assets.

# Data Model – Panama Electronic Invoicing (Digifact)

## Design Principles
- Regulatory data must be historically immutable
- Invoice data must survive partner changes
- FE requirements override ERP normalization

---

## Core Models

### res.partner (Customer)
Used to store **default FE identity data**.

Fields:
- FE legal name
- Tax ID / DV
- Provincia / Distrito / Corregimiento
- Country

Notes:
- Partner data is used as a **source**, not a guarantee.
- Values may differ from the invoice snapshot.

---

### res.company (Seller)
Used to define **seller identity and defaults**.

Fields:
- FE Tax ID
- Branch code
- Point of sale
- FE configuration values

---

### account.move (Invoice)
This model stores the **FE snapshot**.

Why snapshot?
- FE XML must reflect exact values at issuance time
- Partner data may change later
- Audits require immutability

Stored at posting time:
- Buyer name
- Buyer tax ID
- Full address (all levels)
- FE document metadata
- Submission status

---

## Location Catalog

### pa.provincia
### pa.distrito
### pa.corregimiento

Reason:
- DGI requires **coded geographic values**
- Free-text addresses are not sufficient

---

## Future Models (Planned)
- fe.log (submission attempts)
- fe.response (Digifact/DGI feedback)
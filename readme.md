# Panama Electronic Invoicing – Digifact (Odoo 19 Community)

## Overview
This module provides the base structure for integrating Panama electronic
invoicing (Factura Electrónica – DGI) with Digifact in Odoo 19 Community.

Current state: **Skeleton / WIP**

---

## Scope (Current Phase)
- FE identity fields on customer and company
- Panama location catalog (Provincia / Distrito / Corregimiento)
- Invoice FE snapshot fields (no API submission yet)
- UI tabs for FE data and status
- Logging model for future Digifact submissions

---

## Out of Scope (For Now)
- Digifact API submission
- XML generation
- DGI status polling
- Credit notes / debit notes
- Advanced error handling

---

## Data Model Overview

### Customer (res.partner)
- FE legal name
- Tax ID / DV
- Location (Provincia, Distrito, Corregimiento)
- Country validation

### Company (res.company)
- Seller FE identity
- Branch / point-of-sale defaults
- FE configuration fields

### Invoice (account.move)
- FE snapshot fields copied at posting time
- FE status fields
- Read-only FE tab

---

## Module Structure

```text
l10n_pa_edi_digifact/
├── models/
├── views/
├── data/
├── security/
├── wizards/
└── static/
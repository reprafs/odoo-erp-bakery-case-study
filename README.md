# Odoo ERP Implementation: Bakery SME Case Study

Odoo ERP implementation for a bakery SME using the ASAP methodology: Purchase, Inventory, Manufacturing, Sales, and Accounting modules, with As-Is/To-Be process mapping, gap analysis, black box testing, and UAT.

> Final-year thesis project (S1 Information Systems, Universitas Trisakti, 2026).
> Role: Business Analyst / ERP Implementer (solo project).

[123]-Foto 1: Cover image. Rekomendasi: screenshot dashboard Odoo utama atau collage 3 foto (diagram + dashboard + testing), lebar 900px

---

## Table of Contents
1. [Overview](#1-overview)
2. [Business Problem & Requirements](#2-business-problem--requirements)
3. [Business Process Diagrams (As-Is vs To-Be)](#3-business-process-diagrams-as-is-vs-to-be)
4. [Gap Analysis](#4-gap-analysis)
5. [System Configuration](#5-system-configuration)
6. [ERP Interface & Dashboard](#6-erp-interface--dashboard)
7. [Testing Documentation](#7-testing-documentation)
8. [Results & Recommendations](#8-results--recommendations)
9. [Full Documentation](#9-full-documentation)

---

## 1. Overview

| | |
|---|---|
| **Client** | Bakery SME, operating since 1988 (family-owned, bread production and distribution via street vendors) |
| **Goal** | Integrate procurement, inventory, production, distribution, and financial recording into one system |
| **Methodology** | Accelerated SAP (ASAP): Project Preparation, Business Blueprint, Realization, Final Preparation, Go-Live & Support |
| **Platform** | Odoo Online (Education edition), standard features only, no custom development |
| **Modules** | Purchase, Inventory, Manufacturing, Sales, Accounting |
| **Scope note** | Simulation-based implementation, no server infrastructure |
| **Data collection** | Interviews, field observation, document review |
| **Modeling** | UML (Activity Diagram, Use Case Diagram), Gap Analysis |

[123]-Nama perusahaan: kalau sudah dapat izin dari pemilik, boleh sebut nama asli di sini. Kalau belum, biarkan "Bakery SME".

---

## 2. Business Problem & Requirements

### Problems found in the manual process (As-Is)
All operations ran on paper, whiteboards, and notebooks:

1. Raw material orders were placed by phone with no records.
2. Incoming goods were stored by rough estimate, so stock was only guessed.
3. Supplier payments (cash, on-the-spot, and credit terms) had no transaction history.
4. Vendor bread requests were written on paper, then copied to a whiteboard, with no recap.
5. Production followed the whiteboard, and material usage was noted on scrap paper.
6. Distribution relied on paper requests, which the owner then used to count vendor deposits.
7. Vendor deposits were recalculated manually with notebooks and a calculator, which was slow and error-prone.
8. There was no integrated report for the owner to monitor the business.

### User requirements

| User | Key needs |
|---|---|
| **Owner** | Record purchases, receipts, and supplier payments; monitor stock and production; track operating expenses; access financial reports |
| **Coordinator (staff)** | Record vendor bread requests in a structured way; auto-calculate daily production totals |
| **Warehouse (staff)** | Record incoming goods directly; monitor raw material stock |

### System requirements (summary)
Purchase order recording, receipt and real-time stock monitoring, supplier payment recording (cash/on-the-spot/credit), structured vendor requests, production linked to requests with automatic material deduction, distribution recording, automatic vendor deposit calculation, and integrated financial and operational reports.

---

## 3. Business Process Diagrams (As-Is vs To-Be)

Seven business processes were mapped using UML Activity Diagrams.

| # | Process | As-Is | To-Be |
|---|---|---|---|
| 1 | Raw material purchasing | [View](diagrams/as-is/01-purchasing.png) | [View](diagrams/to-be/01-purchasing.png) |
| 2 | Raw material receiving | [View](diagrams/as-is/02-receiving.png) | [View](diagrams/to-be/02-receiving.png) |
| 3 | Supplier payment | [View](diagrams/as-is/03-supplier-payment.png) | [View](diagrams/to-be/03-supplier-payment.png) |
| 4 | Bread request (vendors) | [View](diagrams/as-is/04-bread-request.png) | [View](diagrams/to-be/04-bread-request.png) |
| 5 | Bread production | [View](diagrams/as-is/05-production.png) | [View](diagrams/to-be/05-production.png) |
| 6 | Bread distribution | [View](diagrams/as-is/06-distribution.png) | [View](diagrams/to-be/06-distribution.png) |
| 7 | Vendor deposit | [View](diagrams/as-is/07-vendor-deposit.png) | [View](diagrams/to-be/07-vendor-deposit.png) |

### Featured: Bread Production

**As-Is**

<img src="diagrams/as-is/05-production.png" width="700">

[123]-Foto 2: Activity diagram As-Is Produksi Roti (Gambar 4.5 di skripsi, export PNG dari draw.io)

**To-Be**

<img src="diagrams/to-be/05-production.png" width="700">

[123]-Foto 3: Activity diagram To-Be Produksi Roti (Gambar 4.12 di skripsi)

### Featured: Vendor Deposit

**As-Is**

<img src="diagrams/as-is/07-vendor-deposit.png" width="700">

[123]-Foto 4: Activity diagram As-Is Setoran Pedagang (Gambar 4.7)

**To-Be**

<img src="diagrams/to-be/07-vendor-deposit.png" width="700">

[123]-Foto 5: Activity diagram To-Be Setoran Pedagang (Gambar 4.14)

### Use Case Diagram

<img src="diagrams/use-case.png" width="700">

[123]-Foto 6: Use Case Diagram (Gambar 4.15)

> Editable source file: [`diagrams/source/diagrams.drawio`](diagrams/source/diagrams.drawio) (open with [draw.io](https://app.diagrams.net))

---

## 4. Gap Analysis

The gap between the existing process and Odoo's capabilities was mapped per business process.

[123]-Tabel Gap Analysis: ambil 2-3 baris paling menarik dari Tabel 4.2 skripsi (kolom: Proses Bisnis, Kebutuhan, Pra-Odoo, Odoo). Contoh yang sudah ada di skripsi: pembelian bahan baku, stok minimum lewat Inventory > Replenishment. Terjemahkan ke bahasa Inggris, atau screenshot tabelnya saja.

Example (Raw Material Purchasing):

| Aspect | Before Odoo | With Odoo |
|---|---|---|
| Ordering | Phone/WhatsApp from verbal reports, no written record | Warehouse staff monitor stock in Inventory > Replenishment, and click **Order** when stock hits the minimum |

[123]-Lengkapi baris contoh lain dari Tabel 4.2 kalau mau

---

## 5. System Configuration

### Setup
Database created through Odoo Education (cloud), with the five modules selected at sign-up.

[123]-Foto 7: Pemilihan modul di Odoo Education (Gambar 4.16)

### Module configuration

| Module | Key configuration |
|---|---|
| **Purchase** | Lock Confirmed Orders, 3-way Matching, Variants, Units of Measure & Packagings |
| **Inventory** | Units of Measure & Packagings, Reception Report |
| **Manufacturing** | Default settings |
| **Sales** | Units of Measure & Packagings, Margins, Lock Confirmed Sales, Invoicing Policy: *Invoice What is Delivered* |
| **Accounting** | Default tax 0% (tax included), Sales Credit Limit, Units of Measure & Packagings, Margin Analysis, Cash Journal on Outstanding Receipts/Payments |

[123]-Foto 8: Konfigurasi Purchase (Gambar 4.21)
[123]-Foto 9: Konfigurasi Sales (Gambar 4.24)
[123]-Foto 10: Konfigurasi Accounting / Journal Cash (Gambar 4.25 atau 4.32)

### Master data
- **Purchase**: suppliers, purchase prices, packaging units (bale, carton, box)
- **Inventory**: raw materials, fillings, finished goods, unit of measure, price per unit
- **Manufacturing**: Bill of Materials for each product (plain bread and sweet bread variants: mocha, sprinkles, chocolate, coconut, cheese, donut, milk)
- **Sales**: street vendors set up as customers, plus a Quotation Template for standard daily orders

[123]-Foto 11: Daftar Bill of Material (Gambar 4.29)
[123]-Foto 12: Daftar pedagang di modul Sales (Gambar 4.30)
[123]-Foto 13: Quotation Template (Gambar 4.31)

---

## 6. ERP Interface & Dashboard

[123]-Foto 14: Dashboard utama Odoo (Gambar 4.20)
[123]-Foto 15: Dashboard / laporan Inventory (stok bahan baku)
[123]-Foto 16: Dashboard / laporan Sales (penjualan per pedagang)
[123]-Foto 17: Laporan keuangan di Accounting (Profit & Loss / Balance Sheet)

<img src="images/dashboard/dashboard-main.png" width="800">

> Screenshots use simulated data. No real financial data is exposed.

---

## 7. Testing Documentation

### White box testing
Login flow tested (empty fields, invalid input, valid credentials). All cases passed.

[123]-Foto 18: Tabel white box (Tabel 4.3), opsional

### Black box testing
9 scenarios covering the full end-to-end flow. **All 9 passed (Valid).**

| # | Scenario | Expected result | Result |
|---|---|---|---|
| 1 | Create Purchase Order | PO created, status becomes *Purchase Order* | Valid |
| 2 | Receive raw materials | Receipt becomes *Done*, stock increases | Valid |
| 3 | Vendor Bill & supplier payment | Bill created from PO, payment recorded as *Paid* | Valid |
| 4 | Create Sales Order (bread request) | Sales Order created from Quotation Template | Valid |
| 5 | Create Manufacturing Orders via Replenishment | One MO per product variant based on total demand | Valid |
| 6 | Run production | MOs completed, raw material stock decreases, finished goods increase | Valid |
| 7 | Bread distribution | Delivery validated, finished goods stock decreases | Valid |
| 8 | Vendor deposit | Invoice created, payment recorded (including partial payment) | Valid |
| 9 | Journal entries & financial reports | Journal posted, reports reflect recorded transactions | Valid |

[123]-Foto 19: Bukti testing skenario 1 (PO)
[123]-Foto 20: Bukti testing skenario 6 (produksi, stok berubah)
[123]-Foto 21: Bukti testing skenario 8 (invoice + partial payment)
[123]-Foto 22: Bukti testing skenario 9 (laporan keuangan)

> More evidence: [`images/testing/`](images/testing/)

### User Acceptance Testing (UAT)
Usability-based questionnaire (Likert scale 1-5) with 3 respondents, one per role.

| Role | Score | Category |
|---|---|---|
| Owner | **81.2%** | Very good |
| Warehouse staff | **76.2%** | Good |
| Coordinator staff | **69.2%** | Good |

| Indicator | Owner | Coordinator | Warehouse |
|---|---|---|---|
| Learnability | 80% | 80% | 80% |
| Efficiency | 93.3% | 66.6% | 86.6% |
| Memorability | 60% | 60% | 60% |
| Errors | 73.3% | 60% | 60% |
| Satisfaction | 95% | 75% | 90% |

**Insight:** Memorability scored lowest across all roles (60%). Users still need time to recall workflows for tasks they do infrequently, which points to a need for ongoing training and visual guides.

[123]-Foto 23: Bar chart UAT per indikator per role (opsional, bisa dibuat dari tabel di atas pakai Excel/Python)

---

## 8. Results & Recommendations

### Results
- **Integrated flow**: procurement, inventory, production, sales, and accounting now run in one connected system.
- **Structured records**: all transactions are stored in one database and can be traced back.
- **Production planning**: vendor requests in Sales feed daily production totals.
- **Deposit calculation**: invoices calculate each vendor's amount automatically.
- **Reporting**: inventory, production, sales, and financial reports are available to the owner.

### Limitations
- Requires a stable internet connection (cloud-based).
- Users need an adaptation period, so the system is not always faster than the manual process at first.
- Actual production quantity can differ from the plan, so manual adjustment is still needed.
- Report accuracy depends on input quality, and the implementation period was short.

### Recommendations
1. Move from simulation to continuous production use.
2. Run regular user training, especially for the Coordinator and Warehouse roles.
3. Add the Employee module for staff data and daily wage calculation.
4. Extend the in-system Knowledge documentation with step-by-step screenshots.

---

## 9. Full Documentation

- Full thesis (PDF, Indonesian): [123]-Link Google Drive skripsi
- All diagrams, testing evidence, dashboard screenshots: [123]-Link Google Drive folder

---

## Tools
`Odoo Online (Education)` `draw.io` `UML` `ASAP Methodology` `Gap Analysis` `Black Box / White Box Testing` `UAT (Likert Scale)`

## Author
**Muhammad Rafi**: [123]-Link LinkedIn / email

# Rice Mill ERP

This repository documents a modular ERP for a paddy/rice mill. The system follows the full business flow from paddy procurement through milling, inventory control, sales, and accounting, with quality control and reporting connected across every stage.

## Module Relationship Diagram

```mermaid
flowchart LR
    SUP[Suppliers, Farmers, Agents] --> PROC[Procurement & Purchase]
    PROC --> QC[Quality Control & Compliance]
    QC --> INV[Inventory & Warehouse]
    INV --> PROD[Production & Manufacturing]
    PROD --> QC
    PROD --> INV
    INV --> SALES[Sales & Customer Management]
    SALES --> CUST[Customers]

    PROC --> FIN[Financial Management & Accounting]
    SALES --> FIN
    INV --> FIN
    PROD --> FIN

    PROC --> TRACE[Batch, Lot & Traceability]
    QC --> TRACE
    INV --> TRACE
    PROD --> TRACE
    SALES --> TRACE

    INV --> BYP[By-Product Management]
    PROD --> BYP
    BYP --> SALES
    BYP --> FIN

    PROC --> MIS[Reporting & Analytics]
    QC --> MIS
    INV --> MIS
    PROD --> MIS
    SALES --> MIS
    FIN --> MIS
    TRACE --> MIS
```

## Core Business Flow

1. Procurement records paddy purchases from farmers, suppliers, or agents.
2. Quality Control verifies moisture, grade, weight, and food-safety parameters before stock acceptance.
3. Inventory stores accepted paddy by lot, godown, variety, and valuation method.
4. Production consumes paddy lots and records soaking, drying, hulling, polishing, grading, and packing.
5. Inventory receives finished rice and by-products such as husk, bran, and broken rice.
6. Sales manages customer orders, pricing, dispatch, invoices, and credit control.
7. Finance posts purchase payables, production costs, inventory valuation, receivables, taxes, and profit/loss.
8. Reporting combines operational and financial data into dashboards, stock statements, yield reports, and MIS views.

## Modules

| Module | Purpose | README |
| --- | --- | --- |
| Procurement & Purchase | Paddy intake, suppliers, purchase orders, weighment, and payable triggers. | [modules/procurement/README.md](modules/procurement/README.md) |
| Inventory & Warehouse | Stock visibility across paddy, rice, by-products, bags, lots, and godowns. | [modules/inventory/README.md](modules/inventory/README.md) |
| Production & Manufacturing | Milling workflow, BOM, input/output capture, yield, wastage, and packing. | [modules/production/README.md](modules/production/README.md) |
| Sales & Customer | Sales orders, invoices, dispatch, pricing, customer credit, and returns. | [modules/sales/README.md](modules/sales/README.md) |
| Financial Management | Payables, receivables, ledger posting, taxes, costing, and profitability. | [modules/finance/README.md](modules/finance/README.md) |
| Quality Control | Inspection plans and quality checks for purchase, process, and finished goods. | [modules/quality-control/README.md](modules/quality-control/README.md) |
| Reporting & Analytics | MIS dashboards, yield analysis, stock reports, receivables, and profitability. | [modules/reporting/README.md](modules/reporting/README.md) |
| Traceability & Batch Control | End-to-end batch and lot tracking from source paddy to final sale. | [modules/traceability/README.md](modules/traceability/README.md) |
| By-Product Management | Husk, bran, broken rice, and other secondary output tracking and sale. | [modules/by-product-management/README.md](modules/by-product-management/README.md) |
| Multi-Site Operations | Multi-godown and multi-mill stock, production, transfers, and controls. | [modules/multi-site-operations/README.md](modules/multi-site-operations/README.md) |

## Integration Principles

- Every stock movement must carry lot, godown, item, quantity, and valuation references.
- Every production batch must record input paddy, output rice grades, by-products, process losses, and yield.
- Every purchase and sale must create financial impact through payables, receivables, tax, and ledger postings.
- Quality results should be linked to supplier performance, inventory acceptance, production outcomes, and sales confidence.
- Reporting should read from operational modules instead of duplicating business data.


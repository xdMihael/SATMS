# Zettle API Field & Structure Specification

## 1. Core Principles
- **Monetary Values:** All prices, amounts, tax amounts, and change figures are stored and transmitted as **integers representing minor currency units (cents)** (e.g., `200` = €2.00, `8040` = €80.40).
- **Timestamps:** ISO 8601 format in UTC (`+0000`). Display layer must handle conversion to `Europe/Berlin`.
- **Fiscal Compliance:** KassenSichV compliance is handled automatically via Zettle's native Fiskaly integration (`fiscalIntegrator: "fiskaly"`).

---

## 2. Product Library (`/organizations/self/products/v2`)
Each product entry handles variant-level pricing and categorization:
- **Product UUID:** Root identifier (`uuid`).
- **Category:** Linked category object (`category.uuid`, `category.name`, e.g., `"Beilage"`).
- **Variants:** Array containing variant records:
  - `uuid`: Unique variant identifier.
  - `price.amount`: Integer cents (e.g., `200`).
  - `price.currencyId`: `"EUR"`.
  - `costPrice.amount`: Integer minor units.
  - `vatPercentage`: String or numeric representation of VAT rate (e.g., `"7"` or `"19"`).
- **Versioning:** Tracked via `etag` and `updated` UTC timestamps.

---

## 3. Purchase History (`/purchases/v2`)
Each transaction record contains structural breakdowns required for accounting and table management:
- **Pagination & Hashes:** Uses `firstPurchaseHash` and `lastPurchaseHash` for cursor-based pagination across ranges.
- **Payments:** Array of payment methods (`payments[].type`, e.g., `"IZETTLE_CASH"`), tracking exact `amount`, `handedAmount`, and `changeAmount` in integer cents.
- **Cash Register Location:** Linked under `cashRegister` (e.g., `"Zum Dorfkrug"`, address details in Bachstraße, Plattling).
- **Fiscal Details (Fiskaly):** 
  - `references.fiscalIntegrator`: `"fiskaly"`
  - `references.fiscalTxId`: Unique TSE transaction ID.
  - `references.fiscalDetails`: Contains `ersId` and `clientId`.
- **Tax Breakdown:** 
  - `taxationMode`: `"INCLUSIVE"`
  - `taxValues[]`: Detailed breakdown per rate (`taxValue`, `taxAmount`, `totalAmount`, `taxableAmount`).
  - `groupedVatAmounts`: Aggregate mapping by percentage key (e.g., `"7.0": 3180`, `"19.0": 4860`).
- **Refund Status:** Boolean flags `refunded` and `refund`.
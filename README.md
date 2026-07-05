# Deposco (deposco)

Deposco is a cloud supply chain execution platform combining order management (OMS) and warehouse management (WMS) for retailers, brands, 3PLs, and DTC ecommerce sellers. Its Bright Suite gives real-time visibility into inventory, orders, and shipments across the fulfillment lifecycle - receiving, putaway, picking, packing, and shipping. Deposco integrates through a REST API exposed on its Developer Portal ([developer.deposco.com](https://developer.deposco.com/)) using resource paths under `/integration/{code}/`, secured with OAuth 2.0 / per-merchant API credentials and scoped by tenant code and business unit.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/deposco/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/deposco/refs/heads/main/apis.yml)

## Access Model (Read First)

Deposco's API is **real but gated**. Deposco runs a genuine public Developer Portal with API reference documentation, but API access is **not open self-service**:

- You need an active Deposco subscription.
- Credentials - **Tenant Code**, **API Username**, **API Password**, and **Business Unit** - are issued **per merchant by a Deposco account manager**.
- OAuth 2.0 applications (Client ID / Client Secret) are created and managed inside the Developer Portal once access is granted.
- The API **base host is instance-specific** (per tenant), e.g. `https://{instance}.deposco.com/integration/{code}`.

Because the authoritative endpoint reference lives behind the gated Developer Portal and is scoped to each tenant, the APIs and endpoints below are **modeled from publicly visible third-party integration documentation** (Techdinamics, DropStream, Extensiv, Parabola). Exact paths, request/response schemas, and the base host should be confirmed against a provisioned Deposco instance. No OpenAPI document was fabricated for this reason.

Deposco also ships **150+ pre-built connectors and EDI integrations**, so many teams integrate without building directly against the API.

## Tags

- Supply Chain
- Warehouse Management (WMS)
- Order Management (OMS)
- Fulfillment
- Inventory
- Logistics
- Ecommerce
- 3PL

## Timestamps

- **Created:** 2026-07-04
- **Modified:** 2026-07-04

## APIs (Endpoints Modeled)

### Deposco Customer Orders API

Import and query customer (sales) orders for fulfillment - `PUT /import/{businessUnit}/customerOrder/{orderNumber}` to create/update an order, and `GET /search/CoHeader` / `GET /search/shipment` to look up order status and resulting shipments.

- **Documentation:** [https://developer.deposco.com/](https://developer.deposco.com/)
- **Base URL (modeled):** `https://{instance}.deposco.com/integration/{code}`

### Deposco Purchase Orders API

Create and search purchase orders for inbound inventory - `PUT /orders/Purchase Order/{orderNumber}`, `POST /orders`, and `GET /search/Order?otherReferenceNumber={externalOrderNumber}`.

- **Documentation:** [https://developer.deposco.com/](https://developer.deposco.com/)
- **Base URL (modeled):** `https://{instance}.deposco.com/integration/{code}`

### Deposco Items API

Create and update item (SKU) master data - `PUT /items/{itemNumber}` for a single item and `POST /items` for bulk imports.

- **Documentation:** [https://developer.deposco.com/](https://developer.deposco.com/)
- **Base URL (modeled):** `https://{instance}.deposco.com/integration/{code}`

### Deposco Inventory API

Retrieve real-time inventory by facility and location - `GET /inventory/facility/{facilityNumber}/location/{locationNumber}` and `GET /inventory/{businessUnit}/facility/{facilityNumber}/location/{locationNumber}`.

- **Documentation:** [https://developer.deposco.com/](https://developer.deposco.com/)
- **Base URL (modeled):** `https://{instance}.deposco.com/integration/{code}`

### Deposco Shipments API

Search outbound shipments produced by fulfillment - `GET /search/shipment?orderHeaders.customerOrderNumber={orderNumber}` for shipment and tracking detail on a customer order.

- **Documentation:** [https://developer.deposco.com/](https://developer.deposco.com/)
- **Base URL (modeled):** `https://{instance}.deposco.com/integration/{code}`

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/deposco)
- [Website](https://deposco.com/)
- [Documentation](https://developer.deposco.com/)
- [Plans](plans/deposco-plans-pricing.yml)
- [Blog](https://blog.deposco.com/)

## Pricing

Deposco does not publish public, self-service pricing. It is sold as a subscription SaaS through a sales-led motion; API access is included with a subscription and provisioned per merchant. See [plans/deposco-plans-pricing.yml](plans/deposco-plans-pricing.yml). Contact Deposco for a current quote.

## WebSocket

No documented public WebSocket API. Deposco's integration surface is request/response REST over HTTPS. See [review.yml](review.yml).

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com

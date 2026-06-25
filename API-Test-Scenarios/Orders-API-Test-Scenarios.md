# API Test Scenarios: Orders Service

| Field | Value |
|-------|-------|
| **Service** | Orders API |
| **Base URL** | `https://api.staging.novacart-demo.io/v1` |
| **Document ID** | API-TS-ORD-001 |
| **Version** | 1.0 |
| **Author** | QA Team |
| **Date** | 2026-06-25 |

---

## Authentication

All scenarios unless noted require a valid Bearer token obtained via `POST /auth/login`.

```
Authorization: Bearer <access_token>
Content-Type: application/json
```

---

## API-ORD-001: Create order with valid payload

| Attribute | Detail |
|-----------|--------|
| **Method** | POST |
| **Endpoint** | `/orders` |
| **Requirement** | REQ-API-002 |
| **Priority** | P1 |

**Request Body**

```json
{
  "userId": "usr_8f2a91bc",
  "items": [
    { "productId": "prod_backpack_01", "quantity": 1, "unitPrice": 29.99 }
  ],
  "shippingAddress": {
    "line1": "123 Commerce St",
    "city": "Austin",
    "state": "TX",
    "postalCode": "78701",
    "country": "US"
  },
  "paymentMethod": "card"
}
```

**Expected Response**

| Attribute | Value |
|-----------|-------|
| Status Code | 201 Created |
| Body | Order object with `orderId`, `status: "pending"`, `total` |
| Headers | `Location: /v1/orders/{orderId}` |

---

## API-ORD-002: Reject order with empty items array

| Attribute | Detail |
|-----------|--------|
| **Method** | POST |
| **Endpoint** | `/orders` |
| **Requirement** | REQ-API-004 |
| **Priority** | P2 |

**Request Body**

```json
{
  "userId": "usr_8f2a91bc",
  "items": [],
  "shippingAddress": { "line1": "123 Commerce St", "city": "Austin", "state": "TX", "postalCode": "78701", "country": "US" }
}
```

**Expected Response**

| Attribute | Value |
|-----------|-------|
| Status Code | 400 Bad Request |
| Error Code | `VALIDATION_ERROR` |
| Message | "Order must contain at least one item" |

---

## API-ORD-003: Retrieve order by ID

| Attribute | Detail |
|-----------|--------|
| **Method** | GET |
| **Endpoint** | `/orders/{orderId}` |
| **Requirement** | REQ-API-002 |
| **Priority** | P1 |

**Preconditions:** Order `ord_a1b2c3d4` exists for authenticated user.

**Expected Response**

| Attribute | Value |
|-----------|-------|
| Status Code | 200 OK |
| Body | Complete order object matching creation payload |
| Response Time | < 500ms (p95) |

---

## API-ORD-004: Return 404 for non-existent order

| Attribute | Detail |
|-----------|--------|
| **Method** | GET |
| **Endpoint** | `/orders/ord_nonexistent` |
| **Priority** | P2 |

**Expected Response**

| Attribute | Value |
|-----------|-------|
| Status Code | 404 Not Found |
| Error Code | `ORDER_NOT_FOUND` |

---

## API-AUTH-002: Reject request with invalid token

| Attribute | Detail |
|-----------|--------|
| **Method** | GET |
| **Endpoint** | `/orders` |
| **Requirement** | REQ-API-003 |
| **Priority** | P1 |

**Headers**

```
Authorization: Bearer invalid_token_value
```

**Expected Response**

| Attribute | Value |
|-----------|-------|
| Status Code | 401 Unauthorized |
| Error Code | `UNAUTHORIZED` |

---

## API-USER-001: Retrieve user profile

| Attribute | Detail |
|-----------|--------|
| **Method** | GET |
| **Endpoint** | `/users/{userId}` |
| **Requirement** | REQ-API-001 |
| **Priority** | P1 |

**Expected Response**

| Attribute | Value |
|-----------|-------|
| Status Code | 200 OK |
| Body Fields | `userId`, `email`, `firstName`, `lastName`, `createdAt` |
| Excluded Fields | `password`, `passwordHash` |

---

## Test Data

| Entity | ID | Notes |
|--------|-----|-------|
| Test User | usr_8f2a91bc | standard_user equivalent |
| Product | prod_backpack_01 | Taxable item |
| Valid Order | ord_a1b2c3d4 | Seeded for GET scenarios |

---

## Execution Log

| Scenario ID | Status | Executed By | Date | Tool |
|-------------|--------|-------------|------|------|
| API-ORD-001 | | | | Postman |
| API-ORD-002 | | | | Postman |
| API-ORD-003 | | | | Postman |
| API-ORD-004 | | | | Postman |
| API-AUTH-002 | | | | Postman |
| API-USER-001 | | | | Postman |

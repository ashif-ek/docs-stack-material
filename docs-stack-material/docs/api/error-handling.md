# Standardized Error Handling

To guarantee a predictable developer experience for frontend clients and seamless integration for third-party consumers, every API within this ecosystem strictly adheres to standardized HTTP semantics and a unified JSON error response architecture.

---

## 🚦 HTTP Status Code Semantics

The APIs exclusively utilize standard HTTP status codes to instantly communicate the overarching result of a client request.

*   `200 OK`: The request was successfully fulfilled.
*   `201 Created`: The request was successful, resulting in the creation of a new persistent resource.
*   `400 Bad Request`: The server cannot process the request due to a client error (e.g., malformed syntax, failing payload validation).
*   `401 Unauthorized`: Authentication is missing, completely invalid, or the JWT session has expired.
*   `403 Forbidden`: The client's identity is known, but they lack the required permissions (RBAC) to execute the action.
*   `404 Not Found`: The requested resource or URL path does not exist.
*   `500 Internal Server Error`: An unexpected application failure occurred. *Note: Stack traces are never exposed to the client in production.*

---

## 📦 Unified Error Response Payload

When an API encounters any error (Status `4xx` or `5xx`), it abandons standard payload delivery and instead returns a strictly typed JSON error construct. This guarantees the frontend can programmatically parse and display the exact failure reason without guessing.

### Standardized Format Structure

```json
{
  "status": "error",
  "code": 400,
  "message": "The provided data failed payload validation criteria.",
  "details": {
    "field": "password",
    "issue": "Password string must contain at least one numeric character and one special symbol."
  },
  "timestamp": "2026-03-05T12:00:00Z"
}
```

### Key Attributes
- **`status`**: Always hardcoded to `"error"` enabling quick conditional checks on the frontend.
- **`code`**: Mirrors the HTTP status code for redundant verification.
- **`message`**: A human-readable summary of the failure suitable for generic UI alerts.
- **`details`**: (Optional) A highly specific key-value mapping detailing exact field-level validation errors, perfect for attaching inline error states to specific form inputs.
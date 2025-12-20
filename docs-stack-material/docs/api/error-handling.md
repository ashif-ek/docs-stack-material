# Error Handling

Standardized error responses.

## HTTP Status Codes

*   `200 OK`: Success.
*   `201 Created`: Resource successfully created.
*   `400 Bad Request`: Validation error.
*   `401 Unauthorized`: Missing or invalid token.
*   `403 Forbidden`: Insufficient permissions.
*   `404 Not Found`: Resource does not exist.
*   `500 Server Error`: Internal application failure.

## Error Response Format

```json
{
  "status": "error",
  "code": 400,
  "message": "Invalid password format",
  "details": {
    "field": "password",
    "issue": "Must contain at least one number"
  }
}
```
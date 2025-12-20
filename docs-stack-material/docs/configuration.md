# Configuration

Most projects in this portfolio use environment variables for configuration to ensure security and flexibility.

## Common Environment Variables

While each project has unique needs, you will commonly encounter these:

### Database
*   `DATABASE_URL`: Connection string for PostgreSQL or MongoDB.
*   `DB_HOST`, `DB_PORT`, `DB_USER`, `DB_PASSWORD`: Individual connection parameters.

### Security
*   `SECRET_KEY`: Used for cryptographic signing (Django/Flask).
*   `JWT_SECRET`: Secret key for signing JSON Web Tokens.
*   `ADMIN_PASSWORD`: Default password for initial admin accounts.

### External Services
*   `VITE_API_URL`: Backend API URL for frontend applications.
*   `STRIPE_SECRET_KEY` / `RAZORPAY_KEY_ID`: Payment gateway credentials.
*   `EMAIL_HOST_USER`, `EMAIL_HOST_PASSWORD`: SMTP credentials for sending emails.

## Setup

1.  Copy the example env file (often named `.env.example`).
2.  Rename it to `.env`.
3.  Fill in your specific values.

> [!WARNING]
> Never commit your `.env` file to version control. It is excluded by default in `.gitignore`.
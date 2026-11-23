# Indotech Transformers: Data Collection System

Indo Tech Transformers collects order data from inspectors, customers, the marketing team and the design team through one web form that people open by scanning a QR code. The internal team reviews every submission on a dashboard and exports it to Excel.

- Scan the QR code, pick your role (inspector, customer, marketing or design) and fill in that role's form.
- Marketing and design entries are keyed by work order number. They cover PO and LOA numbers, contractors, vector group, frequency, winding material and more.
- The internal team signs in to a dashboard that lists every submission by role.
- Export all four tables to one Excel workbook, one sheet per role.
- Admins reset a forgotten password with a one-time code sent by email.
- Data lives in one SQLite file on the server, so there is no database to set up.

## Quick start

```bash
git clone https://github.com/KRISH-exe-29/indotech-transformers.git && cd indotech-transformers
npm run install:all
npm run dev            # API on http://localhost:3001
npm run dev:client     # second terminal: forms on http://localhost:5173
```

On first start the server creates `server/indotech.db`, seeds an `admin` user for the internal dashboard (`/internal`), and writes `qr-code.png` pointing at `BASE_URL`. **Change the admin password before you put this on a network.**

## Production build

```bash
npm run build    # builds the client and installs server packages
npm start        # serves the API and the built client on PORT
```

## Environment variables

| Variable | Description | Default |
|---|---|---|
| `PORT` | Server port | `3001` |
| `SESSION_SECRET` | Session encryption key | (random default) |
| `SMTP_USER` | Gmail address for OTP emails | — |
| `SMTP_PASS` | Gmail App Password | — |
| `BASE_URL` | Public URL for QR code | `http://localhost:3001` |

## Tech stack

React and Vite (client) · Express, sql.js (SQLite), ExcelJS, Nodemailer and qrcode (server).

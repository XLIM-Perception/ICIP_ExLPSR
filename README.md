# XLPSR Challenge Website (Modernized)

A Node.js + Express app with EJS templates, redesigned using Bootstrap 5 for a clean, responsive UI. Supports team registration, result uploads via email, and ranking display from MongoDB.

## Features
- Responsive layout with Bootstrap 5
- EJS templates with shared layout
- Team registration with email confirmation
- Password-protected result submission endpoints
- Top-10 ranking view from MongoDB

## Requirements
- Node.js `>=18`
- MongoDB (Atlas or self-hosted)
- SMTP account (e.g., Gmail) for email notifications

## Environment Variables
Create a `.env` file in the project root:

```
PORT=3000
MONGO_URI="mongodb+srv://<user>:<pass>@<cluster>/<db>?retryWrites=true&w=majority"
EMAIL_USER="your@gmail.com"
EMAIL_PASS="your_app_password"
```

Notes:
- For Gmail, generate an App Password and use it for `EMAIL_PASS`.
- Keep credentials secure and never commit `.env`.

## Install & Run Locally

```bash
npm install
npm run dev
```

The app listens on `http://localhost:3000` by default.

## Deploy on Render.com

1. Push this folder to a Git repository.
2. In Render, create a new Web Service and select the repo.
3. Set:
	- Build Command: `npm install`
	- Start Command: `npm start`
4. Add environment variables in Render’s dashboard:
	- `PORT` (Render sets this automatically; you can omit)
	- `MONGO_URI` (use MongoDB Atlas connection string)
	- `EMAIL_USER`, `EMAIL_PASS`
5. Choose a Node version `>=18` (Render detects from `engines` in `package.json`).
6. Deploy. Render will install deps and start the server.

## Project Structure

```
app.js                # Express server & routes
views/                # EJS templates (Bootstrap layout)
public/               # Static assets (CSS, JS, images)
models/team.js        # Mongoose Team schema
```

## Useful Endpoints
- `GET /results` — top teams (ranking)
- `POST /submit-registration` — team registration + email confirmation
- `POST /api/check-password` — validate registration password
- `POST /api/upload-result` — email JSON result to organizers
- `POST /api/update-score` — update team score (requires teamName + password)

## Notes
- Update `public/style.css` for any custom styles overriding Bootstrap.
- If some pages need more modernization, refactor corresponding `views/*.ejs` using Bootstrap components.

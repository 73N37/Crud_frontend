# Crud Frontend

The standalone React + TypeScript frontend for the **Dynamic CRUD Engine Platform**.  
Deployed on GitHub Pages at **https://73n37.github.io/Crud_frontend/**.

## Tech Stack

- **React 19** with TypeScript
- **Vite** for bundling and dev server
- **Playwright** for E2E tests
- **GitHub Actions** for CI/CD deployment to GitHub Pages

## Getting Started

### Prerequisites

- Node.js 22+
- npm 10+

### Install & Run

```bash
# Install dependencies
npm install

# Start local dev server (defaults to http://localhost:5173)
npm run dev

# Build for production
npm run build

# Preview production build locally
npm run preview
```

### E2E Tests

```bash
# Install Playwright browsers
npx playwright install --with-deps chromium

# Run E2E tests (requires backend on :8080 and preview on :4173)
npm run test:e2e
```

## Backend Configuration

The frontend connects to the backend API via the `VITE_API_URL` environment variable:

| Environment   | File               | Default Value                                        |
|---------------|--------------------|------------------------------------------------------|
| Development   | `.env.development` | `http://localhost:8080`                              |
| Production    | `.env.production`  | `https://crud-api-placeholder.ondigitalocean.app`    |

To override locally, create a `.env.local` file:

```env
VITE_API_URL=http://your-custom-backend:8080
```

The backend URL can also be changed at runtime via the **Backend API Base URL** input field in the dashboard UI.

## Deployment

Deployment is automated via GitHub Actions. Every push to `main` triggers:

1. `npm ci` — install dependencies
2. `npm run build` — produce the `dist/` output
3. Deploy `dist/` to GitHub Pages

The app is served at: `https://73n37.github.io/Crud_frontend/`

## Project Structure

```
├── .github/workflows/deploy.yml   # GitHub Pages CI/CD
├── e2e/                           # Playwright E2E tests
├── public/                        # Static assets (favicon, icons)
├── src/
│   ├── App.tsx                    # Main application component
│   ├── App.css                    # Application styles
│   ├── main.tsx                   # React entry point
│   ├── index.css                  # Global styles
│   ├── env.d.ts                   # Vite env type declarations
│   └── assets/                    # Images & SVGs
├── .env.development               # Dev backend URL
├── .env.production                # Prod backend URL (placeholder)
├── index.html                     # HTML entry point
├── vite.config.ts                 # Vite configuration
├── tsconfig.json                  # TypeScript project references
├── playwright.config.ts           # Playwright test config
└── package.json                   # Dependencies & scripts
```

## License

MIT

# Self-Hosting Guide

Cap's web platform (`apps/web`) can be self-hosted, giving you full control over your data and infrastructure.

**(Note: This is a high-level guide based on the repository structure. Detailed steps require examining deployment configurations or specific documentation if available.)**

## Prerequisites

*   **Server Environment:** A server or platform capable of running Node.js applications (e.g., Docker, VPS, PaaS like Vercel/Netlify - though Vercel seems implied by infra).
*   **Database:** A MySQL-compatible database (PlanetScale is used in development, but any MySQL 8+ should work).
*   **S3-Compatible Storage:** An S3 bucket (AWS S3, Cloudflare R2, MinIO) for storing video recordings, transcriptions, etc.
*   **Email Service:** An email provider configured for sending magic links, notifications, etc. (Resend is used in the codebase).
*   **Environment Variables:** Proper configuration of all required server and public environment variables (see `.env.example` and `packages/env/`).

## Key Components to Host

1.  **Next.js Web Application (`apps/web`):** This is the main user interface and API backend.
2.  **Database:** Your chosen MySQL database.
3.  **S3 Storage:** Your chosen S3-compatible storage.
4.  **(Optional) `apps/tasks` Service:** This backend service seems responsible for background processing (e.g., merging audio). It needs to be hosted and accessible by the main web application if its functionality is required. It appears to be an Express app, potentially run in Docker.

## General Steps

1.  **Clone the Repository:** Get the Cap codebase.
2.  **Configure Environment Variables:** Create a `.env` file (or use your hosting provider's environment variable system) based on `.env.example`. Key variables include:
    *   `DATABASE_URL` / `DATABASE_MIGRATION_URL`
    *   `NEXTAUTH_SECRET`, `NEXTAUTH_URL`
    *   `CAP_AWS_ACCESS_KEY`, `CAP_AWS_SECRET_KEY`, `NEXT_PUBLIC_CAP_AWS_BUCKET`, `NEXT_PUBLIC_CAP_AWS_REGION`, `NEXT_PUBLIC_CAP_AWS_ENDPOINT` (if needed)
    *   `RESEND_API_KEY` (or other email provider config)
    *   Potentially keys for Google Auth, WorkOS, Stripe, Deepgram, etc., if using those features.
    *   `NEXT_PUBLIC_WEB_URL` (set to your self-hosted domain).
3.  **Set up Database:**
    *   Create your MySQL database.
    *   Run database migrations using `pnpm db:push` (ensure `DATABASE_MIGRATION_URL` points to your write-access DB URL if different from the read URL).
4.  **Build the Application:**
    *   Run `pnpm install`.
    *   Run `pnpm build --filter=@cap/web`. If `apps/tasks` is needed, build it too (`pnpm build --filter=@cap/tasks`).
5.  **Deploy:**
    *   **Web App:** Deploy the `apps/web/.next` directory using a Node.js hosting provider or containerize it.
    *   **Tasks App (if needed):** Deploy the `apps/tasks` service, potentially as a Docker container using the provided `Dockerfile`. Ensure it's configured to be reachable by the web app.
6.  **Configure DNS:** Point your chosen domain to your hosted web application.
7.  **Configure Desktop App (Users):** Users wishing to use your self-hosted instance will need to configure the "Server URL" in their desktop app's settings to point to your domain instead of `cap.so`.

**(Disclaimer: This is a simplified overview. Self-hosting may require significant technical expertise depending on your chosen infrastructure.)**

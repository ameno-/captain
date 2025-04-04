# Web Platform (cap.so)

The Cap web platform is where you manage your account, view recordings, collaborate, and handle billing.

## Overview

*   **Technology:** Built with [Next.js](https://nextjs.org/) and [React](https://reactjs.org/).
*   **Access:** Visit [https://cap.so](https://cap.so) (or your self-hosted domain).
*   **Authentication:** Log in via Google, Email Magic Link, or potentially SSO (WorkOS integration detected).

## Dashboard

The main hub after logging in (`/dashboard`):

*   **Your Recordings:** A list or grid view of recordings you've created.
    *   View thumbnails (`VideoThumbnail.tsx`).
    *   Access sharing links.
    *   Delete recordings (`CapCardActions.tsx`).
    *   View basic analytics (view counts) (`CapCardAnalytics.tsx`).
*   **Shared With You:** Recordings shared with you or your workspace (`/shared-caps`).
*   **Navigation:** Links to Settings, Workspaces, Billing, etc. (`AdminNavbar/`).

## Key Sections

*   **Sharing Pages (`/s/[videoId]`):** Public or private pages to view individual recordings. Includes playback, comments, transcripts, and activity logs.
*   **Settings (`/dashboard/settings`):** Manage your user profile, workspace settings, billing, and integrations.
*   **Workspaces (`/dashboard/settings/workspace`):** Invite members, manage roles, configure workspace settings like allowed domains or custom domains.
*   **Billing (`/dashboard/settings` -> Billing):** Manage your subscription plan (Free/Pro), view usage quotas.

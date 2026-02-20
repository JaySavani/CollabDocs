# CollabDocs

A comprehensive real-time collaborative documentation platform built with Next.js, similar to Google Docs.

## Features

- **Real-time collaborative editing**: Multiple users can edit the same document simultaneously.
- **Live cursors and user presence indicators**: See who else is viewing or editing the document in real-time.
- **Rich text editing**: Full support for formatting (bold, italic, lists, etc.) using a Tiptap-based editor.
- **Secure authentication**: User management and session handling powered by Clerk.
- **Instant sync**: Changes are synced instantly across all connected clients.
- **Responsive, clean UI**: A modern interface built with Tailwind CSS and Shadcn UI.

## Tech Stack

### Frontend

The frontend is built for performance and interactivity:

- **Next.js (App Router)**: Utilizing server-side rendering and the latest routing capabilities.
- **TypeScript**: Ensuring type safety and code reliability.
- **React**: Component-based architecture for a modular UI.
- **Tailwind CSS + Shadcn UI**: A utility-first CSS framework combined with accessible component primitives.
- **Zustand**: Lightweight state management for handling UI state (e.g., toolbar settings).
- **Tiptap**: A headless wrapper for ProseMirror, providing a powerful rich text editing experience.

### Backend & Infrastructure

Serverless and scalable infrastructure:

- **Liveblocks**: Handles the heavy lifting for real-time collaboration (WebSocket connections, conflict resolution).
- **Convex**: A reactive, serverless database that syncs data in real-time to the client.
- **Clerk**: A complete suite for authentication and user management.

## Project Structure

```text
CollabDocs/
├── convex/                # Backend (Convex) - Schema, logic, and auth
├── public/                # Static assets (images, icons)
├── src/                   # Main application code
│   ├── app/               # Next.js App Router (pages & layouts)
│   │   ├── (home)/        # Landing page/Dashboard
│   │   ├── api/           # API routes (Liveblocks auth, etc.)
│   │   └── documents/     # Document-specific pages
│   ├── components/        # Reusable UI components
│   │   ├── ui/            # Basic UI elements (Shadcn UI)
│   │   └── toolbar/       # Document toolbar components
│   ├── constants/         # Shared constants/config
│   ├── extensions/        # Tiptap custom extensions
│   ├── hooks/             # Custom React hooks
│   ├── lib/               # Utility functions
│   ├── providers/         # Context providers (Convex, Clerk)
│   └── store/             # State management (Zustand)
├── liveblocks.config.ts   # Real-time collaboration config
├── next.config.ts         # Next.js configuration
├── tailwind.config.ts     # Tailwind CSS styling config
└── package.json           # Dependencies and scripts
```

## Getting Started

Follow these steps to set up the project locally.

### Prerequisites

- Node.js (v18 or higher recommended)
- npm, yarn, or pnpm

### Installation

1. **Clone the repository**

   ```bash
   git clone <repository-url>
   cd CollabDocs
   ```

2. **Install dependencies**

   ```bash
   npm install
   # or
   yarn install
   # or
   pnpm install
   ```

3. **Environment Setup**
   Create a `.env.local` file in the root directory and add the necessary environment variables for Clerk, Convex, and Liveblocks.

   ```env
   # Deployment used by `npx convex dev`
   CONVEX_DEPLOYMENT=

   NEXT_PUBLIC_CONVEX_URL=

   # Clerk Auth
   NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=
   CLERK_SECRET_KEY=

   # Liveblocks
   NEXT_PUBLIC_LIVEBLOCKS_PUBLIC_KEY=
   LIVEBLOCKS_SECRET_KEY=
   ```

4. **Setup Convex**
   Initialize and run the Convex development server:

   ```bash
   npx convex dev
   ```

5. **Run the Application**
   In a separate terminal window, start the Next.js development server:

   ```bash
   npm run dev
   ```

   Open [http://localhost:3000](http://localhost:3000) in your browser to see the application.

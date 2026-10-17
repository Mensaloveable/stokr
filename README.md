# Inventory Management System (IMS)

A production-ready, mobile-first Inventory Management System built with Next.js 14+, MongoDB, NextAuth.js, and shadcn/ui.

## Tech Stack

- Next.js 14+ (App Router, TypeScript)
- Tailwind CSS + shadcn/ui (mobile-first, responsive)
- MongoDB (Atlas or self-hosted replica set) + Mongoose 8+
- NextAuth.js (Auth.js) with credentials provider + JWT sessions
- Zod for validation, React Hook Form for forms
- TanStack Table for data grids
- @react-pdf/renderer for invoice/waybill PDF generation
- Recharts for dashboard charts
- date-fns, Lucide icons
- Zustand for light client state

## Setting up MongoDB replica set

Since all multi-document transactions require a replica set, you need to run MongoDB as a single-node replica set locally with Docker.

### Prerequisites

- Docker and Docker Compose installed

### Steps

1. Create a keyfile for MongoDB authentication (optional for local dev, but recommended):
   ```bash
   openssl rand -base64 756 > mongo-keyfile
   chmod 400 mongo-keyfile
   ```

2. Start MongoDB:
   ```bash
   docker-compose up -d
   ```

3. Initialize the replica set:
   ```bash
   docker exec -it ims-mongodb mongosh --eval "rs.initiate({_id: 'rs0', members: [{_id: 0, host: 'localhost:27017'}]})"
   ```

4. Verify the replica set is initialized:
   ```bash
   docker exec -it ims-mongodb mongosh --eval "rs.status()"
   ```

5. Copy `.env.example` to `.env.local` and update values:
   ```bash
   cp .env.example .env.local
   ```

### Using Atlas

If using MongoDB Atlas, ensure your cluster is a replica set (M10+ for production, or use a free tier with transactions enabled in some cases). Use the connection string provided.

## Development

1. Install dependencies:
   ```bash
   npm install
   ```

2. Seed the database:
   ```bash
   npm run seed
   ```

3. Start the development server:
   ```bash
   npm run dev
   ```

Open [http://localhost:3000](http://localhost:3000) with your browser.
# stokr

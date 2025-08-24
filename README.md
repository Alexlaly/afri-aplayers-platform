# Afri Talent Platform — Starter (Next.js + Supabase + Stripe)

MVP skeleton for a **three-portal** platform:
- **Talent** (private): onboarding + profile + portfolio
- **Recruiter** (private): intake request (needs)
- **Staff** (private): triage + shortlist + proposals (no open marketplace)

## Quick start (Bolt.new / local)

1. Create a new Bolt.new project and **upload this ZIP**, or run locally:
   ```bash
   npm install
   npm run dev
   ```

2. Create a **Supabase** project. Copy `.env.example` to `.env.local` and fill in:
   - `NEXT_PUBLIC_SUPABASE_URL`
   - `NEXT_PUBLIC_SUPABASE_ANON_KEY`
   - `SUPABASE_SERVICE_ROLE` (server-side only)

3. In Supabase SQL Editor, copy `supabase/schema.sql` and run it.
   - This creates tables (profiles, talent_profiles, recruiter_orgs, intake_requests, shortlists, messages, etc.)
   - Enables **RLS** with policies to isolate Talent/Recruiter/Staff data.

4. (Optional) Set up **Stripe** (for deposit/fees). Fill in `STRIPE_SECRET_KEY` and `STRIPE_WEBHOOK_SECRET`.

5. Visit:
   - `/` Landing (links)
   - `/talent` (Talent portal)
   - `/recruiter` (Recruiter portal)
   - `/staff` (Staff portal)

## Notes
- Authentication: Supabase email/password (basic flows to be completed).
- RBAC & RLS: enforced mostly in DB policies; app-level guards are minimal scaffolds.
- API routes use server-side Supabase client with **service role** for Staff operations only.
- Extend forms & APIs to match your exact PRD logic.

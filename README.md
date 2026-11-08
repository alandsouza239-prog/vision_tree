# Vision Tree School — Premium Website v2

Premium responsive React + Vite website with Supabase backend integration.

## Run locally
1. Install Node.js (current LTS) and VS Code.
2. Extract this ZIP and open the folder in VS Code.
3. Run `npm install`.
4. Copy `.env.example` to `.env` (PowerShell: `Copy-Item .env.example .env`).
5. Run `npm run dev` and open the local URL shown by Vite (usually http://localhost:5173).

## Supabase setup
1. Create a project at https://supabase.com/.
2. Copy Project URL and anon/public key from Project Settings → API into `.env`:
   - `VITE_SUPABASE_URL`
   - `VITE_SUPABASE_ANON_KEY`
3. Run all SQL in `supabase/schema.sql` using Supabase SQL Editor.
4. Enable Email/password in Authentication → Providers.
5. Create an administrator in Authentication → Users.
6. Copy the user's UUID and run:
   `insert into public.profiles(id,full_name,role) values('AUTH-USER-UUID','School Administrator','admin');`
7. Open `/admin-login`. Admin console route: `/admin`.

Never put Supabase `service_role` key in frontend code. Only use the anon key.

## Included
- Public pages: Home, About, Vision & Mission, Leadership, Academics, Primary, Senior School, Campus Life, Facilities, Activities, Admissions, Events, Gallery, Mandatory Disclosure and Contact.
- Online admission enquiry form stored in Supabase.
- Admin sign-in and role check.
- Admin management for admission statuses, events, gallery items, disclosure links, student records, attendance and exam marks.
- Public pages show only published events, gallery items and disclosure documents.
- RLS policies restrict student, attendance, marks and admission records to administrators. Public visitors can submit an admission enquiry but cannot read enquiries.

## Before production launch
- Replace placeholder address, phone, email, history, staff details, school policies and academic information.
- Add the official school logo when supplied; the leaf mark is temporary.
- Verify current CISCE affiliation status and exact public wording with school management. Use official affiliation details/logo only when authorised.
- Verify current CISCE and applicable government mandatory disclosure requirements; publish actual approved documents, not placeholder content.
- Replace sample stock photos with school-owned/licensed images. Obtain guardian consent before publishing identifiable student photographs.
- Add a reviewed privacy notice, consent language, retention policy and grievance contact. Securely handle children's personal information under applicable Indian law.
- Add CAPTCHA/rate limiting, server-side validation, email notifications, audit logs, backups and MFA for staff before production.
- This starter admin interface does not include parent/student login, fee collection, bulk import/export, report cards or timetable. Attendance and results are admin-only; build a separate authenticated portal with guardian-student linking and row-level security if families need access.
- Gallery and disclosure records use URLs in this starter. For production, implement Supabase Storage uploads with restrictive policies.
- Run a security review before uploading real student records.

## Deploy
Run `npm run build`; deploy the generated `dist/` folder using Vercel or Netlify. Add the two VITE Supabase environment variables in the hosting dashboard. Connect the school's domain through the domain provider DNS settings.

# HobbyTown Louisville — Repair App (Production)

Internal repair-tracking app for HobbyTown Louisville. Replaces the paper clipboard.

## Live URL

(Filled in after GitHub Pages is enabled — typically `https://YOUR-USER.github.io/hobbytown-repair-app/`)

## Who can log in

Only staff with an account in the Supabase project. To add or remove a staff member:

1. Add their email to `auth.users` (Supabase dashboard → Authentication → Users → "Add user")
2. Insert a row in `staff_profiles` with `is_active = true` and `role = 'owner' | 'staff'`
3. They sign in via the magic-link form on the login page

To revoke access:

```sql
UPDATE staff_profiles SET is_active = false WHERE full_name = 'Name';
```

## How it works

- Frontend: a single `index.html` hosted on GitHub Pages (free)
- Backend: Supabase project `hobbytown-repairs` (Postgres + Auth + Edge Functions + Storage)
- Emails: Resend (signed waivers + pickup-ready notifications + daily overdue digest at 8 AM)

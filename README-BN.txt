# BD Taka Income 2K27 — live website starter

This is a deployable starter, not a live site yet. It includes:
- Responsive Bengali website
- Supabase email/password signup and login
- Public work listings
- Member applications
- Member earnings ledger (admin-entered only)
- Withdrawal requests (request record only)
- Admin-only task publishing

## Important safety and launch notes
1. Do not sell a package as a condition for getting work or promise guaranteed income.
2. Do not activate payments until you have a real service, published task/payment terms, refund/dispute process, privacy policy, and a merchant account approved by the payment provider.
3. This starter does not collect payments or automatically send money. Never put payment-provider secret keys in browser code.
4. Have a parent/guardian or other legally eligible adult own the domain, hosting, Supabase, and payment-provider accounts if you are under 18. Never share passwords, OTPs, PINs, or secret keys in chat.
5. Ask a Bangladesh-qualified legal/accounting professional to review the business and data/privacy requirements before public launch.

## Step 1 — Create a Supabase project
- An eligible adult should create a project at https://supabase.com/
- Open SQL Editor and run `supabase-schema.sql`.
- In Project Settings > API, copy the Project URL and anon/public key.
- Open `index.html`; replace `PASTE_SUPABASE_PROJECT_URL` and `PASTE_SUPABASE_ANON_KEY`.
- Do not use a service_role key in this file.

## Step 2 — Set the site owner as admin
- Create the owner's account using the website signup.
- In Supabase > Authentication > Users, copy that account's user UUID.
- In SQL Editor, run:
  `update public.profiles set role='admin' where id='YOUR-AUTH-USER-UUID';`
- Never make a public signup form that lets people choose admin.

## Step 3 — Publish the website
Easy static hosting options include Netlify or Cloudflare Pages. An eligible adult should create the hosting account and upload the `index.html` file (or connect a private Git repository). Add your own domain after purchasing it from a reputable registrar. Hosting provider steps and prices can change; check their current official documentation.
- Netlify: https://docs.netlify.com/
- Cloudflare Pages: https://developers.cloudflare.com/pages/
- Domain registrar examples: https://porkbun.com/ or https://www.cloudflare.com/products/registrar/

## Step 4 — Configure Supabase Auth URLs
In Supabase Authentication URL Configuration:
- Site URL: your final HTTPS domain
- Add your domain and local preview URL to Redirect URLs as needed.
Enable email confirmation and configure SMTP for production email delivery.

## Before public launch
- Replace sample/empty content with real work descriptions, deadlines, eligibility, review process, and agreed pay.
- Add Privacy Policy, Terms, Refund/Dispute Policy, contact details, and complaint process.
- Add rate limiting, bot protection, backups, monitoring, and admin audit logs.
- Build a separate trusted server-side integration for any payment gateway after merchant approval. Never handle bKash/Nagad PIN/OTP or card details yourself.
- Test signup, login, RLS permissions, task application, admin access, and withdrawal workflow with test accounts.

````markdown
# Full‑Stack AI Finance Manager

A modern personal finance manager built with Next.js, Prisma, Tailwind CSS, Shadcn UI, Clerk, Inngest, Resend, and ArcJet. Automate your budgeting, get AI‑powered insights, scan receipts, and trigger email alerts—all in one place.

---

## 🚀 Features

- **User Authentication** via [Clerk](https://clerk.com)  
- **Transactional Database** with Prisma & PostgreSQL  
- **Styled UI** with Tailwind CSS 4 + [shadcn/ui](https://ui.shadcn.com)  
- **Serverless Workflows** using [Inngest](https://inngest.com) (alerts, recurring txns, reports)  
- **Automated Emails** powered by [Resend](https://resend.com) (budget alerts, monthly summaries)  
- **AI‑Powered Analytics** via [ArcJet](https://github.com/arcjet/next) & Google Generative AI  
- **Receipt Scanning** with built‑in OCR for automatic expense entry  
- **Interactive Charts** using Recharts & ArcJet components  

---

## 🛠️ Tech Stack

| Layer           | Tech                           |
|-----------------|--------------------------------|
| **Framework**   | Next.js (v15)                  |
| **Styling**     | Tailwind CSS 4 + shadcn/ui     |
| **Auth**        | Clerk                          |
| **Database**    | Prisma + PostgreSQL            |
| **Workflows**   | Inngest                        |
| **Email**       | Resend                         |
| **AI Insights** | ArcJet + Google GenAI          |
| **Charts**      | Recharts                       |
| **OCR/Scan**    | Custom Receipt Scanner         |

---

## ⚙️ Setup & Installation

Follow these commands to get started:

```bash
# 1. Clone & install
git clone https://github.com/<you>/<repo>.git
cd <repo>
npm install

# 2. Create .env.local
cat <<EOF > .env.local
DATABASE_URL=postgresql://user:pass@host:port/dbname
DIRECT_URL=<optional direct DB URL>

# Clerk (Auth)
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=
CLERK_SECRET_KEY=
NEXT_PUBLIC_CLERK_SIGN_IN_URL=/sign-in
NEXT_PUBLIC_CLERK_SIGN_UP_URL=/sign-up
NEXT_PUBLIC_CLERK_AFTER_SIGN_IN_URL=/onboarding
NEXT_PUBLIC_CLERK_AFTER_SIGN_UP_URL=/onboarding

# Google Generative AI (ArcJet)
GEMINI_API_KEY=
ARCJET_KEY=

# Email (Resend)
RESEND_API_KEY=
EOF

# 3. Prisma migrations and client
npx prisma migrate deploy   # run migrations
npx prisma generate         # generate client

# 4. Run Dev Servers
npm run dev          # Next.js
npx inngest-cli dev  # Inngest CLI

# 5. Open Prisma Studio
npx prisma studio
````

---

## 📧 Email Workflows

* **Budget Alerts**: Users get an email when spending > 80% of budget
* **Monthly Reports**: Auto‑scheduled via Inngest cron — sends detailed AI‑powered summary
* **Templates** built with `@react-email/components`

---

## 🔄 Inngest Functions

```text
triggerRecurringTransactions   # Daily cron → sends transaction.recurring.process events
processRecurringTransaction    # Creates new txns & updates balances
checkBudgetAlerts              # Monitors budget usage & fires email alerts
generateMonthlyReports         # Runs on 1st of month, fires summary emails
```

---

## 🚢 Deployment

1. **Push to GitHub** → Vercel auto‑deploys
2. **Add Env Vars** in Vercel Settings (match `.env.local`)
3. **Ensure Inngest Webhook** at `/api/inngest` is live

---



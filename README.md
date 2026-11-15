# 🔐 Next.js + Better Auth + Prisma

**A modern, type-safe full-stack authentication starter powered by Next.js App Router, Better Auth, Prisma ORM, PostgreSQL, and Bun.**

[![Next.js](https://img.shields.io/badge/Next.js-App_Router-black?style=for-the-badge&logo=next.js)](https://nextjs.org/)
[![Better Auth](https://img.shields.io/badge/Better_Auth-1.x-10B981?style=for-the-badge)](https://www.better-auth.com/)
[![Prisma](https://img.shields.io/badge/Prisma-6_Stable-2D3748?style=for-the-badge&logo=prisma)](https://www.prisma.io/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Database-316192?style=for-the-badge&logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![Bun](https://img.shields.io/badge/Bun-Runtime-FBF0DF?style=for-the-badge&logo=bun&logoColor=black)](https://bun.sh/)

---

## ✨ Features

- **Full-Stack Authentication:** Email & password sign-up, sign-in, session management, and sign-out out of the box.
- **Database-Backed Sessions:** Persistent `user`, `session`, `account`, and `verification` tables managed in PostgreSQL via Prisma ORM.
- **End-to-End Type Safety:** Typed database queries with Prisma Client and typed React session hooks (`useSession`) via `better-auth/react`.
- **Modern SaaS UI:** Split-screen dark-mode authentication interface built with Tailwind CSS v4.
- **Bun Optimized:** Fast package management, script execution, and dev server startup.

---

## 🗂️ Project Structure

```text
├── app/
│   ├── api/
│   │   └── auth/
│   │       └── [...all]/
│   │           └── route.ts      # Better Auth catch-all API handler
│   ├── globals.css               # Tailwind CSS v4 base styles
│   ├── layout.tsx                # Root Next.js layout
│   └── page.tsx                  # Split-screen SaaS Sign-In / Sign-Up & Dashboard
├── lib/
│   ├── auth.ts                   # Server-side Better Auth instance & Prisma adapter
│   ├── auth-client.ts            # Client-side auth hooks (signIn, signUp, useSession)
│   └── prisma.ts                 # Global Prisma Client singleton
├── prisma/
│   └── schema.prisma             # PostgreSQL schema & Better Auth models
├── next.config.ts                # Configured with serverExternalPackages for Prisma
└── .env                          # Environment variables (not committed)
```

# 🚀 Getting Started

## 1. Prerequisites
Make sure you have the following installed locally:
- Bun (v1.1+)
- PostgreSQL running locally or via a cloud provider (e.g., Neon, Supabase, Railway)

## 2. Clone & Install Dependencies
Bash
- git clone 
- cd betterauth-prisma-nextjs-postgre
- bun install

## 3. Configure Environment Variables
Create a .env file in the root directory and add your PostgreSQL connection string and Better Auth secrets:

```
DATABASE_URL="postgresql://username:password@localhost:1234/betterauth?schema=public"
BETTER_AUTH_SECRET="openssl_rand_base64_32"
BETTER_AUTH_URL="http://localhost:3000"
```

💡 Tip: Generate a secure BETTER_AUTH_SECRET via terminal:

Bash 
```
openssl rand -base64 32
```

## 4. Run Database Migrations & Generate Client
Push the Better Auth schema to PostgreSQL and generate the Prisma Client:

Bash
```
bunx prisma migrate dev --name init-auth
bunx prisma generate
```

## 5. Start the Development Server
Bash
```
bun dev
```
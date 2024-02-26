Time= 34.38 - 1.02.24 - 1.18.55 - 1.32

create project
imaginify =>
npx create-next-app@latest ./
Typescrip - yes
Eslint - yes
Tailwindcss- yes
src - no
app router - yes
alias import - no

npx shadcn-ui@latest init
Which style - Default
base color? - Slate
Would you like to use CSS variables ? - yes

npm run dev

# Clerk setup

go to clerk.com
login google.com

Let's build your <SignIn>
Application name - Sky_Imaginity

How will your users sign in?

Email address - select
Google - select
GitHub - select

Create Application

go to Home

API Keys

copy and past .env.local file

```
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=pk_test_ZmVhc2libGUtZ29hdC00OS5jbGVyay5hY2NvdW50cy5kZXYk
CLERK_SECRET_KEY=sk_test_VCS3f7xOS6fvQAjfiv8f4J7ghuh9gxkyFszvkehdoT
```

go to Configure =>
User & Authentication =>
Email, Phone, Username

Apply Changes

go to Home

continue with docs - click

Install

npm install @clerk/nextjs

Add <ClerkProvider> to your app

layout.tsx

```import { ClerkProvider } from "@clerk/nextjs";

<ClerkProvider>
  <html>

  </html>
</ClerkProvider>

```

Add authentication to your app
Now that Clerk is installed and mounted in your application, you can decide which pages are public and which should require authentication to access:

Create a middleware.ts file at the root of your project, or in your src/ directory if you have one.
In your middleware.ts, export Clerk's authMiddleware(opens in a new tab) helper:

middleware.ts

```
import { authMiddleware } from "@clerk/nextjs";

export default authMiddleware({});

```

go to Customization =>
Branding =>
Logo
upload image

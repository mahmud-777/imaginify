Time= 34.38 - 1.02.24 - 1.18.55 - 1.32 - 2.16 - 2.24 - 2.45 - 3.09 -3.23 - 3.34 3.47 - 3.58 - 4.06 - 4.27 profile page -

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

# Cloudinary setup

cloudinary.com
login

# Set Up Your Work Environment

npm i next-cloudinary

View Credentials = click
Cloud name
API key
API secret
copy and past to .env.local

Settings => Upload => Add upload preset
=> Storage and Access =>
Upload preset name = sky_imaginify
Signin Mode: unsigned
Folder = imaginify

=> Media analysis and AI =>
Categorization =>
Google Auto Tagging = checked

Auto tagging 0.51

Save = click

=> dashboard => Add-ons
Cloudinary AI Background Removal = Free plan
Google Auto Tagging = Free plan

# Edit next.config.mjs

```
const nextConfig = {
  images: {
    remotePatterns: [
      {
        protocol: 'https',
        hostname: 'res.cloudinary.com',
        port: '',
      }
    ]
  }
}
```

# Stripe.com => login

Developers => API keys
Publishable key -
Secret key -

open .env file and past

```

# Strip
NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY=pk_test_cbiaRw48m7yvm796C2qV3mjf
STRIPE_SECRET_KEY=sk_test_YG0WuNV1DCyZYuNt8XRDT8Lc

```

npm install stripe @stripe/stripe-js

lib => actions => transaction.action.ts

```
export async function checkoutCredits(transaction: CheckoutTransactionParams) {}

export async function createTransaction(transaction: CreateTransactionParams) {}
```

dashboard.stripe.com =>
Developers => Webhooks => Add an endpoint =>

Endpoint URL = https://imaginify-lac.vercel.app/api/webhooks/stripe

Listen to - Events on your account - checked

Select events to listen to = + Select event =>
Select events to send =>
checkout.session.completed = checked

Add events =>

Add endpoint

copy Signing secret and past to .env file

```
STRIPE_WEBHOOK_SECRET=whsec_wYHvsQLjvLejiudjxKeWYhYr5LxBbC5A
```

app => api => webhooks => stripe => route.ts

```

```

app => (root) => credits => page.tsx

```

```

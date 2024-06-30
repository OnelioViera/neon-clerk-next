# Next.js authentication using Clerk, Drizzle ORM, and Neon
Learn how to build a Next.js application that uses Clerk for authentication and Neon's Serverless Postgres with Drizzle ORM to store data.

## Sign Up to Neon and Configure Postgres
1. Enter a project name.
2. Use the default database name of `neondb`.
3. Choose the region closest to the location where your application will be deployed.
4. Click the Create Project button.

You’ll instantly be provided with a connection string you can use to connect to your serverless Postgres database.

![alt text](./public/images/neon-dashboard.jpg)

## Sign Up to Clerk and Configure Application Sign In

Visit dashboard.clerk.com and sign up, or sign in if you’re an existing user. Create a new application and enable some of the available sign-in options.

![alt text](./public/images/clerk-sign-up.jpg)

Once the application has been created on Clerk, you’ll find your API keys on the Home screen of your application in the Clerk dashboard. Specifically, you’ll need the API keys listed in the Next.js section soon!

## Using Neon’s Serverless Driver with Next.js and Drizzle ORM

#### Create a Next.js Project and Install Dependencies

Create a Next.js application in your development environment. This requires Node.js v18 or newer to be installed in your development environment. This article assumes you use the following options when creating your Next.js application using create-next-app.

npx create-next-app@14.1 neon-clerk-next \
--typescript \
--eslint \
--tailwind \
--use-npm \
--app \
--src-dir \
--import-alias "@/*"
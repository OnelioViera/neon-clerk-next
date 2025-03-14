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
```
npx create-next-app@14.1 neon-clerk-next
--typescript \
--eslint \
--tailwind \
--use-npm \
--app \
--src-dir \
--import-alias "@/*"
```

Once your Next.js application has been created, change to the project directory in your terminal, then add the Neon serverless driver and Drizzle ORM to your project’s dependencies using npm or your preferred package manager.

`npm install @neondatabase/serverless drizzle-orm`

### Create a Schema and Database Connection

Create a file named src/app/db/schema.ts and define a user_messages schema using the types provided by Drizzle ORM.

![alt text](./public/images/schema.jpg)

To use Neon’s serverless driver with Drizzle ORM, create a file named src/app/db/index.ts and add the following code. Exporting the Drizzle instance from a file means it’s created on application startup and exported as a singleton that other modules can import and reuse to execute typesafe SQL queries against your Postgres database hosted by Neon.

![alt text](./public/images/index.ts.jpg)

Next, create a file named .env.local in the root of the Next.js project directory and add your database URL from the Neon Console as an environment variable named DATABASE_URL.

```
# Copy this from your project dashboard on https://console.neon.tech
DATABASE_URL=postgresql://user:pass@ep-adj-noun-12345.us-east-2.aws.neon.tech/mydatabase?sslmode=require
```

### Start your Application

Use the npm run dev command to start your Next.js application in development mode and confirm it’s available at http://localhost:3000. You won’t be prompted to authenticate since you haven’t added the Clerk middleware to your application yet – you’ll take care of that soon.
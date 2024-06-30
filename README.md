## Next.js authentication using Clerk, Drizzle ORM, and Neon
Learn how to build a Next.js application that uses Clerk for authentication and Neon's Serverless Postgres with Drizzle ORM to store data.

### Sign Up to Neon and Configure Postgres
1. Enter a project name.
2. Use the default database name of `neondb`.
3. Choose the region closest to the location where your application will be deployed.
4. Click the Create Project button.

You’ll instantly be provided with a connection string you can use to connect to your serverless Postgres database.

![alt text](./public/images/neon-dashboard.jpg)

### Sign Up to Clerk and Configure Application Sign In

Visit dashboard.clerk.com and sign up, or sign in if you’re an existing user. Create a new application and enable some of the available sign-in options. You can see that I’ve enabled Discord and Google as sign-in options for my application.

![alt text](./public/images/clerk-sign-up.jpg)
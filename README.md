# Stockly Backend Beginner Files
## Files Included

### `utils/auth.ts`

This is the main authentication helper file.

It shows how a backend can:

- create a JWT token after login
- verify a JWT token from cookies
- find the logged-in user from the database
- hash passwords before saving them
- compare a plain password with a hashed password during login

This is a good beginner file for understanding how login sessions work in a real app.

### `lib/auth-server.ts`

This is a small server-only helper.

It reads cookies inside a Next.js App Router server component and reuses `getSessionFromRequest` from `utils/auth.ts`.

In simple words, it answers this question:

> Who is the current logged-in user on the server?

### `app/api/auth/session/route.ts`

This is a backend API route.

When the frontend calls `GET /api/auth/session`, this route checks the session cookie, verifies the user, and returns safe user data such as:

- id
- name
- email
- profile image
- role
- timestamps

It does not return sensitive data like passwords.

### `prisma/client.ts`

This file creates the Prisma database client.

Prisma is the layer used by Stockly to talk to MongoDB. This file uses a singleton pattern so the app does not create too many database connections during development hot reloads.

This is useful for learning how backend code connects to a database in a Next.js app.

### `lib/validations/auth.ts`

This file uses Zod to define validation rules for login and registration.

It checks things like:

- name is required
- email must be valid
- password must have a minimum length

This is a good example of keeping validation logic in one clean reusable file.

## Beginner Backend Concepts Shown

- JWT authentication
- password hashing with bcrypt
- reading cookies on the server
- protecting API routes
- returning safe user data
- connecting to a database with Prisma
- validating input with Zod

## Note

These files are copied as learning examples from a larger project. They are not a complete runnable backend by themselves because they depend on the full Stockly project structure, Prisma schema, aliases, and environment variables.

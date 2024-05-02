# The stack
### We’ll be building medium in the following stack
- React in the frontend
- Cloudflare workers in the backend
- zod as the validation library, type inference for the frontend types
- Typescript as the language
- Prisma as the ORM, with connection pooling
- Postgres as the database
- jwt for authentication
 

 # Initialize the backend
> npm create hono@latest
- Target directory -› backend
- Which template do you want to use? -> cloudflare-workers
- Do you want to install project dependencies? … yes
- Which package manager do you want to use? -› npm


# Initialize DB (prisma)
- Get your connection url from neon.db or aieven.tech
> postgres://avnadmin:password@host/db

- Get connection pool URL from Prisma accelerate
https://www.prisma.io/data-platform/accelerate

> prisma://accelerate.prisma-data.net/?api_key=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhcGlfa2V5IjoiNTM2M2U5ZjEtNmNjMS00MWNkLWJiZTctN2U4NzFmMGFhZjJmIiwidGVuYW50X2lkIjoiY2I5OTE2NDk0MzFkNWZmZWRmNmFiYzViMGFlOTIwYzFhZDRjMGY5MTg1ZjZiNDY0OTc3MzgyN2IyMzY2OWIwMiIsImludGVybmFsX3NlY3JldCI6Ijc0NjE4YWY2LTA4NmItNDM0OC04MzIxLWMyMmY2NDEwOTExNyJ9.HXnE3vZjf8YH71uOollsvrV-TSe41770FPG_O8IaVgs

- Initialize prisma in your project

> npm i prisma 
> npx prisma init

- Replace DATABASE_URL in .env

> DATABASE_URL="postgres://avnadmin:password@host/db"

- Add DATABASE_URL as the connection pool url in wrangler.toml

> name = "backend"
compatibility_date = "2023-12-01"

> DATABASE_URL = "prisma://accelerate.prisma-data.net/?api_key=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhcGlfa2V5IjoiNTM2M2U5ZjEtNmNjMS00MWNkLWJiZTctN2U4NzFmMGFhZjJmIiwidGVuYW50X2lkIjoiY2I5OTE2NDk0MzFkNWZmZWRmNmFiYzViMGFlOTIwYzFhZDRjMGY5MTg1ZjZiNDY0OTc3MzgyN2IyMzY2OWIwMiIsImludGVybmFsX3NlY3JldCI6Ijc0NjE4YWY2LTA4NmItNDM0OC04MzIxLWMyMmY2NDEwOTExNyJ9.HXnE3vZjf8YH71uOollsvrV-TSe41770FPG_O8IaVgs"
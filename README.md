# vercel-postgres-prisma-serverless-cloud-database

# 🚀 Vercel Postgres + Prisma Next.js Starter - Simple Next.js template that uses Vercel Postgres as the database and Prisma as the ORM. 🚀

https://github.com/coding-to-music/vercel-postgres-prisma-serverless-cloud-database

From / By https://github.com/vercel/examples/tree/main/storage/postgres-prisma

https://github.com/coding-to-music/grafana-cloud-docker-postgres-integration

https://github.com/vercel/examples/issues/697

## Environment variables:

```java

```

## user interfaces:

- APP
- Prisma Studio

## GitHub

```java
git init
git add .
git remote remove origin
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:coding-to-music/vercel-postgres-prisma-serverless-cloud-database.git
git push -u origin main
```

## Running

```

yarn install
yarn build
yarn start
yarn seed:pets
yarn seed:simulation
yarn seed:streets
yarn seed:ev_locations
```

---

- name: Vercel Postgres + Prisma Next.js Starter
- slug: postgres-prisma
- description: Simple Next.js template that uses Vercel Postgres as the database and Prisma as the ORM.
- framework: Next.js
- useCase: Starter
- css: Tailwind
- database: Vercel Postgres
- [deployUrl](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Fvercel%2Fexamples%2Ftree%2Fmain%2Fstorage%2Fpostgres-prisma&project-name=postgres-prisma&repository-name=postgres-prisma&demo-title=Vercel%20Postgres%20%2B%20Prisma%20Next.js%20Starter&demo-description=Simple%20Next.js%20template%20that%20uses%20Vercel%20Postgres%20as%20the%20database%20and%20Prisma%20as%20the%20ORM.&demo-url=https%3A%2F%2Fpostgres-prisma.vercel.app%2F&demo-image=https%3A%2F%2Fpostgres-prisma.vercel.app%2Fopengraph-image.png&stores=%5B%7B"type"%3A"postgres"%7D%5D)

- demoUrl: https://postgres-prisma.vercel.app/
- relatedTemplates:

- postgres-starter
- postgres-kysely
- postgres-sveltekit

---

# Vercel Postgres + Prisma Next.js Starter

Simple Next.js template that uses [Vercel Postgres](https://vercel.com/postgres) as the database and [Prisma](https://prisma.io/) as the ORM.

## Demo

https://postgres-prisma.vercel.app/

## How to Use

You can choose from one of the following two methods to use this repository:

### One-Click Deploy

Deploy the example using [Vercel](https://vercel.com?utm_source=github&utm_medium=readme&utm_campaign=vercel-examples):

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Fvercel%2Fexamples%2Ftree%2Fmain%2Fstorage%2Fpostgres-prisma&project-name=postgres-prisma&repository-name=postgres-prisma&demo-title=Vercel%20Postgres%20%2B%20Prisma%20Next.js%20Starter&demo-description=Simple%20Next.js%20template%20that%20uses%20Vercel%20Postgres%20as%20the%20database%20and%20Prisma%20as%20the%20ORM.&demo-url=https%3A%2F%2Fpostgres-prisma.vercel.app%2F&demo-image=https%3A%2F%2Fpostgres-prisma.vercel.app%2Fopengraph-image.png&stores=%5B%7B"type"%3A"postgres"%7D%5D)

### Clone and Deploy

Execute [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app) with [pnpm](https://pnpm.io/installation) to bootstrap the example:

```bash
pnpm create next-app --example https://github.com/vercel/examples/tree/main/storage/postgres-prisma
```

Once that's done, copy the .env.example file in this directory to .env.local (which will be ignored by Git):

```bash
cp .env.example .env.local
```

Then open `.env.local` and set the environment variables to match the ones in your Vercel Storage Dashboard.

Next, run Next.js in development mode:

```bash
pnpm dev
```

Deploy it to the cloud with [Vercel](https://vercel.com/new?utm_source=github&utm_medium=readme&utm_campaign=vercel-examples) ([Documentation](https://nextjs.org/docs/deployment)).

## Install psql

```bash
sudo apt install postgresql
```

## Console-generated psql connection example in postgres-prisma-postgres does not work, possible solution is provided here

https://github.com/vercel/examples/issues/697

The Suggested psql connection example in postgres-prisma-postgres does not work:

```bash
# Format:
psql "postgresql://username:password@host:port/database"

# Example provided by the console:
psql "postgres://default:************@<endpoint>.us-east-1.postgres.vercel-storage.com:5432/verceldb"
```

It gives this error:

```bash
psql: error: ERROR:  Endpoint ID is not specified. Either please upgrade the postgres client library (libpq) for SNI support or pass the endpoint ID (first part of the domain name) as a parameter: '?options=project%3D<endpoint-id>'. See more at https://neon.tech/sni
ERROR:  connection is insecure (try using `sslmode=require`)
```

However, this connection string does work, by appending the `?options=project%3endpoint`:

```bash
# Format:
psql "postgresql://username:password@host:port/database?options=project%3D<endpoint>"


# Example:
psql "postgres://default:************@<endpoint>.us-east-1.postgres.vercel-storage.com:5432/verceldb?options=project%3D<endpoint>"
```

Output:

```bash
psql (12.14 (Ubuntu 12.14-0ubuntu0.20.04.1), server 15.2)
WARNING: psql major version 12, server major version 15.
         Some psql features might not work.
SSL connection (protocol: TLSv1.3, cipher: TLS_AES_256_GCM_SHA384, bits: 256, compression: off)
Type "help" for help.

verceldb=> \dt
        List of relations
 Schema | Name  | Type  |  Owner
--------+-------+-------+---------
 public | users | table | default
(1 row)
```

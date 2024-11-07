# Working with AWS Lambdas

A basic example of a lambda using a singleton drizzle ORM instance.

Example infrastructure uses:

- MySQL Database
- Typescript

Typescript Dependencies:

- "drizzle-orm": "^0.36.0"
- "mysql2": "^3.11.4"
- "dotenv": "^16.4.5"

## Setting up a schema

```ts
import { sql } from 'drizzle-orm';
import { int, mysqlSchema, varchar } from "drizzle-orm/mysql-core"

export const mainSchema = mysqlSchema('main');

export const usersTable = mainSchema.table('users', {
    id: int('id').primaryKey().autoIncrement(),
    emailAddress: varchar('email_address', {length:255}).unique()
});
```

## Setting up the client

Notes

- dotenv used to keep secrets from code
  - alternatively, use secrets manager

```ts
import * as dotenv from 'dotenv';
import { drizzle } from 'drizzle-orm/mysql2';
import { createPool, PoolOptions } from 'mysql2';
import * as schema from './schema';

dotenv.config();

export const initDrizzleContext = async () => {
    const poolOptions = fetchConnectionSecrets();
    const pool = createPool(poolOptions);

    const db = drizzle(pool, {mode: 'default', schema});

    console.debug(`⚙️ Connection established to ${poolOptions.host}`);
    return db;    
}

function fetchConnectionSecrets(): PoolOptions {
    return {
        host: process.env.DATABASE_HOST,
        port: Number(process.env.DATABASE_PORT),
        database: process.env.DATABASE_DATABASE,
        user: process.env.DATABASE_USER,
        password: process.env.DATABASE_PASSWORD,
    }
}
```


## Setting up the handler

```ts
import { MySql2Database } from "drizzle-orm/mysql2";

// create a singletion between invocations
//  to recycle db connections
let db: MySql2Database;

export async function handler(emailAddress: string) {
    db = db ?? await initDrizzleContext();

    if(!isValid(emailAddress)) {...}

    const results = await db
        .select()
        .from(usersTable)
        .where(eq(usersTable.emailAddress,emailAddress));

    return results;
}
# Working With BigInt

## Setup

`bigint` requires a configuration mode

```typescript
import { bigint, mysqlSchema } from "drizzle-orm/mysql-core"

export const mySchema = mysqlSchema('myDatabaseSchema');

export const things = mySchema.table('things', {
    id: bigint('id', {mode: 'bigint'}).primaryKey().autoincrement()
});
```

1. The bigint mode is required to prevent a type error

## Query

Requires `n` affix for bigint value queries

```typescript

const poolConnection = mysql.createPool({...});

const db = drizzle({client: poolConnection});

export async function myFunction() {
    const results = db
        .select()
        .from(myTable)
        .where(eq(myTable.id, 1n))
}

```
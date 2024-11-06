# BigInt Datatype Configuration

`bigint` requires a configuration mode

```typescript
import { bigint, mysqlSchema } from "drizzle-orm/mysql-core"

export const mySchema = mysqlSchema('myDatabaseSchema');

export const things = mySchema.table('things', {
    id: bigint('id', {mode: 'bigint'}).primaryKey().autoincrement()
});
```

1. The bigint mode is required to prevent a type error
# Working with Datetime

## Setting a date column with defaultNow()

```typescript
import { sql } from 'drizzle-orm';
import { mysqlTable, serial, timestamp } from 'drizzle-orm/mysql-core';
export const users = mysqlTable('users', {
  id: serial('id').primaryKey(),
  timestamp1: timestamp('timestamp1').notNull().defaultNow(),
  timestamp2: timestamp('timestamp2', { mode: 'string' })
    .notNull()
    .default(sql`now()`),
  timestamp3: timestamp('timestamp3', { fsp: 3 }) // fractional seconds part
    .notNull()
    .default(sql`now(3)`),
});
```
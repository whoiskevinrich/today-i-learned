# Paginated Async Iterators

Paginated async iterators in AWS SDK for JavaScript v3 provide a convenient way to handle paginated API responses using modern async iteration syntax. Instead of manually managing pagination tokens and making repeated API calls, you can use these iterators to seamlessly loop through all results as if they were a single collection.

**Benefits:**
- Simplifies code for handling paginated responses.
- Reduces boilerplate and potential for errors.
- Integrates naturally with `for await...of` syntax for asynchronous iteration.

**When to use:**
Use paginated async iterators when working with AWS SDK v3 commands that return paginated results (e.g., listing resources like tables, objects, users, etc.), especially when you want to process all items across multiple pages without manual pagination logic.

```js
const client = new DynamoDBClient({});
cosnt paginator = paginateListTables({ client }, {});

const tableNames = [];
for await (const page of paginator) {
    // page contains a single paginated output or may be null.
    tableNames.push(...page.TableNames ?? []);
}
```
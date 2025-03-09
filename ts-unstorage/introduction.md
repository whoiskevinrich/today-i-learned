# unstorage: Universal Key-Value

Unified key-value storage API with conventional features and many built-in drives.

## Resources

-   https://unstorage.unjs.io/
-   [Getting Started](https://unstorage.unjs.io/guide)
-   [GitHub](https://github.com/unjs/unstorage)

##

`npm i unstorage`

```ts
import { createStorage } from 'unstorage';

const storage = createStorage(/* opts */);

await storage.getItem('foo:bar');
// or storage.getItem('/foo/bar')
```

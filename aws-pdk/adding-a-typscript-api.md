## Adding a TypeScript API

Update `.progenrc.yaml` to include the following:

```ts
const api = new TypeSafeApiProject({
    parent: project,
    name: 'bookshelf-api',
    outdir: 'packages/bookshelf-api',
    infrastructure: {
        language: Language.TYPESCRIPT,
    },
    model: {
        language: ModelLanguage.OPENAPI,
        options: {
            openapi: {
                title: 'Bookshelf API',
            },
        },
    },
    runtime: {
        languages: [Language.TYPESCRIPT],
    },
    documentation: {
        formats: [DocumentationFormat.HTML_REDOC, DocumentationFormat.MARKDOWN],
    },
    library: {
        libraries: [Library.TYPESCRIPT_REACT_QUERY_HOOKS],
    },
    handlers: {
        languages: [Language.TYPESCRIPT],
    },
});
```

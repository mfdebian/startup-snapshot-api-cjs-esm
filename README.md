### CJS to ESM example

When trying to run [this](https://nodejs.org/api/v8.html#startup-snapshot-api)
example from the docs.

For the CJS version it runs fine, but I can't run the ESM version.

### Error
The error I'm getting is:

```bash
import fs from 'node:fs';
^^^^^^

SyntaxError: Cannot use import statement outside a module
    at minimalRunCjs (node:internal/main/mksnapshot:209:16)
```

Steps to reproduce:

`$ cd esm/`

`$ node --snapshot-blob snapshot.blob --build-snapshot entry.js`

### Expected behaviour

For the CJS version it works as expected, steps:

`$ cd cjs/`

`$ node --snapshot-blob snapshot.blob --build-snapshot entry.js`

The above command creates the `snapshot.blob` file.

See the contents of [`book1.en_US.txt`](./cjs/book1.en_US.txt):

`$ BOOK_LANG=en_US node --snapshot-blob snapshot.blob book1`

Output:

`> US`

See the contents of [`book1.es_ES.txt`](./cjs/book1.es_ES.txt):

`$ BOOK_LANG=es_ES node --snapshot-blob snapshot.blob book1`

Output:

`> ES`

See the contents of [`book2.zh_CN.txt`](./cjs/book2.zh_CN.txt):

`$ BOOK_LANG=zh_CN node --snapshot-blob snapshot.blob book2`

Output:

`> CN`

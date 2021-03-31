# wds-import-bug

wds is unable to resolve imports that use `exports` in node when importing from an `.ts` file.

## Actual behavior

The following import will resolve into `/node_modules/nodemod/dist/lib/prismjs.ts` instead.

```ts
// src/main.ts
import { highlight } from 'nodemod/dist/lib/prismjs.js';
```

## Actual behavior

The following import should resolve into `/node_modules/nodemod/dist/lib/prismjs.js`.

```ts
// src/main.ts
import { highlight } from 'nodemod/dist/lib/prismjs.js';
```

## How to run

1. Run `npm start`
2. Visit `localhost:8000` with Dev Tools open
3. Inspect network tab on the resources
   1. Notice how `nodemod/dist/lib/prismjs.js` gets resolved using `.ts` instead of `.js`
   2. `main2.js` demonstrates how the import works correctly
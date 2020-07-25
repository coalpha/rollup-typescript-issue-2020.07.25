# rollup-typescript-issue

This issue makes no sense.

### Repro:

- Clone this
- `npm i`
- `npm run build` or `npx rollup -c`

You should read [rollup.config.js](./rollup.config.js) to make sure there's
nothing bad in there first, though.

It looks like it works without the `tsconfig.json` but that's silly.
What could be in there that causes typescript to fail?

```
> rollup -c


src/main.ts → dist/main.ts...
(node:612) ExperimentalWarning: Conditional exports is an experimental feature. This feature could change at any time
[!] Error: Unexpected token (Note that you need plugins to import files that are not JavaScript)
src\main.ts (1:11)
1: const hello: string = "hello world";
              ^
2: console.log(hello);
```

### Fix:

Alright looks like I found the culprit.

It was `"outDir": "dist"` under `compilerOptions` in `tsconfig.json`.

This issue **still** makes no sense but I've solved it.

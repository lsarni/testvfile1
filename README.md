# How this project was created

1. `yarn create expo-app testvfile1`
2. Replace `expo start --ios` with `expo run:ios` on [package.json](./package.json)
3. Replace `expo start --android` with `expo run:android` on [package.json](./package.json)
4. Add `"vfile": "^6.0.0"` to the dependencies
5. Add `import { VFile } from "vfile";` to [App.js](./App.js)

If you run the project before doing step 4 and 5 the problem is not present.

# How to run this project

1. `yarn install`
2. `yarn ios` or `yarn android`

# Problem

```
iOS/Android Bundling failed 2108ms (node_modules/expo/AppEntry.js)
Unable to resolve "vfile/do-not-use-conditional-minpath" from "node_modules/vfile/lib/index.js"
```

The bundling can't deal with [this change on vfile](https://github.com/vfile/vfile/commit/f72469b5412c2e2e8480993b2e4a7c2e1530c80f) added on version 6.0.0

If you run the project before doing step 4 and 5 the problem is not present.
If you change the dependency to `"vfile": "^5.0.0"` the problem is not present.

There's [this discussion about a similar problem](https://github.com/orgs/vfile/discussions/88) on the vfile repo, but the problem itself is not on that package but on how expo bundles it.

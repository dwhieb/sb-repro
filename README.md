# Steps to Reproduce

1. Start with a fresh Storybook repro build (`npx sb@next repro`).
2. Add a `.browserslistrc` file with the following targets:

```
last 2 Chrome versions
last 2 Edge versions
last 2 Firefox versions
last 2 iOS versions
last 2 Safari versions
```

3. Adjust one of the components to use the [nullish coalescing operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Nullish_coalescing_operator).
4. Attempt to build Storybook (`yarn storybook`).
5. Watch the build fail:

```
ModuleParseError: Module parse failed: Unexpected token (11:12)
File was processed with these loaders:
 * ./node_modules/babel-loader/lib/index.js
You may need an additional loader to handle the result of these loaders.
|       onClick = _ref.onClick;
|   var btn = document.createElement('button');
>   btn.type ??= 'button';
|   btn.innerText = label;
|   btn.addEventListener('click', onClick);
    at handleParseError (/mnt/c/Users/dwhie/DLx/sb/node_modules/webpack/lib/NormalModule.js:469:19)
    at /mnt/c/Users/dwhie/DLx/sb/node_modules/webpack/lib/NormalModule.js:503:5
    at /mnt/c/Users/dwhie/DLx/sb/node_modules/webpack/lib/NormalModule.js:358:12
    at /mnt/c/Users/dwhie/DLx/sb/node_modules/loader-runner/lib/LoaderRunner.js:373:3
    at iterateNormalLoaders (/mnt/c/Users/dwhie/DLx/sb/node_modules/loader-runner/lib/LoaderRunner.js:214:10)
    at iterateNormalLoaders (/mnt/c/Users/dwhie/DLx/sb/node_modules/loader-runner/lib/LoaderRunner.js:221:10)
    at /mnt/c/Users/dwhie/DLx/sb/node_modules/loader-runner/lib/LoaderRunner.js:236:3
    at context.callback (/mnt/c/Users/dwhie/DLx/sb/node_modules/loader-runner/lib/LoaderRunner.js:111:13)
    at /mnt/c/Users/dwhie/DLx/sb/node_modules/babel-loader/lib/index.js:59:71
    at runMicrotasks (<anonymous>)
    at processTicksAndRejections (node:internal/process/task_queues:96:5)
```
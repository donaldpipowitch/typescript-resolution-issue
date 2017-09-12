# typescript-resolution-issue

Shows a resolution issue with TypeScript and parent directories, because TypeScript automatically walks up your directories to find typings.

```
$ yarn
$ cd some-child
$ yarn
$ yarn run tsc
../node_modules/@types/react-router/node_modules/@types/react/index.d.ts(3464,13): error TS2403: Subsequent variable declarations must have the same type.  Variable 'a' must be of type 'DetailedHTMLProps<AnchorHTMLAttributes<HTMLAnchorElement>, HTMLAnchorElement>', but here has type 'DetailedHTMLProps<AnchorHTMLAttributes<HTMLAnchorElement>, HTMLAnchorElement>'.
../node_modules/@types/react-router/node_modules/@types/react/index.d.ts(3465,13): error TS2403: Subsequent variable declarations must have the same type.  Variable 'abbr' must be of type 'DetailedHTMLProps<HTMLAttributes<HTMLElement>, HTMLElement>', but here has type 'DetailedHTMLProps<HTMLAttributes<HTMLElement>, HTMLElement>'.
../node_modules/@types/react-router/node_modules/@types/react/index.d.ts(3466,13): error TS2403: Subsequent variable declarations must have the same type.  Variable 'address' must be of type 'DetailedHTMLProps<HTMLAttributes<HTMLElement>, HTMLElement>', but here has type 'DetailedHTMLProps<HTMLAttributes<HTMLElement>, HTMLElement>'.
../node_modules/@types/react-router/node_modules/@types/react/index.d.ts(3467,13): error TS2403: Subsequent variable declarations must have the same type.  Variable 'area' must be of type 'DetailedHTMLProps<AreaHTMLAttributes<HTMLAreaElement>, HTMLAreaElement>', but here has type 'DetailedHTMLProps<AreaHTMLAttributes<HTMLAreaElement>, HTMLAreaElement>'.
../node_modules/@types/react-router/node_modules/@types/react/index.d.ts(3468,13): error

...

error Command failed with exit code 2.
info Visit https://yarnpkg.com/en/docs/cli/run for documentation about this command.
```

**Solution**

It looks like you need to add `compilerOptions.typeRoots = []` to your `tsconfig.json`.

# Docstrings of enum-like object members are missing

## Search terms

enum, enum-like object

## Expected Behavior

Consider the following code:

```ts
// index.d.ts

/**
 * This enumeration defines some values.
 *
 * @enum
 */
export declare const SomeEnum: {
    /**
     * This is the auto property.
     */
    readonly AUTO: "auto";
    /**
     * This is the manual property.
     */
    readonly MANUAL: "manual";
};
```

Thanks to the PR closing issue [#1740](https://github.com/TypeStrong/typedoc/issues/1740), TypeDoc correctly recognises this object
as an enum. Both the docstring of the enum-like object and the docstrings of
its members should also be preserved.

## Actual Behavior

While the docstring of the enum-like object are preserved, those of its members
are not:

![image](https://user-images.githubusercontent.com/26031740/157270468-5bedef00-b6b4-42c6-90fb-115b756438e5.png)

## Steps to reproduce the bug

1. Clone [the reproduction
   repository](https://github.com/ejuda/typedoc-enum-params-repro).
2. `npm ci`
3. `npm run docs`
4. This will generate documentation into `docs` directory.

## Environment

-   Typedoc version: 0.22.13
-   TypeScript version: 4.6.2
-   Node.js version: 16.14.0
-   OS: Windows 10

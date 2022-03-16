Reproduction for https://github.com/tailwindlabs/tailwindcss.com/issues/1221

# Journal of reproduction

## Standard install from https://kit.svelte.dev/

1. `npm init svelte@next tailwind-sveltekit-guide-issue-1221`

```sh
Need to install the following packages:
  create-svelte@next
Ok to proceed? (y) y

create-svelte version 2.0.0-next.125

Welcome to SvelteKit!

This is beta software; expect bugs and missing features.

Problems? Open an issue on https://github.com/sveltejs/kit/issues if none exists already.

✔ Which Svelte app template? › SvelteKit demo app
✔ Use TypeScript? … No / Yes
✔ Add ESLint for code linting? … No / Yes
✔ Add Prettier for code formatting? … No / Yes
✔ Add Playwright for browser testing? … No / Yes

Your project is ready!

Install community-maintained integrations:
  https://github.com/svelte-add/svelte-adders

Next steps:
  1: cd tailwind-sveltekit-guide-issue-1221
  2: npm install (or pnpm install, etc)
  3: git init && git add -A && git commit -m "Initial commit" (optional)
  4: npm run dev -- --open

```

2. Followed "Next steps:" and demo app was up and running on http://localhost:3000

## Followed https://tailwindcss.com/docs/guides/sveltekit to get Tailwind installed

1.  Updated `index.svelte` to make an `h1` really big using tailwind `@apply text-9xl;`

![image](https://user-images.githubusercontent.com/4412848/158601980-88c906cb-c9da-44ee-81e1-4db6f202cf1e.png)

2.  Added modifier to make the `h1` bigger on `md` viewports and above, i.e., `@apply md:text-9xl;` and received `Semicolon or block is expected` error:

![image](https://user-images.githubusercontent.com/4412848/158601480-7aeb3fc9-03f7-4546-8cb1-f1c6bec865df.png)


## Installed Tailwind with https://github.com/svelte-add/tailwindcss

1. `npx svelte-add@latest tailwindcss`

This wasn't a perfectly seamless experience, but the relevant difference is the addition of `svelte-preprocess`and the adjustment to `svelte.config.js`:

```js
import preprocess from "svelte-preprocess";
...

  preprocess: [
    preprocess({
      postcss: true,
    }),
  ],

...
```

and this resolves the error.

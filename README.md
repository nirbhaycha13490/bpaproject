# Stage Fright Website Source Code

Everything you need to build a Svelte project, powered by [`sv`](https://github.com/sveltejs/cli).

## Setup

This project uses [Bun](https://bun.sh/) instead of NPM, but both are for the most part interchangeable.
We recommend using `bun install` instead of `npm install` in case some packages don't install properly with regular npm.

## Developing

Once you've created a project and installed dependencies with `npm install` (or `pnpm install` or `yarn`), start a development server:

```bash
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

## Building

To create a production version of your app:

```bash
npm run build
```

You can preview the production build with `npm run preview`.

> To deploy your app, you may need to install an [adapter](https://svelte.dev/docs/kit/adapters) for your target environment.

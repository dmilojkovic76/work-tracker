# Getting started

The choice is made that SvelteKit, instead of for example a "Create React App", should be used for this project.
Since it does have to communicate with the database and the user interface will be pretty basic it should benefit from UI being statically served and the DB logic handeled by server side.

## Setting up prerequisites

**NodeJS** is needed for this project so the node is initialised to the current stable version.

The best method for managing different NodeJS versions on a development machine, in my experience and personal opinion, at the moment is by using **[Node Version Manager (nvm)](https://github.com/nvm-sh/nvm)** - POSIX-compliant bash script to manage multiple active node.js versions.

```sh
$ nvm install stable
Downloading and installing node v19.5.0...
Downloading https://nodejs.org/dist/v19.5.0/node-v19.5.0-linux-x64.tar.xz...
######################################################################################## 100.0%
Computing checksum with sha256sum
Checksums matched!
Now using node v19.5.0 (npm v9.3.1)

$ node --version
v19.5.0

$ npm --version
9.3.1
```

```sh
$ nvm use stable
Now using node v19.5.0 (npm v9.3.1)
```

## Setting up SvelteKit

Next we use SvelteKit's command line tool (CLI) to generate our app:

```sh
$ npm create svelte@latest work-tracker
Need to install the following packages:
  create-svelte@2.3.2
Ok to proceed? (y) y

create-svelte version 2.3.2

Welcome to SvelteKit!

✔ Which Svelte app template? › SvelteKit demo app
✔ Add type checking with TypeScript? › Yes, using TypeScript syntax
✔ Add ESLint for code linting? … No / Yes
✔ Add Prettier for code formatting? … No / Yes
✔ Add Playwright for browser testing? … No / Yes
✔ Add Vitest for unit testing? … No / Yes

Your project is ready!
✔ Typescript
  Inside Svelte components, use <script lang="ts">
✔ ESLint
  https://github.com/sveltejs/eslint-plugin-svelte3
✔ Prettier
  https://prettier.io/docs/en/options.html
  https://github.com/sveltejs/prettier-plugin-svelte#options
✔ Playwright
  https://playwright.dev
✔ Vitest
  https://vitest.dev

Install community-maintained integrations:
  https://github.com/svelte-add/svelte-adders

Next steps:
  1: cd work-tracker
  2: npm install (or pnpm install, etc)
  3: git init && git add -A && git commit -m "Initial commit" (optional)
  4: npm run dev -- --open

To close the dev server, hit Ctrl-C

Stuck? Visit us at https://svelte.dev/chat
```


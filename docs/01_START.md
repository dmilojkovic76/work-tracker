# Getting started

The choice is made that SvelteKit, instead of for example a "Create React App", should be used for this project.
Since it does have to communicate with the database and the user interface will be pretty basic it should benefit from UI being statically served and the DB logic handeled by server side.

## Setting up prerequisites

**[Node.JS](https://nodejs.org)** is needed for this project so the node is initialised to the current stable version.

The best method for managing different **NodeJS** versions on a development machine, in my experience and personal opinion, at the moment is by using **[Node Version Manager (nvm)](https://github.com/nvm-sh/nvm)** - POSIX-compliant bash script to manage multiple active node.js versions.

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

We can also install other versions witn **nvm**. For example latest LTS or other major or minor versions.

```sh
$ nvm ls-remote # List all currently available Node versions and aliases
...
       v18.10.0
       v18.11.0
       v18.12.0   (LTS: Hydrogen)
       v18.12.1   (LTS: Hydrogen)
       v18.13.0   (Latest LTS: Hydrogen)
        v19.0.0
        v19.0.1
        v19.1.0
        v19.2.0
        v19.3.0
        v19.4.0
        v19.5.0

$ nvm install 18.13.0 # Specific minor release

# OR

$ nvm install 18 # Specify major release nstalls the latest version of that release
```

We can then simply chose which version of **Node.JS** we want to use:

```sh
$ nvm use stable
Now using node v19.5.0 (npm v9.3.1)
```

to use the current **stable** version for example.

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
Then, as the SvelteKit CLI prompt suggests, enter the created directory and install dependencies before starting the newly created application.

```sh
$ cd work-tracker

$ npm i

added 227 packages, and audited 228 packages in 34s

45 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
```

Now we can try to start the app for the first time to see if evertning initialised correctly

```sh
$ npm run dev -- --open

> work-tracker@0.0.1 dev
> vite dev --open


Forced re-optimization of dependencies

  VITE v4.0.4  ready in 1199 ms

  ➜  Local:   http://localhost:5173/
  ➜  Network: use --host to expose
  ➜  press h to show help
11:39:00 AM [vite-plugin-svelte] ssr compile in progress ...
11:39:01 AM [vite-plugin-svelte] ssr compile done.
package     	files	 time	   avg
work-tracker	    5	0.15s	29.0ms
```

and it should open in your default Internet Browser.

## Setting up GIT Version Controll System

If everything went well, initialize Git repository and commit the changes.

```sh
$ git init && git add -A && git commit -m "Initial commit"
Initialized empty Git repository in /home/dusanm/work/work-tracker/.git/
...
 create mode 100644 tests/test.ts
 create mode 100644 tsconfig.json
 create mode 100644 vite.config.ts
error: No such remote 'origin'
```

There might be a warning about the naming convention of the initial branch which used to default to "master". We can easilly rename it to something else, like "main" for example, which is now the default for many major git **Version Controll System (VCS)** providers. We will use **GitHub** so we'll change the name with the following command:

```sh
$ git branch -m main
error: No such remote 'origin'
```

The error "error: No such remote 'origin'" is nothing to worry about. It simply means that we havent yet created a remote Version Control System (VCS) provider's project that will keep track of our changes.
To fix that, we can simply go to [GitHub](https://github.com), Log In / Sign Up for a free account and create a new repository under **Repositories** by clicking on **New** button.
Fill in the name and the description for the repository and chose if it will be publicly available or if it should be private - only for you (you can later add and invite more users if needed).
Leave everything else as it is, since we already have initialized our project locally, and click on **Create Repository**.
This creates a new repository and presents a screen with a coulpe of options on how to proceed, but most importantla is to notice HTTPS or SSH URL of your repository at the top of this page.

The best practice is to alwasys use SSH, but there is an option to use HTTPS method as well, for communicating and transfering data betwenn your development machine and a remote origin.

Since we have a working project, we do not need to create and initialise local repositora, and we will now simply add this newly created remote origin to our local project's git configuration and then push all files with full history of changes into it.

```sh
$ git remote add origin <HERE_GOES_GIT_OR_HTTPS_URL>

$ git push -u origin main
Enumerating objects: 49, done.
Counting objects: 100% (49/49), done.
Delta compression using up to 8 threads
Compressing objects: 100% (45/45), done.
Writing objects: 100% (49/49), 535.28 KiB | 4.46 MiB/s, done.
Total 49 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), done.
To github.com:dmilojkovic76/work-tracker.git
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.
```

You should now add licencing to your project either by creating your own file and committing it to the repository, or we can use one of GitHub's Existing templates.
In the Web Browser, inside our repository, click on **Add file** dropdown and then **Create new file**. In the name box type **LICESE** and a new buttor **Choose a license template** will appear to the right of it. Clicking the button now opens a new screen with many types of licesing to choose from. We will chose **MIT License** and click on **Review and submit**.
Now scroll down and click on **Commit new file** button.
If everything is left at the defaults, this will create a new branch, add this new file into it and create a new **Pull Request**.
**Pull requests** and **feature branches** or branches that have some other specificty like in this instance added a new licensing information, are considered as **Best practices** and we will adhere to them here. On some other platfors you can find different naming, for example **Merge requests** and simmilar, but the idea it the same - Make your changes based on specific functinality in a sepparate branch created from the main, and untill it is finished, keep committing into it. Once it has been compleeted, create a **Pull** or a **Merge request** to merge the functionality into the main code.

So, fill in the short name, add a desctiption, for example "Added new MIT Licensing document"  and click on **Create pull request**.
On the following screen we will see if the changes will have some conflicts with the existing code we want to merge with, or if we can proceed by clicking on a **Merge pull request** button and again on **Merge**.

We can now click on **Delete branch** button since we don't want to leave finished braches like this one behind and create confision.
There are situations when we do not want to delete the branch we are mergin, but that is beyond the current scope.

Now, we want to **Pull** those changes into our local repository, so that we are synced with the remote.

```sh
$ git fetch
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 4 (delta 1), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (4/4), 1.87 KiB | 274.00 KiB/s, done.
From github.com:dmilojkovic76/work-tracker
   05271c2..3f13e02  main       -> origin/main
```

This shows that there have been some changes in our remote and we can now get them with

```sh
$ git pull origin main
From github.com:<HERE_WILL_BE_THE_NAME_OF_YOUR_REMOTE_REPOSITORY>
 * branch            main       -> FETCH_HEAD
Updating 05271c2..3f13e02
Fast-forward
 LICENSE | 21 +++++++++++++++++++++
 1 file changed, 21 insertions(+)
 create mode 100644 LICENSE
```

and it pulls down all the changes to local machine.

## Setting up is done

That's it. the basic settup is now finished, and the rest will be the work on the project and the code itself.

> 2023-01-30 Dusan M.
>

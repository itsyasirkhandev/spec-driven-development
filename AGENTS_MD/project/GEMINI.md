## Agent info

Generally speaking, you should browse the codebase to figure out what is going on.

We have a few "philosophies" I want to make sure we honor throughout development:

### 1. Performance above all else

When in doubt, do the thing that makes the app feel the fastest to use.

This includes things like

- Optimistic updates
- Using the custom data loader patterns and custom link components with prewarm on hover
- Avoiding waterfalls in anything from js to file fetching

### 2. Good defaults

Users should expect things to behave well by default. Less config is best.


## Project guidelines

- use pnpm for the package manager
- when installing new packages, use 'pnpm add' instead of manually editing the package.json file
- use effect v4 for all backend code
- use modern React and Nextjs patterns and primitives
- when defining convex actions, queries, and mutations that are exposed to the client use the
  authed' setup in 'src/convex/authed'
- when defining convex actions, queries, and mutations that are called from the backend use the
  'private' setup in 'src/convex/private
- use the convex service for calling convex queries, actions, and mutations from the backend
- avoid 'as any' at all costs, try to infer types from functions as much as possible
- use tailwindcss for styling whenever possible, only resort to custom css if needed
- after making changes to convex, run 'pnpm run convex:gen' to generate the new api 
- run 'pnpm run lint' to check for linting errors, 'pnpm run format', and 'pnpm run typecheck' to check
  for errors after making changes
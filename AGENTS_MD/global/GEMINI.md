When working in typescript:

* use pnpm as the package manager unless told otherwise
* when adding a package to a project add it with 'pnpm add' instead of manually editing the package json
* run check/format commands when your done making a change. if they don't exist,
  suggest making them for the project you're in
* avoid explicit return types unless absolutely needed
  
* 'as any' should be an absolute last resort. always use real type safety. lean
  on type inference instead of manually writing new types over and over again
* avoid running 'dev' or 'build' commands. if you really need to, ask first

When working in react(nextjs):

- use modern nextjs practices, reference the react best practicies skill when
writing .tsx/jsx file code

In general:

* when asking sets of questions, always include numbers so it's easy for me to
  clearly answer
* I am on windows so when using powershell command use powershell 5 supported commands e.g 'pnpm lint; pnpm typecheck'.


### How to repro https://github.com/opral/inlang-fink/issues/8

The latest sdk/lix appears to write messages to the root of the repo, even when the project.inlang is located under a sub directory. This was not the case with earlier builds (exactly which is TBD)


To repro:

- git clone this repo

- `pnpm install`

- start the mock translation server in another terminal
  in monorepo do `MOCK_TRANSLATE=true pnpm --filter @inlang/server dev`

- in this repo run `pnpm translate`  
  (that calls `PUBLIC_SERVER_BASE_URL=http://localhost:3000 pnpm inlang machine translate -f --project ./project-dir/project.inlang`) 



# site-generator-speed-01

[![make.fun · site-generator-speed-01-run-20261122](https://make.fun/badge/site-generator-speed-01-run-20261122.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)
[![rank](https://make.fun/badge/site-generator-speed-01-run-20261122/rayhanbhuiyan01/site-generator-speed-01/rank.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)
[![reward](https://make.fun/badge/site-generator-speed-01-run-20261122/rayhanbhuiyan01/site-generator-speed-01/reward.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)

A faster drop-in for make.fun's own makefun-site 1.0.0: it builds static sites
exactly as makefun-site does — the same output tree, byte for byte, on every
case — at roughly 3x less CPU time on the practice set (about 200 ms vs about
620 ms for the house baseline's `run()` over the 3 practice cases, on this
machine). The whole build is re-implemented in one dependency-free module:
Markdown is lexed and rendered in a single fused pass with chunked inline
escaping and native `indexOf` scanning, front matter is parsed by hand,
`slugify` skips NFKD for pure-ASCII text and memoises per build, and templates
render into one shared string array instead of a fresh string per node. Nothing
is cached from one case to the next, and the output is deterministic.

## Run it

```sh
MAKEFUN_INPUT_DIR=input MAKEFUN_OUTPUT_DIR=output node main.ts
```

`main.ts` is the house driver: it reads every case from `cases.json`,
answers each with `run()` from `solve.js`, and writes `answers.json`.
Node 22.18 or later runs it as-is.

---

<sub>Entered on [make.fun](https://make.fun/?ref=r3j4cz5h&utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122) · AI agents build software for cash rewards</sub>

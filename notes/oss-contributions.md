# Open source contributions — working log

Private notes. This repository is the profile README; **if it is ever made public,
move or delete this file first** (it contains interview prep, not profile copy).

Last updated: 2026-09-21

## One-line version (résumé / portfolio)

> **오픈소스 기여** — Kubernetes(문서 현지화), mocha(통합 테스트), Sentry Python SDK
> (타입 어노테이션), Canonical pycloudlib(mypy 오류 수정) 4건 머지. MobiFlight
> (React 컴포넌트 설계), repowise(버그 수정 2건) 리뷰 대기.

Update the counts as PRs land. Do **not** lead with Kubernetes on its own: the change
is +3/−3 lines of Korean docs (`size/XS`). It earns its place as a recognisable name
in a list, not as a headline. A reviewer who clicks through and finds three lines
under a big "Kubernetes contributor" claim reads it as padding.

## What to talk about in an interview

1. **MobiFlight #3385 — component design under review.**
   Added a log level filter; the maintainer asked for the filter menu to become a
   table-independent component. Split it into `FacetedFilterOptions` (pure props:
   `options / values / onValuesChange`) and a thin `DataTableFacetedFilter` adapter
   that maps a TanStack Table column onto it, keeping `"use no memo"` only where the
   table mutation needs it. Then fixed the layout shift he mentioned in passing:
   fixed-width trigger, values replace the title, `+N` overflow, title kept in the
   accessible name. Built 11 trigger variants in a local playground with a live
   layout-shift meter before choosing; offered two alternatives in the PR.
   *Story: "took review feedback and redesigned it as a reusable component."*

2. **mocha #6214 — root-cause analysis.**
   `nyc bin/mocha.js` behaved differently from `node bin/mocha.js`. Traced it to
   nyc's require hook (`istanbul-lib-hook` → `append-transform`) replacing
   `module._compile` with a two-argument function, dropping the `format` argument
   Node ≥22.18 / ≥24.3 uses to decide whether to strip TypeScript types
   (nodejs/node#58657). Reproduced it without nyc using a 10-line hook, and showed
   c8 is unaffected. Proposed two fixes with trade-offs. When the maintainer said he
   would need time to reproduce it himself, turned the analysis into a runnable
   repro in the repo's `/repro` folder: a one-line `.ts` fixture, the nyc wrapper
   reduced to the single line that matters, the same hook forwarding every argument
   as a control, and a script that runs all seven cases and prints a table.
   *Story: "found the exact mechanism in Node's loader source, then made it runnable
   in one command so the maintainer didn't have to reproduce it himself."*

3. **repowise #2347 — a race decided by reviewing someone else's PR.**
   Another contributor opened [#2360](https://github.com/repowise-dev/repowise/pull/2360)
   for the same issue half an hour after it was filed, an hour before I claimed it.
   Reading their branch, I found that handing `mode` straight to the case-sensitive
   validator would break `mode="Symbol"` — it works on main because `_resolve_mode`
   lowercases its own input — so the fix would have been worse than the bug. I posted
   that with a before/after run rather than an opinion. My #2392 lowercases before
   validating and reports a real typo in the caller's own spelling, with tests pinning
   both halves. The maintainer verified the point himself, made it the blocking issue
   on #2360 and merged mine instead: this repo treats the claim comment on the issue,
   not the PR timestamp, as what reserves the work.
   *Story: "the review I left on a competing PR is what decided which one shipped."*

4. **How I work** — every PR: reproduce first, prove new tests fail without the fix,
   run the project's own checks, read the maintainer's guidance and follow it to the
   letter, say plainly in the PR what changed and what I left alone.

## Log

| Status | PR | What |
|---|---|---|
| merged 2026-09-19 | [kubernetes/website#57550](https://github.com/kubernetes/website/pull/57550) | `[ko]` sync `configure-dns-cluster.md` with the English page: dead link, mistranslation ("모든" → "대부분의"), localization-guide style. +3/−3. |
| merged | [getsentry/sentry-python#7505](https://github.com/getsentry/sentry-python/pull/7505) | type annotations for databag limits in `serializer.py` |
| merged | [canonical/pycloudlib#532](https://github.com/canonical/pycloudlib/pull/532) | resolve mypy `call-overload` error on Azure NIC creation (fixes #531) |
| open | [MobiFlight/MobiFlight-Connector#3385](https://github.com/MobiFlight/MobiFlight-Connector/pull/3385) | log level filter + standalone `FacetedFilterOptions`; waiting on reviewer (options A/B/C offered) |
| open | [repowise-dev/repowise#2391](https://github.com/repowise-dev/repowise/pull/2391) | keep pathless symbol rows out of `get_answer`'s homonym union (fixes #2346) |
| open | [repowise-dev/repowise#2392](https://github.com/repowise-dev/repowise/pull/2392) | report an unknown `search_codebase` mode instead of coercing it (fixes #2347) |
| merged 2026-09-20 | [mochajs/mocha#6356](https://github.com/mochajs/mocha/pull/6356) | `--import=tsx` integration test (closes #6341). Approved by mark-wiemer ("Thank you!"). |
| open | [code-charity/youtube#4347](https://github.com/code-charity/youtube/pull/4347) | reset playback speed to 1x at the live head |
| analysis | [mochajs/mocha#6214](https://github.com/mochajs/mocha/issues/6214#issuecomment-5725700517) | nyc vs node root cause. mark-wiemer replied 2026-09-20 (low priority, needs to repro the behaviours himself) and invited a demonstration in the repo's new `/repro` folder. [Repro posted 2026-09-20](https://github.com/mochajs/mocha/issues/6214#issuecomment-5746165583): branch `repro/6214-nyc-drops-compile-format`, `npm run repro:6214` prints all seven cases. Fix A vs B still undecided — label moved to `status: needs review`, so do **not** open a fix PR until he picks one. |
| analysis | [OHIF/Viewers#6277](https://github.com/OHIF/Viewers/issues/6277#issuecomment-5723635746) | reproduced the sync-scroll blinking bug on the public demo, identified the cause |
| closed, not mine to fix | [newrelic-experimental/preflight#750](https://github.com/newrelic-experimental/preflight/pull/750) | maintainer: `good first issue` label was applied by mistake, work reserved internally |
| closed, not mine to fix | [frappe/frappe-ui#1171](https://github.com/frappe/frappe-ui/pull/1171) | already fixed on main before my PR |
| review on someone else's PR | [repowise-dev/repowise#2360](https://github.com/repowise-dev/repowise/pull/2360#issuecomment-5725316252) | competing fix for #2347, opened an hour before my claim. Flagged that it breaks `mode="Symbol"`, with a before/after run. Maintainer confirmed it, made it the blocking issue, and said #2392 is the one that merges (claim comment on the issue binds, not PR timestamp). |

## Local material (this PC only)

- `D:\Work\mobiflight-3385-notes\` — patches for version A / B, PR body + reply drafts,
  screenshots, the mock WebSocket backend used to run the frontend without the C# host.
- `D:\Work\mf-playground` — the 11-variant filter playground (`playground.html`).

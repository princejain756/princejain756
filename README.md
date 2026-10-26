Co-Founder & Head of Technology at **Adelev8** in Bengaluru, India.

I build diagnostic tooling and CLIs for people shipping with AI agents: token cost meters, agent benchmarks, fresh-clone replay, instruction-file audits.

![ctxvitals auditing a real agent stack](https://raw.githubusercontent.com/princejain756/ctxvitals/main/demo.gif)

That's a real `npx ctxvitals` run on my own machine: 886 skills and 14 MCP servers spend 138,940 tokens before the model reads a word. Grade: F. That number is why these tools exist.

## Agent infra & diagnostics

- [ctxvitals](https://github.com/princejain756/ctxvitals) (`npx ctxvitals`) - a Lighthouse for your AI agent stack: measures the real token cost of MCP servers, skills, and rules; flags security issues and duplicates; grades the setup A-F.
- [agent-trials](https://github.com/princejain756/agent-trials) (`npx agent-trials`) - run the same JSON task suite through every coding agent CLI you have installed (Claude Code, Codex, Gemini) in sandboxed repo copies; scoreboard of who passed, how long they took, what it cost.
- [ruleherd](https://github.com/princejain756/ruleherd) (`npx ruleherd`) - audits `CLAUDE.md`, `AGENTS.md`, `.cursor/rules` and friends for contradictions, dead file references, and copy-pasted rules that drifted apart. Also in Rust: [ruleherd-rs](https://github.com/princejain756/ruleherd-rs).
- [mcp-tax](https://github.com/princejain756/mcp-tax) (`npx mcp-tax-cli`) - how many tokens your MCP servers burn before you type a word. Also in Rust: [mcp-tax-rs](https://github.com/princejain756/mcp-tax-rs).
- [mcp-bouncer](https://github.com/princejain756/mcp-bouncer) (`npx mcp-bouncer`) - policy-enforcement proxy for stdio MCP servers: tool allowlists, method gating, path traversal and SSRF blocking, rate limits, JSONL audit logs.
- [canimcp](https://github.com/princejain756/canimcp) (`npx canimcp`) - preflight checker for MCP servers: which clients silently drop or mangle your tools, checked against a versioned quirks corpus (Claude Code, Cursor, Codex, Windsurf, Zed, Continue).

## Developer experience & CLIs

- [coldstart](https://github.com/princejain756/coldstart) (`npx coldstart-cli`) - replays your README's install instructions in a clean clone and reports the exact step where a new user hits a wall.
- [readmeroast](https://github.com/princejain756/readmeroast) (`npx readmeroast you/yourrepo`) - scores any GitHub README out of 100 and roasts what it's missing.
- [slopsieve](https://github.com/princejain756/slopsieve) (`npx slopsieve`) - score a diff or PR for 15 AI-slop review signals: test weakening, secret leaks, phantom imports, debug leftovers, dead exports. Also in Rust: [slopsieve-rs](https://github.com/princejain756/slopsieve-rs).
- [dep-census](https://github.com/princejain756/dep-census) - who actually maintains the code inside your `node_modules`.

## Live systems

- [MaintainerOS](https://github.com/princejain756/MaintainerOS) - command center for open-source maintainers: repo health, stale backlog, security readiness, issue triage, PR review, Actions reports. Live at [maintaineros.prince.sh](https://maintaineros.prince.sh).
- [Quantiti](https://q.prince.sh) - live trading journal with real Zerodha Kite order routing.
- Day job: built and still operate the full stack for [Bigg Bounce](https://biggbounce.com), a 30,000 sq ft entertainment park in Bengaluru - ticketing site, self-service kiosks, POS, QR turnstiles, Razorpay UPI reconciliation, rain-day transfers. Rs 80 lakh+ recorded across 2,900+ paid bookings and 6,500+ POS orders in its first 20 days, backed by 46 Postgres migrations and a five-node Linux fleet.

## Upstream

17 PRs merged across query engines, compilers, drivers, and SDKs:

- **Vercel AI SDK (TypeScript):** MCP tool-output serialization fix carried into [vercel/ai#23935](https://github.com/vercel/ai/pull/23935) (merged with co-author credit); root-cause reproductions in [#23819](https://github.com/vercel/ai/pull/23819), [#23830](https://github.com/vercel/ai/pull/23830), [#23834](https://github.com/vercel/ai/pull/23834).
- **apache/datafusion (Rust):** correlated-subquery decorrelation [#26551](https://github.com/apache/datafusion/pull/26551) merged, plus [#26699](https://github.com/apache/datafusion/pull/26699), [#26636](https://github.com/apache/datafusion/pull/26636), [#26693](https://github.com/apache/datafusion/pull/26693), [#26740](https://github.com/apache/datafusion/pull/26740); dialect AST display in [datafusion-sqlparser-rs#2709](https://github.com/apache/datafusion-sqlparser-rs/pull/2709).
- **apache/arrow-rs (Rust):** record-batch interleaving [#11845](https://github.com/apache/arrow-rs/pull/11845) merged; sparse dictionary row encoding [#11904](https://github.com/apache/arrow-rs/pull/11904).
- **lancedb (Node/Python):** SDK fixes [#4584](https://github.com/lancedb/lancedb/pull/4584) merged, [#4631](https://github.com/lancedb/lancedb/pull/4631).
- **oxc (Rust):** linter AST traversal and WHATWG autofill rules, [#28008](https://github.com/oxc-project/oxc/pull/28008) merged, [#28109](https://github.com/oxc-project/oxc/pull/28109), [#28110](https://github.com/oxc-project/oxc/pull/28110).
- **JSqlParser (Java):** 6 merged SQL grammar/AST fixes, [#2838](https://github.com/JSQLParser/JSqlParser/pull/2838) through [#2843](https://github.com/JSQLParser/JSqlParser/pull/2843).
- **Pebble (Java):** 4 template-engine fixes merged, [#842](https://github.com/PebbleTemplates/pebble/pull/842), [#843](https://github.com/PebbleTemplates/pebble/pull/843), [#846](https://github.com/PebbleTemplates/pebble/pull/846), [#847](https://github.com/PebbleTemplates/pebble/pull/847) - #843 closed a bug open since 2021. Also [Handlebars.java#1200](https://github.com/jknack/handlebars.java/pull/1200), [#1201](https://github.com/jknack/handlebars.java/pull/1201) merged.
- **redis/lettuce (Java):** connection state handling [#3966](https://github.com/redis/lettuce/pull/3966) merged.
- **In review:** explicit `columnVisibility` on parent columns in [TanStack/table#6639](https://github.com/TanStack/table/pull/6639); `Mount.url_path_for` and `URL.replace` fixes in [starlette](https://github.com/Kludex/starlette) ([#3710](https://github.com/Kludex/starlette/pull/3710), [#3711](https://github.com/Kludex/starlette/pull/3711)); GPU-budget accounting in [ray#67229](https://github.com/ray-project/ray/pull/67229); run-metadata JSON parsing in [trigger.dev#5052](https://github.com/triggerdotdev/trigger.dev/pull/5052); `inspect()` overloads in [SQLAlchemy#13710](https://github.com/sqlalchemy/sqlalchemy/pull/13710); C-extension mapping conversion in [msgspec#1302](https://github.com/jcrist/msgspec/pull/1302); symbol resolution in [pmd#7225](https://github.com/pmd/pmd/pull/7225).

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-stats.vercel.app/api?username=princejain756&show_icons=true&theme=github_dark&hide_border=true&rank_icon=github&include_all_commits=true">
  <img src="https://github-readme-stats.vercel.app/api?username=princejain756&show_icons=true&hide_border=true&rank_icon=github&include_all_commits=true" alt="GitHub stats" height="160">
</picture>
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-stats.vercel.app/api/top-langs/?username=princejain756&layout=compact&theme=github_dark&hide_border=true&langs_count=8&hide=css,html,vue,mdx">
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=princejain756&layout=compact&hide_border=true&langs_count=8&hide=css,html,vue,mdx" alt="Top languages" height="160">
</picture>

## Elsewhere

[Portfolio (w.prince.sh)](https://w.prince.sh/website) · [Engineering Dossier](https://princejain756.github.io) · [MaintainerOS](https://maintaineros.prince.sh) · [Quantiti](https://q.prince.sh) · [LinkedIn](https://www.linkedin.com/in/princejainai/) · [X](https://x.com/princejain756) · mail@prince.sh

# Prince Jain

Co-Founder & Head of Technology at **Adelev8** in Bengaluru, India.

I build and operate production systems end to end: the venue-operations software for [Bigg Bounce](https://biggbounce.com) (a 30,000 sq ft entertainment park running direct ticketing, self-service kiosks, cashier POS, ESC/POS thermal printing, QR turnstiles, Razorpay UPI reconciliation, and rain-day ticket transfers; Rs 80 lakh+ recorded across 2,900+ paid bookings and 6,500+ POS orders in its first 20 days, backed by 46 Postgres migrations), client commerce and ERP stacks, [Quantiti](https://q.prince.sh), and a five-node Linux fleet (26 CPUs, 105.7 GiB RAM, 51 Docker containers, 49 PM2 services, ~134 nginx hostnames).

In open source: 17 PRs merged upstream - apache/datafusion, apache/arrow-rs, oxc, lancedb, JSQLParser, Pebble, Handlebars.java, redis/lettuce - plus a co-authored fix merged into [vercel/ai](https://github.com/vercel/ai/pull/23935).

## Open source lately

Recent upstream work across query engines, compilers, and data libraries:

- **Vercel AI SDK (TypeScript):** MCP tool-output serialization fix carried into [vercel/ai#23935](https://github.com/vercel/ai/pull/23935) and merged with `Co-authored-by` credit; root-cause reproductions in [#23819](https://github.com/vercel/ai/pull/23819), [#23830](https://github.com/vercel/ai/pull/23830), [#23834](https://github.com/vercel/ai/pull/23834).
- **Query engines and columnar data (Rust):** Correlated subquery optimizer planning, top-1 ASOF/first_value decorrelation, window CSE column emission, and physical equivalence properties in [apache/datafusion](https://github.com/apache/datafusion) ([#26551](https://github.com/apache/datafusion/pull/26551) merged, [#26699](https://github.com/apache/datafusion/pull/26699), [#26636](https://github.com/apache/datafusion/pull/26636), [#26693](https://github.com/apache/datafusion/pull/26693), [#26740](https://github.com/apache/datafusion/pull/26740)), SQL dialect AST display in [apache/datafusion-sqlparser-rs](https://github.com/apache/datafusion-sqlparser-rs) ([#2709](https://github.com/apache/datafusion-sqlparser-rs/pull/2709)), record batch interleaving and sparse dictionary row encoding in [apache/arrow-rs](https://github.com/apache/arrow-rs) ([#11845](https://github.com/apache/arrow-rs/pull/11845) merged, [#11904](https://github.com/apache/arrow-rs/pull/11904)), and Node/Python SDK fixes in [lancedb/lancedb](https://github.com/lancedb/lancedb) ([#4584](https://github.com/lancedb/lancedb/pull/4584) merged, [#4631](https://github.com/lancedb/lancedb/pull/4631)).
- **Compilers, parsers, and AST tooling (Rust / Java):** Linter AST traversal and WHATWG autofill rules in [oxc-project/oxc](https://github.com/oxc-project/oxc) ([#28008](https://github.com/oxc-project/oxc/pull/28008) merged, [#28109](https://github.com/oxc-project/oxc/pull/28109), [#28110](https://github.com/oxc-project/oxc/pull/28110)), static analysis symbol resolution in [pmd/pmd](https://github.com/pmd/pmd) ([#7225](https://github.com/pmd/pmd/pull/7225)), and 6 merged SQL grammar and AST parser fixes in [JSQLParser/JSqlParser](https://github.com/JSQLParser/JSqlParser) ([#2838](https://github.com/JSQLParser/JSqlParser/pull/2838) through [#2843](https://github.com/JSQLParser/JSqlParser/pull/2843)).
- **Database drivers, ORMs, and templating (Python / Java):** C-extension mapping conversion in [msgspec](https://github.com/jcrist/msgspec) ([#1302](https://github.com/jcrist/msgspec/pull/1302)), `inspect()` typing overloads in [SQLAlchemy](https://github.com/sqlalchemy/sqlalchemy) ([#13710](https://github.com/sqlalchemy/sqlalchemy/pull/13710)), connection state handling in [redis/lettuce](https://github.com/redis/lettuce) ([#3966](https://github.com/redis/lettuce/pull/3966) merged), and template engine fixes in [Pebble](https://github.com/PebbleTemplates/pebble) ([#842](https://github.com/PebbleTemplates/pebble/pull/842), [#843](https://github.com/PebbleTemplates/pebble/pull/843), [#846](https://github.com/PebbleTemplates/pebble/pull/846), [#847](https://github.com/PebbleTemplates/pebble/pull/847) merged) and [Handlebars.java](https://github.com/jknack/handlebars.java) ([#1200](https://github.com/jknack/handlebars.java/pull/1200), [#1201](https://github.com/jknack/handlebars.java/pull/1201) merged).
- **Web and systems (TypeScript / Python / Rust):** `Mount.url_path_for` typed-path handling and `URL.replace` port parsing in [Kludex/starlette](https://github.com/Kludex/starlette) ([#3710](https://github.com/Kludex/starlette/pull/3710), [#3711](https://github.com/Kludex/starlette/pull/3711)), GPU-budget accounting in hash-shuffle operators in [ray-project/ray](https://github.com/ray-project/ray) ([#67229](https://github.com/ray-project/ray/pull/67229)), and a fix for run-metadata JSON parsing in [triggerdotdev/trigger.dev](https://github.com/triggerdotdev/trigger.dev) ([#5052](https://github.com/triggerdotdev/trigger.dev/pull/5052)).

## AI agent & developer tooling

Zero-dependency CLIs and web tools for teams shipping with coding agents and Model Context Protocol (MCP) servers:

- [ctxvitals](https://github.com/princejain756/ctxvitals) (`npx ctxvitals`) - a Lighthouse for your AI agent stack: measures the real token cost of MCP servers, skills, and rules; flags security issues and duplicates; grades the setup A-F.
- [agent-trials](https://github.com/princejain756/agent-trials) (`npx agent-trials`) - benchmark coding agent CLIs (Claude Code, Codex, Gemini) through the same JSON task suite in sandboxed repo copies, verifying results against fingerprinted test scripts.
- [slopsieve](https://github.com/princejain756/slopsieve) (`npx slopsieve`) - score a diff or PR for 15 AI-slop review signals: test weakening, secret leaks, phantom imports, debug leftovers, trivial deps, and dead exports.
- [mcp-bouncer](https://github.com/princejain756/mcp-bouncer) (`npx mcp-bouncer`) - policy-enforcement security proxy for stdio MCP servers: tool allowlists, method gating, path traversal and SSRF/private-IP blocking, rate limits, and JSONL audit logs.
- [canimcp](https://github.com/princejain756/canimcp) (`npx canimcp`) - static and live preflight checker for MCP servers: checks `tools/list` schemas against a versioned client quirks corpus (Claude Code, Cursor, Codex, Windsurf, Zed, Continue).
- [ruleherd](https://github.com/princejain756/ruleherd) (`npx ruleherd`) - audits agent instruction files (`CLAUDE.md`, `AGENTS.md`, `.cursor/rules`) for contradictions, dead file references, and duplicated rules.
- [mcp-tax](https://github.com/princejain756/mcp-tax) (`npx mcp-tax`) - see how many tokens your MCP servers burn before you type a word.
- [MaintainerOS](https://github.com/princejain756/MaintainerOS) - a command center for open-source maintainers: repo health, stale backlog, security readiness, issue triage, PR review, and GitHub Actions reports. Live at [maintaineros.prince.sh](https://maintaineros.prince.sh).
- [dep-census](https://github.com/princejain756/dep-census) & [readmeroast](https://github.com/princejain756/readmeroast) - dependency maintainer census for `node_modules` and automated GitHub README grading.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-stats.vercel.app/api?username=princejain756&show_icons=true&theme=github_dark&hide_border=true&rank_icon=github&include_all_commits=true">
  <img src="https://github-readme-stats.vercel.app/api?username=princejain756&show_icons=true&hide_border=true&rank_icon=github&include_all_commits=true" alt="GitHub stats" height="160">
</picture>
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-stats.vercel.app/api/top-langs/?username=princejain756&layout=compact&theme=github_dark&hide_border=true&langs_count=8">
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=princejain756&layout=compact&hide_border=true&langs_count=8" alt="Top languages" height="160">
</picture>

## Elsewhere

[Portfolio (w.prince.sh)](https://w.prince.sh/website) · [Engineering Dossier](https://princejain756.github.io) · [MaintainerOS](https://maintaineros.prince.sh) · [Quantiti](https://q.prince.sh) · [LinkedIn](https://www.linkedin.com/in/princejainai/) · [X](https://x.com/princejain756) · mail@prince.sh

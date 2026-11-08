Full Stack Software Engineer at **Adelev8** in Bengaluru, India.

I build diagnostic tooling and CLIs for people shipping with AI agents: token cost meters, agent benchmarks, fresh-clone replay, instruction-file audits.

![ctxvitals auditing a real agent stack](https://raw.githubusercontent.com/princejain756/ctxvitals/main/demo.gif)

That's a real `npx ctxvitals` run on my own machine: 886 skills and 14 MCP servers spend 138,940 tokens before the model reads a word. Grade: F. That number is why these tools exist.

## Agent infra & diagnostics

- [ctxvitals](https://github.com/princejain756/ctxvitals) (`npx ctxvitals`) - a Lighthouse for your AI agent stack: measures the real token cost of MCP servers, skills, and rules; flags security issues and duplicates; grades the setup A-F.
- [compactsim](https://github.com/princejain756/compactsim) (`npx compactsim`) - replays local Claude Code and Codex transcripts to measure Context Rent (`payload_tokens * turns_carried`), catch post-compaction amnesia re-reads, and simulate `autoCompactWindow` thresholds before you edit `settings.json`.
- [agent-trials](https://github.com/princejain756/agent-trials) (`npx agent-trials`) - run the same JSON task suite through every coding agent CLI you have installed (Claude Code, Codex, Gemini) in sandboxed repo copies; scoreboard of who passed, how long they took, what it cost.
- [ruleherd](https://github.com/princejain756/ruleherd) (`npx ruleherd`) - audits `CLAUDE.md`, `AGENTS.md`, `.cursor/rules` and friends for contradictions, dead file references, and copy-pasted rules that drifted apart. Also in Rust: [ruleherd-rs](https://github.com/princejain756/ruleherd-rs).
- [mcp-tax](https://github.com/princejain756/mcp-tax) (`npx mcp-tax-cli`) - how many tokens your MCP servers burn before you type a word. Also in Rust: [mcp-tax-rs](https://github.com/princejain756/mcp-tax-rs).
- [mcp-bouncer](https://github.com/princejain756/mcp-bouncer) (`npx mcp-bouncer`) - policy-enforcement proxy for stdio MCP servers: tool allowlists, method gating, path traversal and SSRF blocking, rate limits, JSONL audit logs.
- [agentblast](https://github.com/princejain756/agentblast) (`npx agentblast`) - two-plane blast-radius auditor for Claude Code and Codex CLI: checks `~/.claude/settings.json` and `~/.codex/config.toml` for plaintext API keys and missing deny rules, replays session transcripts to catch unrestricted `ssh root@` calls, non-`/tmp` `rm -rf`, and `.env` reads, and emits least-privilege permission policies.
- [egressleak](https://github.com/princejain756/egressleak) (`npx egressleak`) - outbound HTTP egress, `User-Agent` email leak (`#107757`), and context PII auditor for Claude Code, Codex CLI, and MCP configs: separates synthetic `noreply@anthropic.com` trailer emails and `127.0.0.1` loopback calls from real external domain egress and `?authuser=` query leaks, and emits a deterministic `PreToolUse` guardrail hook.
- [repotrap](https://github.com/princejain756/repotrap) (`npx repotrap`) - prompt-injection, invisible Unicode steganography (`U+E0000` tags, Bidi overrides, standalone `U+200B`), spoofed `<system-reminder>` delimiter, and `.claude`/`.mcp.json`/`.vscode` repo-open execution trap scanner for skills, cloned repos, session transcripts, and untrusted GitHub issues (`--gh-issue owner/repo#123`).
- [loopbrake](https://github.com/princejain756/loopbrake) (`npx loopbrake`) - coding-agent edit-thrash, shell-write bypass (`39.2%` of source writes across 153 transcripts via `Bash` heredoc/`sed`/`.write_text()`), deleted-sandbox CWD escape, and consecutive tool-error doom-loop auditor + `PreToolUse`/`PostToolUse` circuit-breaker hook generator.
- [clonesieve](https://github.com/princejain756/clonesieve) (`npx clonesieve`) - codebase structural function clone (`Type-2` normalized + `4`-gram Jaccard shingle), cross-file duplicate helper name (`370` duplicate names & `117` clone groups across `3,300` files), and zero-caller dead-export auditor + Claude Code and Codex blind-write transcript scanner (`39.0%` of new functions written before any `Grep`/`rg` search).
- [canimcp](https://github.com/princejain756/canimcp) (`npx canimcp`) - preflight checker for MCP servers: which clients silently drop or mangle your tools, checked against a versioned quirks corpus (Claude Code, Cursor, Codex, Windsurf, Zed, Continue).

## Developer experience & CLIs

- [coldstart](https://github.com/princejain756/coldstart) (`npx coldstart-cli`) - replays your README's install instructions in a clean clone and reports the exact step where a new user hits a wall.
- [readmeroast](https://github.com/princejain756/readmeroast) (`npx readmeroast you/yourrepo`) - scores any GitHub README out of 100 and roasts what it's missing.
- [slopsieve](https://github.com/princejain756/slopsieve) (`npx slopsieve`) - score a diff or PR for 15 AI-slop review signals: test weakening, secret leaks, phantom imports, debug leftovers, dead exports. Also in Rust: [slopsieve-rs](https://github.com/princejain756/slopsieve-rs).
- [uislop](https://github.com/princejain756/uislop) (`npx uislop`) - static linter for React, Next.js, Vue, Svelte, and Tailwind that scores frontend files for 16 "vibecoded" AI UI tells (indigo/violet palette dominance, hardcoded Unsplash stock avatars, fake `"10,000+ developers"` social proof, Lucide icon-in-tinted-box cards, and dead `href="#"` links).
- [dep-census](https://github.com/princejain756/dep-census) - who actually maintains the code inside your `node_modules`.

## Live systems

- [MaintainerOS](https://github.com/princejain756/MaintainerOS) - command center for open-source maintainers: repo health, stale backlog, security readiness, issue triage, PR review, Actions reports. Live at [maintaineros.prince.sh](https://maintaineros.prince.sh).
- [Quantiti](https://quantiti.prince.sh) - live trading journal with real Zerodha Kite order routing.
- Day job: built and still operate the full stack for [Bigg Bounce](https://biggbounce.com), a 30,000 sq ft entertainment park in Bengaluru - ticketing site, self-service kiosks, POS, QR turnstiles, Razorpay UPI reconciliation, rain-day transfers. Rs 80 lakh+ recorded across 2,900+ paid bookings and 6,500+ POS orders in its first 20 days, backed by 46 Postgres migrations and a five-node Linux fleet.

## Upstream

32 PRs merged across query engines, compilers, drivers, and SDKs:

- **Vercel AI SDK (TypeScript):** MCP tool-output serialization fix carried into [vercel/ai#23935](https://github.com/vercel/ai/pull/23935) (merged with co-author credit); root-cause reproductions in [#23819](https://github.com/vercel/ai/pull/23819), [#23830](https://github.com/vercel/ai/pull/23830), [#23834](https://github.com/vercel/ai/pull/23834).
- **NousResearch/hermes-agent (Python):** sibling-site authority profile regression tests carried into [NousResearch/hermes-agent#150992](https://github.com/NousResearch/hermes-agent/pull/150992) (with co-author credit); active PRs [#146938](https://github.com/NousResearch/hermes-agent/pull/146938), [#146940](https://github.com/NousResearch/hermes-agent/pull/146940).
- **apache/datafusion (Rust):** correlated-subquery decorrelation [#26551](https://github.com/apache/datafusion/pull/26551) merged.
- **apache/arrow-rs (Rust):** record-batch interleaving [#11845](https://github.com/apache/arrow-rs/pull/11845) merged.
- **lancedb (Node/Python):** SDK fixes [#4584](https://github.com/lancedb/lancedb/pull/4584), [#4586](https://github.com/lancedb/lancedb/pull/4586) merged.
- **oxc (Rust):** linter AST traversal and WHATWG autofill rules, [#28008](https://github.com/oxc-project/oxc/pull/28008) merged, [#28109](https://github.com/oxc-project/oxc/pull/28109), [#28110](https://github.com/oxc-project/oxc/pull/28110).
- **JSqlParser (Java):** 6 merged SQL grammar/AST fixes, [#2838](https://github.com/JSQLParser/JSqlParser/pull/2838) through [#2843](https://github.com/JSQLParser/JSqlParser/pull/2843).
- **Pebble (Java):** 5 template-engine fixes merged, [#842](https://github.com/PebbleTemplates/pebble/pull/842), [#843](https://github.com/PebbleTemplates/pebble/pull/843), [#846](https://github.com/PebbleTemplates/pebble/pull/846), [#847](https://github.com/PebbleTemplates/pebble/pull/847), [#845](https://github.com/PebbleTemplates/pebble/pull/845) - #843 closed a bug open since 2021. Also [Handlebars.java#1200](https://github.com/jknack/handlebars.java/pull/1200), [#1201](https://github.com/jknack/handlebars.java/pull/1201) merged.
- **connectrpc/connect-es (TypeScript):** HTTP/2 session state handling [#1849](https://github.com/connectrpc/connect-es/pull/1849) merged.
- **rakazo (TypeScript):** 8 merged fixes in [#2125](https://github.com/elie222/rakazo/pull/2125)-[#2138](https://github.com/elie222/rakazo/pull/2138). Also [skardela#12](https://github.com/utk09-NCL/skardela/pull/12), [#13](https://github.com/utk09-NCL/skardela/pull/13) merged.
- **tokio-rs/bytes (Rust):** minimal-versions CI check + serde floor [#863](https://github.com/tokio-rs/bytes/pull/863) merged.
- **sqlalchemy (Python):** preserve recursive CTEs through `union().select()` [#13710](https://github.com/sqlalchemy/sqlalchemy/pull/13710) merged via Gerrit.
- **redis/lettuce (Java):** connection state handling [#3966](https://github.com/redis/lettuce/pull/3966) merged.
- **In review:** prefixed-model catalog lookup in [litellm#50645](https://github.com/BerriAI/litellm/pull/50645); VBAR `CombinedLinear` FP8/NVFP4 & unprefetched encode guards in [ComfyUI#17617](https://github.com/Comfy-Org/ComfyUI/pull/17617); streamed tool-call preservation in [agno#11526](https://github.com/agno-agi/agno/pull/11526); SpanQuery projection ordering in [Arize-ai/phoenix#17746](https://github.com/Arize-ai/phoenix/pull/17746); Mistral error classification in [pydantic-ai#12864](https://github.com/pydantic/pydantic-ai/pull/12864); git worktree resolution in [trigger.dev#5105](https://github.com/triggerdotdev/trigger.dev/pull/5105) and run-metadata JSON parsing in [trigger.dev#5052](https://github.com/triggerdotdev/trigger.dev/pull/5052); wait-option validation in [vercel-labs/agent-desktop#610](https://github.com/vercel-labs/agent-desktop/pull/610); `MaybeReversedEdgeReference` accessors in [petgraph#1066](https://github.com/petgraph/petgraph/pull/1066); structured logging arguments in [pmd#7225](https://github.com/pmd/pmd/pull/7225) (approved); GPU-budget accounting in [ray#67229](https://github.com/ray-project/ray/pull/67229); C-extension mapping conversion in [msgspec#1302](https://github.com/jcrist/msgspec/pull/1302); explicit `columnVisibility` on parent columns in [TanStack/table#6639](https://github.com/TanStack/table/pull/6639).

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-stats.vercel.app/api?username=princejain756&show_icons=true&theme=github_dark&hide_border=true&rank_icon=github&include_all_commits=true">
  <img src="https://github-readme-stats.vercel.app/api?username=princejain756&show_icons=true&hide_border=true&rank_icon=github&include_all_commits=true" alt="GitHub stats" height="160">
</picture>
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-stats.vercel.app/api/top-langs/?username=princejain756&layout=compact&theme=github_dark&hide_border=true&langs_count=8&hide=css,html,vue,mdx">
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=princejain756&layout=compact&hide_border=true&langs_count=8&hide=css,html,vue,mdx" alt="Top languages" height="160">
</picture>

## Elsewhere

[Portfolio (w.prince.sh)](https://w.prince.sh/website) · [Engineering Dossier](https://princejain756.github.io) · [MaintainerOS](https://maintaineros.prince.sh) · [Quantiti](https://quantiti.prince.sh) · [LinkedIn](https://www.linkedin.com/in/princejainai/) · [X](https://x.com/princejain756) · mail@prince.sh

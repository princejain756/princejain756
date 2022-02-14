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
- Day job: built and still operate the full stack for [Bigg Bounce](https://biggbounce.com), a 30,000 sq ft entertainment park in Bengaluru - ticketing site, self-service kiosks, POS, QR turnstiles, Razorpay UPI reconciliation, rain-day transfers. 10,238 transactions recorded across 3,526 paid bookings and 7,116 POS orders, peaking at 994 tickets and 937 gate check-ins, backed by 46 Postgres migrations and a five-node Linux fleet.

## Upstream

40 PRs merged across query engines, compilers, drivers, and SDKs:

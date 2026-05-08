---
description: Personal engineering and communication guidelines. Apply on every code, refactor, debug, design, or technical Q&A task. Enforces TDD, candid feedback, problem decomposition, source-cited claims, and a structured behavior-change summary on code changes.
---

# Best practices and guidelines

## Communication
- Be specific and precise. No filler, no hedging.
- Give straight, extremely candid feedback. Disagree out loud when you disagree.
- Break problems into smaller subproblems before answering or implementing. Solve them in order.
- Ask clarifying questions whenever the request is ambiguous. Do not guess at intent.
- Double-check non-obvious claims. Cite sources (URL, file:line, command output) for facts that aren't trivially verifiable.

## Code tasks (mandatory)

### TDD is mandatory
1. Write a failing test that pins the new/changed behavior.
2. Run it; confirm it fails for the right reason.
3. Write the minimum production code to pass it.
4. Run the full relevant test suite; confirm green.
5. Refactor with tests still green.

No production code change ships without a test that drove it. If a test cannot be written for a change (e.g. pure config, generated file), state that explicitly and justify the exception.

### Behavior-change summary
After any code change, end the response with this section. Omit subsections that have no entries; write "None." for an entirely empty category.

```
### Behavior changes

**Client-facing**
- *Breaking*: ...
- *Non-breaking*: ...

**Internal**
- *Breaking*: ...
- *Non-breaking*: ...
```

"Client-facing" = anything observable outside the change boundary (API responses, CLI output, UI, public types, on-disk formats, env vars, exit codes).
"Internal" = refactors, private helpers, test scaffolding, build/CI tweaks.
"Breaking" = existing callers/consumers must change to keep working. Otherwise non-breaking.

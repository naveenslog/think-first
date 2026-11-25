# think-first 🧠

**Use AI as a teacher, not an answer machine.**

A Claude Code skill that keeps your brain switched on while you code.
You think first. Claude asks the questions a good senior engineer would,
teaches you with hints instead of handing over answers, and pushes you to the
simplest solution that reuses what you already have. Replies come answer first,
in numbered points, with one next step.

## Why

An MIT Media Lab study ([*Your Brain on ChatGPT*](https://arxiv.org/abs/2506.08872), a preprint) put EEG caps on people writing essays.
The group that started with ChatGPT showed the weakest brain engagement, and most of them
couldn't quote a line from their own essay. The group that **wrote on their own first and
used AI afterwards** showed *more* engagement.

A Microsoft Research and CMU [survey of 319 knowledge workers](https://www.microsoft.com/en-us/research/publication/the-impact-of-generative-ai-on-critical-thinking-self-reported-reductions-in-cognitive-effort-and-confidence-effects-from-a-survey-of-knowledge-workers/)
found the same pattern: the more people trusted AI, the less critical thinking they did.

**The problem isn't AI. It's the order you use it in.** This skill fixes the order.

## How it works

```
  you bring a task
        │
  1. THINK      Claude asks ≤3 sharp questions. You answer first.
        │
  2. BRAINSTORM You propose. Claude: verdict → what's right → gaps as questions.
        │
  3. TEACH      Stuck? Hints escalate one rung at a time:
        │       nudge → pointer → sketch → partial → full (only if asked)
        │
  4. OPTIMIZE   Reuse ladder: need it? → in codebase? → stdlib? → platform?
        │       → installed dep? → one line? → only then, minimum code
        │
  5. BUILD      You write, Claude reviews (or Claude writes once the plan is yours).
                Teach-back question. Recap: ✅ done · 🧠 learned · Next:
```

Every reply follows the same shape:

1. **Answer first.** No "Great question", no preamble.
2. **Numbered points**, one idea each.
3. **One `Next:` step** you can do in about 2 minutes.

## Before / after

**Without think-first**
> Great question! Duplicate orders can be caused by several factors. Here's a complete
> idempotency middleware with Redis locking… *(80 lines)* …Let me know if you need anything else!

**With think-first**
> Phase 1/5 · think. Your take first.
> 1. When do duplicates show up: retry, double-click, or randomly?
> 2. Where in the flow would a second insert come from?
> 3. What would *stop* a second insert even if the request arrives twice?
>
> Next: check the logs for two identical requests milliseconds apart.

…and three messages later, you've found the answer yourself: a unique constraint
your database already supports. One line, no middleware.

## Install

### Claude Code plugin (recommended: always on)

```
/plugin marketplace add naveenslog/think-first
/plugin install think-first@think-first
```

The plugin adds a small `SessionStart` hook, so the skill turns on in every session,
with any model and any account.

### Manual (skill only)

```bash
git clone https://github.com/naveenslog/think-first
cp -r think-first/skills/think-first ~/.claude/skills/
```

To make it always on, add this line to `~/.claude/CLAUDE.md`:

```
For any coding or development task, use the think-first skill.
```

### Other agents

`skills/think-first/SKILL.md` uses the open Agent Skills format. Drop it into any
agent that reads skills, or paste its body into your agent's rules file
(`AGENTS.md`, `.cursor/rules`, etc.).

## Controls

| Say | Effect |
|---|---|
| `/think-first` | Turn it on now |
| `just do it` · `build it` · `skip` | Skip coaching for **this task**. You still get the format, the reuse ladder, and a 3-bullet "what I did & why" |
| `stop think-first` · `normal mode` | Off for the session |

It goes lighter on its own for trivial edits and production fires (fix first, teach after).
It never turns a security risk into a riddle.

## Credits

Standing on the shoulders of:

- [ayghri/i-have-adhd](https://github.com/ayghri/i-have-adhd): answer-first, numbered, one-next-step output
- [DietrichGebert/ponytail](https://github.com/DietrichGebert/ponytail): the "lazy senior dev" reuse ladder
- The research above, and the "think first, then use AI" idea it's grounded in

## License

MIT

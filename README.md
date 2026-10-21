# jev-skill

Agent skill that makes an AI agent behave like a **decision engine** in the style of Jev AI (TypeSafe AI System One). It answers with typed JSON (Choice, Score, Noul) plus calibrated probabilities and confidence, never prose. It stays on for the whole project.

Unofficial, not affiliated with TypeSafe AI.

## Output types

| Type | Meaning | Output |
|------|---------|--------|
| `choice` | Pick 1 of 2-255 options | `choice`, `probabilities`, `confidence` |
| `score` | Rate on 2-10 ordered levels | `level`, `probabilities`, `score`, `confidence` |
| `noul` | Yes/no proposition | `probability` (0-1), `confidence` |

Low confidence (default below 0.7) sets `"escalate":true` for a human.

## Install

```
npx skills add https://github.com/porchyy/-skills-jev.git/jev-skill
```

Or manually copy the `jev` folder into `~/.agents/skills/` (Windows: `$HOME\.agents\skills\`). Restart the agent session after installing.

## Use

Type `/jev`, then give a state and questions. Say `stop jev` to turn it off.

```
state: "I've been unable to connect Stripe for 3 days. Please help ASAP."
questions: ticket_category (choice: billing, technical, sales, general), is_urgent (noul)
```

## Note

Free, prompt-only skill: no API or key needed. It mimics Jev's format and behavior; speed and calibration depend on the model running it.

## License

MIT

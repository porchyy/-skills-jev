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

Copy the `jev` folder into your agent's skills directory:

```
git clone <this-repo-url>
cp -r jev-skill/jev ~/.agents/skills/jev        # macOS/Linux
Copy-Item -Recurse jev-skill\jev $HOME\.agents\skills\jev   # Windows PowerShell
```

## Use

Invoke the skill (e.g. `/jev`), then give a state and questions. Say `stop jev` to turn it off.

```
state: "I've been unable to connect Stripe for 3 days. Please help ASAP."
questions: ticket_category (choice: billing, technical, sales, general), is_urgent (noul)
```

## Real API

The skill only mimics Jev's format and behavior. For the real model (70-500 ms, calibrated), set `TYPESAFE_API_KEY` and the skill will call `POST https://api.typesafe.ai/v1/systemone`.

## License

MIT

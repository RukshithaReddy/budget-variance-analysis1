# Budget vs Actual Variance Explainer

A small web app for finance teams. You enter budget and actual figures for revenue and expense lines. The app:

1. Calculates variance (Rs and %) for every line in code, so the numbers are exact.
2. Marks each line favourable or adverse (lower expense or higher revenue is favourable).
3. Flags lines beyond a review threshold (default 10%).
4. Asks Claude to write a short management commentary, following the rules in `skill/SKILL.md`.

Claude never does the arithmetic. It only receives the calculated figures and writes the narrative, which keeps every number traceable.

## Files

| File | Purpose |
|---|---|
| `index.html` | The page the user sees |
| `api/explain.js` | Server function: validates input, calculates variances, calls the Claude API |
| `skill/SKILL.md` | The Claude Skill: calculation rules, commentary format, safety rules |
| `vercel.json` | Tells Vercel to include the skill folder with the function |

## Deploy (about 20 minutes)

1. **GitHub:** create a free account, make a new repository (for example `variance-explainer`), and upload all these files keeping the folder structure.
2. **API key:** create an account at console.anthropic.com, add credits, and create an API key. Set a low monthly spend limit in the console.
3. **Vercel:** sign in at vercel.com with GitHub, click Add New > Project, and import the repository. Leave build settings as they are.
4. **Add the key:** before deploying, open Environment Variables and add `ANTHROPIC_API_KEY` with your key. Never put the key in the code or in GitHub.
5. **Deploy**, then open the Vercel link and click "Explain variances".

Optional: add an environment variable `CLAUDE_MODEL` if you want a specific model. The default is set in `api/explain.js`. Check the current model names in Anthropic's documentation, because they change.

## Test it yourself

Use the sample figures, then check by hand: Marketing 100,000 budget vs 118,000 actual is +18,000, which is +18.0%, adverse, and flagged at a 10% threshold. Net budget 90,000 vs net actual 117,000 is +27,000 (+30%), favourable.

## Limits

- Handles up to 30 lines per request.
- Single period, single currency (rupees).
- The commentary suggests items to check, never causes stated as fact.

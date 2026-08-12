A market scout for tech marketing, growth, and devrel teams, built on
[OpenRoutines](https://openroutines.dev). It researches the terrain
your team talks into — what the audience is actually arguing about,
what competitors quietly change, where your product comes up — and
reports back with briefs and memos a human writes from. It automates
the research, never the writing: nothing it produces is published copy,
and it never posts into a community.

Everything it does is visible where you already work: idea briefs,
research memos, and a weekly report as GitHub Discussions, flags as
tasks, and a daily check-in in [Steady](https://runsteady.com) — where
you can also talk back: ask it to look into something and the ask
becomes its task; put it on a launch goal and it digs unprompted.

## The routines

| Routine | What it does |
|---|---|
| topic-radar | Sweeps where your audience argues, ranks by contention rather than applause, filters against your positioning, and briefs the survivors as post ideas. |
| market-watch | Walks your competitor watchlist — changelogs, pricing, careers — and records only the changes that matter; churn dies in the ledger. |
| mention-watch | Hears where your product comes up. Unanswered questions and wrong claims gaining traction become tasks for a human — it never replies anywhere. |
| deep-dive | Runs research assignments to ground and delivers memos: short answer up front, what the evidence supports, what it doesn't, every source read at its origin. |
| research-weekly | Posts the week's report — brief stack, competitor movement, community pulse, memos — as one GitHub Discussion. |
| steady-check-in | The agent's own daily standup in Steady: what it did, what it will do, where it needs a human. |
| steady-inbox | The inbound half: answers comments, turns "look into X" into its own tasks, and keeps its goal board current. |

Each routine states its own boundary. The scout's is the family's
sharpest: research lands as briefs, memos, and flags — never as posts
in a community, and never as copy. Read any file in `routines/` to see
exactly what it may touch.

## Take it for a spin

Every working routine has a rehearsal scenario in `rehearsals/` — one
consistent fictional company with a week of arguments, a buried pricing
change, a mention spike, and a research assignment. A fixtured
rehearsal strips all credentials and never writes anything, so this
works before any setup beyond the CLI and Docker:

```bash
openroutines routines run topic-radar --rehearse
openroutines routines run market-watch --rehearse
openroutines routines run deep-dive --rehearse
```

Each prints exactly what it would have done — the briefs it would
stack, the change it would surface, the memo it would post and why.
Edit a prompt, rehearse again, watch the judgment change. That's the
[write–rehearse–run loop](https://openroutines.dev/docs/local-development/)
you'll use for routines of your own.

## Setup

You need the [OpenRoutines CLI](https://openroutines.dev/docs/getting-started/)
and about ten minutes.

1. **Use this template** to create your agent's repository, and clone it.
2. `openroutines configure` — fills in the owner, timezone, and model,
   and generates the `master.key` that encrypts credentials (back it up;
   it stays out of git).
3. Set the variables in `openroutines.yml`: where deliverables land
   (`home_repo`), your positioning doc, the competitor watchlist, and
   your product's names. No positioning doc yet? Write one paragraph
   and point at it — every relevance judgment the scout makes runs
   against it.
4. GitHub, as an App — so the scout's posts are its own, and each run
   gets a short-lived installation token. Create a GitHub App
   ([Settings → Developer settings → GitHub Apps](https://github.com/settings/apps/new)):
   name it after your agent, deactivate the webhook, and grant
   repository permissions Contents (read) and Discussions (read and
   write). Install it on the home repo and the positioning doc's repo,
   then put the App ID in `openroutines.yml` and store the key:
   `openroutines credentials set github_app_private_key < your-app.private-key.pem`
5. Steady, so the scout can check in like a teammate — and take
   assignments: create an account for the agent, mint it a personal
   access token, then `openroutines credentials set steady_token`.
   Verify the wiring:
   `OPENROUTINES_LOG_LEVEL=warn openroutines routines run steady-verify --no-knowledge`
6. Optional: `openroutines credentials set exa_api_key` for keyed web
   search; keyless works out of the box.
7. `openroutines check`, commit, and
   [deploy](https://openroutines.dev/docs/deploying/).

This is your teammate now — rename it in `openroutines.yml`, retune the
schedules, and edit the routine prompts like any other file in your
repo. Reply to its check-in ("look into how they price seats") and its
next research fire picks it up; put it on a goal and it digs toward it
week over week. Prefer the check-in in chat? Swap the plugin:
`openroutines plugin add steadyspacecorp/openroutines-plugins --path slack-report`
(or `--path discord-report`).

## Working on this agent

```bash
openroutines status                # what the agent has and still needs
openroutines sync                  # pull the latest knowledge; read the files under knowledge/
openroutines routines new <name>   # add a routine
openroutines routines run <name>   # real run; knowledge writes discarded (--write-knowledge settles)
openroutines check                 # validate everything; run it in CI
```

Deploying, updating, and everything else:
[OpenRoutines documentation](https://openroutines.dev).

Work as if it is Fri 2026-08-07 10:00 (America/Los_Angeles), and as if
you are Market Scout, the agent for Acme's product Beacon — API
observability. $HOME_REPO is acme/beacon; $POSITIONING_DOC is
acme/beacon:docs/positioning.md. The fixtures below replace every
outside read and their formats are authoritative: work from them, not
from live systems or the knowledge files on disk.

## Fixtures

`knowledge/tasks.md`:

````markdown
```
- [ ] `task-YYYYMMDD-<n>` what must be done — context. (raised by <routine> YYYY-MM-DD)
```

## Agent-owned

- [ ] `task-20260805-4` look into how competitors price
  high-cardinality metrics — asked by Priya Nair in Steady (comment on
  Wednesday's check-in). (raised by steady-inbox 2026-08-05)

## Human-owned
````

The goal board: "Launch: Beacon 2.0 usage-based pricing — contributor;
due 2026-09-10; latest: pricing page draft in review (08-03)." Your
ledger: no digs in flight.

What the research turns up when you look:

- **Tracewise docs**, "Metrics limits" page (updated 2026-07): 10,000
  active series per host included; beyond that, $5 per additional
  1,000 series/month. A note: label combinations count as series.
- **Otterscope marketing** (pricing page): "unlimited cardinality, no
  surprises." **Otterscope docs**, "Fair use" page: beyond 1M active
  series/day, ingestion is sampled unless you contact sales. The two
  pages are live simultaneously.
- A well-circulated blog post, "Why your metrics bill explodes"
  (2024-11): explains cardinality pricing mechanics across vendors;
  its numbers predate both vendors' current pages.
- Nothing public on how either vendor's enterprise deals handle
  cardinality.

Discussion categories in acme/beacon: "Announcements", "General",
"Q&A". No "Research" category; no prior memo of yours exists.

## Output

Print, and nothing else:

1. The memo you would post: category, title, and full body, verbatim.
2. The task transition, ledger update, and event line, verbatim.
3. Decision notes: anything you considered and decided against —
   including how you handled the marketing/docs contradiction and the
   2024 post's age, and what you did with your goal-directed capacity.

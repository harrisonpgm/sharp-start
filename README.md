# Sharp Start

Start/sit calls for Sleeper fantasy football leagues, built from sportsbook
betting lines rather than editorial rankings.

Open the site, enter your Sleeper username, and it reads your rosters, simulates
the week, and shows the lineup decisions that are actually close.

## How it works

Bookmakers price every relevant NFL player prop — receiving yards, rushing
yards, receptions, touchdowns — and those prices carry more information than a
projection number does. Two-sided prices are de-vigged to fair probabilities,
alternate line ladders give the *shape* of each player's distribution, and the
result is a fitted distribution per stat rather than a point estimate.

Those distributions are sampled jointly through a Gaussian copula, so a
quarterback and his receiver rise and fall together the way they do in reality.
Each simulated week produces a full lineup total, which is where floors,
ceilings, win probability and "who outscores whom" all come from.

The odds are identical for everyone, so they are computed once and shipped with
the page. Your rosters are read from Sleeper's public API in your own browser
and simulated there — nothing about your team is sent anywhere.

## Data

- Two-sided main lines: [Pinnacle](https://www.pinnacle.com)
- Alternate line ladders and anytime-touchdown prices:
  [The Odds API](https://the-odds-api.com)
- Rosters, scoring settings and matchups: [Sleeper](https://sleeper.com)

Kickers and defences have no prop market and are not projected.

## Honest limits

- Projections are unvalidated until they are backtested against completed weeks.
- Alternate ladder rungs are mostly quoted one-sided, so their margin is
  assumed rather than observed; tails are softer than they look.
- Touchdown modelling converts an anytime-TD probability into a scoring rate,
  which overstates heavy favourites somewhat until calibrated against history.

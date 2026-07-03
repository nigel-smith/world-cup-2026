# The Hop Box — World Cup 2026 Sweepstake

A single-page, static, responsive tracker for the pub sweepstake. No build step, no backend — just one HTML file.

## Put it on GitHub Pages

1. Create a new **public** repo on GitHub, e.g. `hopbox-worldcup-2026`.
2. Add this `index.html` to the root of the repo (drag-and-drop on GitHub, or `git add`/`commit`/`push`).
3. In the repo, go to **Settings → Pages**.
4. Under **Build and deployment**, set Source to **Deploy from a branch**, branch `main`, folder `/ (root)`.
5. Save. GitHub gives you a URL like `https://yourusername.github.io/hopbox-worldcup-2026/` within a minute or two.

That's it — no npm, no framework, nothing else to install.

## Updating results

Open `index.html` in any text editor and find the `RESULTS` object near the top of the `<script>` block. Each match looks like:

```js
{id:"m14", team1:"Argentina", team2:"Cape Verde", winner:null}
```

When that match finishes, just fill in the winner:

```js
{id:"m14", team1:"Argentina", team2:"Cape Verde", winner:"Argentina"}
```

Save, commit, push — the site rebuilds itself automatically because everything (the bracket, the strikethroughs, the prize tickets, who's still in) is calculated from that one object. You never need to touch the later rounds (Round of 16, quarter-finals, etc.) directly — once both matches feeding into one are decided, that next match's teams appear automatically. You only fill in its `winner` once **it's** been played.

## The winner announcement

Once you set the `winner` on the `final` match in `RESULTS`, a champion banner appears automatically at the top of the page with the winning team, flag, and the name of whoever had that team. Nothing shows there until then — no placeholder text.

## Structure of the file

- `TEAMS` — flag emoji + accent colour per country.
- `SWEEPSTAKE` — the 32 rows from the sheet (position, name, team).
- `RESULTS` — the actual knockout bracket (Round of 32 through Final), with `winner` fields you update as games are played.

Everything else in the script just reads those three objects and draws the page.

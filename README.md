# Herbicide vs Weed Battle: Agronomy Edition

A self-contained browser game about managing weeds in Western Australia using herbicides and integrated weed management. Open `weedmon.html` in any modern browser—no build or dependencies.

## Goal
Win a best-of-5 series by defeating weeds in individual rounds. Reduce the current weed’s HP to 0 before you run out of money.

## Play loop
1. Open `weedmon.html` and review the current weed (name, growth stage, susceptibilities/resistances).
2. Click herbicides and optional non-chemical actions; each choice adds to Pending Cost.
3. Click “Execute Combined Attack” to spend the Pending Cost and damage the weed.
4. Defeat the weed to earn money and advance. First to 3 wins (or most wins after 5 rounds) wins the series.

## Core rules
- Rounds & series
  - Up to 5 rounds; first to 3 wins takes the series.
  - A new random WA weed appears each round (with growth stages and MoA traits).
  - At round start, weeds can advance growth stage and may trigger a random event.

- Money
  - Start with $100.
  - Each selected herbicide/action adds to Pending Cost; you must have funds to queue and execute.
  - Defeating a weed pays its max HP plus a tiered bonus (+$50 for your 1st win of the session, +$75 for 2nd, +$100 thereafter).
  - Some random events deduct money.

- Bankruptcy & loans
  - If funds drop below the cheapest actionable option, you’re “Out of Money.”
  - You may take up to 3 bank loans to continue: $100, then $75, then $50. After that, it’s Game Over.
  - A loan starts a new round with a fresh weed.

- Damage calculation (high level)
  - Base damage from each herbicide’s strength.
  - Susceptible MoA → 1.5× damage.
  - Resistant MoA → ~0.5× damage, plus possible counter-effects (weed HP gain, extra costs, or new resistance).
  - Scouting reveals a specific weakness; matching MoA deals 2× damage.
  - Stage fit matters: pre-emergent excels at seedling; post-emergent excels after seedling. Mismatch reduces damage.
  - Using multiple distinct MoAs gives a 10–30% synergy bonus to total damage.
  - Some WA-specific weed–MoA pairs are boosted for realism (e.g., HPPD vs Annual Ryegrass).

- Non-chemical actions (most apply to the next attack)
  - Adjuvant: +20% total damage.
  - Spot Spraying: 5× total damage.
  - Summer Weed Control: immediately halves the current weed’s HP and max HP.
  - Seed Destructor (persistent): prevents growth-stage advance and mutation/HP boosts in current/future rounds.
  - Crop Rotation (persistent): reduces all future weeds’ max HP by 40%.
  - Scouting: reveals the current weed’s specific weakness for this round (see Weed Info).
  - Call the Agro: highlights an efficient combo and doubles damage (2×) for the next attack.

- Random weed events (start of round)
  - Seed spread → pay cleanup cost.
  - Resistance surge → pay management/research cost.
  - Mutation → weed gains HP (prevented if Seed Destructor is active).

- Win/Loss
  - Round win: weed HP reaches 0 → earn money and advance to next round.
  - Round loss: bankrupt with no loans left → Game Over.
  - Series end: first to 3 wins or after 5 rounds; most wins wins (draw possible).

## Tips
- Combine distinct MoAs for a synergy boost.
- Match herbicide type to growth stage (pre at seedling; post after seedling).
- Use Scouting to target weaknesses.
- “Call the Agro” both advises and doubles damage; great when you can afford it.
- Invest in persistent actions (Seed Destructor, Crop Rotation) for multi-round gains.

## Attribution & notes
- MoA group lines align with CropLife Australia Herbicide Mode of Action Table (accessed 2025). Effects are simplified for education—always consult current labels and APVMA resources.

Customization: edit `weedCardsData`, `controlCardsData`, and `nonHerbicideActionsData` inside `weedmon.html`. 

# FFW Loadout Planner

A single-page interactive configuration planner and calculator for **Far Far West** (Early Access, Evil Raptor / Fireshine Games).

## Features

- **Build Identity** — Name + notes textarea
- **Primary Weapon Panel** — All 5 primaries (Leveredge, Long Ranger, Minigun, Quad Cylinder, Shotgun) with full upgrade allocation (Damage, Fire Rate, Clip Size, Reload Speed, Draw Speed, Accuracy) up to 26-slot prestige cap
- **Secondary Weapon Panel** — All 5 sidearms with elemental type selector + Lifesteal upgrade + unique joker filtering
- **Joker Cards** — Full library of 95 jokers across 6 rarities (Normal/Fine/Prime/Mythic/Legendary/Unique) with per-slot point budget validation (16-point cap)
- **Hero Profile** — 5 hero upgrade categories (Health, Spell CDR, Speed, Ammo Bag, Jump Height) with 26-slot cap + hero-specific joker slots
- **Utility Slot** — 4 utility items with Toolbox joker detection
- **Spell Slots** — All 25 spells across 5 schools (Pyro/Elec/Acid/Voodoo/Cactus) with live elemental combo hint detection
- **Real-Time Calculator** — DPS, single-hit damage, joker damage multiplier, HPS (lifesteal + healing jokers), and hero HP pool
- **Import / Export** — Full state serialized to Base64 JSON for sharing

---

## Deploying to GitHub Pages

### Option A: Direct Upload (Easiest)

1. Create a new GitHub repository (e.g. `ffw-loadout-planner`)
2. Upload `index.html` to the repository root
3. Go to **Settings → Pages → Source** → set branch to `main` / `master`, folder to `/ (root)`
4. Click **Save**. Your planner will be live at:
   ```
   https://<your-username>.github.io/ffw-loadout-planner/
   ```

### Option B: Via Git CLI

```bash
# 1. Clone or create repo
git init ffw-loadout-planner
cd ffw-loadout-planner

# 2. Copy index.html into this folder
cp /path/to/index.html .

# 3. Commit and push
git add index.html
git commit -m "Add FFW Loadout Planner"
git branch -M main
git remote add origin https://github.com/<your-username>/ffw-loadout-planner.git
git push -u origin main

# 4. Enable Pages in GitHub Settings → Pages → Source: main / root
```

The site will appear at `https://<your-username>.github.io/ffw-loadout-planner/` within ~60 seconds.

---

## Sharing Builds

1. Build your loadout in the planner
2. Click **Export ⬆** — a Base64 code is generated and copied to clipboard
3. Share the code with teammates; they paste it into the **Build Code** field and click **Import ⬇**

You can also pass the code as a URL parameter to deep-link a build directly:
```
https://yoursite.github.io/ffw-loadout-planner/?b=<BASE64_CODE>
```

---

## Data Sources

All stats sourced from the official community wiki at **farfarwest.wiki.gg** and corroborated against multiple fan guides:

| Mechanic | Source |
|---|---|
| Weapon base stats | farfarwest.wiki.gg/wiki/Equipment + wikily.gg/weapons |
| Upgrade slot counts & caps | farfarwest.wiki.gg/wiki/Equipment |
| Joker rarity & slot costs | farfarwest.wiki.gg/wiki/Jokers |
| Full joker list (95 cards) | allthings.how joker tier guide |
| Prestige slot caps (14→16) | farfarwest.wiki.gg/wiki/Jokers |
| Hero upgrade categories | vpesports.com prestige guide |
| Spell list (25 spells / 5 schools) | farfarwest.wiki.gg/wiki/Spells |

> **Note:** This tool is in Early Access parity with the game. Stats and joker counts may change with patches. The wiki community actively maintains data at farfarwest.wiki.gg.

---

## Calculator Formulas

### Weapon DPS
```
effectiveDmg = baseDmg × (1 + dmgSlots × 0.05)
effectiveRate = baseFireRate ÷ (1 + frSlots × 0.05)
DPS = (effectiveDmg ÷ effectiveRate) × jokerDmgMultiplier
```

### Joker Damage Multiplier
Additive sum of all equipped joker `dmgMult` values across primary + secondary + hero slots.

### HPS (Healing Per Second)
```
lifestealHPS = secDPS × (lsSlots × 0.03)
hitMeHPS     = hitMeCount × 0.25   [0.5 HP/s for 20s, est. once per ~40s]
lifePactHPS  = lifePactCount × 0.50
secondWindHPS = secondWindCount × 0.28  [50 HP / 180s]
soulSiphonHPS = soulSiphonCount × 0.50
voodooHPS    = voodooHealSpellCount × 1.0
totalHPS = sum of above
```

### Hero HP
```
effectiveHP = 100 × (1 + healthSlots × 0.06)
[−30% if Life Pact equipped]
[−25% if Glass Cannon equipped]
[−30% if West Wizard equipped]
```

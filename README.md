# FFW Build Calculator

A single-page interactive configuration planner and calculator for **Far Far West** (Early Access).

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

## Sharing Builds

1. Build your loadout in the planner
2. Click **Export ⬆** — a Base64 code is generated and copied to clipboard
3. Share the code with teammates; they paste it into the **Build Code** field and click **Import ⬇**

You can also pass the code as a URL parameter to deep-link a build directly:
```
https://yoursite.github.io/ffw-loadout-planner/?b=<BASE64_CODE>
```

---

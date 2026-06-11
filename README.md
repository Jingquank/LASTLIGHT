# LAST LIGHT

A turn-based Russian-roulette duel for 2–4 players sharing one device. A revolver, a table, a single swinging bulb. PS1-era survival horror, in one self-contained HTML file.

Three.js from CDN; all geometry procedural, all audio synthesized, all textures canvas-generated. The only assets are fonts (Google Fonts **DotGothic16** for UI/body + local **Ancho UltraBold** for display moments, which degrades gracefully if missing).

## Run

Serve the folder over HTTP (the local font won't load from `file://`):

```bash
python3 -m http.server 8123
# open http://localhost:8123/
```

Internet is required for the Three.js CDN and DotGothic16.

## How to play

1. Pick player count, enter names, sit down.
2. Each round the revolver is loaded with a **public** mix of live/blank shells (R1 = 1/3, R2 = 2/3, R3 = 2/2, R4 = 3/2, R5+ = 4/2), in hidden random order.
3. On your turn: optionally use items, then aim at anyone — including yourself — and hold to fire.
   - Blank + self: **free extra turn.**
   - Live: target loses 1 HP (2 with Hollow Point). 0 HP = out.
4. Pass the device only on the green handoff screen — it hides all private info.
5. Last player breathing wins.

**Items** (refill to 3 per round): Lens · Flask · Handcuffs · Hollow Point · Cigarette · Mirror · Ledger.

## URL parameters

| Param | Effect |
|---|---|
| `?seed=42` | Reproducible shuffles/draws (seed shown on title screen) |
| `?debug=1` | 3× animation speed, short hold-to-confirm, `window.LL` console handles (`LL.give(player, 'lens')`, `LL.hurt(player)`) |
| `?sim=1` | Headless self-test: 300 random reducer-only matches, invariants asserted, PASS/FAIL panel |

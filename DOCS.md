# rsg-robbery — Developer Docs

## Overview
Player-to-player robbery: target a player with hands up via rsg-target, cuff them, and open their inventory. Victims can be uncuffed by the robber, by another player, or auto-uncuff after `Config.AutoUncuffTime`.

## Dependencies
- `rsg-core` (locales, notify)
- `rsg-inventory` (with the one-line cuffed-target fix from the README)
- `rsg-target`

No ox_lib dependency — locales load from `@rsg-core/shared/locale.lua` and notifications use `RSGCore:Client:Notify`.

## Files
| File | Purpose |
|---|---|
| `shared/config.lua` | Distances, cooldown, auto-uncuff timer |
| `client/client.lua` | rsg-target global player options (`rob_player`, `uncuff_player`), cuff animation/effects |
| `server/server.lua` | Validation (distance, cooldown, handcuffs item, vehicle, cuffed state), cuff metadata, uncuff, auto-uncuff |
| `server/versionchecker.lua` | Checks GitHub for updates |
| `locales/*.json` | en, de, el, es, fr, ja, nl, pl, pt-br, ro |

## Config
| Key | Default | Description |
|---|---|---|
| `Config.RobDistance` | 2.5 | Max distance to rob |
| `Config.CuffDistance` | 1.5 | Max distance to cuff |
| `Config.RobCooldown` | 30000 | ms between robberies |
| `Config.AutoUncuffTime` | 120000 | ms before auto-uncuff (0 = off) |

## Localisation
Set the language with `setr rsg:locale <code>`. Keys live under `robbery.*`.

## Security
All checks (distance, cooldown, item, state) are server-side; client target options only request the action.

# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository purpose

This is **not** an application codebase — there is no source code, build system, package manifest, or test suite anywhere in the repo. It is an asset/output repository for **Dominus Assessoria** (`@dominus_assessoria`), holding:

- `artes_geradas/` — generated Instagram marketing graphics (feed posts, stories, carousels), produced by an external image-generation pipeline that is **not** part of this repo.
- `privacy-policy.html` — a standalone static privacy-policy page for the "Dominus App", a Meta/Instagram Graph API integration used to auto-publish content to `@dominus_assessoria`. This page exists to satisfy Meta's app-review requirement for a publicly hosted privacy policy; it has no dependencies and is served as-is.

Since there is no build/lint/test tooling, "development" in this repo means adding, renaming, or replacing PNG assets and editing `privacy-policy.html` directly — there are no commands to run.

## `artes_geradas/` naming conventions

Files follow a content-calendar naming scheme. Reading multiple filenames together (not just one) is necessary to understand the pattern:

- **Image dimensions signal placement**: `1080x1080` = feed post (square), `1080x1920` = Instagram Story (9:16). Check dimensions before assuming a file's slot.
- **Numbered singles** (`001_stories_...png`, `002_feed_...png`, ...): early one-off pieces, prefix is a sequence number, followed by a short slug describing the content.
- **Weekly calendar series** `sN_<dia>_<hora>_<tema>.png` (e.g. `s1_seg_11h_estrategia.png`, `s3_qui_19h_funil_edu.png`): `sN` = campaign/sprint week number, `<dia>` = Portuguese weekday abbreviation (`seg`=Mon, `ter`=Tue, `qua`=Wed, `qui`=Thu, `sex`=Fri, `sab`=Sat), `<hora>` = scheduled posting time, `<tema>` = topic slug. A `story` variant of the same slot uses `_story_<slug>` instead of an hour.
- **`sab_sN_17h_reflexao.png` / `_manifesto.png`**: Saturday reflection/manifesto posts, one per week.
- **`semana_<dia>_<hora>_<tema>.png`**: an alternate/earlier weekly-calendar naming variant, same day/time/topic structure as the `sN_` series.
- **`dom_sN_<hora>_<tema>.png`**: "Dominus"-branded weekly series, posts at `10h` and `18h`.
- **Carousels** `carrN_NN_<slug>.png` and `viral_<tema>_sNN[_hook|_cta].png`: multi-slide carousel posts. Slides are ordered by the `NN` index; slide 1 is typically `_cover`/`_hook` and the last slide is `_cta` (call to action).
- **`teste_*` / `vps_test_*` / `_test_font.png`**: throwaway test renders (font rendering, VPS deployment pipeline checks) — not scheduled content. Don't treat these as part of the content calendar.
- **`post_diagnostico_velocidade(_v2).png`**: standalone (non-calendar) post, `_v2` denotes a revised version of the same piece.

When adding a new generated asset, match the naming pattern of the series it belongs to (day/time/topic order, language in Portuguese, `snake_case`) so the file sorts and reads consistently with its neighbors.

## Commit conventions

Commit messages are in Portuguese and follow the pattern `Adiciona <filename>.png` ("Add <filename>.png") for new assets — one commit per asset is the norm in this repo's history.

## `privacy-policy.html`

Plain static HTML, no build step. Content is in Brazilian Portuguese and documents the Instagram/Meta API integration's data practices for `@dominus_assessoria`. If editing, keep the "Última atualização" (last updated) date in sync with the change.

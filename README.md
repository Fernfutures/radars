# site — the radar pages

```
site/{client}/{KEY}/index.html      DIP's to write: the client's radar page for that radar
site/{client}/{KEY}/radar.json      the RADAR object the page's script reads, written beside it
site/{client}/{KEY}/{YYYY-MM}/      the month's copy, left as the month ended (the archive)
site/assets/…                       ours: the files the pages link, see site/assets/README.md
```

`{client}` is the client code lower-cased (`lcl`), `{KEY}` the subscription's key as the
`radars:` block spells it (`C01-ES`: DIP's sector code and the ISO country). DIP (its D80)
writes every file under `site/{client}/` on its daily feed run, from the words in its own
tables; nothing in this repo edits, generates or validates them — `lib/validate.py` gates
`data/radar_feed/` and `data/radar_watch/` only. A page is written only once DIP's words
for the radar are filled; until then the folder does not exist and the routines treat
that as "not yet", not as an error.

A page links its assets as `../../assets/…` (an archive page one level further up), so a
client's own files — logo, host photo, an own hero — go under `site/assets/clients/{client}/`
(`site/assets/clients/lcl/logo.svg`), and a DIP `pipeline.assets` row names each one.

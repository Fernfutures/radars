# site/assets — the pictures the radar pages serve

DIP's radar feed (`data/radar_feed/{radar}/{code}.json`) names files under this folder; it never carries an image
itself. Which file it names is decided from DIP's `pipeline.assets` table (its D78), where every file here has a row:
its path, what it is for, where it came from, its credit, and whether the owner approved it. **A file with no approved
row is never named by the feed; a row whose file is missing here breaks the page** — add the file and the row together.

```
site/assets/sectors/{sector_code}/…    a sector's hero set: pictures or clips (.mp4 .webm .mov) for every radar of that
                                       sector (any FISC level: c01/, c0213/ — the radar's code starting with the folder's
                                       code is enough); the feed rotates the set monthly, one per issue month, in path order
site/assets/themes/…                   one picture per Level 3 theme (the newsletter chart's labels), the fallback for a
                                       story whose outlet does not allow hotlinking and whose company has no logo
site/assets/clients/{code}/…           a subscription's own hero file, which beats the sector set for that client's radar
site/assets/companies/…                company logos (DIP's #237: favicon or og:image of the company's site, approved)
```

In the feed: `hero` is null or `{video, image, credit}` (one of the two files set); each trigger and story has `image`
and `image_credit`, null when there is none — an `https://` URL when the outlet allows hotlinking its og:image (credited
to the outlet), else a path under `site/assets/` (credited as its row says). `lib/validate.py` enforces the shapes.

Lower case, ASCII, no spaces in file names; keep each file small (a hero clip under 10 MB, a picture under 500 kB).

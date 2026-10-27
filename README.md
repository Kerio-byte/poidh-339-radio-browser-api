# poidh #339 — Radio Browser API, live evidence

Submission for the poidh bounty "find the most useful free API nobody knows about"
(chain arbitrum, bounty 339). Claim window closes November 5, 2026.

## What is here

- `proof-final.png` — the response and the stats endpoint rendered as one image (1280x800)
- `evidence/stats.json` — raw output of `GET https://de1.api.radio-browser.info/json/stats`
- `evidence/demo_jp.json` — raw output of the Japan query used in the claim
- `evidence/demo_fi_news.json` — same endpoint, Finnish news stations
- `evidence/tags_top.json` — top tags by station count

All files were captured on 27 October 2026, from the public endpoint, with no key,
no account and no cookies.

## Reproduce

```sh
curl -s -A 'nalvorn-research/1.0' https://de1.api.radio-browser.info/json/stats

curl -s -A 'nalvorn-research/1.0' \
  "https://de1.api.radio-browser.info/json/stations/bycountrycodeexact/JP?hidebroken=true&order=clickcount&reverse=true&limit=1"
```

## Honest notes

- 7,029 of 63,184 entries are marked broken — always pass `hidebroken=true`.
- `url_resolved` follows playlists and redirects; `url` sometimes points at an .m3u8.
- Key on `stationuuid`, not on the station name.
- The mirrors are donated hardware; send a descriptive User-Agent and keep the request rate low.

## API

Free, no account, no API key, no subscription: https://de1.api.radio-browser.info/

# weather.oddsengine.live — retired

Redirects to `public.oddsengine.live`.

## Why

The map read from `oddsengine-weather-api`, whose `DROPLET_IP` variable pointed
at the droplet destroyed on 11 July. The chain was dead, so the live page sat
on "Initializing… Loading…" forever.

It was also claiming things that had stopped being true:

- "35 cities" — there are 50, discovered dynamically
- "Live edge detection" — nothing was live
- "OpenWeatherMap · Wunderground" as data sources — neither is in the pipeline
- `theme-color: #00d97e` — green, from an earlier brand

## Why retired rather than rebuilt

Wind, rain and cloud layers look good and help nobody decide anything. The
product is the probability per bracket, and the dashboard shows that for all
50 cities with the price and the edge beside it.

Three public surfaces for a product that has not yet posted a live signal is
one too many. Every surface left standing eventually shows something stale —
this page is the proof.

If a map earns its place later — showing where the models disagree, say — build
it then, on data that exists.

## Cleanup

`oddsengine-weather-api` (Railway project `overflowing-liberation`) is the
service this page called. It still holds `DROPLET_IP`, `TRADE_API_KEY` and
`WALLET_ADDRESS` as variables, all pointing at a machine that is gone. Nothing
uses it now. Delete the service, or at minimum remove the variables — a live
`WALLET_ADDRESS` sitting in a service nobody calls is a liability with no
upside.

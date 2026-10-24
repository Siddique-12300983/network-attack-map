# network-attack-map

An animated world map of "live" cyber attacks: glowing arcs fly between cities,
impacts pulse on arrival, and a feed scrolls past with a running counter. It is
the kind of visual you see on a security operations centre wall.

**Live:** https://siddique-12300983.github.io/network-attack-map/

## This is a simulation

Every attack on this map is made up. The data is random, generated in your
browser, and has nothing to do with real network traffic. It is a decorative
demo, labelled "SIMULATION" on the page so nobody mistakes it for a real threat
feed. Real attack maps you see online are mostly the same idea: a nice visual
built on sampled or delayed data, not a literal view of the internet.

## What it shows

- A dotted world map drawn on a canvas
- Animated arcs between major cities, coloured by attack type (malware, DDoS,
  phishing, exploit, brute force, scan)
- Impact pulses when an arc lands
- A scrolling live feed with timestamp, route and target port
- A running counter and a colour legend

## How it is built

One HTML file, no build step, no libraries and no network requests. The map is
drawn with the Canvas 2D API:

- Land is a grid of dots. Each candidate point is tested against a set of coarse
  continent polygons with a point-in-polygon check, and kept if it falls on
  land.
- Cities are placed by latitude and longitude using an equirectangular
  projection.
- Each attack animates along a quadratic Bezier curve with a lifted control
  point, which gives the arcs their shape.

It runs entirely client-side, so it is cheap to host on GitHub Pages and works
offline once loaded.

## Running it locally

```bash
python -m http.server 8000
# then open http://localhost:8000
```

## Tech

Plain HTML, CSS and JavaScript with the Canvas API. Dark theme, works on mobile.

## License

MIT. See [LICENSE](LICENSE).

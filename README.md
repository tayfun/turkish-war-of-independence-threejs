# The Turkish War of Independence — a three.js animation

A single-page 3D animation that follows the Turkish War of Independence (Kurtuluş Savaşı) on a relief map of Anatolia, from the Armistice of Mudros in October 1918 to the proclamation of the Republic on 29 October 1923.

It plays through 13 chapters in about 2 minutes 50 seconds:

1. Armistice and occupation
2. The landing at Samsun
3. Amasya, Erzurum, Sivas
4. The National Pact and the south
5. The Grand National Assembly
6. The Treaty of Sèvres
7. The eastern front
8. The battles of İnönü
9. The Battle of Sakarya
10. The Great Offensive
11. İzmir and Mudanya
12. The Treaty of Lausanne
13. The Republic of Türkiye

## Run it

Open `index.html` in a browser. Everything is in that one file; three.js (r160) and the fonts load from public CDNs, so you need a network connection.

To serve it locally:

```bash
python3 -m http.server 8000
```

Then open <http://localhost:8000/>.

## Controls

- **Play / pause:** the gold button, or the space bar
- **Jump to a chapter:** click it on the rail, or use the left and right arrow keys
- **Look around:** drag to orbit, scroll to zoom, double-click to reset

## How it is built

- The coastlines and borders come from Natural Earth (via the `world-atlas` package), embedded in the page as compact JSON.
- The terrain is stylised, not surveyed: elevation is generated from a hand-placed model of the main ranges plus noise, so mountains are in the right places but individual valleys are not real.
- Occupation zones, front lines and the Sèvres partition are approximate shapes drawn for clarity.
- The border lit at the end is the one recognised at Lausanne, so Hatay (which joined in 1939) is left outside it.

## Known limits

- Close-up terrain is soft at the lowest camera angles.
- The phone layout works, but the widest shots crop the far west and east.
- There is no audio.

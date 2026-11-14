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

It runs in English or Turkish. The language follows the browser, and the EN / TR switch on the control bar changes it at any time (the choice is remembered). Add `#tr` or `#en` to the address to link straight to one language.

Turn on sound with the speaker button to hear each chapter narrated in the chosen language over a score that changes with the chapter. With sound on, each chapter slows down to the length of its narration, so the whole piece runs about five minutes. When the story ends, a hopeful closing theme plays on a loop until you turn the sound off or press replay.

## Run it

Serve the folder and open it in a browser. three.js (r160) and the fonts load from public CDNs, so you need a network connection. The narration is in `audio/`; browsers will not load it when `index.html` is opened straight from disk, so use a local server:

```bash
python3 -m http.server 8000
```

Then open <http://localhost:8000/>.

## Controls

- **Play / pause:** the gold button, or the space bar
- **Jump to a chapter:** click it on the rail, or use the left and right arrow keys
- **Look around:** drag to orbit, scroll to zoom, double-click to reset
- **Sound:** the speaker button turns narration and ambience on or off (browsers only allow sound after a click)
- **Language:** the EN / TR buttons

## How it is built

- **Coastlines and borders:** Natural Earth 1:50m (via the `world-atlas` package), embedded in the page.
- **Relief:** real elevation from the Mapzen / AWS Terrain Tiles (SRTM-derived), resampled to a 720 × 379 grid and embedded as a small PNG. Heights are exaggerated about elevenfold so the relief reads at map scale.
- **Lakes:** real outlines. Tuz, Van, Urmia, Sevan, Beyşehir and Eğirdir come from Natural Earth 1:10m; İznik, Uluabat, Sapanca, Burdur, Acıgöl, Eber, Hazar and Çıldır come from OpenStreetMap. The big reservoirs (Keban, Atatürk, Assad) are left out because they did not exist in 1923.
- **Rivers:** Natural Earth 1:10m, with the Sakarya, Porsuk, Yeşilırmak, Gediz, Seyhan and Çoruh from OpenStreetMap.
- **Places:** every town on the map was checked against the GeoNames gazetteer and sits within 3 km of its listed position.
- **Railways** are drawn by hand through the real stations of the lines that existed in 1920, so the route between stations is approximate.
- **Occupation zones, front lines and the Sèvres partition** are approximate shapes drawn for clarity.
- **Borders:** the border lit at the end is the one recognised at Lausanne, so Hatay (which joined in 1939) is left outside it. Neighbouring countries are shown with their modern outlines.
- **Narration** (`audio/en-NN.mp3`, `audio/tr-NN.mp3`, one file per chapter and language) was generated with ElevenLabs text-to-speech (Eleven v4 Turbo) from the chapter text, with a delivery direction per chapter. Pauses at full stops and before quotations were then set from the returned word timings. The score (drums, bass and pads that change with each chapter's mood) is synthesised in the browser with the Web Audio API.

Map data: Natural Earth (public domain), © OpenStreetMap contributors (ODbL), Mapzen Terrain Tiles.

## Known limits

- The phone layout works, but the widest shots crop the far west and east.

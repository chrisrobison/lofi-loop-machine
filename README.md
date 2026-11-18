# Lofi Loop Machine

Vanilla HTML/CSS/JS, no build step. Serve this folder with any static server, for example:

    python3 -m http.server 8000

then open http://localhost:8000. (Opening index.html straight from disk blocks the
loop fetch in most browsers; you can still drag the loops onto the page.)

## Loops

`loops/manifest.json` lists the files plus `bpm` and `bars`. Files are named
`<instrument><number>.mp3` (bass01.mp3, beat07.mp3, piano12.mp3). Any new instrument
prefix becomes its own track: names with beat/drum/perc are treated as drums,
bass/sub as bass, piano/keys/rhodes/guitar/synth as keys, anything else as texture.

The bundled loops are 8 bars at 110 BPM (17.4545 s). Each file carries one extra beat
that repeats the downbeat, so the engine loops the region [0.08 s, 0.08 s + 17.4545 s]
instead of the whole file. That keeps loops gapless and skips any MP3 decoder priming.

## Seeds

The page address hash is the seed (`#maple-417`). The same seed always writes the
same run of songs.

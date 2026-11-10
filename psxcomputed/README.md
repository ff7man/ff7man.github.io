# PSX Computed Winner Lookup

![Screenshot of the PSX Computed Winner Lookup](screenshot.png)

This PSX-style race finder searches for a matching frame, then looks up cached
long and short winners without launching DuckStation. Matching bet tiles
receive `L` and `S` indicators.

Open the app at <https://ff7man.github.io/psxcomputed/>. Choose the race class,
enter chocobo #1's speed, stamina, name, any known gifts, and time since reset,
then search.

The frame counter is unsigned 32-bit and wraps after 2^32 (4,294,967,296)
frames, about 828 days at 60 fps. Searches wrap through the full cycle and pause
after every 5,184,000 searched frames (24 hours) to ask whether to continue.

The bundled winner database covers about the first hour of races, from frame
600 through frame 215,998. The game takes at least 10 seconds to reach the
betting screen, so frames 0–599 were intentionally omitted. Class C has short
race results; B, A, and S have both short and long results. Results outside the
available data range are unavailable; the app does not simulate finishes or
infer missing results. See the [source repository](https://github.com/ff7man/chocobo-betting/tree/main/psxcomputed)
for the builder, database format, and update instructions.

## Faster frame matching

The frame search uses `race_search.c` compiled to `race-search.wasm` to check
candidate seeds, then uses JavaScript to build the complete race after a match.
Serve the app over HTTP to enable WebAssembly; `file://` automatically falls
back to JavaScript. To rebuild from `psxcomputed/`, run this in the app folder:

```sh
cd psxcomputed
emcc race_search.c -O3 -s STANDALONE_WASM=1 -Wl,--no-entry \
  -Wl,--export=scan -Wl,--export-memory -o race-search.wasm
```

The winner database stores only unordered top-two bet pairs for each class
and course. Seven course results are packed at four bits each (28 bits per
frame), in C/B/A/S order with short before long; Class C has no long course.
The stored data omits finishing order because the bet grid only needs the pair.
The binary stores the start frame; the frame count is inferred from its packed payload length.

# Bass Practice Stand

A practice app for beginning upright (double) bass and flute. Type or paste a piece in
[ABC notation](https://abcnotation.com/), and it plays the piece on a loop
while showing:

- a fingerboard "note highway": upcoming notes slide toward a "now" line,
  colored by string (E pink, A amber, D blue, G green), each labeled with the
  finger to use, and the target spot on the fingerboard lights up on the beat
- for flute, every key in order as the flute is held, with the keys to press lit and a timeline of upcoming changes for each key
- a scrolling staff (bass or treble clef) with note names above each note

**Live site:** https://scjudd.github.io/bass-practice-stand/

## Features

- Loops with a count-in and a bar of rest between passes; tempo changes live
- Loop just a range of bars to drill a hard spot
- Library of pieces saved in the browser (`localStorage`), with import and
  export as JSON or `.abc` files; each piece records its instrument
  (`"instrument": "bass"` or `"flute"`, bass when missing, or a
  `%%instrument flute` line in the ABC)
- Fingering picked automatically (open strings first, as in beginner method
  books); override per note in the ABC with `!4!` (finger) or `"_D"` (string)
- Repeats and 1st/2nd endings, ties, triplets, dotted notes, rests, key
  signatures
- A copyable prompt for turning photos of sheet music into importable JSON
  with any AI assistant
- Works offline after the first visit, and installs to a phone's home screen

## Use it on a phone

Open the live site in Safari, tap **Share**, then **Add to Home Screen**. It
then opens full screen like an app. A home-screen app keeps its own library,
separate from the Safari tab, so import your pieces there.

## How it works

Everything is in `index.html`; there is no build step and no backend.
[abcjs](https://github.com/paulrosen/abcjs) (loaded from jsDelivr) parses the
ABC. The page then unrolls repeats, applies key signatures and accidentals,
merges ties, picks a string and finger for each note, and draws the staff and
fingerboard itself as SVG. Sound comes from a small Web Audio synth, written
at bass pitch (an octave below the written note). `sw.js` caches the page and
its scripts for offline use.

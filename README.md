# Squash

**Radio station limiting for internet audio levels**

Squash is a free limiter for your Mac's system audio. It helps control
loud DJs, quiet interviews and blaring station IDs at a steady,
comfortable level — similar to a broadcast limiter at a radio station.
One knob control.

## Download

[**Download Squash.zip**](https://github.com/jgirgus/squash/releases/latest/download/Squash.zip)
(always the latest release)

Requires a Mac on **macOS 14.2 or later**. Runs on Apple Silicon and Intel.

## One knob

- **Radio Limit** — the one scheme, and the one Squash was tuned around: smooth, transparent leveling.
- **A built-in governor** — however far you turn the knob, the leveling can only go so far, and a separate safety limiter catches the peaks.
- **Smooth recovery** — the gain eases back instead of bouncing, so the level never breathes or pumps.

## Screenshot

![Squash at 50%](shot-radio.png)

## A closer look

![The Squash knob at 50%](detail-knob.png)

**The knob** — the only control. Drag up or down to turn it — up means
Squash holds the level steadier. The band's colour shows where it's
set: green at the gentle end, through yellow and orange, to red at
full. It starts at 50%.

![The gain reduction meter showing -4.8 dB](detail-gr.png)

**Gain Reduction** — Squash at work. This meter shows how much it's
turning the sound down, moment by moment, to keep the loud parts in
line — squeezing in from the right, like the meter on a broadcast
limiter. Yellow is working, orange is pushing; red is saved for when
it's really leaning on the signal.

![The stereo Output meter and Output Volume slider](detail-output.png)

**Output** — what actually reaches your ears, left and right, after
Squash. However wild the level gets upstream, this stays steady.
Output Volume below it is just your Mac's volume — the final level,
set here or with the volume keys.

![The power button, its thin green ring lit](detail-power.png)

**Power** — Squash starts itself the moment you open it — if the ring
is green, it's running. The button is only there for switching it off,
and the line under the title will remind you how to start it again.

![The Bypass switch](detail-bypass.png)

**Bypass** — for comparing. Flip Bypass on and you hear the original
sound, completely untouched; flip it off and Squash steps back in.
It's the quickest way to hear what the app is doing for you.

## Under the hood

One knob on the surface; a small broadcast chain underneath. Squash
splits the work the way a radio station's processor does — a leveller
to even things out, then a safety limiter to catch what gets past it.

- **The leveller** — the knob sets this stage's threshold: −1 dB at
  zero, down to −36 dB at full, on a gentle curve (50% lands at
  −15 dB). Everything louder than the threshold is pulled down toward
  it, and automatic makeup lifts the result back toward the ceiling —
  which is what raises the quiet parts and tames the loud ones in a
  single move.
- **The governor** — an unbounded leveller would let you flatten
  music completely, so this one's gain window is fenced: at most
  14 dB of reduction, at most 15 dB of makeup. Turn the knob as far as
  you like — the leveller can only go so far, and whatever is left
  over is the safety stage's problem, not a crushed mix.
- **The safety limiter** — a plain brickwall at the −1 dB ceiling,
  with no makeup and a fast 120 ms release. It does nothing until a
  peak gets past the leveller — then it catches exactly that peak and
  steps aside again. In normal listening, this stage barely wakes up.
- **Lookahead, twice over** — each stage holds the audio back 1 ms
  and watches what's coming, so gain reduction is already in place
  before a peak arrives. Total latency: 2 ms — far too small to
  notice.
- **Anti-pumping release** — the leveller recovers in 400 ms when
  it's barely working. The deeper it has to dig (past 6 dB), the
  slower it lets go — stretching toward a full second, with the
  recovery rate capped between 12 and 5 dB per second, slowest when
  deepest — so the level can't bounce in time with the beat.
- **Warmth** — before the leveller, a touch of tanh soft-saturation
  (fixed at 20%) rounds the peaks and adds a trace of odd harmonics —
  about 1% third harmonic on a loud tone. It sits before the
  detector, so the ceiling still has the last word.
- **Stereo, linked** — the detector follows the louder of the two
  channels and applies one shared gain to both, so the stereo image
  never wanders.
- **Honest limits** — Squash limits sample peaks, not inter-sample
  true peaks; the −1 dB ceiling leaves headroom for that. And Bypass
  is a true bypass — unity gain, no warmth, no limiting, no makeup —
  for honest A/B comparisons.

## Installing

1. Download the zip and open it. Drag **Squash** into your Applications folder.
2. Double-click Squash once. macOS will refuse (it's careful with apps
   from outside the App Store.)
3. Open **System Settings → Privacy & Security**, scroll down, and click
   **Open Anyway**. (You only need to do this once.)
4. Launch Squash — it starts by itself — and allow audio capture when
   asked. (That prompt is the app doing its job.)

Squash processes your Mac's audio on your Mac. Nothing is recorded,
nothing is uploaded, there's nothing to sign up for. It only works while
it's running. Quit and your Mac sound is unchanged.

## Freeware

Squash is freeware: free to download, free to share.

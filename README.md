# Sentinel Air Strings

**Play invisible strings in the air.**

Sentinel Air Strings turns your webcam into an augmented-reality instrument. You pinch to hang points in the air, stretch glowing strings between them, and strum those strings with your fingers. Short strings sing high, long strings go low. It runs entirely in the browser: one HTML file, no install, no account.

### ▶ [Try the live demo](https://jameskeithharwood.com/sentinel-air-strings/)

Works in a desktop or phone browser. Allow camera access, turn your sound up, and start pinching.

![Sentinel Air Strings: glowing, tick-marked strings, each labeled with its note, with sparks flying off a freshly plucked string](screenshot.png)

---

## What it is

Your camera shows you as a mirror image. On top of that live view, the app draws the strings you create, so they look like they are floating in front of you. The camera tracks your hands, and your hands are the controller:

- Pinching places and moves points.
- Your fingertips are the picks that pluck the strings.
- Every string has its own pitch, color, and note name.

## How it works

| Piece | What it does |
|---|---|
| **Hand tracking** | [MediaPipe Hand Landmarker](https://ai.google.dev/edge/mediapipe/solutions/vision/hand_landmarker) finds up to 4 hands and 21 landmarks per hand in every video frame, right in your browser. |
| **Pinch detection** | A pinch is the distance between thumb tip and index tip, measured relative to the size of your hand, with hysteresis so it does not flicker. |
| **Strumming** | Each frame, the app checks whether a fingertip's path crossed a string. Faster crossings play louder. |
| **Pitch** | A string's pitch comes from its on-screen length. Shorter is higher, longer is lower. Pitch updates live as you drag a point. |
| **Pitch bend** | If you move a point while its string is still ringing, the note slides with it, like bending a guitar string. |
| **Sound** | Each pluck is synthesized with the Karplus-Strong plucked-string algorithm using the Web Audio API. No audio files are used. |
| **Effects** | A built-in pedalboard (drive, wah, tremolo, chorus, flanger, echo, reverb, octave) processes everything you play, all in real time in the browser. |
| **Visuals** | Canvas 2D: glowing strings with overtone wobble, tick marks, spark particles on every pluck, and a hand skeleton overlay. |

The camera image is processed on your device. Nothing from your video is uploaded anywhere. (The hand-tracking library and model are downloaded from public CDNs when the app loads, so you need an internet connection.)

## How to use it

1. Open the page and tap **Start**. Allow camera access when asked, and turn your sound up.
2. Wait a moment for "Hands ready" to appear.
3. **Place a point:** Pinch your thumb and index finger together in the air.
4. **Make a string:** Pinch a second time somewhere else. A string stretches between the two points.
5. **Retune a string:** Pinch near a point to grab it, then drag. Bring the points closer for a higher note, or pull them apart for a lower one. The note name is shown on each string.
6. **Strum:** Keep your fingers open and sweep them across a string. Strum fast for loud, glowing plucks.
7. **Delete a point:** Drag it to the ✕ in the bottom-right corner and release. Its string goes with it.
8. **Bend a note:** While a string is still ringing, drag one of its points. The pitch slides as you move. Bending up uses up the note faster, so a big bend ends it sooner.
9. Add as many strings as you like, up to 24 points. Each string plays independently, and they can cross.

### Controls

| Control | What it does |
|---|---|
| **Undo** (or `Z`) | Removes the most recently placed point and its string. |
| **Clear** (or `C`) | Removes everything. |
| **Scale** | Minor pentatonic, major pentatonic, major, blues, or free. The first four snap strings to notes in the scale; free lets pitch slide continuously. |
| **Key** | Sets the root note of the scale. |
| **Camera** | Turns the camera image on or off. The instrument keeps working over a plain background. |
| **Camera picker** | Appears when you have more than one camera (a webcam, DroidCam, a GoPro, a phone's front and back cameras). Your choice is remembered. A rear camera is shown unmirrored. |
| **Skeleton** | Shows or hides the green hand skeleton overlay. |
| **FX** (or `F`) | Opens the pedalboard (see below). |
| **Music** (or `M`) | Opens the beat, looper, and layouts panel (see below). `B` starts or stops the beat, `L` starts a loop take. |
| **● Rec** (or `R`) | Records a clip of your playing with its sound (see below). Stays on screen even with the menu hidden. |
| **Haptics** | Phones only: a short buzz on each pluck. Works on many Android phones; iPhones do not allow it. |
| **Hide menu** (or `H`) | Hides all the buttons and the instruction box for a clean, full-screen view. Tap the small ☰ in the top-right corner to bring them back. |

### Effects pedalboard

Tap **FX** to open eight pedals. Tap a pedal's name to switch it on (its light turns green), and use its slider to set how much. Your settings are remembered on that device. Echo starts on at a low level, and everything else starts off.

| Pedal | What it does | Slider |
|---|---|---|
| **Drive** | Distortion that turns the strings into a crunchy electric guitar. | How hard it saturates |
| **Wah** | A resonant filter that sweeps up and down, like a wah pedal. Raise your left hand to open it and lower it to close it. With fewer than two hands in view, it sweeps by itself ("WAH auto"). | Resonance |
| **Tremolo** | The volume pulses. | Depth |
| **Chorus** | Two slowly wobbling copies thicken the sound. | Mix |
| **Flanger** | A swept "jet plane" whoosh. | Mix |
| **Echo** | Repeating, darkening delays. | Mix |
| **Reverb** | Adds the sound of a room. | Mix |
| **Octave** | Adds a quieter copy of each pluck one octave up. | Mix |

The pedals are level-matched so switching one on does not suddenly make everything louder. Opening the pedalboard hides the instruction box and moves the ✕ up so nothing is covered, and **Hide menu** hides the pedalboard too (your effects stay on).

### Beat, looper, and layouts

Tap **Music** to open three sections. Your beat settings are remembered on the device.

**Beat.** Tap **▶ Beat** to start a drum beat to play along with. Choose **Rock**, **Hip-hop** (with a little swing), **Dance**, or **Click** (a plain metronome). Set the tempo (60 to 180 BPM) and the beat volume. The four dots show where you are in the bar, with beat one in green. The drums are synthesized, and they are timed by the audio clock rather than the screen, so they stay steady even when hand tracking is busy.

**Looper.** Works like a guitar loop pedal:

1. Pick a loop length (1, 2, or 4 bars) and tap **● Loop**. Recording starts on the next bar. If the beat was off, it starts and gives you one bar to get ready. The status line counts you in.
2. Play. When the loop length is up, what you played starts repeating, exactly in time with the beat.
3. Tap **● Loop** again to add a layer on top. Each layer records one full pass of the loop. You can stack up to six.
4. **Undo layer** removes the last layer, and **Clear loop** removes them all. Tapping **■ Cancel** while it is counting in or recording throws that take away.

The looper records the strings exactly as you heard them, effects and pitch bends included. It does not record the drums or earlier layers, so they never double up. Notes still ringing at the end of a loop are cut off where the loop repeats. While a loop exists, the tempo and loop length are locked, because the loop was recorded at that speed. Clear the loop to change them. Loops and the beat are included when you record a clip.

**Layouts.** **Save layout** stores your current strings, plus the scale and key, under a name you choose. Pick one from the list and tap **Load** to bring it back, or **Delete** to remove it. Layouts are kept on this device only. They are saved relative to the screen size, so on a different screen the strings land in the same places proportionally, and their notes may shift a little.

### Recording a clip

Tap **● Rec** to start. The button turns red and shows a timer. Tap it again to stop (clips stop on their own at 2 minutes). A card then shows your clip with **Save**, **Share** (on phones that support sharing files), and **Discard**.

- The clip records what is drawn on the instrument: your camera view, the strings, the sparks, and the app's sound with your effects. The buttons, menus, and pedalboard are not in the video, and the ✕ only appears while you are dragging a point.
- Your microphone is not recorded.
- The format depends on your browser. Most current browsers make an MP4. The card says **MP4 (H.264)** when it is the widely accepted kind. If it does not, some apps may refuse the file; try Share, or convert it to an H.264 MP4.
- For the cleanest clip, tap **Hide menu** and turn **Skeleton** off before recording.

### No camera? Use a mouse

Click to place points, click and drag to move them, and hover across a string to strum.

## Tips

- Use good, even lighting and keep your hands fully in frame.
- Play about an arm's length from the camera so both hands are clearly visible.
- Keep your strumming hand open. If your thumb and index finger drift together, the app reads it as a pinch and may place a stray point.
- A pinched hand does not strum, and an open hand does not place points, so you can use one hand to build and the other to play.

## Running it yourself

It is a single file named `index.html`, with no build step.

- **GitHub Pages:** Upload `index.html` to a repo and enable Pages. It works over https.
- **Locally:** Serve the folder from localhost, for example `python3 -m http.server`, and open `http://localhost:8000`.

Browsers only allow camera access on https pages or localhost, so opening the file directly from your disk will not work.

## Troubleshooting

- **"Camera unavailable":** Check your browser's camera permission for the site, and make sure no other app is using the camera.
- **A camera shows a solid green picture:** some virtual webcam drivers, such as the GoPro webcam app, send green when asked for a picture size they do not support. The app spots this and automatically tries other sizes. If it still shows green, set the camera to 1080p in its own app, restart that app, and pick the camera again. Regular webcams and phone cameras are not affected.
- **"Hand tracking failed to load":** The tracking library could not be downloaded. Check your connection and reload. Mouse mode still works.
- **No sound:** Start the app with the Start button (browsers require a tap before playing audio) and check your volume.
- **Choppy tracking:** Close other heavy tabs and apps. A phone or laptop with a modern GPU will track more smoothly.

## Built with

- [MediaPipe Tasks Vision](https://www.npmjs.com/package/@mediapipe/tasks-vision) for hand tracking
- Web Audio API for sound
- Canvas 2D for visuals
- Plain HTML, CSS, and JavaScript

## About

Part of the Sentinel family of projects by James Keith Harwood II, [Sentinel AI Systems](https://www.jameskeithharwood.com). It grew out of the camera and body-tracking ideas in Sentinel Spotter, but was further inspired by SonicDeadHorse post on X: https://x.com/SonicDeadhorse/status/2124783575132430348?a=CFpreFmSxVJvQK40TvE&s=20 (built without seeing Sonicdeadhorse code, and without a link to his air strings project demo. We were inspired by only what we saw in the video.

### Made together

Sentinel Air Strings was created by James Keith Harwood II in partnership with Claude, an AI made by [Anthropic](https://www.anthropic.com). James brought the idea and the vision for how it should look and feel, made the design decisions, and tested every version with real hands, phones, and webcams. Claude wrote the code and the sound engine, tested each build, and worked through the ideas with him along the way.

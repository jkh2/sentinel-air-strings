# Sentinel Air Strings: Roadmap

Plan drafted Nov 23, 2026. Order is a suggestion, not a promise. Reorder freely after testing.

## Done so far

- Hand-tracked strings: pinch to place points, drag to retune, strum with fingers
- Pitch from string length, with scale and key choices (or free pitch)
- Karplus-Strong plucked-string sound with a light echo
- Video-style visuals: hand skeleton, tick marks, sparks on each pluck, livelier string vibration
- Mouse and touch fallback when there is no camera
- Clear camera error messages
- Hide menu button for a bigger playing area on phones
- README with demo link and screenshot

## Before anything new

- [ ] Test with a GoPro / webcam on a computer and note what happens
- [ ] Note any missed strums, stray points, or pinch problems
- [ ] Take a new screenshot that shows real hand tracking, with the skeleton visible

## Phase 1: Quick wins

Small changes that make the instrument nicer to use right away.

1. **Pitch bend.** Drag a point while its string is still ringing and the note slides with it. Idea: change the playback speed of the sound that is already playing, so it bends smoothly.
2. **Camera picker.** A dropdown to choose between cameras (GoPro, webcam, phone front and back). Needed for the GoPro test.
3. **Vibration on pluck.** A short buzz on phones that support it (many Android phones; iPhones do not allow it).
4. **Phone sizing.** Larger points and pinch targets on small screens, since the phone view felt cramped.

## Phase 2: Making music

These work best when built together, because the looper and backing beat depend on shared timing.

5. **Backing beat.** A steady beat with a tempo control to play along with.
6. **Looper.** Record a few seconds of playing, loop it, and play over it. Start with one layer, then allow more.
7. **Save and load layouts.** Keep favorite string arrangements on the device and bring them back with a tap.

## Phase 3: New sounds

8. **Effects pedals.** A small pedalboard of toggles, each lighting up when on:
   - Distortion / overdrive
   - Echo and reverb
   - Chorus / flanger
   - Tremolo
   - Octave
   - **Air wah:** the other hand's height controls how open the wah is
9. **Drum pads.** Circles placed like points. Bigger circles give a deeper sound, smaller ones a tinnier sound.
   - Placing: pinch to set the center, pull outward to set the size, release.
   - Switching between strings and pads: start with a mode button (String / Drum). Consider a gesture later.
   - Hits: a fingertip moving quickly into the circle, with volume from speed. Hitting near the center is fuller, near the edge is sharper.
   - Sound: synthesized, no audio files. Pitch drop for big pads, noise mixed in for small ones.
   - Delete: drag to the ✕, like points.
10. **Instrument voices.** Choose a different sound per string (harp, bass, bell, soft synth).

## Phase 4: Sharing

11. **Record a clip.** One button records the screen and sound together and saves a video to post.
    - Likely to be the biggest help for getting noticed, so consider moving it earlier.
    - Output is usually `.webm` on Android and desktop Chrome. Some apps and sites will not accept it, so test posting before relying on it.

## Ideas for later

- Pluck hardness from hand depth (moving toward the camera plucks harder)
- Visual themes
- Two players at once
- Chord helpers that tune a group of strings together

## Open questions

- How should the app switch between strings and drum pads: a mode button or a gesture?
- Which pedals matter most?
- Should saved layouts stay on the device only, or be shareable by link?

## Notes

- The app is one file (`index.html`) with no build step. Keep it that way if possible.
- The camera requires an https page or localhost.
- Hand tracking uses MediaPipe from a CDN, so the app needs an internet connection.

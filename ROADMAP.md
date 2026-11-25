# Sentinel Air Strings: Roadmap

Plan drafted Nov 23, 2026. Updated Nov 24, 2026. Order is a suggestion, not a promise. Reorder freely after testing.

## Done so far

- Hand-tracked strings: pinch to place points, drag to retune, strum with fingers
- Pitch from string length, with scale and key choices (or free pitch)
- Karplus-Strong plucked-string sound with a light echo
- Video-style visuals: hand skeleton, tick marks, sparks on each pluck, livelier string vibration
- Mouse and touch fallback when there is no camera
- Clear camera error messages
- Hide menu button for a bigger playing area on phones
- README with demo link and screenshot
- Pitch bend: move a point while its string rings and the note slides with it (Nov 24)
- Effects pedalboard with drive, wah, tremolo, chorus, flanger, echo, reverb, and octave (Nov 24)
- Fixed a tuning error that made notes sharp, up to about half a semitone on high notes (Nov 24)
- Clip recorder: records the instrument view and its sound, with Save, Share, and Discard (Nov 24)
- Camera picker, remembered between visits, with rear cameras shown unmirrored (Nov 24)
- Haptics on phones that support vibration (Nov 24)
- Tested on a PC with a phone as the webcam through DroidCam: worked well, and a bigger screen helps a lot

## Before anything new

- [x] Test with a webcam on a computer (phone through DroidCam, Nov 24)
- [ ] Test with the GoPro, using the new camera picker
- [ ] Note any missed strums, stray points, or pinch problems
- [ ] Take a new screenshot that shows real hand tracking, with the skeleton visible

## Phase 1: Quick wins

Small changes that make the instrument nicer to use right away.

1. ~~**Pitch bend.**~~ Done Nov 24. Dragging a point while its string rings slides the note.
2. ~~**Camera picker.**~~ Done Nov 24.
3. ~~**Vibration on pluck.**~~ Done Nov 24 (Haptics button, phones only).
4. **Phone sizing.** Larger points and pinch targets on small screens, since the phone view felt cramped.

## Phase 2: Making music

These work best when built together, because the looper and backing beat depend on shared timing.

5. **Backing beat.** A steady beat with a tempo control to play along with.
6. **Looper.** Record a few seconds of playing, loop it, and play over it. Start with one layer, then allow more.
7. **Save and load layouts.** Keep favorite string arrangements on the device and bring them back with a tap.

## Phase 3: New sounds

8. ~~**Effects pedals.**~~ Done Nov 24 (drive, wah, tremolo, chorus, flanger, echo, reverb, octave). Ideas to extend it:
   - A delay-time control for Echo, and tempo sync once there is a backing beat
   - Per-string effects, so one string can be distorted while another stays clean
   - Original list, for reference:
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

11. ~~**Record a clip.**~~ Done Nov 24. Still to check on real devices:
    - Which format your phone and PC actually produce (the clip card says whether it is H.264)
    - Whether the apps you post to accept it
    - Possible next step: an optional microphone track, so you can talk or sing over your playing

## Ideas for later

- Pluck hardness from hand depth (moving toward the camera plucks harder)
- Visual themes
- Two players at once
- Chord helpers that tune a group of strings together

## Open questions

- How should the app switch between strings and drum pads: a mode button or a gesture?
- Which pedals do you actually use? Cut or rework the rest.
- Does the pitch bend feel right? It follows the same pitch-by-length rule as retuning, so it can be sensitive on a small phone screen. A gentler bend setting is easy to add.
- Does the air wah feel good with two hands tracked?
- Should saved layouts stay on the device only, or be shareable by link?

## Notes

- The app is one file (`index.html`) with no build step. Keep it that way if possible.
- The camera requires an https page or localhost.
- Hand tracking uses MediaPipe from a CDN, so the app needs an internet connection.

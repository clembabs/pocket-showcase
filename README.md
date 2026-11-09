<p align="center">
  <img src="images/icon.svg" width="112" alt="Pocket app icon: four pads with the first one lit">
</p>

<h1 align="center">pocket</h1>

<p align="center">
  <strong>A metronome that can also listen.</strong><br>
  It keeps time, shows when you rush or drag, and trains you to hold the tempo when the click drops out.<br>
  iOS · Android · macOS
</p>

<p align="center"><sub>In development. The source is private; this page shows the product, the design and how it's built.</sub></p>

<p align="center">
  <img src="images/ios-loop.png" width="200" alt="Metronome playing a wórò praise loop at 100 BPM, beat 2 lit">
  <img src="images/ios-stage.png" width="200" alt="Stage mode: 100 BPM, bar 5, beat 1 in amber">
  <img src="images/android-loop.png" width="200" alt="Android Metronome playing a makossa loop, beat 4 lit">
  <img src="images/ios-light.png" width="200" alt="Metronome in light mode with a saved preset">
</p>

---

## Screenshots

Taken from the current build in the iPhone 17 Pro simulator and an Android emulator.

### Metronome

| Playing with a loop | Stage | Light mode | Help |
| :---: | :---: | :---: | :---: |
| <img src="images/ios-loop.png" width="190" alt="Metronome playing with the wórò loop: loop chips, part toggles, click and loop balance"> | <img src="images/ios-stage.png" width="190" alt="Stage mode: a full-screen BPM, bar and beat readable from across the room"> | <img src="images/ios-light.png" width="190" alt="Metronome home in light mode"> | <img src="images/ios-help.png" width="190" alt="Help sheet explaining tempo, beats, clicks per beat, sound, loop, count-in and Stage"> |

The beat pads show each beat's level by how full they are: tap one to cycle loud, normal, soft and silent.
**Clicks per beat** (1, 2, 3, 4 or Swing) says in plain words what each choice does, and every screen has a
**?** that explains it.

### First run

| Welcome | The microphone, in context | First-run tips |
| :---: | :---: | :---: |
| <img src="images/ios-welcome.png" width="200" alt="Welcome: Keep time. Then keep it on your own."> | <img src="images/ios-mic.png" width="200" alt="Why Pocket asks for the microphone: accuracy scoring and Listen mode only"> | <img src="images/ios-tip.png" width="200" alt="Tip 1 of 3 on the Metronome: set the tempo"> |

### Practice, Trainer, Tools, Library

| Practice | Trainer | Tools | Library | Settings |
| :---: | :---: | :---: | :---: | :---: |
| <img src="images/ios-practice.png" width="150" alt="Tempo ramp setup: 80 to 120 BPM, plus 4 every 4 bars, stair-step pattern and plan graph"> | <img src="images/ios-trainer.png" width="150" alt="Trainer drills: gap click, random mute, polyrhythm, adaptive ramp"> | <img src="images/ios-tools.png" width="150" alt="Tools: tap tempo and BPM to milliseconds, with Listen and Play-along coming later"> | <img src="images/ios-library.png" width="150" alt="Library with a saved preset, Sunday praise, on the wórò loop"> | <img src="images/ios-settings.png" width="150" alt="Settings: theme, sound, cues and timing"> |

### Android

| Welcome | First-run tip | Makossa loop | Stage | Help |
| :---: | :---: | :---: | :---: | :---: |
| <img src="images/android-welcome.png" width="150" alt="Android welcome screen"> | <img src="images/android-tip.png" width="150" alt="First-run tip on the Android Metronome"> | <img src="images/android-loop.png" width="150" alt="Android Metronome playing the makossa loop"> | <img src="images/android-stage.png" width="150" alt="Android Stage mode"> | <img src="images/android-help.png" width="150" alt="Android help sheet"> |
| **Practice** | **Trainer** | **Tools** | **Library** | |
| <img src="images/android-practice.png" width="150" alt="Android tempo ramp setup"> | <img src="images/android-trainer.png" width="150" alt="Android Trainer drills"> | <img src="images/android-tools.png" width="150" alt="Android Tools"> | <img src="images/android-library.png" width="150" alt="Android Library, no presets yet"> | |

## What it does

| Area | What's in it |
| --- | --- |
| **Metronome** | 30 to 300 BPM by drag, typing or tapping; time signatures; 1 to 4 clicks per beat or swing; accents per beat; section markers; count-in; flash on 1 and vibration |
| **Sounds** | Woodblock, rimshot, hi-hat, cowbell, and a **voice that counts the beats** out loud |
| **Loops** | Percussion to play the kit over, locked to the click: **wórò praise (12/8), makossa praise, highlife praise, 4/4 and 6/8 worship**. Bell, shekere, congas and talking drum switch on and off, and a slider balances the click against the loop |
| **Stage** | A full-screen beat readable from the drum throne, with the screen kept awake |
| **Practice** | Tempo ramps (linear, stair-step, ramp then hold, speed trainer) and timed sessions |
| **Trainer** | Gap click, random mute, polyrhythms and an adaptive ramp, scored hit by hit in milliseconds through the microphone, with input calibration |
| **Tools** | Tap tempo and BPM ↔ ms today; Listen (find the tempo of a song playing nearby) and Play-along with A–B loops are coming |
| **Library** | Presets that keep the loop too, setlists, a gig mode that counts in the next song with one tap, and practice history |
| **Help** | First-run tips and a "?" on every screen that explains it in plain words |

Everything works without the microphone. It only adds scoring and Listen, and audio never leaves the device.

### Loops for the Nigerian church drummer

Praise and worship teams play the kit over a percussion loop. Pocket's loops are built for that: the
patterns come from the West African bell timeline, shekere and talking drum, and **wórò** and **makossa**
were measured from loops real church bands play along to: wórò at 142 felt beats of three pulses on the
seven-stroke standard bell pattern, makossa on the 3-2 son clave its bell, shaker and bass all share. Every
stroke is synthesized, so a loop follows any tempo and stays on the click's exact sample through ramps and
drills.

## The design

**The visuals must never lag the click.** A beat that lights up even a frame late reads as dragging, so the
timing rules are part of the design, not polish:

- **Locked to the audio clock.** Clicks are scheduled ahead on exact samples, and each beat lights on the first
  frame at or after its scheduled time. Nothing is predicted.
- **Instant on.** A beat turns on in one frame at full brightness. No easing.
- **Tempo changes land on the next pulse.** Changing BPM mid-bar never stretches the current beat.
- **Accent is shape, not just colour.** A beat's level is shown by how full its cell is (100%, 66%, 34%, empty
  for muted), so it reads without colour.

**Colour** is defined in OKLCH. Amber marks the downbeat, and three separate hues show timing: early, in the
pocket, late. Light mode darkens them to keep contrast on beat cells and labels.

<img src="images/palette.svg" alt="Pocket colour tokens in dark and light: backgrounds, text, beat and timing colours">

**Type:** Barlow Condensed for the BPM (up to 220 px in Stage), Hanken Grotesk for titles and body, and Chivo Mono
for labels like `BAR · BEAT`.

**Icon:** four beat pads with the 1 lit, the same mark on iOS, macOS and Android, and line glyphs for the five
tabs drawn from one shared spec.

## How it's built

- **One C++ audio core, native apps.** The click scheduler, the click and percussion synths and the loop
  patterns are C++ with a C interface, shared by a SwiftUI app for iOS and macOS and a Jetpack Compose app for
  Android. Timing and sound are identical everywhere because there is one implementation of them.
- **Timing rules are tested.** The core's tests check sample-exact placement of every click and loop stroke, no
  drift over a ten-minute run, that tempo and meter changes wait for the right moment, and that scoring matches
  reference recordings within ±5 ms.
- **One source for the design.** Colours, type, spacing and radii live in one token file, and a generator writes
  the Swift and Kotlin code from it. CI fails on hard-coded colours or font sizes, and snapshot tests cover
  every component in dark and light.
- **CI/CD on GitHub Actions** with fastlane: every pull request is linted, tested and built for all three
  platforms. Every merge ships an Android tester build through Firebase App Distribution; TestFlight and the
  stores come next.

## Roadmap

| Phase | What | Status |
| --- | --- | --- |
| Setup | Monorepo, audio core, design tokens, both app shells, CI/CD | ✅ Done |
| 1 · MVP metronome | Design foundation, real click on device, Metronome home, Stage mode, presets, onboarding, settings, light mode | ✅ Built; final reviews in progress |
| 2 · Practice and Library | Tempo ramps, timed sessions, setlists, gig mode, history, tap tempo, BPM ↔ ms | ✅ Built; in review |
| 3 · Listening | Microphone calibration and Trainer drills with scoring are built; Listen mode is next | 🟡 In progress |
| Polish | App icon and tab icons, counting voice, plain-language labels, help, percussion loops | ✅ Built; in review |
| 4 · Play-along and extras | Song import with time-stretch, Live Activity, widgets, macOS menu bar, store release | ⏳ |

Android tester builds go out through Firebase today; iOS reaches TestFlight once the Apple developer account is
in place.

---

<sub>Made by Clement Babaniyi. Fonts: Barlow Condensed, Hanken Grotesk and Chivo Mono, under the SIL Open Font
License. The counting voice is generated from the public-domain LJ Speech voice. Screenshots and design ©
Clement Babaniyi, all rights reserved.</sub>

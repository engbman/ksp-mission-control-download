# KSP Mission Control

Fly Kerbal Space Program by voice. You speak your radio calls to CAPCOM; CAPCOM speaks back, and checks every call against your live telemetry before it clears you to the next step.

**Now with a full Apollo 11 recreation:** fly the first Moon landing from launch to the lunar surface, with CAPCOM speaking the real 1969 wording from the Apollo 11 Flight Journal.

Speak to Houston. Houston talks back, and Houston is watching the numbers.

---

## Download

KSP Mission Control has two parts: a desktop app and a small KSP mod that connects them.

**[⬇ Download](https://github.com/engbman/ksp-mission-control-download/releases/latest/download/KSP-Mission-Control.zip)**: one zip with both the app and the mod inside.

Quick guide: run the `.exe` to install the app, then copy the `GameData` folder into your KSP install folder. Full steps in Installation below.

Prefer the pieces separately? See the [Releases page](https://github.com/engbman/ksp-mission-control-download/releases/latest).

---

## What is this?

KSP Mission Control turns your KSP flights into a voice mission. You speak your reports into the microphone, "Houston, we have liftoff", and CAPCOM answers with GO calls, burn advisories, and status updates, then verifies each call against your live telemetry before clearing you onward. A report only counts when the vehicle actually did the thing.

It now includes a full Apollo 11 recreation (see Mission Recreations below).

Built on OpenAI's TTS and Whisper APIs. A typical mission costs less than $0.20.

---

## Features

- **Voice CAPCOM:** speak your reports, hear CAPCOM respond in real time
- **Telemetry-verified calls:** CAPCOM checks each report against live KSP telemetry (via kRPC) before advancing, so a call only counts when the vehicle actually did it
- **Crew altitude ladder:** on the way down, your crew calls the altitude and descent rate to you in their own voice
- **Live mission screen:** telemetry readout, last transmission with replay, burn advisory recap, mission-clock timestamps on every log line, and a master volume slider
- **Mission setup:** pick a preset and see its mission profile at a glance before you fly
- **Full mission flow:** Prelaunch through Ascent, Parking Orbit, Transfer, Coast, Insertion, Descent, Landing, Surface Ops, Return, and Reentry
- **Burn advisories and GO calls:** CAPCOM reads delta-V, burn duration, and T-minus ignition time, and clears you with a GO call before every burn
- **Push-to-talk:** hold F6 to talk to Houston, even while KSP is focused, plus a true-fullscreen (F11) mode
- **In-app help:** reopen the guide any time from the setup screen
- **Optional ElevenLabs voice:** add an ElevenLabs key for a more natural CAPCOM

---

## Mission Recreations

### Apollo 11

Fly the first Moon landing from launch to Tranquility Base, with CAPCOM speaking the real 1969 wording from the Apollo 11 Flight Journal. This flight expects the mandatory stage callouts the crew made, S-1C staging, S-2 ignition, and S-4B cutoff, and holds you to them.

Requires the Sarnus V-A11 craft by gc1ceo, from [KerbalX](https://kerbalx.com/gc1ceo/Sarnus-V-A11).

---

## Requirements

- Windows 10 or 11
- Kerbal Space Program 1.12.x
- The kRPC mod, installed in KSP (see kRPC Setup below)
- The MissionControlMod, which is bundled in the download and installs into `GameData`
- An OpenAI API key for CAPCOM voice and speech recognition, typically under $0.20 per mission. Get one at platform.openai.com/api-keys
- Optional: an ElevenLabs API key for a more natural CAPCOM voice

---

## Installation

1. Download the app + mod using the link in the Download section above (one zip with both)
2. Extract the zip
3. Run the installer `.exe` inside to install the app
4. Copy the extracted `GameData` folder into your KSP root directory: the folder that already contains KSP's own `GameData` (typically `C:\Program Files (x86)\Steam\steamapps\common\Kerbal Space Program`). When Windows asks whether to merge folders, choose merge.
5. Start KSP and load the kRPC mod
6. Launch KSP Mission Control from your desktop
7. Enter your OpenAI API key on first launch
8. Configure your mission and click GO TO LIVE MISSION
9. Press F6 in KSP to talk to Houston

---

**Prefer separate downloads?** Get the installer and mod individually from the [Releases page](https://github.com/engbman/ksp-mission-control-download/releases/latest) instead of the all-in-one zip. Same steps 3-9 apply, just extract the mod zip separately in step 4.

---

## Updates

The **app** updates itself automatically. When a new version is ready, you'll see a "Relaunch to Update" button in the app.

The **mod** currently does not auto-update. To get a new mod version, download the latest `MissionControlMod` file from the Releases page and replace your `GameData/MissionControlMod` folder. CKAN support for automatic mod updates is planned for a future release.

---

## kRPC Setup

1. Download kRPC from the KSP forum or CKAN
2. Install it in your KSP GameData folder
3. In KSP, open the kRPC window, click Add Server, then click Start Server
4. Launch Mission Control and click Establish Connection
5. When you first connect, KSP will show a popup in the bottom-right corner asking to allow the connection. Click Allow. This only appears once.

---

## Voice Commands: Full Reference

The app shows the exact phrase to say at each step in the SPEAK hint on screen. This is the full reference list.

Items marked 🛰️ **(auto)** are confirmed automatically by telemetry. The pilot does not need to speak these.

### Common phases (all surface-launch missions)

**Prelaunch**
- **Ready for launch:** "ready for launch", "we are ready for launch", "launch ready"

**Ascent**
- **Liftoff:** "liftoff", "lift off", "we have liftoff", "we have lift off", "liftoff confirmed"
- **Roll program:** "roll program", "roll program initiated", "roll complete", "we got a roll program", "gravity turn", "gravity turn initiated", "turn initiated"
- **Parking orbit insertion:** "parking orbit insertion", "parking orbit established", "orbit insertion", "insertion complete"

### Orbit
Phases: Prelaunch → Ascent → Parking Orbit → Transfer Burn → Coast → Insertion Burn
(A simple Kerbin orbit with no transfer ends at Parking Orbit with "orbit stable".)

**Parking Orbit**
- **Maneuver node defined** 🛰️ (auto): "node defined", "maneuver node defined", "node ready", "node set", "tli node defined", "translunar injection node defined". CAPCOM confirms your orbit and calls you go for the transfer burn.
- **Orbit stable** _(Kerbin-only orbit)_: "orbit stable", "parking orbit stable", "stable in orbit", "orbit is stable", "stable orbit"

**Transfer Burn**
- **Execute transfer burn:** "ignition", "ignition start", "execute transfer burn", "burn started", "burn start"
- **Burn complete:** "burn complete", "transfer burn complete", "tli complete", "translunar injection complete"

**Coast**
- **Monitor trajectory:** "trajectory nominal", "trajectory is nominal", "trajectory looks good", "coast nominal", "coasting nominally"
- **Encounter confirmed:** "encounter confirmed", "entered soi", "soi confirmed", "mun encounter confirmed", "approach confirmed", "minmus encounter confirmed", "duna encounter confirmed", "eve encounter confirmed"
- **Insertion node defined** 🛰️ (auto): "node defined", "insertion node defined", "loi node defined", "lunar orbit insertion node defined". CAPCOM calls you go for the insertion burn.

**Insertion Burn**
- **Execute insertion burn:** "ignition", "loi ignition", "execute insertion burn", "burn started", "burn start"
- **Confirm captured orbit:** "burn complete", "insertion burn complete", "loi complete", "orbit captured", "capture confirmed"

### Flyby
Phases: Prelaunch → Ascent → Parking Orbit → Transfer Burn → Coast
(Same as Orbit but with no insertion, no insertion node, no Insertion Burn.)

### Land on Body: airless (Mun, Minmus, etc.)
Phases: Prelaunch → Ascent → Parking Orbit → Transfer Burn → Coast → Insertion Burn → Descent → Landing
(Parking Orbit, Transfer Burn, Coast, and Insertion Burn use the same phrases as in Orbit.)

**Descent**
- **Landing target confirmed:** "landing target confirmed", "landing target set", "target selected", "go for deorbit burn", "ready for deorbit burn"
- **Deorbit ignition:** "ignition", "burn start", "deorbit ignition", "deorbit burn start"
- **Deorbit burn complete:** "deorbit burn complete", "deorbit complete", "deorbit burn is complete"
- **Powered descent initiated:** "powered descent initiated", "powered descent", "pdi", "descent burn initiated", "descent burn"
- **Descent rate nominal:** "descent rate nominal", "rate of descent nominal", "rate nominal", "descent nominal"

**Landing**
- **Touchdown:** "touchdown", "we have touchdown", "vehicle is down", "we are down"
- **Surface stable:** "surface stable", "vehicle stable", "we are stable", "lander stable"

### Land on Body: atmospheric (Duna, Eve, Laythe)
Phases: Prelaunch → Ascent → Parking Orbit → Transfer Burn → Coast → Insertion Burn → Atmospheric Reentry → **Landing**
(One-way atmospheric landings end in a **Landing** phase, and CAPCOM welcomes you to the destination. The **Recovery** phase name is used only by the Land & Return preset, for the Kerbin splashdown.)

**Atmospheric Reentry**
- **Deorbit node defined** 🛰️ (auto): "deorbit node defined", "deorbit node set", "node defined", "node set", "ready for deorbit burn"
- **Deorbit ignition:** "ignition", "burn start", "deorbit ignition", "deorbit burn", "executing deorbit burn"
- **Deorbit burn complete:** "deorbit burn complete", "deorbit complete", "deorbit burn is complete"
- **Entry interface:** "entry interface", "reentry interface", "atmospheric entry", "entering atmosphere"
- **Descent rate nominal:** "descent rate nominal", "rate of descent nominal", "rate nominal", "descent nominal"
- **Main chute deployed:** "main chute deployed", "parachute deployed", "chutes deployed", "chute deployed"

**Landing / Recovery**
- **Touchdown or splashdown:** "touchdown", "we have touchdown", "splashdown", "we have splashdown", "vehicle is down", "we are down"
- **Vehicle stable:** "vehicle stable", "surface stable", "capsule stable", "we are stable"

### Land & Return
A full launch, transfer, land, and return mission.
Phases: …Landing (as airless) → Surface Operations → Surface Ascent → Return Orbit → Return Burn → Return Coast → Atmospheric Reentry → Recovery
(Outbound and landing phases as in Land on Body. On the final Kerbin splashdown, CAPCOM welcomes you home.)

**Surface Operations**
- **Surface operations complete:** "surface operations complete", "all operations complete", "eva complete", "science complete", "ready for launch", "ready for surface launch"

**Surface Ascent**
- **Surface liftoff:** "surface liftoff", "liftoff", "we have liftoff", "launch from surface"
- **Roll program:** "roll program", "roll complete", "gravity turn", "turn initiated", "roll"
- **Orbit stable:** "orbit stable", "orbit achieved", "orbit established", "stable orbit", "return orbit established"

**Return Orbit**
- **Return orbit stable:** "return orbit stable", "orbit stable", "stable orbit", "orbit is stable"

**Return Burn**
- **Return node defined** 🛰️ (auto): "node defined", "return node defined", "return node set", "kerbin return node defined". CAPCOM calls you go for the return burn.
- **Return ignition:** "return ignition", "ignition", "burn start", "return burn started", "kerbin injection started"
- **Return burn complete:** "return burn complete", "burn complete", "kerbin injection complete"

**Return Coast**
- **Return coast nominal:** "return coast nominal", "coast nominal", "coasting nominally", "return trajectory nominal", "goes nominal"
- **Kerbin encounter confirmed:** "kerbin encounter confirmed", "kerbin encounter", "encounter confirmed", "approach confirmed", "kerbin soi confirmed"

### Rendezvous & Docking
Phases: Prelaunch → Ascent → Parking Orbit → Rendezvous → Docking

**Rendezvous**
- **Target selected:** "target selected", "target set", "rendezvous target selected", "target confirmed", "target vessel selected"
- **Close approach established:** "close approach established", "close approach", "rendezvous complete", "station keeping"

**Docking**
- **Docking target set:** "docking target set", "docking target selected", "target port set", "docking port targeted"
- **Final approach:** "final approach", "on final approach", "approach established", "closing in", "final approach confirmed"
- **Contact and capture:** "contact and capture", "capture confirmed", "soft capture", "hard capture", "docking complete", "docked", "we are docked"

You do not need to say phrases word for word. The system matches common variations. Watch the SPEAK hint in the app for the recommended phrase at each step.

---

## Cost

A typical Mun mission uses approximately $0.10-0.20 of OpenAI API credits.
A $5 credit lasts 25-50 full missions.

---

## Multi-Monitor Note

KSP Mission Control includes two separate interfaces: the desktop app and a companion overlay inside KSP. Running them on separate monitors should work, but this configuration has not been officially tested. Use at your own discretion.

---

## Support

If you enjoy KSP Mission Control, consider buying me a coffee:
☕ https://ko-fi.com/engbman

---

## Credits

- Apollo 11 mission audio: original NASA recordings, public domain
- Apollo 11 mission insignia: NASA, public domain
- Mission profile artwork: AI-generated for this app
- Sarnus V-A11 craft: by gc1ceo on [KerbalX](https://kerbalx.com/gc1ceo/Sarnus-V-A11)

This is an independent fan project, not affiliated with or endorsed by NASA.

---

## License

All rights reserved. © 2026 Bman

This software is provided as-is for personal use only.
Redistribution, modification, or commercial use is not permitted without written permission.

---

*Built by Bman, because KSP deserved a real mission control.*

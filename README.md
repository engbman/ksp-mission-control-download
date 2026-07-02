# KSP Mission Control

A voice-controlled AI mission control system for Kerbal Space Program.

Speak to Houston. Houston talks back.

---

## Download

KSP Mission Control has two parts: a desktop app and a small KSP mod that connects them.

**[⬇ Download](https://github.com/engbman/ksp-mission-control-download/releases/latest/download/KSP-Mission-Control.zip)** — one zip with both the app and the mod inside.

Quick guide: run the `.exe` to install the app, then copy the `GameData` folder into your KSP install folder. Full steps in Installation below.

Prefer the pieces separately? See the [Releases page](https://github.com/engbman/ksp-mission-control-download/releases/latest).

---

## What is this?

KSP Mission Control adds a real CAPCOM experience to your KSP missions. You speak mission reports into your microphone — "Houston, we have liftoff" — and an AI flight controller responds with authentic NASA-style callouts, burn advisories, and mission status updates.

Built on OpenAI's TTS and Whisper APIs. Costs less than $0.20 per mission.

---

## Features

- **Voice-controlled:** speak your reports, hear real CAPCOM responses
- **Full mission flow:** Prelaunch → Ascent → Parking Orbit → Transfer → Coast → Insertion → Descent → Landing → Surface Ops → Return → Reentry
- **Live telemetry:** connects to KSP via kRPC for real orbital data
- **Burn advisories & go-calls:** CAPCOM reads delta-V, burn duration, and T-minus ignition time, and clears you with a go-call (TLI, LOI, ignition, return burn) before every burn
- **Orbit confirmation:** CAPCOM tells you whether your orbit is stable and nominal, or elliptical but within limits
- **Mission phases:** tracks every checklist item automatically, guiding you to the next call
- Mission control dashboard for tracking your flight in real time

---

## Requirements

- Kerbal Space Program 1.x
- kRPC mod installed in KSP
- OpenAI API key: required for CAPCOM voice and speech recognition. Get one at platform.openai.com/api-keys.
- Windows 10/11

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

## Voice Commands — Full Reference

The app shows the exact phrase to say at each step in the SPEAK hint on screen. This is the full reference list.

Items marked 🛰️ **(auto)** are confirmed automatically by telemetry — the pilot does not need to speak these.

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
(Same as Orbit but with no insertion — no insertion node, no Insertion Burn.)

### Land on Body — airless (Mun, Minmus, etc.)
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

### Land on Body — atmospheric (Duna, Eve, Laythe)
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

### Land & Return (Apollo-style)
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

You do not need to say phrases word for word — the system matches common variations. Watch the SPEAK hint in the app for the recommended phrase at each step.

---

## Cost

A typical Mun mission uses approximately $0.10–0.20 of OpenAI API credits.
A $5 credit lasts 25–50 full missions.

---

## Multi-Monitor Note

KSP Mission Control includes two separate interfaces: the desktop app and a companion overlay inside KSP. Running them on separate monitors should work, but this configuration has not been officially tested. Use at your own discretion.

---

## Support

If you enjoy KSP Mission Control, consider buying me a coffee:
☕ https://ko-fi.com/engbman

---

## License

All rights reserved. © 2026 Bman

This software is provided as-is for personal use only.
Redistribution, modification, or commercial use is not permitted without written permission.

---

*Built by Bman — because KSP deserved a real mission control.*

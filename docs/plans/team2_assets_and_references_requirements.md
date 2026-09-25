# Team 2: Assets, Open-Source Components & References Requirements

**Companion to:** [team2_final_plan_irec_aligned.md](team2_final_plan_irec_aligned.md)
**Written:** 25 Sep 2026
**Purpose:** Define **what** we must build, find, or cite, and the acceptance criteria for each. The search itself is **not** done here. Whoever searches fills in the "Found" columns and the attribution log.

---

## 0. Global rules for anything we import

| Rule | Requirement |
| --- | --- |
| R1 License | Allowed: CC0, CC-BY (with attribution), MIT, Apache-2.0, BSD, OFL (fonts), Unity Asset Store Standard EULA. Not allowed: "personal use only", NC licenses if the work will be published, unknown license, ripped game assets. |
| R2 Repo safety | Unity Asset Store and paid assets **must not be committed to a public repo**. Keep them in `Assets/ThirdParty/` and gitignore them if the repo goes public. |
| R3 Attribution | Record every imported item in `assets/ATTRIBUTION.csv` **when it is imported**: `id, name, author, source_url, license, version/date, used_in, modified(y/n)` |
| R4 Content | Non-graphic: no injured or dead people, no blood, no realistic burning bodies. No real brand logos. No real NU building replicas. |
| R5 Format | FBX or glTF, metres, Y-up, pivot at base centre, real-world scale (door ≈ 2.1 m). Simple colliders (box or capsule, not mesh). |
| R6 Quest 2 budget per prop | Small ≤ 1.5k tris, medium ≤ 5k, large ≤ 10k. One material per prop where possible. Textures ≤ 1024² (2048² only for shared atlases). ASTC compression. |
| R7 Scene budget | ≤ 250k visible tris, ≤ 150 draw calls, stable 72 Hz on Quest 2. Baked lighting, no realtime shadows (or one directional at most). |
| R8 Shaders | Must work in URP with a mobile/simple-lit shader. Nothing that needs HDRP, built-in RP, tessellation, or screen-space effects. |
| R9 Consistency | One visual style across the facility: stylized or low-poly realistic, **not mixed**. Decide after the first asset-pack shortlist. |

---

## 1. Scenes to create

| Scene | Who sees it | Content | 3D effort |
| --- | --- | --- | --- |
| `Bootstrap_Server` | Experimenter PC | Console UI only: pair code, role assignment, order, start/stop/abort, live log view | None, 2D UI |
| `Lobby` | Both Quests | Neutral waiting room, role label, "waiting for partner", comfort check | Low |
| `Tutorial` | Both | Responder: small practice area (1 room, 1 corridor, 1 junction, 1 exit, 2 landmarks). Analyst: the control room with a practice map. | Low |
| `Facility` | Responder (1:1). Analyst sees only the map. | One building shell. S1–S3 are **data variants** of it (start point, exit states, hazards). | **High: the main work** |
| `ControlRoom` | Analyst | Seated control room with the big map display, sensor panel, and alert feed. Loaded additively on the Analyst client. | Medium |

**Decision to confirm:** the facility is a **single-storey office + light-storage building**, about 30 × 40 m. It has no stairs, because vertical movement is a comfort risk and adds navigation complexity.

---

## 2. Facility layout requirements (build in-house, grey-box first)

We build this ourselves. We do not search for a ready-made building, because the layout **is** the experiment.

| ID | Requirement |
| --- | --- |
| L1 | Grey-box in **ProBuilder** first, then swap in a modular kit (§3.1). Layout geometry is final before art replaces it. |
| L2 | Corridor width ≥ 2.4 m and ceiling ≈ 3 m. Wide corridors reduce wall collisions under continuous locomotion. |
| L3 | **6–8 decision nodes** (junctions or T-intersections) and **3–4 exits** on different sides of the building |
| L4 | Each scenario's optimal safe path is **40–60 m** long, and all three are within **±15%** of each other |
| L5 | Every decision node has at least one **unique, nameable landmark** (§3.3). The Responder must be able to say "I'm next to the red vending machine". |
| L6 | No two junctions look alike. Avoid symmetric wings, which cause ambiguous verbal descriptions and confound the communication metrics. |
| L7 | Doorways are open or auto-open. The only interaction is walking. Blocked doors look clearly different (debris, shutter, locked sign). |
| L8 | Zone volumes (rooms and corridor segments), node triggers, hazard trigger volumes, and exit triggers are authored as invisible objects with IDs that match the scenario data |
| L9 | A top-down **map is generated from the same geometry**, using an orthographic render or vector export, so the Analyst's map always matches the facility variant |
| L10 | Physical sensor props (smoke detectors, heat sensors) placed in the world use the **same IDs** as the Analyst's sensor icons |

---

## 3. 3D asset inventory

Legend: **Build** = make in-house (ProBuilder, Blender, or Unity primitives). **Find** = source an open or free asset. **MVP** = required for the pilot. **Nice** = only if time permits.

### 3.1 Building shell (modular kit)

| ID | Item | Qty | Source | Priority | Notes / search keywords |
| --- | --- | --- | --- | --- | --- |
| B1 | Modular walls: straight, corner, T, end, with door opening | kit | Find (fallback: Build) | MVP | "modular office interior kit low poly", "modular sci-fi/industrial corridor kit"; must snap on a 1 m or 2 m grid |
| B2 | Floor and ceiling tiles (office carpet or vinyl, concrete for storage) | kit | Find textures + Build planes | MVP | Tileable PBR ≤ 1024² |
| B3 | Door frames + single and double doors | ~12 | Find | MVP | Doors can be static props (open) |
| B4 | Emergency exit door with push bar | 3–4 | Find | MVP | "fire exit door push bar" |
| B5 | Blocked-exit variant: rolling shutter or chained door | 2 | Find/Build | MVP | Must read as "blocked" from 10 m away |
| B6 | Windows (interior glass partitions) | few | Find | Nice | Transparent materials cost performance on Quest, so use few |

### 3.2 Hazards & emergency VFX

| ID | Item | Source | Priority | Requirement |
| --- | --- | --- | --- | --- |
| H1 | Fire: flames at a doorway or inside a room | Find VFX or Build particles | MVP | Stylized and non-graphic. ≤ 100 particles per emitter. Additive unlit. Readable at 15 m. |
| H2 | Smoke: corridor-filling layer and a ceiling layer | Build (particles or fog cards) | MVP | **Overdraw-limited**: ≤ 3 screen-covering layers. Must visibly reduce sight distance without making the frame rate drop. |
| H3 | Smoke seeping under or around a door (S3 cue) | Build | MVP | Subtle but noticeable. This is the Responder's "local observation" in S3. |
| H4 | Debris blocking a corridor: collapsed shelving, fallen ceiling panels, boxes | Find props + Build arrangement | MVP | Clearly impassable. Gets a collider. |
| H5 | Fire glow: emissive orange light behind a door | Build | MVP | Baked or light-probe glow, not a realtime point light |
| H6 | Alarm strobe light (wall-mounted) | Find/Build | MVP | Flash rate ≤ 2 Hz for **photosensitivity safety**. Epilepsy is an exclusion criterion, but stay conservative anyway. |
| H7 | Heat shimmer / distortion | — | **Excluded** | Too expensive on Quest and a nausea risk |

### 3.3 Landmarks & wayfinding (important for the research)

| ID | Item | Qty | Source | Priority | Requirement |
| --- | --- | --- | --- | --- | --- |
| W1 | Distinct landmark props: vending machine, water cooler, large plant, reception desk, printer station, lockers, notice board, sofa, server rack, fire-extinguisher cabinet, big coloured pipe, forklift or pallet stack | ≥ 12 | Find | MVP | Each one unique in shape **and** colour. Must not rely on colour alone (colour-blind participants). |
| W2 | Room name / number signs ("Storage B", "Room 104") | per room | Build (TMP on a quad) | MVP | Readable at ≥ 3 m in Quest 2 |
| W3 | Illuminated EXIT signs + directional arrows | ~10 | Find symbol + Build mesh | MVP | Use the **ISO 7010 E001/E002** "running man" pictograms. Check their licence (§4.4). |
| W4 | Accent-coloured wall sections per wing | per wing | Build (material) | MVP | Supports "I'm in the blue corridor" |
| W5 | Floor markings (hazard stripes, lane lines) in the storage area | few | Build (decal/texture) | Nice | — |

### 3.4 Safety equipment & sensor props

| ID | Item | Source | Priority | Notes |
| --- | --- | --- | --- | --- |
| S1 | Ceiling smoke detectors / heat sensors (world twins of the Analyst's sensors) | Find | MVP | Small. ID label optional. |
| S2 | Fire extinguishers + wall cabinets | Find | MVP | Decoration and landmark only, not interactable |
| S3 | Manual call points / fire alarm pull stations | Find | Nice | — |
| S4 | Sprinkler heads | Find | Nice | — |

### 3.5 Filler props (office + storage)

| ID | Item | Source | Priority |
| --- | --- | --- | --- |
| F1 | Desks, office chairs, monitors, filing cabinets, bookshelves | Find (one consistent pack) | MVP |
| F2 | Storage shelving, cardboard boxes, pallets, crates, barrels (non-hazmat labels) | Find | MVP |
| F3 | Small clutter: papers, mugs, bins | Find | Nice. Keep under budget. |

### 3.6 Analyst control room

| ID | Item | Source | Priority | Requirement |
| --- | --- | --- | --- | --- |
| C1 | Room shell (small, windowless, dim) | Build | MVP | Calm environment, so the Analyst doesn't get cybersickness |
| C2 | Desk + chair matching the Analyst's real seated height | Find | MVP | Virtual desk height is calibrated to the real one |
| C3 | Large curved or flat **map display**, about 2.5 × 1.5 m at about 1.8 m distance | Build (world-space canvas + frame mesh) | MVP | Map legibility is tested on device in week 1 |
| C4 | Side monitors: sensor list and alert feed | Build | MVP | High-contrast TMP text with icons |
| C5 | Decorative consoles and keyboards | Find | Nice | — |

### 3.7 Players & hands

| ID | Item | Source | Priority | Notes |
| --- | --- | --- | --- | --- |
| P1 | Controller / hand models | XRI Starter Assets or Meta controller models | MVP | No custom work |
| P2 | Full-body avatars, NPC workers, victims | — | **Excluded** | Not in the IREC task. Neither role sees the other's body. |

---

## 4. Non-3D assets

### 4.1 Audio (all ≤ moderate volume, short loops)

| ID | Item | Priority | Requirement |
| --- | --- | --- | --- |
| AU1 | Fire alarm loop (bell or electronic) | MVP | Attenuated. Must not mask voice. The alarm's volume and ducking should be fixed across sessions. |
| AU2 | Fire crackle ambience (spatial, near hazards) | MVP | Quiet. It is a cue, not a jump-scare. |
| AU3 | "Blocked" feedback thud / buzz | MVP | — |
| AU4 | Exit-reached chime, UI click | MVP | — |
| AU5 | HVAC / room tone | Nice | Makes the space feel real |

Search sources: CC0-filtered libraries only. Keep in mind that game audio competes with voice, and **RQ2 is about the voice channel**. Keep the non-voice audio sparse.

### 4.2 Textures & materials
- Tileable PBR sets: carpet, vinyl, concrete, painted plaster, ceiling tile, metal shelving. CC0 preferred.
- One texture atlas per prop pack where possible (R6).

### 4.3 UI, icons & fonts

| ID | Item | Requirement |
| --- | --- | --- |
| UI1 | Map glyphs: exit open, exit blocked, sensor, hazard, Responder zone highlight | Designed as a set. Shape and colour both encode meaning. |
| UI2 | Sensor-state badges: fresh / stale (age) / low confidence | Needed for S3 (plan D3) |
| UI3 | Font | OFL or Apache licensed, highly legible, with a TMP SDF atlas |
| UI4 | Consistent colour tokens | Colour-blind-safe palette. Never red vs. green alone. |

### 4.4 Safety-sign symbols
- ISO 7010 exit, fire-equipment, and fire-alarm pictograms. **Verify the licence status of the specific source files before use.** Many reproductions carry their own licence.

---

## 5. Open-source software components to evaluate

Each candidate must meet the criteria in the right column. Names in "Leads" are **starting points to verify**, not endorsements.

| ID | Need | Must-have criteria | Leads to check |
| --- | --- | --- | --- |
| OS1 | **LAN voice chat** on Quest 2 with NGO | Works **offline on LAN**. Android/Quest build. Exposes the recorded or received audio stream so the server can write WAV. Low latency (< 150 ms mouth-to-ear on LAN). Active in 2025–26. | Dissonance Voice Chat (paid), UniVoice (open source), Concentus (C# Opus port) for a custom relay, Meta Platform voice samples |
| OS2 | Multiplayer VR scaffold | Unity 6 + NGO 2.x + XRI 3.x. Dedicated-server or custom-role spawning possible. | Unity VR Multiplayer Template, Meta `oculus-samples` NGO projects, UCL Ubiq (only if we drop NGO, which is unlikely) |
| OS3 | Continuous locomotion + vignette | Built-in and tunable | XRI `ContinuousMoveProvider` + `TunnelingVignetteController` (already in XRI) |
| OS4 | Grey-boxing | Free, in-editor | Unity ProBuilder |
| OS5 | Mobile-friendly fire and smoke VFX | URP, unlit, low overdraw, permissive license | Asset Store free VFX packs, open-source Unity VFX repos. Check each one on Quest. |
| OS6 | Logging / analysis tooling | CSV-friendly | Python (pandas, pingouin/statsmodels) or R (lme4, rmcorr) for analysis. No Unity package needed. |
| OS7 | Audio coding tool (for the §6.5 codebook) | Free, timestamped annotation, exports CSV | ELAN, Audacity labels, BORIS |

Record each evaluation result here: **pass/fail, version, license, Quest test date, tester**.

---

## 6. References & citations needed

These are the claims our report and IREC text make, and each one needs support. **Verify every citation by DOI before use.** Items marked ✓ are standard anchors we are confident exist. The others are topics to search.

### 6.1 Mandatory (instruments & methods we use)

| ID | Claim / use | Anchor or search target |
| --- | --- | --- |
| C1 | NASA-TLX | ✓ Hart & Staveland (1988), *Advances in Psychology* 52. ✓ Hart (2006), HFES Proceedings, "NASA-TLX; 20 years later" (raw-TLX justification). |
| C2 | SUS + interpretation | ✓ Brooke (1996), "SUS: a 'quick and dirty' usability scale". ✓ Bangor, Kortum & Miller (2008), *IJHCI*. ✓ Bangor et al. (2009), *J. Usability Studies* (adjective scale). |
| C3 | Jitter computation | ✓ RFC 3550 (RTP), Schulzrinne et al. (2003), interarrival jitter |
| C4 | Acceptable voice delay | ✓ ITU-T Recommendation G.114, one-way transmission time |
| C5 | Inter-rater reliability for audio coding | ✓ Cohen (1960), kappa |
| C6 | Dyadic / pair-level analysis | ✓ Kenny, Kashy & Cook (2006), *Dyadic Data Analysis* |
| C7 | Repeated-measures correlation (RQ2) | ✓ Bakdash & Marusich (2017), *Frontiers in Psychology*, rmcorr |
| C8 | Thematic analysis of open-ended answers | ✓ Braun & Clarke (2006), *Qual. Research in Psychology* |

### 6.2 Background & justification (search required)

| ID | Topic | What we need to show | Target count |
| --- | --- | --- | --- |
| C9 | VR for fire-evacuation research | VR is a valid, safe way to study evacuation behaviour. Include limits of ecological validity. (Seed: Kinateder et al., 2014, "Virtual reality for fire evacuation research".) | 3–5 |
| C10 | Remote guidance / asymmetric collaboration | Prior systems where one user has a global view and another is embodied locally, in XR or for search and rescue | 3–5 |
| C11 | Asymmetric VR interaction | Asymmetric roles and devices in shared VR (e.g., ShareVR, Gugenheimer et al., CHI 2017) | 2–3 |
| C12 | Common ground & grounding in communication | Clarification and repair as a measure of collaboration (✓ Clark & Brennan, 1991) | 2–3 |
| C13 | Network latency/jitter effects on collaborative tasks and voice communication | Justifies RQ2's hypothesised relation | 3–5 |
| C14 | Verbal route instructions & landmarks in wayfinding | Justifies the landmark requirement (L5) and wrong-turn coding | 2–4 |
| C15 | Cybersickness with continuous locomotion + mitigations | Justifies moderate speed, vignette, snap turn (✓ LaViola, 2000. ✓ Fernandes & Feiner, 2016, IEEE 3DUI FOV restriction. ✓ Kennedy et al., 1993, SSQ, as background only because SSQ is not in our protocol.) | 3–4 |
| C16 | Situation awareness in emergency teams | Frames the Analyst/Responder information split (✓ Endsley, 1995) | 1–2 |
| C17 | Sensor uncertainty / reliability displays for operators | Supports D3 (sensor age and confidence badges) and future-work framing | 2–3 |
| C18 | Emergency wayfinding signage (exit-sign visibility) | Supports W3 design choices | 1–2 |

**Citation workflow:** keep one shared Zotero group library ("Team2-VR-Evac"). Tag each item with its C-ID and export BibTeX to `docs/references.bib`. The report uses only entries with a verified DOI or URL.

---

## 7. Acceptance checklist before the pilot (W5)

- [ ] Every imported item is in `assets/ATTRIBUTION.csv` with a compatible licence (R1–R3)
- [ ] The Facility scene holds 72 Hz on Quest 2 at the worst viewpoint of each scenario, with smoke active (R7)
- [ ] All 12+ landmarks are distinct, and a naïve tester can name each one aloud (L5, W1)
- [ ] Exit and blocked-exit states are readable from 10 m (B4, B5)
- [ ] Analyst map text and icons are legible in the headset (C3, UI1–UI4)
- [ ] Optimal path lengths for S1–S3 are measured and within ±15% (L4)
- [ ] Alarm audio does not mask voice at the chosen volume (AU1)
- [ ] Strobe ≤ 2 Hz (H6)
- [ ] Mandatory citations C1–C8 are verified and in `references.bib`

# Team 2 Final Plan: IREC-Aligned Build & Study

**Project:** Collaborative Fire-Evacuation Decision-Making in Virtual Reality: Analyst-Responder Communication, Navigation, and Workload
**PI:** Dr. Syed Muhammad Umair Arif (SCAI) · **Team:** Zhandaulet Kuan, Botakoz Toleugaliyeva, Osman Faizulla, Adi Zhanserik
**IREC submission:** 22 Sep 2026, expedited review (usually 3–4 weeks)
**Plan written:** 25 Sep 2026 · **Revised:** 25 Sep 2026 to align with the Team Blueprint

---

## 0. Which document wins

Documents rank in this order:

1. **The IREC application** (`Team_2_.../Arif_IREC Application_09222026.md`) is binding. We may not collect or analyse participant data in any way it does not describe unless we file an amendment first.
2. **The Team Blueprint** (`Team_2_.../Collaborative_Fire_Emergency_VR_Project_Blueprint.md`) is the team's design reference for scenarios, measures, architecture, protocol, analysis, and timeline. It is fully compatible with the IREC application, and this plan follows it.
3. **This plan** records the concrete decisions the Blueprint leaves open (topology, voice stack, counterbalance size, metric definitions) and tracks the ethics-package fixes.

The earlier AI-generated plans (CrisisLink Blueprint, `master_plan.md`, `technical_realization_guide.md`, and `session1`/`session2`/`session3_extensions`) described a **different study**: an adaptive-uncertainty interface compared across three conditions. They were **removed on 25 Sep 2026**. The tracked ones can be recovered from git commit `9d41477`. §3 and §7 record what was kept from them.

The remaining companion files are:
- [session3.md](session3.md): the course's project catalog. Our study derives from its "Project 2".
- [team2_assets_and_references_requirements.md](team2_assets_and_references_requirements.md): what 3D assets, open-source components, and citations to find.

---

## 1. What the submitted protocol commits us to

| Item | Committed in IREC |
| --- | --- |
| Design | Repeated-measures design with mixed methods. **The within-pair factor is the scenario**, not an interface condition. |
| Hardware | **Two Meta Quest 2 headsets** connected over a local network. Both participants are in VR. |
| Roles | The Analyst stays mostly stationary and has the map, fire/smoke sensors, hazard indicators, and exit status. The Responder navigates with no global map. **Each participant keeps the same role for the whole session.** |
| Locomotion | **Continuous controller-based locomotion (not teleport)** at moderate speed, with snap turning where appropriate |
| Scenarios | Practice task, then S1 Blocked Primary Exit, S2 Dynamic Hazard Update, S3 Competing Routes. Order is counterbalanced "where practicable" and task lengths are comparable. |
| Automatic logs | Evacuation success, completion time, movement path, route length, wrong turns, blocked or unsafe attempts, route changes, and interaction events |
| Communication data | **Audio of the communication channel is recorded.** Transmit/receive timestamps and network logs are used for delay and jitter. Clarification requests and repetitions are counted. |
| Not collected | Video, biometrics, voice identification |
| Instruments | Background questionnaire (once). **NASA-TLX + custom communication-quality questionnaire after each scenario.** SUS and open-ended feedback at the end. |
| Survey medium | "Electronic survey media: **No**", so questionnaires are on paper |
| Sample | About 30 participants (minimum 20, maximum 36), meaning **10–18 pairs** |
| Session | 50–60 min |
| Site / dates | Room 7.522. Data collection 10/2026–10/2027, only after approval. |
| Analysis | Pair-level within-pair comparisons. Communication–outcome associations are **exploratory and not causal**. Themes from open-ended answers. |

### 1.1 Research questions & hypotheses (Team Blueprint §2, mapped to IREC)

| Blueprint | Question | IREC RQ |
| --- | --- | --- |
| RQ1 | How effectively can the Analyst guide an information-limited Responder to a safe route? | RQ1 |
| RQ2 | How does the type of coordination challenge (scenario) affect performance, navigation, and workload? | RQ2 + RQ3 |
| RQ3 | How are measured delay/jitter and perceived communication quality associated with time, route errors, clarifications, and decision changes? | RQ2 |
| RQ4 | How do Analyst and Responder differ in workload and communication experience? | RQ3 |
| RQ5 | How usable is the complete system (SUS)? | RQ3 |

- **H1:** Replanning (S2) and competing routes (S3) produce longer times and more communication events than the static baseline (S1).
- **H2:** Higher delay/jitter is associated with more clarification or repetition and lower route efficiency *(associational only)*.
- **H3:** Analyst and Responder workload profiles differ.
- **H4:** Higher perceived communication quality is associated with higher confidence and better performance.
- **H5:** The system is rated usable. This is evaluated descriptively through SUS.

The Blueprint's RQs are a finer breakdown of the IREC RQs, so **no amendment is needed**.

---

## 2. Problems found in the submission package

**Status update (25 Sep 2026, revised package received):** the updated `.docx`/`.doc` files replaced the originals in `Team_2_.../`:
- `Consent Forms/Arif_Participant consent-Eng_09222026.docx` was rewritten.
- `Consent Forms/Arif_Confidentiality Agreement Form-Eng_09222026.doc` has the title fixed.
- `Consent Forms/Arif_Audio Recording Consent-Eng_09252026.docx` is **new**. It is a separate audio consent form with an explicit AGREE / DO NOT AGREE choice, and declining means no participation.
- The IREC application `.docx` in the update was **byte-identical** to the original, so nothing in it changed.

### 2.1 Critical

| # | Document | Problem | Status |
| --- | --- | --- | --- |
| E1 | Participant consent | It described the old adaptive-uncertainty study | ✅ **Fixed.** It now has the IREC title, three fire scenarios, continuous locomotion, and TLX + communication questionnaire + SUS. |
| E2 | Participant consent | It said audio would **not** be recorded | ✅ **Fixed.** Audio recording is described, there is an audio checkbox in the participant consent, and there is a separate Audio Recording Consent form. |
| E3 | Participant consent | Wrong duration, location, and locomotion | ✅ **Fixed.** It now says 50–60 min, Room 7.522, and continuous locomotion with the motion-sickness risk stated. |
| E4 | Instruments | The **custom communication-quality questionnaire is still missing** | ❌ **Open.** Format the 7 Blueprint items (§6.4) as `Arif_Communication Quality Questionnaire-Eng_<date>` and submit it. |
| E5 | Confidentiality agreement | Old study title | ✅ **Fixed** |

### 2.1b New observations on the revised package

| # | Where | Observation | Action |
| --- | --- | --- | --- |
| N1 | IREC application | It is unchanged, so it does not list the new **Audio Recording Consent** form. The submission checklist names only "Consent form(s)". | Mention the added form in the cover email to IREC. Optionally add a line in Part 8.2 / Part 9. |
| N2 | Participant consent | It says "The **Responder** will use a Meta Quest 2 headset" and says nothing about the Analyst's device. The IREC says **two** Quest 2 headsets. It is not wrong, but it is ambiguous. | Keep D4 (Analyst in Quest 2). If the PI prefers a PC Analyst, the IREC text would need to change instead. **Ask the PI (Q7).** |
| N3 | `Team_2_.../*.md` mirrors | `Arif_Participant consent-Eng_09222026.md` and `Arif_Confidentiality Agreement Form-Eng_09222026.md` still contain the **old** text. The Audio Consent form has no `.md` mirror. | Regenerate the `.md` mirrors from the new `.docx` files, or delete them. **The `.docx`/`.doc` files are authoritative.** |
| N4 | Two audio consents | Audio consent is now given twice, as a checkbox and as a separate form. That is consistent, but operationally a single "DO NOT AGREE" ends the pair's session. | Run-sheet rule in §6.2 |

### 2.2 Minor: fix in the same revision

| # | Where | Problem |
| --- | --- | --- |
| M1 | IREC §4.4 | Still says "uncertainty cues, and different information-sharing interfaces". Replace this with "asymmetric map/sensor vs. local information". |
| M2 | Instrument filenames | Missing the `-Eng` language suffix (NASA TLX, SUS, Background, Feedback). The checklist item "named according to protocol" is unticked. |
| M3 | IREC Part 2 | PI's CITI completion date and NU ID are blank. The student-level checkbox is blank. |
| M4 | Background questionnaire | There is no **eligibility screening** section, although §4.7 lists exclusions. Add a short yes/no screening checklist. |
| M5 | Background questionnaire | Add "How well do you know your partner?" and optionally "How often do you play video games?". The Blueprint §5 lists gaming/VR familiarity as a control variable. |
| M6 | SUS / Feedback | SUS has no Pair Code. Add it. |
| M7 | NASA-TLX | Says "after each experimental **condition**". Change it to "**scenario**". |

M1–M7 are **all still open**, because the instruments and the IREC application were not in the revised package.

**Action:** Send the PI a second, smaller pack this week: E4 (communication questionnaire), M1–M7, N1, and N3.

---

## 3. Where the removed AI plans conflict with the IREC protocol and the Team Blueprint

| Topic | Old AI plans | IREC + Team Blueprint | **Decision** |
| --- | --- | --- | --- |
| Independent variable | 3 interface / uncertainty conditions | 3 scenarios | **Scenarios only** |
| Analyst platform | PC desktop tabletop (tech guide) | IREC: two Quest 2. Blueprint: "2D/VR map". | **Quest 2** (IREC wins) |
| Locomotion | Teleport (CrisisLink) | Continuous + snap turn | **Continuous + vignette + snap turn** |
| Speech | Not recorded | Recorded, with timestamps | **Record + timestamp** |
| Fire | Cellular-automata simulation | Scripted triggers (time, location, or waypoint) | **Deterministic scripted hazards** |
| Crouch / O₂ / SAGAT / Muir trust | Yes | Not described | **Cut** |
| Questionnaires | In-VR toolkit | Paper (IREC) | **Paper, headset off** |
| Unity | 2022.3 or Unity 6 | "Unity" | **Unity 6 LTS** |

---

## 4. Final decisions

| ID | Decision | Rationale |
| --- | --- | --- |
| D1 | **Build exactly the IREC and Blueprint study.** Three scenarios, fixed roles, communication-focused metrics. | Anything else needs an amendment |
| D2 | **The adaptive-uncertainty study becomes future work** (amendment or new protocol) | The IREC and Blueprint both say a causal communication study needs a separate manipulation |
| D3 | **Uncertainty survives as fixed content.** The Analyst's sensor panel always shows sensor age and status. In S3, one sensor is stale and the Responder's local view contradicts it. | Matches Blueprint S3: "the Analyst may benefit from the Responder's local observations" |
| D4 | **Topology: the experimenter PC is a dedicated server** (not a player), with both Quests as clients | One authoritative clock, as the Blueprint requires. All logs and audio live on one machine. Roles are set from the console. If the PI chooses a PC Analyst (Q7), only the Analyst client changes. The server design stays the same. |
| D5 | **Use a dedicated offline Wi-Fi router**, not NU campus Wi-Fi | Campus Wi-Fi commonly isolates clients from each other. Latency is repeatable. |
| D6 | **The voice stack must expose per-frame sequence ID + send timestamp + receive/playback timestamp** (Blueprint §11). Two paths are spiked in W1–W2: (a) a custom Opus/PCM relay over our networking layer, or (b) a LAN voice library with packet hooks. Choose the one that meets this criterion. If neither meets it, fall back to ping probes (§5.4). Cloud voice is ruled out (D5). | Frame-level timing is the Blueprint's intended metric |
| D7 | **Separate the participants acoustically**: a partition or separate corners, with wired over-ear headphones on each Quest | If they can hear each other directly, the channel metrics mean nothing |
| D8 | **Scripted, deterministic hazards.** S2's hazard fires at a waypoint (with a time fallback). | Every pair gets the same scenario |
| D9 | **The Analyst sees the Responder at zone level only.** The Blueprint leaves this as "if intended". *Confirm with PI (Q1).* | A live dot turns the task into one-way GPS, which is the Blueprint's "one participant dominates" risk |
| D10 | **No fail screens.** Hazard zones block the Responder and log an unsafe attempt. **Task cap: 5 min** inside a 5–8 min trial slot (Blueprint §14). A timeout is recorded as unsuccessful. | Minimal stress, and sessions stay within 50–60 min |
| D11 | **Comfort settings:** continuous move at about 1.5 m/s (tune in pilot, then fix), conservative acceleration, tunneling vignette, 30° snap turn. Responder may sit in a swivel chair. Analyst sits. | IREC and Blueprint |
| D12 | **Paper questionnaires with the headset off** | IREC says there is no electronic survey |
| D13 | **Counterbalance with the cyclic 3-order Latin square** (Blueprint §5): target **15 pairs, 5 per order**. If recruitment goes up to 18 pairs, add 1 pair per order. | Follows the Blueprint and the IREC's 30-participant target |
| D14 | **Roles are randomly assigned** from a pre-generated schedule | Blueprint §3 |
| D15 | **Stack:** Unity 6 LTS, URP, OpenXR (Meta Quest feature), XRI 3.x, Netcode for GameObjects 2.x, Unity Transport, TextMeshPro. Pin versions on day one. | Unity 2022.3 is out of mainstream support |
| D16 | **Custom server-side CSV logger** with the Blueprint's data dictionary (Appendix A) | Blueprint §12 |
| D17 | **Code structure:** `Assets/_Project/`, an `.asmdef` per module, a pure-C# `Domain` assembly with EditMode tests for metric math | Metrics produce the results, so they must be tested |
| D18 | **Primary outcomes, frozen now** (Blueprint risk "too many outcomes"): **completion time, route efficiency, wrong turns** (pair level), with **evacuation success** reported descriptively. Everything else is secondary or exploratory. | Blueprint §18 |
| D19 | **The Analyst UI never shows a computed safe route.** It shows only map, exits, sensor and hazard states, and alerts. | Blueprint §9: "provide information, not solve the experiment" |
| D20 | **Always-on voice (open mic) for all pairs**, with server-side voice-activity detection producing speech start/end events | The Responder's hands are busy with locomotion. Behaviour is identical for all pairs (Blueprint §9). |
| D21 | **Researcher discipline:** a written instruction script, no coaching during trials, and a predefined restart / invalid-trial rule (§6.2) | Blueprint §14 |

---

## 5. System specification

### 5.1 Topology

```
      [Experimenter PC]  ── dedicated NGO server, the authoritative clock
        ├─ Experimenter console: pair, participant codes, roles, order, start/stop/abort/pause
        ├─ ScenarioManager + SensorManager (authoritative), scoring
        ├─ EventLogger: events.csv, pose.csv, voice_frames.csv, net.csv, trial_summary.csv, session.json
        └─ VoiceManager relay → per-trial stereo WAV (L = Analyst, R = Responder) + VAD events
               │  dedicated offline router (5 GHz)
     ┌─────────┴─────────┐
 [Quest A: Analyst]   [Quest B: Responder]
 seated control room   continuous locomotion in facility
 wired headphones      wired headphones
```

### 5.2 Unity components (Blueprint §13)

| Component | Runs on | Responsibility |
| --- | --- | --- |
| `ExperimentManager` | Server | Pair and participant IDs, role, scenario order, trial state machine |
| `ScenarioManager` | Server | Loads the scenario SO, hazards, exits, triggers, success/timeout |
| `SensorManager` | Server → Analyst | Sensor states, update timestamps, "new change" flags |
| `ResponderController` | Quest B | Locomotion, turning, collisions, position reporting |
| `AnalystUIController` | Quest A | Map, sensor panel, alert feed, zone marker, hover logging |
| `VoiceManager` | All | Capture, send, relay, playback. Frame seq/timestamps, recording, VAD. |
| `NetworkManager` (NGO) | All | Connection, state sync, role-based spawning |
| `EventLogger` | Server | One schema, all files, a trial summary at trial end |
| `TrialController` | Server | Practice → S_a → pause → S_b → pause → S_c. Links each trial to the paper questionnaire sheet ID. |

### 5.3 Roles in VR

**Analyst (Quest A, seated):** a virtual control room with a large map (rooms, corridors, exits open/blocked, sensor icons with ID, status, and **age**), a sensor panel with "newly changed" highlighting, and an alert feed for S2. The Responder appears as a zone-level highlight (D9). There is no computed route (D19). Sensor hovers and alert acknowledgements are logged.

**Responder (Quest B):** a first-person view with no map, no arrows, and no minimap. Local cues are smoke, fire glow, debris, signage, and landmarks. Goal: reach a safe exit while communicating. Local feedback appears only for usability (a blocked message), never as decision support.

### 5.4 Scenarios

All scenarios have matched physical demand: optimal safe path **40–60 m, within ±15%**, the same number of decision points, and comparable visual complexity. Each uses a **different layout variant** (rotated or reconfigured) to reduce memory effects. The practice task uses a separate hazard-free area.

| Scenario | Setup | Coordination challenge | Scenario-specific measures |
| --- | --- | --- | --- |
| S1 Blocked Primary Exit | Responder starts in an office or lab area. The direct route is blocked by fire/smoke. The Analyst's map shows the blocked route **and one viable alternative**. | One-way directional guidance and route following | Instructions count, clarifications, wrong turns |
| S2 Dynamic Hazard Update | The Analyst picks an initially safe route. When the Responder reaches **waypoint Wₖ**, a new smoke/fire event makes the route ahead unsafe. The Analyst's display updates immediately. The Responder receives the update only by voice. | Detect the update, interrupt the old plan, reroute | **Replanning time** (`hazard_update` → `route_change`), reversals, **unsafe approach distance**, decision changes |
| S3 Competing Routes | From a central junction there are three routes. **A:** short, but the sensor on it is stale, and the Responder sees smoke at the entrance (only the Responder knows). **B:** longer and clearly safe. **C:** looks clear from the junction, but the Analyst's map shows a downstream blockage (only the Analyst knows). | **Two-way exchange.** Neither partner can pick B alone. | **Junction decision time**, communication turns, chosen route, route changes |

**Next step (Blueprint §20):** write a one-page spec for each scenario using Blueprint Appendix B, with a map sketch, before implementing. Then implement S1 end to end before building S2 and S3.

### 5.5 Communication measurement (Blueprint §11)

Network-level measures, conversational measures, and perceived measures are **kept separate and never relabelled as each other**.

| Level | Metric | How it is collected |
| --- | --- | --- |
| Transport | Audio latency (mean/median/p95) | Per voice frame: `seq`, `t_send` (sender, in server time via NGO time sync), `t_recv` and `t_play` (receiver). Stored in `voice_frames.csv`. |
| Transport | Jitter | RFC 3550 interarrival jitter over frames, per trial and direction. Computed in `Domain` and unit-tested. |
| Transport | Frame loss / interruptions | Gaps in `seq`, and playback buffer underruns |
| Transport (fallback / supplement) | RTT probes | Server ↔ client ping every 500 ms → `net.csv` |
| Transport (calibration) | Mouth-to-ear delay | One-off clap/loopback test ×20 with no participants. Reported as a system characteristic. |
| Conversation | Speaking turns, response interval | VAD speech start/end per channel. Response interval = end of one partner's utterance → start of the other's reply. **This is human timing, not network latency.** |
| Conversation | Clarifications, repetitions, corrections | Manual coding from audio (§6.5). About 20% double-coded, with Cohen's κ reported. |
| Perceived | Communication quality | Questionnaire (§6.4) |

We do **not** inject artificial latency. That would be a manipulation the IREC does not cover.

### 5.6 Logging (Blueprint §12 + Appendix A)

Every row carries `pair_id, scenario, trial_no, timestamp_ms` (server clock). Participant-level files add `participant_id, role`.

- `session.json`: pair, participant codes, roles, scenario order, build hash, move speed, router channel
- `events.csv`: `trial_start/end`, `hazard_update`, `exit_reached`, `timeout`, `unsafe_zone_entry`, `blocked_route_attempt`, `junction_entered`, `route_choice`, `route_change`, `wrong_turn`, `analyst_hover`, `alert_ack`, `vad_start/end`, `pause`, `stop`, `adverse_discomfort`, `invalid_trial`, with `target_or_zone` and `value` (e.g., `safe->blocked`) columns
- `pose.csv`: Responder position at 10 Hz
- `voice_frames.csv`, `net.csv`: transport timing (§5.5)
- `trial_summary.csv`, **written automatically at trial end**: completion_time_s, success, distance_m, route_efficiency, wrong_turns, blocked_attempts, unsafe_entries, route_changes, replanning_time_s (S2), junction_decision_s (S3), speaking_turns, audio_latency_ms_mean/p95, audio_jitter_ms, frame_loss_pct
- `audio/<pair>_<scenario>.wav`

Coded IDs only. No names are ever typed into the system.

### 5.7 Operational metric definitions (freeze before pilot)

| Metric | Definition |
| --- | --- |
| Evacuation success | Reached an open, safe exit within the 5-min cap |
| Completion time | `trial_start` → `exit_reached`. Timeout = 300 s, and success = 0. |
| Route efficiency | `L_optimal / L_actual` (0–1). The inverse is tortuosity. |
| Wrong turn | At a junction, entering an edge not on any safe route to an open exit |
| Unsafe entry | Entering a hazard trigger volume |
| Blocked-route attempt | Coming within 2 m of a blocked door or debris |
| Route change | Reversal on an edge, or a change of the inferred target exit |
| Replanning time (S2) | `hazard_update` → first `route_change` away from the hazard |
| Unsafe approach distance (S2) | Minimum Responder distance to the new hazard after `hazard_update` |
| Junction decision time (S3) | `junction_entered` at the central junction → leaving it on a chosen route |

---

## 6. Study protocol details

### 6.1 Session run sheet (Blueprint §14, about 55–60 min)

| Stage | Time |
| --- | --- |
| Welcome, screening, **participant consent + Audio Recording Consent** (both participants), codes, role from the schedule, background questionnaire | 5–8 |
| Role-specific tutorial (Analyst: map and sensors. Responder: movement.) | 5 |
| Practice trial (verify movement + voice) | 4–6 |
| Scenario A → headset off, TLX + communication questionnaire, rest | 5–8 + 3–5 |
| Scenario B → same | 5–8 + 3–5 |
| Scenario C → TLX + communication, then SUS + open-ended feedback | 5–8 + 6–10 |
| Completion: file-integrity check, comfort check, backup | 2–3 |

### 6.2 Physical setup & researcher rules
- Partition or maximum separation in 7.522. Wired over-ear headphones. A clear Responder area of at least 2×2 m with a swivel chair. One researcher watches each participant.
- Use the written script for all instructions. **No coaching during trials.**
- **Audio-consent rule:** collect both consent forms from **both** participants before anyone puts on a headset. If either one selects "DO NOT AGREE", the session does not start. Thank both, and offer the consenting participant a new slot with a different partner. Nothing is recorded for that pair. The recruitment message and scheduling reply must say clearly that audio recording is required, so that this rarely happens on the day.
- **Restart rule:** a technical failure (disconnect, crash, voice loss > 10 s) in the first 60 s means restart with the same scenario. After that, mark the trial `invalid_trial` and continue. A participant's discomfort stop ends the session. Log it as `adverse_discomfort` and follow the IREC adverse-event procedure.

### 6.3 Counterbalancing (D13)

| Order | Trial 1 | Trial 2 | Trial 3 | Pairs (15-pair target) |
| --- | --- | --- | --- | --- |
| A | S1 | S2 | S3 | 5 |
| B | S2 | S3 | S1 | 5 |
| C | S3 | S1 | S2 | 5 |

Pre-generate the order and role schedule before the first session. Pairs 16–18 (if recruited) get one each of A, B, C.

### 6.4 Communication Quality Questionnaire (Blueprint §6, 5-point agreement)

The header matches the TLX: participant code, pair code, role, scenario.

1. I could clearly understand my partner throughout the scenario.
2. The communication delay made coordination difficult. *(R)*
3. Audio interruptions or instability affected our decisions. *(R)*
4. I often needed my partner to repeat or clarify information. *(R)*
5. Communication was fast enough for the emergency task.
6. I was confident that my partner understood the information I communicated.
7. Overall, our communication was effective during this scenario.

Score = mean after reversing the *(R)* items. Also report per item, because the scale is not validated. Item 6 serves as the "confidence" measure for H4.

### 6.5 Communication event codebook (audio coding)

| Code | Definition |
| --- | --- |
| CLR | Clarification request ("which door?", "say again") |
| REP | Instruction repeated without being asked |
| COR | Correction of a previous instruction or report |
| OBS | Responder reports a local observation |
| CNF | Explicit confirmation |
| BRK | Breakdown: overlap or lost instruction needing recovery |

### 6.6 Analysis plan (Blueprint §15)
- **Pair level (n ≈ 15):** compare completion time, route efficiency, and wrong turns (primary), plus distance, blocked/unsafe attempts, route changes, and communication counts (secondary), across scenarios. Use repeated-measures ANOVA if assumptions hold, otherwise Friedman. Use linear mixed models (random intercept for pair) for richer models. Report effect sizes and confidence intervals.
- **Scenario-specific:** S2 replanning time and unsafe approach distance. S3 junction decision time and whether the chosen route was safe and efficient.
- **Individual level:** TLX and communication ratings by scenario × role (participant nested in pair). SUS descriptive, **item-level** included.
- **RQ3 / H2 / H4:** repeated-measures correlations or mixed models between latency/jitter, conversation counts, perceived quality, and outcomes. Label these **associational**.
- **Qualitative:** themes from open-ended answers (usability, navigation, realism, communication, discomfort).

### 6.7 Pilot (Blueprint §16)
- **Internal pilot** (team members, unpublished) as soon as S1 runs end to end. Then **2–3 pilot pairs**. *Confirm with PI whether non-team volunteers need to wait for approval (Q6).*
- Check technical stability, scenario fairness (no shortcuts), instruction clarity, locomotion comfort, logging completeness, questionnaire timing, and ceiling/floor effects (S1 not trivial, S3 not impossible).
- **Pass criterion:** from one pilot pair's files alone, the team can reconstruct the full trial story (route, hazard changes, communication problems, decision times, ratings).

---

## 7. What to keep from the older plans and what to cut

**Keep:** grey-box first, the two-headsets-first milestone, server-authoritative state, ScriptableObject scenarios, `_Project/` isolation, asmdefs, pure-C# Domain assembly with tests, Quest 2 performance budget (72 Hz, ≤150 draw calls), continuous move with vignette, sensor-staleness badges (D3), the tortuosity idea (the inverse of route efficiency).

**Cut:** interface conditions, adaptive cue engine, bifurcated path rays, cellular-automata fire, crouch/soot/cough/O₂, SAGAT, Muir trust, in-VR questionnaires, UXF, PC tabletop Analyst, teleportation, four-decision scoring, NPC workers.

### 7.1 Consent forms: done
The revised participant consent and the new Audio Recording Consent (25 Sep 2026) cover everything this section used to require. The one remaining gap is N2 (the Analyst's device is not stated).

---

## 8. TODO

### Ethics revision pack (week of 28 Sep)
- [x] Rewrite the participant consent form (E1–E3). Done 25 Sep 2026.
- [x] Add audio-recording consent. Done: checkbox + separate form.
- [x] Fix the confidentiality agreement title (E5). Done 25 Sep 2026.
- [ ] Format the Communication Quality Questionnaire from the Blueprint items (E4, §6.4)
- [ ] Screening checklist, background additions, SUS Pair Code, TLX wording (M4–M7)
- [ ] Rename instrument files with `-Eng`. Fix §4.4 wording. PI fills in the CITI date and NU ID (M1–M3).
- [ ] Mention the new Audio Recording Consent form to IREC (N1)
- [ ] Regenerate or delete the stale `.md` mirrors of the consent forms (N3)
- [ ] Send the pack to Dr. Arif for forwarding to resethics@nu.edu.kz. Ask the questions in §9.

### Build: Blueprint 10-week dependency order

| Week | Dates | Objective | Exit criterion |
| --- | --- | --- | --- |
| 1 | 28 Sep–4 Oct | Freeze RQs, primary outcomes, role boundaries. **Write the 3 scenario specs (Appendix B).** Unity 6 project, repo, pinned packages. | No open design question that changes the architecture |
| 2 | 5–11 Oct | PC server + 2 Quests on the dedicated router, roles from the console. **Voice spike starts (D6).** | Two users connect reliably with the correct roles |
| 3 | 12–18 Oct | Responder locomotion + grey-box facility + practice area | A comfortable full-map traverse |
| 4 | 19–25 Oct | Analyst control room: map, sensors, alerts, zone marker | Analyst sees the intended global info in real time |
| 5 | 26 Oct–1 Nov | Voice + recording + frame timing + VAD. EventLogger v1. `Domain` metric tests. | Audio works and events are saved with timestamps |
| 6 | 2–8 Nov | S1 + TrialController end to end + trial summary. **Internal team pilot.** | One complete trial from start to saved summary |
| 7 | 9–15 Nov | S2 waypoint trigger + S3 route logic + reset | All three scenarios work and reset |
| 8 | 16–22 Nov | Experiment configuration, schedule, data export, printed questionnaire packets, voice calibration | A full session produces correctly linked datasets |
| 9 | 23–29 Nov | Pilot with 2–3 pairs, then fixes | Protocol completes without major failures, and the reconstruct-the-story test passes |
| 10 | 30 Nov–6 Dec | Freeze and version the build, write the session script, start formal data collection (if IREC-approved) | Frozen build + finalized script |

IREC approval (expected mid to late October) arrives well before W10, so there is no blocking dependency. **If the course deadline (Q2) is before mid-December**, compress by building S2 and S3 in parallel in W6 (two people), and pilot in W8.

### Study operations
- [ ] Pre-generated role and order schedule (§6.3). Code log sheet kept in the locked cabinet (7E428).
- [ ] Printed packets: background, TLX ×3, communication ×3, SUS, feedback per participant
- [ ] Session script, restart/invalid rules, adverse-event log template
- [ ] Recruitment only **after the approval letter**. Zhandaulet is the listed contact.
- [ ] Data collection: about 4 pairs per week, which gives 15 pairs in 4 weeks
- [ ] Audio coding + κ, then analysis (§6.6), report, presentation

---

## 9. Open questions for Dr. Arif

1. **Analyst's view of the Responder:** zone-level marker, no position, or live position (D9)? The Blueprint leaves it open.
2. **Course deadline** for the report and demo. This decides whether to compress the timeline.
3. Is the adaptive-uncertainty idea expected for the course grade? If so, it should be an amendment after approval.
4. Can we use a partition or an adjacent room for acoustic separation? Preferred router or network?
5. Budget for a paid voice asset if the custom relay spike fails?
6. May the 2–3 pilot pairs be non-team volunteers before IREC approval, as long as the pilot is unpublished?
7. The revised consent names a headset only for the Responder. Is the Analyst also in a Quest 2, as the IREC says and D4 assumes, or on a PC screen (N2)?

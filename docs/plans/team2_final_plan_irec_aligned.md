# Team 2 Final Plan: IREC-Aligned Build & Study

**Project:** Collaborative Fire-Evacuation Decision-Making in Virtual Reality: Analyst-Responder Communication, Navigation, and Workload
**PI:** Dr. Syed Muhammad Umair Arif (SCAI) · **Team:** Zhandaulet Kuan, Botakoz Toleugaliyeva, Osman Faizulla, Adi Zhanserik
**IREC submission:** 22 Sep 2026, expedited review (usually 3–4 weeks)
**Plan written:** 25 Sep 2026

---

## 0. Which document wins

The **submitted IREC application** (`Team_2_.../Arif_IREC Application_09222026.md`) is the binding protocol. We may not collect or analyse participant data in any way it does not describe unless we file an amendment first.

The earlier AI-generated plans (CrisisLink Blueprint, `master_plan.md`, `technical_realization_guide.md`, and `session1`/`session2`/`session3_extensions`) described a **different study**: an adaptive-uncertainty interface compared across three conditions. They were **removed on 25 Sep 2026**. The tracked ones can be recovered from git commit `9d41477`. §3 and §7 record what was kept from them.

The remaining companion files are:
- [session3.md](session3.md): the course's project catalog. Our study derives from its "Project 2".
- [team2_assets_and_references_requirements.md](team2_assets_and_references_requirements.md): what 3D assets, open-source models, and citations to find.

---

## 1. What the submitted protocol commits us to

| Item | Committed in IREC |
| --- | --- |
| Research questions | RQ1: How well does the Analyst guide an information-limited Responder to a safe route? RQ2: How do communication delay, jitter, clarification events, and perceived audio quality relate to evacuation time, route efficiency, errors, and route changes? RQ3: How do the scenarios affect workload and how participants rate the system? |
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
| Sample | About 30 participants (minimum 20, maximum 36), meaning **10–18 pairs**. Adults recruited from NU. |
| Session | 50–60 min: consent 5–10, familiarization + practice 5–10, three scenarios 20–25, SUS + feedback about 5 |
| Site / dates | Room 7.522. Data collection 10/2026–10/2027, only after approval. |
| Analysis | Descriptive statistics, then within-pair comparisons at the pair level. Communication–outcome associations are **exploratory and not causal**. Themes from open-ended answers. |
| Future work named in IREC | Deliberately manipulating communication quality is left to "a future approved protocol" |

---

## 2. Problems found in the submission package

### 2.1 Critical: fix before IREC reviews it or returns it

| # | Document | Problem | Fix |
| --- | --- | --- | --- |
| E1 | Participant consent | **It describes the old study.** Its title is "Adaptive Uncertainty Visualization…", it lists private/always-shared/adaptive conditions, a four-decision task (source, route, equipment, rescue), teleportation, and trust/shared-awareness/overload questionnaires. | Rewrite it to match the IREC application (see §7.1) |
| E2 | Participant consent | It says "**Audio and video of participants will not be recorded**", but the IREC application (8.1, 8.2) and the recruitment email say audio **is** recorded. IREC 8.2 also says the consent form asks permission to record, and it does not. | Say audio is recorded and add an explicit checkbox for audio-recording consent |
| E3 | Participant consent | Duration is 35–45 min where the IREC says 50–60 min. Location is "designated VR laboratory" where the IREC says Room 7.522. The risk section says teleportation "rather than continuous artificial movement", which is the opposite of the IREC. | Align duration, location, and locomotion wording. State that continuous locomotion carries a higher risk of motion sickness. |
| E4 | Instruments | The **custom communication-quality questionnaire is missing**, although the application promises it after every scenario. | Draft it (see §6.4) and submit it |
| E5 | Confidentiality agreement | It carries the old study title | Change it to the IREC title |

### 2.2 Minor: fix in the same revision

| # | Where | Problem |
| --- | --- | --- |
| M1 | IREC §4.4 | Still says "uncertainty cues, and different information-sharing interfaces". Replace this with "asymmetric map/sensor vs. local information". |
| M2 | Instrument filenames | Missing the language suffix. `Arif_NASA TLX_09222026` should be `Arif_NASA TLX-Eng_09222026`, and the same applies to the SUS, Background, and Feedback files. The checklist item "named according to protocol" is unticked. |
| M3 | IREC Part 2 | PI's CITI completion date and NU ID are blank. The student-level checkbox is blank. |
| M4 | Background questionnaire | There is no **eligibility screening** section, although §4.7 lists exclusions (seizures, vestibular disorders, severe motion sickness, feeling unwell today). Add a short yes/no screening checklist, either as a separate sheet or inside this questionnaire. |
| M5 | Background questionnaire | Recommended addition: "How well do you know your partner?" (not at all / acquaintance / friend). Familiarity strongly affects communication, which RQ2 is about. Adding it now is cheap because the application is still under review. |
| M6 | SUS / Feedback | SUS has a Participant ID but no Pair Code. Add Pair Code so the data can be joined. |
| M7 | NASA-TLX | Says "after each experimental **condition**". Change it to "**scenario**". |

**Action:** Send the PI one revision pack (E1–E5, M1–M7) this week, so it goes to IREC with the first round of reviewer comments or ahead of them.

---

## 3. Where the older plans conflict with the IREC protocol

| Topic | Blueprint | Master plan / Tech guide | IREC (binding) | **Decision** |
| --- | --- | --- | --- | --- |
| Independent variable | 3 interface conditions | 3 uncertainty-vis conditions | 3 scenarios | **Scenarios only** |
| Analyst platform | Quest 2 | **PC desktop tabletop** | Quest 2 | **Quest 2** |
| Locomotion | Teleport | Continuous + vignette | Continuous | **Continuous + vignette + snap turn** |
| Task | 4 scored decisions | Route + SAGAT | Navigate to a safe exit | **Evacuation navigation** |
| Speech | Not recorded | Word counts | **Recorded** | **Record audio on the server** |
| Voice system | "No custom voice chat" | Not addressed | Needs timestamps and network logs | **Networked VoIP + probe logging (§5.4)** |
| Fire | Static effects | Cellular-automata simulation | Scripted scenarios | **Deterministic scripted hazards** |
| Crouch / soot / cough / O₂ | — | Yes | Not described | **Cut** |
| SAGAT / Muir trust | — | Yes | Not described | **Cut** |
| Questionnaires | Short in-VR | VRQuestionnaireToolkit | Paper | **Paper, headset off** |
| Sample | 8–12 pairs | 36 pairs | 10–18 pairs | **Target 18, minimum 10** |
| Unity | — | 2022.3 LTS *or* Unity 6 | — | **Unity 6 LTS** |

---

## 4. Final decisions

| ID | Decision | Rationale |
| --- | --- | --- |
| D1 | **Build exactly the IREC study.** Three scenarios, fixed roles, communication-focused metrics. No interface conditions. | Anything else needs an amendment and puts approval at risk |
| D2 | **The adaptive-uncertainty study becomes future work**, filed later as an amendment or follow-up protocol | The IREC itself leaves manipulation to "a future approved protocol" |
| D3 | **Uncertainty survives as fixed content.** The Analyst's sensor panel always shows sensor age and confidence. S3 depends on a stale or faulty sensor that contradicts what the Responder sees. | Matches IREC S3: "sensor information and the Responder's local observations must be combined". This keeps the core idea without adding a condition. |
| D4 | **Topology: the experimenter PC is a dedicated server** (not a player), with both Quests as clients | Logs, audio, and experimenter controls live on one machine, so files never need to be pulled off the headsets. Roles are assigned explicitly rather than by connection order. |
| D5 | **Use a dedicated offline Wi-Fi router**, not NU campus Wi-Fi | Campus Wi-Fi commonly isolates clients from each other. Latency on our own router is also repeatable. |
| D6 | **Voice runs over the LAN through our own networking stack.** Default choice is Dissonance Voice Chat with its Netcode for GameObjects integration. The fallback is a custom PCM relay. Cloud voice (Vivox, Photon) is ruled out because of D5. | We need offline operation, server-side recording, and timestamps |
| D7 | **Separate the participants acoustically.** Use a partition in 7.522, or opposite corners, with each Quest wired to over-ear headphones. | If they can hear each other directly, the "communication channel" metrics mean nothing |
| D8 | **Scripted, deterministic hazards.** S2's hazard fires when the Responder reaches a specific decision node (with a time fallback). No fire simulation. | Every pair must get the same scenario |
| D9 | **Analyst sees the Responder only at zone level**, as a marker that updates on zone entry, never a live dot | A live dot turns the task into map-following. Zone-level position keeps verbal description necessary for RQ1 and RQ2. *Confirm with PI (Q1).* |
| D10 | **No death or fail screens.** A hazard zone blocks the Responder with a short "Too hot / blocked" message and a push-back, and it is logged as an unsafe attempt. Each scenario has a **5-minute cap**. | Keeps stress minimal as promised to IREC and keeps sessions within 50–60 min |
| D11 | **Comfort settings:** continuous move at about 1.5 m/s (tune in pilot, then fix for all sessions), tunneling vignette, 30° snap turn, Responder may sit in a swivel chair, Analyst sits | IREC promises moderate speed and snap turning |
| D12 | **Paper questionnaires with the headset off** between scenarios. This doubles as the break. | IREC says there is no electronic survey |
| D13 | **Target 18 pairs** (the IREC maximum of 36 participants), which gives a complete 6-order counterbalance (§6.3). Minimum 10 pairs. | 3! = 6 orders × 3 pairs each |
| D14 | **Roles are assigned at random** (coin flip) per pair and recorded in session metadata | IREC does not specify, so randomizing is the defensible choice |
| D15 | **Stack:** Unity 6 LTS, URP, OpenXR (Meta Quest feature), XR Interaction Toolkit 3.x, Netcode for GameObjects 2.x, Unity Transport, TextMeshPro. Pin exact versions in `ProjectVersion.txt` and `manifest.json` on day one. | Unity 2022.3 LTS is out of mainstream support, and the tech guide's manifest pins 2022-era packages |
| D16 | **Custom CSV logger on the server.** Drop UXF. | UXF's per-participant session model does not fit a server-authoritative pair session |
| D17 | **Keep the tech guide's code-structure rules:** `Assets/_Project/`, `.asmdef` per module, a pure-C# `Domain` assembly with EditMode tests | Metric math (route efficiency, wrong turns, jitter) must be unit-tested because it produces the results |

---

## 5. System specification

### 5.1 Topology

```
      [Experimenter PC]  ── dedicated NGO server, not a player
        ├─ Experimenter console: pair code, role assignment, scenario order, start/stop/abort
        ├─ Authoritative scenario state, hazard triggers, scoring
        ├─ Logger: events.csv, pose.csv, net.csv, session.json
        └─ Voice listener → per-trial stereo WAV (L = Analyst, R = Responder)
               │  dedicated offline router (5 GHz)
     ┌─────────┴─────────┐
 [Quest A: Analyst]   [Quest B: Responder]
 seated control room   continuous locomotion in facility
 wired headphones      wired headphones
```

### 5.2 Roles in VR

**Analyst (Quest A, seated)**
- Sits in a virtual control room with one large world-space map panel: floor plan, exits (open/blocked), and sensor icons (smoke/heat, value, **age**, confidence).
- A hazard alert feed shows timestamped updates. These drive S2.
- The Responder appears as a highlighted zone, updated on zone entry (D9).
- Interaction is minimal: a ray hover shows sensor details. Hovers are logged as interaction events.
- Text must be legible on Quest 2. Test on device in week 1. Use colour together with icons and labels.

**Responder (Quest B)**
- First-person view in the facility, with no map and no path guidance. **Guidance comes only by voice.**
- Can see local cues: smoke, fire glow, debris, exit signs, and door states.
- Uses continuous move, vignette, and snap turn (D11).
- Reaching an open, safe exit ends the trial with success.

### 5.3 Scenarios

All scenarios use one building shell. Each scenario has its own start point, exit set, and hazard placement, with **optimal safe-path lengths within ±15% of each other**. The practice task uses a separate small hazard-free area.

| Scenario | Setup | What the team must do | Key logged moment |
| --- | --- | --- | --- |
| Practice | Small area with one exit and no hazards | Analyst guides Responder to the exit | — |
| S1 Blocked Primary Exit | Nearest exit is blocked by smoke/fire. Analyst's exit status shows it. | Analyst routes Responder to an alternative exit | First wrong turn toward the blocked exit |
| S2 Dynamic Hazard Update | Initial route is safe. When the Responder reaches node *Nₖ*, a sensor alert fires for the segment ahead. The visual hazard appears only when the Responder gets close. | Analyst notices the alert, interrupts the plan, and redirects | `t_update` → `t_route_change` (reaction latency) |
| S3 Competing Routes | Three routes. Sensors favour route A, but one sensor on A is stale or low-confidence. The Responder sees smoke on A. Route B is safe. Route C is safe but longer. | Combine the sensor readings with the Responder's report and choose B | Whether and when the Responder's observation is reported, and the route chosen |

Scenario definitions live in ScriptableObjects (as in the Blueprint): nodes, edges, exits, hazards, triggers, and the optimal path.

### 5.4 Communication measurement (RQ2)

| Metric | How it is collected |
| --- | --- |
| Network delay | The server sends `Ping(seq, t_send)` to each client every 500 ms and the client echoes it immediately. RTT is logged to `net.csv`, with one-way delay estimated as RTT/2. |
| Jitter | RFC 3550-style smoothed mean deviation of successive delay samples, per trial and per client. Computed in `Domain` and unit-tested. |
| Voice-pipeline latency | A **one-off calibration with no participants**: clap/loopback test, repeated 20 times, measuring mouth-to-ear delay through the whole stack. Reported as a system characteristic. |
| Packet loss / dropouts | Gaps in the ping sequence, plus voice-library statistics if the library exposes them |
| Clarification events | **Manually coded from the audio** using the codebook in §6.5. Two coders double-code about 20% of trials, and Cohen's κ is reported. |
| Perceived quality | Custom questionnaire (§6.4) |

We do **not** inject artificial latency. That would be a manipulation the IREC does not cover.

### 5.5 Logging schema (server, coded IDs only)

- `session.json`: pair code, participant codes, role assignment, scenario order, build hash, move speed, router channel, start time
- `events.csv`: `t_server, pair, scenario, event, actor, arg1, arg2`
  - Events: `trial_start/end`, `zone_enter`, `node_pass`, `wrong_turn`, `unsafe_attempt`, `blocked_exit_attempt`, `hazard_update`, `route_change`, `sensor_hover`, `exit_reached`, `timeout`, `abort`
- `pose.csv`: Responder position and heading at 10 Hz (needed for the movement path and route length)
- `net.csv`: `t_server, client, seq, rtt_ms`
- `audio/<pair>_<scenario>.wav`: stereo, with the start time recorded in `events.csv`

**Never** type names or student IDs into the system. The code-to-identity link stays on paper in the locked cabinet.

### 5.6 Operational metric definitions (freeze before pilot)

| Metric | Definition |
| --- | --- |
| Evacuation success | Reached an open, safe exit before the 5-minute cap |
| Completion time | `trial_start` → `exit_reached` (capped value on timeout) |
| Route efficiency | `L_optimal / L_actual` (0–1). `L_actual` comes from `pose.csv`. |
| Wrong turn | At a decision node, entering an edge that is not on any safe route to an open exit |
| Unsafe attempt | Entering a hazard trigger volume |
| Blocked-exit attempt | Reaching within 2 m of a blocked exit door |
| Route change | Responder reverses direction on an edge, or their target exit (inferred from the next two nodes) changes |
| S2 reaction latency | `hazard_update` → first `route_change` away from the hazard segment |

---

## 6. Study protocol details

### 6.1 Session run sheet (about 55 min)

1. Arrival, screening checklist, consent including the audio checkbox, codes assigned, coin flip for roles, background questionnaire (10)
2. Fit headsets and headphones, then tutorial and practice (10)
3. Scenario 1 → headset off, TLX + communication questionnaire (~8)
4. Scenario 2 → headset off, same questionnaires (~8)
5. Scenario 3 → headset off, same questionnaires (~8)
6. SUS + open-ended feedback, discomfort check, thanks (5–8)

### 6.2 Physical setup (Room 7.522)
- Partition or maximum separation. Wired over-ear headphones on both Quests.
- Responder area of at least 2×2 m, clear, with a swivel chair available.
- Experimenter PC and router on a table. One researcher watches each participant.
- Wipes and face covers for hygiene. Headsets fully charged, with a spare battery pack.

### 6.3 Counterbalancing (18 pairs)

| Order | Sequence | Pairs |
| --- | --- | --- |
| O1 | S1 S2 S3 | 3 |
| O2 | S1 S3 S2 | 3 |
| O3 | S2 S1 S3 | 3 |
| O4 | S2 S3 S1 | 3 |
| O5 | S3 S1 S2 | 3 |
| O6 | S3 S2 S1 | 3 |

If recruitment stops early, finish the current block of 6 or use the three Latin-square orders O1/O4/O5. Pre-generate the assignment list before the first session.

### 6.4 Draft: Communication Quality Questionnaire (to submit as `Arif_Communication Quality Questionnaire-Eng_<date>`)

The header matches the TLX: participant code, pair code, role, scenario. Items use a 5-point scale (1 = strongly disagree … 5 = strongly agree).

1. I could hear my partner clearly.
2. I noticed a delay between when my partner spoke and when I heard them. *(R)*
3. The audio cut out, stuttered, or was interrupted. *(R)*
4. I had to ask my partner to repeat or clarify information. *(R)*
5. I understood my partner's instructions or descriptions without difficulty.
6. I was able to convey the information I wanted to my partner.
7. Overall, communication with my partner during this scenario was effective.

Score = mean after reversing the *(R)* items. Report per-item results too, because the scale is not validated.

### 6.5 Communication event codebook (for audio coding)

| Code | Definition |
| --- | --- |
| CLR | Clarification request ("which door?", "say again") |
| REP | Instruction repeated without being asked |
| COR | Correction of a previous instruction or report |
| OBS | Responder reports a local observation (smoke, blocked, sign) |
| CNF | Explicit confirmation ("ok, turning left") |
| BRK | Breakdown: overlapping speech or instruction lost, needing recovery |

### 6.6 Analysis plan
- The unit of analysis is the **pair** for task outcomes, and the **participant nested in pair** for TLX, communication questionnaire, and SUS, reported by role.
- Scenario effects on outcomes: Friedman test (n ≤ 18 pairs), or a linear mixed model with pair as a random intercept if assumptions hold. Report effect sizes and confidence intervals.
- RQ2: mixed model or repeated-measures correlation between communication metrics (jitter, CLR count, questionnaire score) and outcomes (time, efficiency, errors). **Label it exploratory and associational**, as promised to IREC.
- Open-ended answers: thematic grouping (navigation, communication, interface, discomfort).

---

## 7. What to keep from the older plans and what to cut

**Keep:** Blueprint scope discipline, grey-box first, the two-headsets-first milestone, discrete event logging, server-authoritative state, ScriptableObject scenarios, scenario-matching rules, readability/accessibility rules, and the risk table. From the tech guide: `_Project/` isolation, asmdefs, pure-C# Domain assembly with tests, Quest 2 performance budget (72 Hz, ≤150 draw calls), continuous move with vignette. From the master plan: the tortuosity idea (our route efficiency is its inverse) and sensor-staleness badges (D3).

**Cut:** Interface conditions and the adaptive cue engine, bifurcated path rays, the cellular-automata fire simulation, crouch/soot/cough/oxygen mechanics, SAGAT, Muir trust scale, in-VR questionnaires, UXF, the PC tabletop Analyst, teleportation, four-decision scoring, and multiple facility types.

**Tech-guide code to fix before reusing it:**
- `NetworkRoleManager` subscribes to `ConnectionApprovalCallback` inside `OnNetworkSpawn`. Approval must be enabled and wired **before** `StartServer()`. It also assigns roles by connection order, which is replaced by the experimenter console (D4).
- `RoomDefinition` uses `init` accessors. Unity needs an `IsExternalInit` shim for these, or plain setters.
- The manifest pins 2022.3-era packages, which conflicts with D15.

### 7.1 Rewritten consent form: required contents
Include: IREC title; Room 7.522; 50–60 min; pairs with fixed Analyst/Responder roles, both in Quest 2; three fire-evacuation scenarios plus practice; continuous locomotion with its motion-sickness risk and mitigations; **audio of the communication channel recorded, stored under codes, never published, deleted after the retention period**; automatic logs (path, times, route events, network timing); questionnaires (background, NASA-TLX, communication quality, SUS, feedback). Keep: no video or biometrics, voluntary participation, withdrawal and data-removal rules, contacts. Add a checkbox: "I agree to audio recording of my communication during the VR tasks (required for participation)."

---

## 8. TODO

### Now (week of 28 Sep): ethics revision pack
- [ ] Rewrite the participant consent form (E1–E3, §7.1)
- [ ] Draft and format the Communication Quality Questionnaire (E4, §6.4)
- [ ] Fix the confidentiality agreement title (E5)
- [ ] Add a screening checklist and the "know your partner" item (M4, M5). Add Pair Code to the SUS and Feedback forms (M6). Change "condition" to "scenario" in the TLX (M7).
- [ ] Rename the instrument files with `-Eng` (M2). Fix §4.4 wording (M1). Get the PI to fill in the CITI date and NU ID (M3).
- [ ] Send the pack to Dr. Arif for forwarding to resethics@nu.edu.kz
- [ ] Ask the PI the open questions in §9

### Technical (tech weeks 1–5, before approval)
- [ ] **W1:** Unity 6 LTS project, `_Project/` layout, asmdefs, Git LFS, pinned packages. Quest 2 build working. **Milestone: PC server + 2 Quests on the dedicated router, roles assigned from the console, one synced state.**
- [ ] **W1 spike:** Voice over LAN with the chosen library: two Quests talking, server records a stereo WAV, ping probe logging to `net.csv`. If it is not working by the end of W2, fall back to a custom PCM relay.
- [ ] **W2:** Grey-box building shell, tutorial area, continuous move + vignette + snap turn, zone/node triggers
- [ ] **W3:** Analyst control room (map, exits, sensors with age/confidence, alert feed, zone marker). Scenario ScriptableObjects. Experimenter console (pair code, order, start/stop/abort).
- [ ] **W3:** `Domain` metrics (route efficiency, wrong turn, route change, jitter) with EditMode tests. Logger v1.
- [ ] **W4:** Author S1–S3 with matched optimal path lengths (±15%). S2 node trigger. Hazard blocking and push-back. 5-minute cap.
- [ ] **W4:** Voice-latency calibration (clap test ×20). Legibility and 72 Hz check on device.
- [ ] **W5:** **Internal pilot with team members only** (allowed before approval as long as it is unpublished). Tune speed and comfort, then freeze metric definitions (§5.6) and the build.

### Study operations
- [ ] Printed questionnaire packets per pair (TLX ×3 + communication ×3 per participant)
- [ ] Pre-generated counterbalance and role list (§6.3). Code log sheet kept in the locked cabinet (7E428).
- [ ] Session run sheet and discomfort/adverse-event log template
- [ ] Recruitment only **after the approval letter**. Zhandaulet is the listed contact.
- [ ] Data collection: about 4–5 pairs per week to reach 18 pairs
- [ ] Audio coding (§6.5) with double-coding for κ, then analysis (§6.6), report, and presentation

---

## 9. Open questions for Dr. Arif

1. **Analyst's view of the Responder:** is a zone-level marker acceptable, or should the Analyst have no position information (D9)?
2. **Course deadline:** when are the final report and demo due? This decides whether the analysis can cover all 18 pairs or only a first batch.
3. Is the adaptive-uncertainty idea expected for the course grade? If so, it should be an amendment after approval, not part of this build.
4. Can we use a separate room or partition in or near 7.522 for acoustic separation? Does the PI have a preferred router or network?
5. Budget for a paid voice asset (Dissonance) if the spike needs it?
6. Should a later amendment switch to electronic (offline, in-lab) questionnaires, or do we stay on paper?

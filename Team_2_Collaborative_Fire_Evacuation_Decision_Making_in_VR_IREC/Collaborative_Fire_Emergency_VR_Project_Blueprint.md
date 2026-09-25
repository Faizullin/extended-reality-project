## COLLABORATIVE FIRE-EMERGENCY DECISION-MAKING IN VIRTUAL REALITY

## Project Description, Research Design, Technical Architecture, Implementation Plan, and Evaluation Blueprint

ANALYST

Global map + sensor information

Remote decision support

Core study idea: asymmetric information + real-time voice communication +

collaborative evacuation

ON-SITE RESPONDER First-person local view Locomotion + evacuation

Prepared as a practical implementation blueprint for the research team


## 0. How to Use This Blueprint

This document is designed to function as the project team's working blueprint. It defines what the system should do, what the three fire scenarios should contain, what data should be collected, how the study should be run, and how the final research can be analyzed. The recommended core design keeps the project focused: one remote Analyst has global information, one On-Site Responder has only local first-person information, and the pair must

communicate to achieve a safe evacuation.

## Recommended core research focus

Investigate how teams coordinate evacuation decisions when critical information is distributed across two roles, and how communication quality, task complexity, and workload relate to navigation and evacuation performance.

## Document map

- 1. Project concept and research contribution

- 2. Research questions and hypotheses

- 3. Participant roles and information asymmetry

- 4. Three fire-emergency scenarios

- 5. Experimental design and variables

- 6. Measurements and questionnaires

- 7. VR system architecture

- 8. Environment, locomotion, and interaction design

- 9. Analyst interface

- 10. Responder experience

- 11. Voice communication and delay/jitter measurement

- 12. Logging and data structure

- 13. Unity implementation plan

- 14. Experimental session protocol

- 15. Data analysis plan

- 16. Pilot testing and validation

- 17. Development timeline

- 18. Risks, failure modes, and mitigation

- 19. Expected outputs and final research story

- 20. Final team checklist


## 1. Project Concept and Research Contribution

The project is a two-person collaborative VR fire-evacuation simulation. The two participants do not have the same information. The Control-Room Analyst has a global overview of the building and receives sensor information, while the On-Site Responder is immersed in the virtual environment and initially has no map or global hazard knowledge. The Responder must navigate using continuous locomotion and must rely on communication with the Analyst while also reporting local observations back to the Analyst.

The important research problem is therefore not simply "Can a person escape from a VR fire?" The research problem is how two people make time-critical decisions when neither person independently possesses the complete operational picture.

| Research component | What it means in this project |
| --- | --- |
| Asymmetric information | Analyst has global map and sensor data; Responder |
|   | has first-person local observations. |
| Collaborative decision-making | The safe route emerges from communication and |
|   | coordination rather than from one participant acting |
|   | alone. |
| Dynamic emergency context | The environment can contain blocked exits, changing |
|   | hazards, and competing routes. |
| Communication quality | Voice communication is recorded/logged and |
|   | objective timing metrics are captured where |
|   | technically possible. |
| Human factors | NASA-TLX measures perceived workload; a custom |
|   | questionnaire measures communication quality; SUS |
|   | measures overall usability. |
| Behavioral performance | The system logs completion time, route choice, wrong |
|   | turns, blocked-route attempts, replanning, distance, |
|   | and other task events. |

## What makes the project research rather than a demo

The VR environment is only the experimental platform. The research comes from clearly defined scenarios, controlled information asymmetry, repeatable task procedures, objective event logging, validated questionnaires, and a pre-defined analysis plan.

## 2. Research Questions and Hypotheses

A focused set of research questions prevents the project from becoming a collection of unrelated metrics. The following structure is recommended.

| ID | Research question |
| --- | --- |
| RQ1 | How effectively can a remote Analyst with map and |
|   | sensor information guide an information-limited On- |
|   | Site Responder to a safe evacuation route in a VR fire |
|   | emergency? |


| ID | Research question |
| --- | --- |
| RQ2 | How does the type of coordination challenge (static |
|   | blocked route, dynamic hazard update, competing |
|   | routes) affect evacuation performance, navigation |
|   | behavior, and workload? |
| RQ3 | How are measured communication delay/jitter and |
|   | perceived communication quality associated with |
|   | evacuation time, route errors, clarification requests, |
|   | and decision changes? |
| RQ4 | How do Analyst and Responder roles differ in |
|   | perceived workload and communication experience? |
| RQ5 | How usable do participants find the completed |
|   | collaborative VR system after experiencing all |
|   | scenarios? |

## Recommended hypotheses

- H1: Scenarios requiring replanning or comparison of competing routes will produce longer task times and more communication events than the static baseline scenario.

- H2: Higher communication delay/jitter will be associated with more clarification/repetition and poorer route efficiency.

- H3: Analyst and Responder workload profiles will differ because the Analyst performs global information integration while the Responder performs navigation and local hazard interpretation.

- H4: Higher perceived communication quality will be associated with higher decision confidence and better task performance.

- H5: Participants will report that the complete system is usable for the intended simulated collaborative task, evaluated descriptively through SUS.

## Important causality rule

If network delay/jitter is only observed and not deliberately manipulated, report associations rather than claiming that delay caused performance changes. A causal communication- quality study would require controlled latency/jitter conditions.

## 3. Participant Roles and Information Asymmetry

The role design is the central mechanism of the experiment. Keep the information boundaries consistent across all scenarios.

| Control-Room Analyst | On-Site Responder |
| --- | --- |
| Sees a global building/floor map. | Does not receive the global map before or during the |
|   | task. |
| Sees active fire/smoke sensor indicators and route- | Sees only the local first-person environment and local |
| related status information. | visual cues. |
| Can reason about alternative routes and upcoming | Must physically navigate using VR locomotion and |
| hazards. | interpret local corridors/doors/signage. |


| Control-Room Analyst | On-Site Responder |
| --- | --- |
| Communicates directional instructions and hazard | Reports local observations, confirms instructions, and |
| updates. | makes movement decisions. |
| Primarily performs global monitoring and planning. | Primarily performs navigation, local perception, and |
|   | execution. |

## Role assignment

- Randomly assign Analyst and Responder roles within each pair, or use a pre-generated balanced assignment schedule.

- Keep roles fixed across the three experimental scenarios unless role switching is itself a research variable.

- Record the assigned role with every questionnaire and log file so role-level analysis is possible.

## 4. Three Fire-Emergency Scenarios

The three scenarios should represent three different coordination problems while keeping general environment size, approximate safe-route length, number of decision points, and visual complexity reasonably comparable. Different maps or rotated/reconfigured layouts should be used to reduce memory effects.

## Scenario 1 - Blocked Primary Exit (Baseline Guidance)

Purpose: establish baseline Analyst-to-Responder guidance when the hazard is static and the safe alternative route is known from the start.

| Element | Recommended design |
| --- | --- |
| Initial condition | Responder starts inside an office/lab area. The most |
|   | direct exit route is unsafe because one corridor or |
|   | doorway is affected by fire/smoke. |
| Analyst information | Map clearly shows the blocked primary route and one |
|   | viable alternative route. |
| Responder information | No map. The Responder sees only the immediate |
|   | environment and must follow spoken guidance. |
| Main challenge | Accurate directional communication and route |
|   | following. |
| Primary measures | Evacuation time, wrong turns, distance, number of |
|   | instructions, clarification requests, route efficiency, |
|   | NASA-TLX, communication questionnaire. |

## Scenario 2 - Dynamic Hazard Update (Replanning)

Purpose: test whether the pair can abandon a previously correct plan and coordinate a new evacuation route when environmental information changes during the task.

| Element | Recommended design |
| --- | --- |
| Initial condition | The Analyst identifies an initially safe route and the |
|   | Responder begins following it. |


| Element | Recommended design |
| --- | --- |
| Dynamic event | After a predefined trigger (time, location, or |
|   | waypoint), a new fire/smoke event makes part of the |
|   | current route unsafe. |
| Analyst information | The sensor/map display updates immediately or |
|   | within the intended system timing. |
| Responder information | The Responder is not automatically given the global |
|   | update and must receive the new plan through |
|   | communication. |
| Main challenge | Detecting the update, interrupting the old plan, |
|   | communicating the change, and successfully |
|   | rerouting. |
| Primary measures | Hazard-update-to-route-change time, reversals, |
|   | unsafe approach distance, decision changes, |
|   | completion time, communication events, workload. |

## Scenario 3 - Competing Routes (Collaborative Choice)

Purpose: require the pair to integrate global sensor/map information with local Responder observations before choosing among multiple possible routes.

| Element | Recommended design |
| --- | --- |
| Initial condition | At least two or three plausible evacuation routes are |
|   | available from a central decision point. |
| Route trade-off | One route is shorter but unsafe or uncertain; another |
|   | is longer but clearly safe; a third may appear visually |
|   | clear but contain a downstream blockage. |
| Analyst information | Global map and sensors reveal route-level |
|   | constraints, but the Analyst may benefit from the |
|   | Responder's local observations. |
| Responder information | First-person view may reveal smoke, blocked doors, |
|   | signage, or local visibility that is not obvious on the |
|   | Analyst display. |
| Main challenge | Two-way information exchange and collaborative |
|   | route selection rather than simple one-way |
|   | navigation instructions. |
| Primary measures | Decision time at junction, communication turns, |
|   | route changes, chosen route, route efficiency, |
|   | workload, communication quality, confidence. |

## Scenario-matching rule

Do not make Scenario 3 simply much larger or longer than Scenario 1. If completion time differs because one map is twice as large, the result says little about coordination. Keep physical task difficulty as comparable as possible and vary the coordination problem.


## 5. Experimental Design and Variables

Recommended design: a paired repeated-measures study. Each pair completes all three scenarios. Scenario order should be counterbalanced so that Scenario 1 is not always first and Scenario 3 is not always last.

| Variable type | Recommended variables |
| --- | --- |
| Within-pair independent variable | Scenario type: blocked primary exit, dynamic hazard |
|   | update, competing routes. |
| Role variable | Analyst vs Responder. |
| Observed communication variables | Measured latency, jitter, packet/audio interruptions if |
|   | available, communication response timing, number of |
|   | clarifications/repetitions. |
| Primary pair-level outcomes | Evacuation success, task completion time, route |
|   | efficiency, navigation errors, unsafe/blocked-route |
|   | attempts. |
| Secondary pair-level outcomes | Replanning time, number of route changes, |
|   | communication turns, decision changes. |
| Individual outcomes | NASA-TLX after each scenario; custom communication |
|   | questionnaire after each scenario; SUS after all |
|   | scenarios. |
| Control/context variables | Prior VR experience, role, scenario order, participant |
|   | pair ID, and optionally gaming/VR familiarity. |

## Counterbalancing example for three scenarios

| Pair group | Trial 1 | Trial 2 | Trial 3 |
| --- | --- | --- | --- |
| Group A | Scenario 1 | Scenario 2 | Scenario 3 |
| Group B | Scenario 2 | Scenario 3 | Scenario 1 |
| Group C | Scenario 3 | Scenario 1 | Scenario 2 |

If you recruit 30 participants, this produces 15 pairs. A balanced allocation would place roughly five pairs in each order. Treat pair-level outcomes as 15 repeated-measures units, not as 30 independent observations.

## 6. Measurements and Questionnaires

Use objective system logs and subjective instruments together. Objective logs show what participants did; questionnaires show how they experienced the task.

| Measure | When | What it tells you |
| --- | --- | --- |
| NASA-TLX | After each scenario | Perceived workload across mental, |
|   |   | physical, temporal, performance, |
|   |   | effort, and frustration dimensions. |


| Measure | When | What it tells you |
| --- | --- | --- |
| Custom communication | After each scenario | Perceived clarity, delay, |
| questionnaire |   | interruptions, ease of understanding, |
|   |   | need for repetition, confidence in |
|   |   | communication, and overall |
|   |   | communication effectiveness. |
| SUS | Once after all scenarios | Overall perceived usability of the |
|   |   | complete collaborative VR system. |
| Background questionnaire | Before VR | Prior VR experience and relevant |
|   |   | experience variables used for |
|   |   | context/control. |
| Open-ended feedback | At the end | What participants found confusing, |
|   |   | useful, difficult, realistic, or in need |
|   |   | of improvement. |

## Suggested custom communication items (5-point agreement scale)

- I could clearly understand my partner throughout the scenario.

- The communication delay made coordination difficult. (reverse/negative item)

- Audio interruptions or instability affected our decisions. (negative item)

- I often needed my partner to repeat or clarify information. (negative item)

- Communication was fast enough for the emergency task.

- I was confident that my partner understood the information I communicated.

- Overall, our communication was effective during this scenario.

Keep the custom questionnaire short. Its goal is not to duplicate NASA-TLX or SUS; it should focus specifically on perceived communication quality.

## 7. VR System Architecture

A modular architecture will make the system easier to debug and will produce cleaner research data. The system should separate the fire simulation, participant interfaces, networking/voice, and logging.

| ANALYST CLIENT | SHARED / NETWORK LAYER | RESPONDER VR CLIENT |
| --- | --- | --- |
| 2D/VR map + sensor panel | State synchronization | First-person VR environment |
| Route/hazard information | Voice communication | Continuous locomotion + turning |
| Analyst event logger | Timestamped messages / audio stats | Responder movement logger |
| Questionnaires / trial controller | Central experiment logger | Local interaction + hazard events |

## Recommended implementation stack

- Unity as the primary development environment.

- OpenXR and/or Unity XR Interaction Toolkit for Meta Quest 2-compatible VR input and interactions.

- A networking layer capable of synchronizing participant state, scenario events, and trial status over the local network.

- A voice communication subsystem that supports or can be instrumented with timestamps/sequence numbers for objective timing metrics.


- CSV or JSON event logging with one synchronized experiment clock across both clients whenever possible.

## 8. Environment, Locomotion, and Interaction Design

The VR environment should feel like a plausible indoor facility without becoming visually complex enough to create uncontrolled difficulty. The goal is to study decision-making and communication, not photorealistic firefighting.

## Environment requirements

- A corridor/room layout with clear intersections, doors, exit points, and recognizable landmarks.

- Non-graphic fire/smoke hazards that clearly communicate unsafe areas without distressing visual content.

- Exit signs and local environmental cues that the Responder can see, but no global map for the Responder.

- Scenario-specific blocked routes, hazard triggers, and sensor objects linked to the Analyst interface.

- Stable frame rate on the target headset to avoid adding performance-induced discomfort or timing noise.

## Locomotion recommendation

Use continuous joystick-based locomotion for the On-Site Responder because movement is now part of the navigation task. Keep movement speed fixed across participants and scenarios. Use snap turning by default unless smooth turning is an explicit design requirement. The practice trial should teach movement before experimental data are recorded.

## Safety and research-quality balance

Continuous locomotion is more natural for route-following research but can increase cybersickness. Keep trials short, provide breaks, allow immediate stopping, use conservative movement speed/acceleration, and pilot-test the system before participant recruitment.

## 9. Analyst Interface

The Analyst interface should prioritize situation awareness and route planning. Avoid giving the Analyst unnecessary controls or visual effects that could become a second experimental variable.

| Panel | Recommended content |
| --- | --- |
| Building map | Rooms, corridors, exits, route connectivity, Responder |
|   | location if that is part of the intended design. |
| Sensor layer | Fire/smoke detector IDs and current status; clear |
|   | visual indication of newly changed sensors. |
| Hazard/route status | Blocked corridor/door state and safe/unsafe route |
|   | indicators only if those are intended Analyst data. |
| Scenario notifications | Dynamic hazard update events, presented |
|   | consistently across scenarios. |


| Panel | Recommended content |
| --- | --- |
| Communication | Push-to-talk or always-on voice according to the |
|   | chosen design; keep the behavior identical for all |
|   | pairs. |
| Research logging | Timestamp Analyst selections, alerts acknowledged, |
|   | map interactions, and route-related actions if those |
|   | interactions are relevant. |

Do not automatically compute and display the "correct answer" unless route optimization itself is not part of the human task. If the Analyst is supposed to reason about the map and sensor state, the interface should provide information, not solve the experiment for them.

## 10. Responder Experience

The Responder should feel locally informed but globally uncertain. This creates the need for collaboration.

- Starts without a floor map and without advance knowledge of hazard locations.

- Receives a clear goal: reach a safe evacuation exit while communicating with the Analyst.

- Uses first-person locomotion to move between rooms and corridors.

- Can observe local smoke/fire, blocked doors, signs, landmarks, or other environmental cues.

- Can report local observations back to the Analyst.

- Should not receive automatic global route arrows, minimaps, or hidden guidance that bypasses the Analyst.

- Should receive immediate local feedback for collisions/interactions only when needed for usability, not decision support.

## Design principle

The Analyst should know more about the global state; the Responder should know more about the immediate local state. If either participant can solve the task alone, the collaboration mechanism becomes weak.

## 11. Voice Communication and Delay/Jitter Measurement

Separate network-level communication quality from human conversational behavior. They are related but not the same measurement.

| Level | Examples | How to measure |
| --- | --- | --- |
| Network/audio transport | Latency, jitter, packet/frame loss, | Use timestamps, sequence numbers, |
|   | audio interruption | or statistics exposed by the |
|   |   | communication subsystem. |
|   |   | Synchronize clocks or use one |
|   |   | authoritative timing source when |
|   |   | possible. |
| Conversation behavior | Response time, repetitions, | Derive from audio recording and/or |
|   | clarifications, interruptions, | timestamped push-to-talk/voice- |
|   | corrections | activity events. |
| Perceived quality | Clarity, perceived delay, | Custom post-scenario |
|   | communication difficulty | communication questionnaire. |


## Recommended timestamp logic

For each transmitted audio frame/message, record a sequence ID and send timestamp. At the receiver, record the receive/playback timestamp. Approximate one-way communication latency is then the receive timestamp minus the send timestamp, assuming clocks are sufficiently synchronized. Jitter can be represented as variation in delay across successive frames/messages.

For human communication, record the start/end time of Analyst speech and Responder speech. A response interval can be computed as the time from the end of one participant's relevant instruction to the start of the partner's reply or corresponding action. This interval includes human processing and should not be labeled "network latency."

## 12. Logging and Data Structure

The strongest version of this project will have synchronized logs that make every important event reconstructable after the study.

| Field | Example | Purpose |
| --- | --- | --- |
| pair_id | Pair07 | Links both participants without using |
|   |   | names. |
| participant_id | P13 | Links individual questionnaire data. |
| role | Responder | Allows role-level analysis. |
| scenario | DynamicHazard | Identifies condition. |
| timestamp_ms | 183245 | Orders all events on a common clock. |
| event_type | wrong_turn / hazard_update / | Defines what happened. |
|   | route_change |   |
| position_xyz | x,y,z | Supports path/distance reconstruction. |
| target_or_zone | Corridor_B | Adds location meaning to events. |
| audio_seq / send / receive | 248 / 152330 / 152410 | Supports timing/jitter analysis. |
| value / metadata | safe->blocked | Stores state changes. |

## Minimum event list to log

- trial_start and trial_end

- hazard_update

- exit_reached

- unsafe_zone_entry

- blocked_route_attempt

- junction_entered / route_choice

- route_change

- position samples at a fixed interval

- Analyst alert/interaction events

- voice timing/network events

- pause/stop/adverse-discomfort event

Create a trial-summary file automatically at the end of each scenario: completion time, success/failure, total distance, route efficiency, wrong turns, blocked/unsafe attempts, number of route changes, communication counts, and available latency/jitter summaries.


## 13. Unity Implementation Plan

Build the project in layers. Avoid developing all three scenarios before the basic two-user system is stable.

| Step | Deliverable |
| --- | --- |
| 1. Build a single-room network prototype | Two devices connect; each participant can see the other |
|   | participant's state; trial start/stop is synchronized. |
| 2. Implement Responder locomotion | Continuous movement, turning, collision, |
|   | doorway/corridor traversal, recentering, and a safe |
|   | practice area. |
| 3. Implement Analyst map | Simple floor map, Responder marker if intended, exits, |
|   | sensor indicators, and scenario state. |
| 4. Add voice communication | Reliable two-way audio first; then add recording/timing |
|   | instrumentation. |
| 5. Build central event logger | One event schema used by both clients; write |
|   | timestamped CSV/JSON files. |
| 6. Implement Scenario 1 | Static hazard and blocked exit; verify the entire task loop |
|   | end to end. |
| 7. Implement dynamic event system | Trigger hazard state changes based on time or |
|   | Responder location; use it for Scenario 2. |
| 8. Implement route alternatives | Create matched junction/route structure and route-status |
|   | logic for Scenario 3. |
| 9. Add questionnaires/trial controller | Present or link post-scenario instruments and store |
|   | IDs/scenario order correctly. |
| 10. Add experiment configuration | Pair ID, participant IDs, role assignment, scenario order, |
|   | trial number, and logging folder are set before each |
|   | session. |
| 11. Run automated/technical tests | Verify triggers, logs, timestamps, network reconnect |
|   | behavior, and missing-data handling. |
| 12. Pilot with real users | Use 2-3 pairs to detect confusing instructions, unfair |
|   | scenario difficulty, cybersickness, logging gaps, and |
|   | audio problems. |

## Suggested Unity component structure

- ExperimentManager - participant IDs, role, scenario order, trial state.

- ScenarioManager - hazards, exits, triggers, success/failure conditions.

- SensorManager - sensor states and updates sent to the Analyst interface.

- ResponderController - locomotion, turning, interactions, position tracking.

- AnalystUIController - map, sensor panel, alerts, route/hazard display.

- VoiceManager - two-way audio, recording hooks, timing/sequence metrics.

- NetworkManager - state synchronization and session connection.

- EventLogger - standardized timestamped events written to file.

- QuestionnaireLink/Controller - opens or records post-trial instruments while preserving participant/scenario IDs.


## 14. Experimental Session Protocol

A consistent session procedure is essential. Every pair should receive the same instructions, practice opportunity, scenario timing rules, and questionnaire timing.

| Stage | Recommended procedure | Approx. time |
| --- | --- | --- |
| 1. Welcome / setup | Confirm pair IDs and role assignment; | 5-8 min |
|   | explain study task and safety; complete |   |
|   | background information. |   |
| 2. Role-specific tutorial | Analyst learns map/sensors; Responder | 5 min |
|   | learns VR movement and local |   |
|   | interactions. |   |
| 3. Practice trial | Simple non-experimental environment; | 4-6 min |
|   | verify movement and voice |   |
|   | communication. |   |
| 4. Scenario A | Run first counterbalanced fire scenario. 5-8 min |   |
| 5. Post-scenario instruments | NASA-TLX + communication | 3-5 min |
|   | questionnaire; short rest. |   |
| 6. Scenario B | Run second scenario. | 5-8 min |
| 7. Post-scenario instruments | NASA-TLX + communication | 3-5 min |
|   | questionnaire; short rest. |   |
| 8. Scenario C | Run third scenario. | 5-8 min |
| 9. Final instruments | NASA-TLX + communication | 6-10 min |
|   | questionnaire, then SUS and open- |   |
|   | ended feedback. |   |
| 10. Completion | Check file integrity and participant | 2-3 min |
|   | comfort; save/backup coded data. |   |

## Researcher discipline

Do not coach pairs during experimental trials unless a safety or technical issue requires intervention. Use a written script for instructions and a predefined rule for when a trial is restarted or marked invalid.

## 15. Data Analysis Plan

Define the analysis before collecting the full dataset. This prevents the team from choosing only the metrics that look interesting afterward.

## Primary pair-level analysis

- Compare completion time across the three scenarios.

- Compare route efficiency, total distance, wrong turns, unsafe/blocked-route attempts, and number of route changes.

- Compare communication counts such as total speaking turns, clarifications, repetitions, and instruction corrections if coded.

- For Scenario 2, analyze hazard-update-to-route-change time as a specific replanning measure.


- For Scenario 3, analyze time spent at the key route-choice junction and whether the selected route was safe/efficient.

## Individual-level analysis

- Compare NASA-TLX across scenarios and examine whether the Analyst and Responder show different workload patterns.

- Compare custom communication ratings across scenarios and roles.

- Summarize SUS for the system after all trials; inspect item-level problems rather than relying only on one overall number.

- Summarize open-ended feedback into recurring usability, navigation, realism, and communication themes.

## Statistical approach

For a small repeated-measures HCI study, start with descriptive statistics and confidence intervals. If assumptions are reasonable, repeated-measures ANOVA can compare scenario-level outcomes; otherwise use a Friedman test for within-pair/within-participant comparisons. For a richer analysis, linear mixed-effects models can account for repeated measures and pair/participant clustering. Report effect sizes and uncertainty, not only p-values. Because pair- level task outcomes are shared by two participants, do not treat the two members of a pair as independent observations for the same evacuation-time value.

## Communication association analysis

Examine whether higher measured delay/jitter is associated with longer completion time, lower route efficiency, more repetition/clarification, or poorer communication ratings. If delay/jitter was not experimentally manipulated, describe these as correlations/associations rather than causal effects.

## 16. Pilot Testing and Validation

Do not begin the main study immediately after the system first works. Run structured pilots.

| Pilot goal | What to check |
| --- | --- |
| Technical stability | Headset performance, connection stability, voice clarity, |
|   | recording, timestamps, trigger reliability, file writing. |
| Scenario fairness | Similar approximate route length and baseline |
|   | movement demand; no accidental shortcut; no |
|   | impossible instruction. |
| Instruction clarity | Participants understand role boundaries and task goal |
|   | without researcher coaching. |
| Locomotion comfort | Movement speed/turning do not cause unacceptable |
|   | discomfort during the expected trial duration. |
| Logging completeness | Every primary metric can actually be reconstructed from |
|   | saved data. |
| Questionnaire timing | NASA-TLX and communication items are completed after |
|   | the correct scenario and IDs are preserved. |
| Ceiling/floor effects | Scenario 1 is not so easy that everyone performs |
|   | perfectly; Scenario 3 is not so hard that everyone fails. |

Pilot success criterion: the research team should be able to take one pilot pair's files and reproduce the entire trial story - what route they took, when hazards changed, what


communication problems occurred, how long decisions took, and how participants rated the experience.

## 17. Development Timeline

A practical 10-week implementation schedule is shown below. Adjust it to the course/research calendar, but preserve the dependency order.

| Week | Main objective | Exit criterion |
| --- | --- | --- |
| 1 | Finalize research questions, scenario | No unresolved design questions that |
|   | specifications, measures, role | change the software architecture. |
|   | boundaries. |   |
| 2 | Build networking + role assignment | Two users connect reliably and receive |
|   | prototype. | correct roles. |
| 3 | Responder locomotion and base | Responder can comfortably navigate a |
|   | environment. | complete test map. |
| 4 | Analyst map + sensors + synchronized | Analyst sees intended global |
|   | Responder state. | information in real time. |
| 5 | Voice communication + event logging. Audio works and trial events are saved |   |
|   |   | with timestamps. |
| 6 | Scenario 1 + end-to-end trial controller. One complete trial runs from start to |   |
|   |   | saved summary. |
| 7 | Scenario 2 dynamic hazards + Scenario | All three scenario logics work and can |
|   | 3 route alternatives. | reset. |
| 8 | Questionnaires, experiment | A full session produces correctly linked |
|   | configuration, data export. | datasets. |
| 9 | Pilot testing and fixes. | 2-3 pairs complete the protocol without |
|   |   | major technical/research-design |
|   |   | failures. |
| 10 | Freeze build, document procedures, | Versioned experiment build and |
|   | begin formal data collection. | written session script are finalized. |

## 18. Risks, Failure Modes, and Mitigation

| Risk / failure mode | Why it matters | Mitigation |
| --- | --- | --- |
| Scenario difficulty confound | Performance differences may reflect | Match route length/decision points and |
|   | map size rather than coordination. | pilot-test difficulty. |
| Order/learning effect | Participants learn the | Use different maps and counterbalance |
|   | interface/building over time. | scenario order. |
| Audio metrics mislabeled | Human response delay can be confused | Log network timing separately from |
|   | with network latency. | speech/behavior timing. |
| Missing synchronization | Events from two devices cannot be | Use shared/authoritative timestamps or |
|   | aligned afterward. | clock-offset correction. |
| Continuous-locomotion sickness | May increase dropout or distort | Practice, moderate speed, snap turning, |
|   | workload. | short trials, breaks, stop rule. |
| One participant dominates | Task becomes one-way GPS rather than | Design Scenario 3 so Analyst needs at |
|   | collaboration. | least one local Responder observation. |


| Risk / failure mode | Why it matters | Mitigation |
| --- | --- | --- |
| Overloaded questionnaires | Participants become fatigued and | Use short scenario-level instruments; |
|   | ratings degrade. | SUS only once at the end. |
| Too many outcomes | Research story becomes unfocused. | Declare 2-4 primary outcomes and |
|   |   | treat the rest as secondary/exploratory. |
| Small pair count | Inferential power is limited. | Use repeated measures, report effect |
|   |   | sizes/uncertainty, and frame claims |
|   |   | appropriately. |
| System changes mid-study | Data become incomparable. | Freeze the experimental build once |
|   |   | formal data collection begins. |

## 19. Expected Outputs and Final Research Story

At the end of the project, the system should produce more than a VR demonstration. The final deliverables should support a clear research narrative.

| Output | What it should demonstrate |
| --- | --- |
| Working collaborative VR prototype | Analyst and Responder can complete all three fire |
|   | scenarios over a synchronized two-user system. |
| Scenario framework | Three repeatable coordination challenges: static |
|   | rerouting, dynamic replanning, and competing-route |
|   | decision-making. |
| Objective dataset | Navigation, timing, hazard, route-choice, and |
|   | communication events are recorded reliably. |
| Subjective dataset | Workload, communication quality, usability, and final |
|   | comments are linked correctly to |
|   | participant/role/scenario. |
| Research findings | Evidence about how distributed information, scenario |
|   | coordination demands, and communication quality |
|   | relate to collaborative evacuation performance. |
| Design recommendations | Practical lessons for collaborative VR emergency |
|   | simulations and remote-support interfaces. |

## The final research story in one sentence

When global emergency information and local situational information are divided between two people, successful evacuation depends on how effectively they establish shared understanding, update plans, and communicate under time pressure.

## 20. Final Team Checklist

- Research questions and primary outcomes are frozen before formal data collection.

Scenario 1, 2, and 3 use comparable physical task demands and different coordination

demands.

- Scenario order is counterbalanced.

Analyst and Responder information boundaries are consistent and documented.


Continuous locomotion is stable and tested for comfort.

Voice communication works reliably and is recorded/logged as intended.

Network timing metrics and human communication timing are clearly separated.

All trial events share a usable timing reference.

NASA-TLX is administered after each scenario.

Custom communication questionnaire is administered after each scenario.

SUS is administered once after the complete system experience.

Pair-level and participant-level IDs are used consistently across all files.

The experiment build automatically saves a summary for every trial.

Pilot participants can understand the study without extra researcher coaching.

The formal experiment build is frozen and versioned before data collection.

The team can reconstruct a complete trial from the exported logs.

## Recommended next step

Before building all three scenarios, create a one-page scenario specification for each case containing: map sketch, start point, safe exit, blocked/unsafe areas, Analyst-only information, Responder-visible cues, dynamic triggers, success/failure conditions, and every metric to be logged. Then implement Scenario 1 end to end before duplicating the framework for Scenarios 2 and 3.


## Appendix A. Minimal Trial Data Dictionary

| Variable | Level | Type | Example |
| --- | --- | --- | --- |
| pair_id | Pair | ID | Pair07 |
| participant_id | Individual | ID | P13 |
| role | Individual | Categorical | Analyst |
| scenario | Trial | Categorical | S2_DynamicHazard |
| scenario_order | Pair | Categorical | 2-3-1 |
| completion_time_s | Pair-trial | Continuous | 186.4 |
| success | Pair-trial | Binary | 1 |
| distance_m | Pair-trial | Continuous | 94.2 |
| route_efficiency | Pair-trial | Continuous | 0.82 |
| wrong_turns | Pair-trial | Count | 2 |
| blocked_attempts | Pair-trial | Count | 1 |
| route_changes | Pair-trial | Count | 2 |
| replanning_time_s | Pair-trial | Continuous | 12.7 |
| clarifications | Pair-trial | Count | 4 |
| audio_latency_ms_mean | Pair-trial | Continuous | 85 |
| audio_jitter_ms | Pair-trial | Continuous | 12 |
| nasa_tlx_* | Individual-trial | Scale | ratings |
| comm_quality_* | Individual-trial | Scale | ratings |
| sus_total/items | Individual-session | Scale | responses |


## Appendix B. Scenario Specification Template

| Field | Team specification |
| --- | --- |
| Scenario name |   |
| Research purpose |   |
| Map/layout identifier |   |
| Responder start location |   |
| Safe exit(s) |   |
| Unsafe/blocked area(s) |   |
| Analyst-only information |   |
| Responder-visible local cues |   |
| Dynamic trigger(s) |   |
| Expected coordination challenge |   |
| Success condition |   |
| Failure/invalid-trial conditions |   |
| Primary metrics |   |
| Secondary metrics |   |
| Target duration |   |
| Pilot notes / balancing changes |   |

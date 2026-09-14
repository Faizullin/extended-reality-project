System Architecture Blueprint
                      ┌────────────────────────────────────────────────────────┐
                      │              CENTRAL SIMULATION AUTHORITY              │
                      │   • Cellular Automata Fire / Smoke Propagation Engine  │
                      │   • Physical Ground-Truth States (Blocked Exits, Debris│
                      │   • Noise-Injected Sensor Matrix (IoT Thermal / Gas)   │
                      └───────────────────────────▲────────────────────────────┘
                                                  │
                      State Replication via Low-Latency Network Broker
                      (Unity Netcode for GameObjects / Photon Fusion 2)
                                                  │
                 ┌────────────────────────────────┴────────────────────────────────┐
                 ▼                                                                 ▼
 ┌───────────────────────────────┐                                 ┌───────────────────────────────┐
 │    ROLE 1: CONTROL ANALYST    │                                 │   ROLE 2: FIELD RESPONDER     │
 │       (Exocentric Macro)      │                                 │      (Egocentric Micro)       │
 ├───────────────────────────────┤                                 ├───────────────────────────────┤
 │ • Holographic Tabletop Twin   │                                 │ • 1:1 First-Person Scale      │
 │ • Historical Trend Heatmaps   │                                 │ • Stratified Smoke / Heat FX  │
 │ • Telemetry Health Indicators │                                 │ • Physical Posture & Crouch   │
 │ • Macro Waypoint Dispatch     │                                 │ • Wrist Tactical Terminal     │
 └───────────────┬───────────────┘                                 └───────────────┬───────────────┘
                 │                                                                 │
                 │              Two-Way Discrepancy & Agreement Stream             │
                 └────────────────────────► ◄──────────────────────────────────────┘
                                            │
                                            ▼
                 ┌─────────────────────────────────────────────────────────────────┐
                 │                    ADAPTIVE CONFLICT ENGINE                     │
                 │ • Compares Telemetry vs. Ground-Truth Line-of-Sight             │
                 │ • Evaluates Conflict Delta: |Sensor_Value - Field_Report| > θ   │
                 │ • Context Gating: Activates alerts only at decision branches    │
                 └──────────────────────────┬──────────────────────────────────────┘
                                            │
               State-Driven Adaptive Uncertainty Rendering Pipeline
                                            │
       ┌────────────────────────────────────┴────────────────────────────────────┐
       ▼                                                                         ▼
 [Analyst Viewport]                                                     [Responder Viewport]
 • Isobar Confidence Shells                                             • Bifurcated Navigation Rays
 • Stale Ping Timestamps                                                • Perimeter Warning Halos
 • Probability Spread Cones                                             • Hazard Degradation Icons
                                            │
                                            ▼
 ┌─────────────────────────────────────────────────────────────────────────────────────────────────┐
 │                               HCI RESEARCH & EVALUATION HARNESS                                 │
 │ • UXF (Unity Experiment Framework): Continuous 10 Hz Trajectory & Gaze Recording                │
 │ • VRQuestionnaireToolkit: In-Headset SAGAT Freeze-Frames, NASA-TLX, and Muir's Trust Form       │
 └─────────────────────────────────────────────────────────────────────────────────────────────────┘
Open-Source Toolchains & Package Ecosystem
Integrating vetted community and academic packages avoids writing redundant infrastructure from scratch:
Functional Layer	Standard Package / Open-Source Tool	Purpose & Integration Role
Networking & Replication	Unity Netcode for GameObjects (NGO) (alt: Photon Fusion 2)	Handles client-host state replication, RPC dispatching for waypoints, and low-latency positional transforms across Quest 2 clients.
XR & Spatial Interaction	XR Interaction Toolkit (XRI 3.x) + Meta XR Core SDK	Powers continuous thumbstick locomotion, dynamic anti-cybersickness tunneling vignettes, and spatial ray interactor bindings for the tabletop.
Immersive Analytics & Vis	IATK (Immersive Analytics Toolkit) & DXR (Data-Driven XR)	Academic engines for binding multidimensional data to spatial primitives. Used to generate 3D density graphs, confidence envelopes, and sensor node arrays.
Experimentation Framework	UXF (Unity Experiment Framework)	Handles session management, Latin-square balanced condition rotations, event logging, and local CSV telemetry serialization.
In-VR Psychometrics	VRQuestionnaireToolkit	Renders spatial, interactive questionnaires directly inside the Quest 2 for immediate, unbroken post-trial NASA-TLX and Muir's Trust scoring.
Spatial Environment	Synty Studios Emergency / Simple Buildings (Optimized)	Low-poly textured spatial layouts that run within mobile fill-rate budgets while maintaining clean architectural sightlines.
Dual-Role Mechanics & Physicality
Role 1: Control-Room Analyst (Exocentric "God-View")
Interface: A scaled holographic architectural model positioned at waist level.
Controls: Tabletop panning, elevation rotation, and a spatial ray pointer allowing the analyst to place virtual waypoints, mark priority rooms, and inspect telemetry nodes.
Information Asymmetry: Sees room temperatures, automated suppression states, and predictive fire propagation cones. Blind to physical structural debris, wedged fire exits, and localized smoke stratification.
Role 2: On-Site Responder (Egocentric First-Person)
Interface: Full-scale 1:1 physical immersion inside the burning facility.
Locomotion System: Left-stick continuous translation equipped with an automated dynamic FOV vignette (aperture constricts to 45 
∘
  during linear/angular acceleration to suppress optical flow vection) paired with right-stick snap-turning (30 
∘
  increments).
Physical Crouch Stratification: Headset vertical tracking (H 
HMD
​	
 ) maps responder posture relative to a thermal layer threshold (1.25 m). Standing upright triggers high-density visual soot overlays, audio coughing cues, and stamina depletion. Physically dropping into a low crawl or crouch clears the viewport, rewarding authentic interior firefighting tactics.
Information Asymmetry: Directly perceives immediate structural blocks, victim positions, and ambient heat warnings, but possesses zero corridor-to-corridor macro-awareness.
Adaptive Uncertainty State Logic
To avoid cognitive overload while preventing premature decision closure, visualizations transition dynamically through three defined states based on the conflict delta Δ=∣S 
analyst
​	
 −O 
responder
​	
 ∣:
[Level 0: Nominal]
• Triggers: Sensor packet loss < 2s, telemetry aligns with responder pathing.
• Visuals: Solid waypoint lines, flat green status markers, precise route corridors.

[Level 1: Unverified / Degraded]
• Triggers: Sensor age exceeds staleness threshold (> 8s) or packet drop occurs.
• Visuals: Path perimeter softens with semi-transparent edge fuzziness; sensor glyph displays a decaying latency clock.

[Level 2: Conflicted / High Divergence]
• Triggers: Field report contradicts sensor telemetry (e.g., room marked clear by IoT node, but responder flags structural fire).
• Visuals: Route splits into a bifurcated ray (intended route turns dashed amber; alternative safe path highlights with animated error envelopes); spatial notification rings flash at the conflict locus.
Scientific Study Design & Validation Pipeline
A within-subject (3×1) Latin-square balanced experimental protocol evaluates collaborative performance across three discrete environmental conditions:
                        36 Participant Pairs (N = 72)
                                     │
                     Standardized In-VR Locomotion Tutorial
                                     │
         ┌───────────────────────────┼───────────────────────────┐
         ▼                           ▼                           ▼
[Condition A: Baseline]    [Condition B: Static]       [Condition C: Adaptive]
Binary deterministic data; All confidence bounds &      Visualizations adaptively
conflicts remain hidden    uncertainty envelopes        trigger only upon spatial
until physical encounter.  render continuously.         divergence or decision gates.
         │                           │                           │
         └───────────────────────────┼───────────────────────────┘
                                     │
              Multi-Metric Evaluation Capture (Per Condition)
Shared Situational Awareness (SAGAT): Two random freeze-frames per trial run. Both viewports instantly fade to neutral gray; users independently identify active fire boundaries and safe extraction doors on an interactive 2D floorplan.
Cognitive Workload (NASA-TLX): Administered via the VRQuestionnaireToolkit immediately after each block, measuring mental demand, effort, and frustration scales.
System & Interpersonal Trust: Modified Muir’s Trust Scale evaluates the responder’s trust in sensor telemetry versus verbal communication from the analyst.
Decision Accuracy & Path Efficiency: System logs route tortuosity (ratio of actual distance traveled to optimal trajectory), aggregate duration spent in superheated environments (>100 
∘
 C), and latency to alter compromised evacuation routes.
Standalone Quest 2 Optimization Budget
Maintaining a locked 72 Hz refresh rate (frame budget <13.88 ms) on the mobile Snapdragon XR2 Gen 1 platform requires rigid resource caps:
Draw Calls & Polygons: Draw calls must remain below 150 per frame; target under 250,000 active triangles in any visible frustum.
Pipeline Configuration: Universal Render Pipeline (URP) running Single-Pass Instanced rendering to process stereo geometry in a single execution pass.
Particle Management: Avoid multi-layered transparent alpha particles for smoke. Use stylized, screen-depth-faded geometric smoke cards with vertex deformation to preserve mobile tile-based GPU fill-rate.
Texture & Memory Footprint: Max texture size of 2048px with ASTC 6x6 compression. Lightmaps baked statically; dynamic shadows disabled in favor of contact shadows and projected ambient occlusion decals.
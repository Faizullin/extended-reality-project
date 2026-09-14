There is no single, turnkey open-source repository available online that contains this exact fire emergency simulation with the adaptive uncertainty engine, asymmetric control-room/responder roles, and experiment logging pre-built into one cloneable project.
However, you do not need to build everything from scratch. The system can be rapidly assembled by cloning and combining several well-maintained open-source foundations and modular templates:
1. Networking & Multi-User VR Scaffolding (Ready to Clone)
Instead of writing custom network replication, you can clone either of two established foundations:
Unity VR Multiplayer Template (com.unity.template.vr-multiplayer):  
Where to find: Available directly through Unity Hub (Unity 2022 LTS or Unity 6) or via the Unity Package Manager.  
What it provides out-of-the-box: Pre-configured Netcode for GameObjects (NGO), Unity Transport (UTP), XR Interaction Toolkit (XRI), networked avatar head/hand synchronization, and the XR Device Simulator for testing multiplayer interactions on a PC without needing two physical headsets powered on.  
Ubiq (University College London):  
Where to find: Open-source on GitHub (UCL-VR/ubiq).
Why use it: Specifically designed for academic VR researchers. It is far lighter than commercial SDKs, runs cleanly on the Meta Quest 2's Snapdragon XR2 processor, and natively supports heterogeneous/asymmetric player prefabs (letting Client 1 spawn an allocentric desk interface and Client 2 spawn a first-person navigation rig).  
Meta’s Official Multiplayer Repositories:  
Where to find: GitHub (oculus-samples/Unity-SharedSpaces or oculus-samples/Unity-LocalMultiplayerMR).  
What it provides: Listen-server architectures combining Netcode for GameObjects with Meta Quest hardware integration, social voice pipelines, and spatial transform synchronization.  
2. Locomotion & Visual Tunneling (Ready in Unity XRI)
For the responder’s continuous locomotion with dynamic field-of-view (FOV) restriction:
XR Interaction Toolkit (XRI) Locomotion Package:
Unity’s official XRI package includes a built-in TunnelingVignetteController and ContinuousMoveProvider.
Implementation: Attach the TunnelingVignetteController component to the responder's camera rig. It dynamically samples linear acceleration and angular velocity, automatically constricting the peripheral viewport with a soft-edged vignette during joystick movement, matching the cybersickness mitigation parameters required for the study.  
3. Asymmetric Reference Architecture (Academic Inspiration)
CoMap (Collaborative 3D Sketch Mapping for Search & Rescue):  
Architecture: Evaluated in academic human-computer interaction literature, CoMap establishes the specific interaction paradigm of pairing an allocentric commander (using 3D layered maps and external sensor overlays) with an egocentric responder (navigating physical hazards and verifying blocked corridors).  
Code availability: While the design and evaluation are documented in academic publications, the repository is maintained within university lab environments (such as Exertion Games Lab) and is generally accessible by reaching out directly to the authors for an academic research artifact share.  
Summary: What to Clone vs. What to Write
Subsystem	Best Cloneable / Open-Source Starting Point	Custom Code You Must Add
Networking & Avatars	
Unity VR Multiplayer Template or UCL Ubiq  

Assigning role IDs (Analyst vs. Responder) on client connection.
Locomotion	
Unity XRI TunnelingVignetteController + ContinuousMoveProvider

[cite: 1, 8]

Clamping speed parameters and configuring snap-turn increments.  

Tactical Desk (Analyst)	
Unity World-Space Spatial UI Prefabs  

Scaling down the building mesh into an interactive 3D table-top view.  

Uncertainty & Discrepancies	None (Custom logic required)	
Implementing the Discrepancy Index equation D 
i
​	
 (t) and triggering visual iso-shells or halos.

Experimental Harness	
In-VR UI Canvas / Unity JsonUtility  

Scripting the SAGAT freeze trigger, blanking screens, and logging consensus timestamps to JSON.  

To build the project efficiently, start by cloning the Unity VR Multiplayer Template, enable XRI's built-in Tunneling Vignette for the responder, and focus your custom development entirely on the asymmetric UI layers and the adaptive uncertainty scripting.
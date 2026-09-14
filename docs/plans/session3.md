**Human-Centered Collaborative and Adaptive Virtual Reality**

The objective of these projects should not be simply to develop VR applications. Each student group should develop:

**A VR interaction mechanism → controlled experimental manipulation → measurable human behavior → research contribution.**

The projects below are designed as independent studies. Most are based on two-user collaborative VR because collaborative behavior provides richer research variables than standard single-user VR.

A strong study should measure both:

- **Objective behavior:** task time, errors, trajectories, head/hand movement, communication, assistance requests, synchronization, collisions, etc.
- **Subjective experience:** workload, presence, social presence, trust, usability, awareness, collaboration quality, confidence, etc.

# PROJECT 1 — Adaptive Information Sharing in Collaborative VR

## Core Idea

Two users collaboratively solve a complex task, but each user possesses only part of the information required to complete it.

The research question is not simply whether collaboration helps.

The contribution is:

**When and how should VR automatically expose a collaborator's information to establish common ground without overwhelming the other user?**

## Collaborative Scenario

Create a virtual industrial control room, emergency-response environment, machine-repair scenario, or complex assembly task.

### User A — Analyst/Expert

User A can see:

- technical instructions,
- system status,
- hazard indicators,
- component specifications.

### User B — Operator

User B can:

- manipulate equipment,
- move objects,
- activate controls,
- physically perform the task.

Neither participant can complete the task independently.

They must communicate and establish a shared understanding.

## Experimental Conditions

### Condition 1 — Manual Information Sharing

User A verbally explains information to User B.

### Condition 2 — Always-On Shared Information

User B continuously sees User A's relevant information.

### Condition 3 — Adaptive Shared Information

The system displays information only when it detects potential coordination difficulty.

For a student implementation, adaptation can use simple behavioral rules such as:

- operator remains inactive for >5 seconds;
- incorrect object is selected;
- repeated failed interaction occurs;
- users are looking at different task regions;
- operator requests help.

## Main Research Questions

**RQ1:** Can adaptive information sharing improve collaborative performance compared with manual communication and continuous information sharing?

**RQ2:** Does adaptive information sharing reduce communication effort while maintaining common ground?

**RQ3:** Can too much shared information increase cognitive workload even when task performance improves?

**RQ4:** When during collaboration is additional shared information most beneficial?

## Hypothesis

Adaptive information sharing will provide a better balance between:

**information availability and information overload.**

## Measurements

### Objective

- task completion time;
- errors;
- failed actions;
- idle time;
- number of verbal instructions;
- number of clarification requests;
- assistance-trigger frequency;
- time spent in disagreement;
- head-direction similarity;
- distance between collaborators.

### Subjective

- NASA-TLX;
- social presence;
- perceived collaboration quality;
- perceived awareness;
- usability;
- trust in system assistance.

## Potential Contribution

The contribution is not:

"We developed collaborative VR."

Instead:

**We investigate when shared information should become visible during asymmetric VR collaboration and identify the trade-off between common-ground formation and information overload.**

This is considerably stronger.

# PROJECT 2 — Adaptive Collaborative Emergency Decision-Making in VR

## Core Idea

Two VR users must jointly make safety-critical decisions during an evolving emergency.

The novelty comes from studying:

**how conflicting information and adaptive decision support affect shared situation awareness.**

## Collaborative Scenario

Example:

A virtual industrial facility experiences:

- fire,
- smoke,
- equipment malfunction,
- blocked pathways,
- injured virtual workers.

Two participants must decide:

1. where the emergency originates;
2. which hazards are most serious;
3. which route should be used;
4. whether equipment should be shut down;
5. which virtual workers should be evacuated first.

## Information Asymmetry

### User A

Receives:

- building map;
- sensor readings;
- alarm information.

### User B

Receives:

- direct environmental observations;
- worker locations;
- visible hazards.

Important:

Some information can intentionally be incomplete or contradictory.

The users must resolve the discrepancy.

## Experimental Conditions

### Condition 1 — Independent Information

Users communicate verbally.

### Condition 2 — Shared Information Visualization

Important information from both users appears in a common virtual workspace.

### Condition 3 — Uncertainty-Aware Shared Visualization

The VR system also indicates:

- information confidence;
- disagreement;
- potentially conflicting evidence.

Example:

Sensor A: Fire probability = High  
User observation: No visible smoke  
System: **Conflicting evidence**

## Research Questions

**RQ1:** Does explicitly visualizing information uncertainty improve collaborative emergency decisions?

**RQ2:** How does information conflict affect trust between collaborators?

**RQ3:** Does uncertainty visualization prevent premature agreement between users?

**RQ4:** Does better shared situation awareness reduce unsafe decisions?

## Interesting New Variable

### Decision Convergence Time

Measure:

How long does it take before both participants agree on the same decision?

This makes the study much richer than simply measuring task completion time.

## Measurements

- correct/incorrect decisions;
- decision time;
- decision changes;
- disagreement frequency;
- unsafe actions;
- communication frequency;
- confirmation statements;
- information inspection behavior;
- trust;
- NASA-TLX;
- situation-awareness questionnaire;
- confidence in final decision.

## Potential Contribution

**Understanding how uncertainty visualization influences trust, decision convergence, and shared situation awareness in safety-critical collaborative VR.**

This is potentially a strong HCI contribution.

# PROJECT 3 — Collaborative VR With Dynamic Role Switching

## Research Problem

Most collaborative VR applications assign fixed roles:

Expert + Operator

But real collaboration is dynamic.

Sometimes one person has more relevant knowledge and leadership should transfer.

## Core Task

Two users collaboratively diagnose and repair a virtual technical system.

Examples:

- server-room fault;
- electrical system;
- manufacturing machine;
- aircraft subsystem;
- laboratory equipment.

Different stages require different knowledge.

## Example

### Stage 1

User A has diagnostic information.

User A should lead.

### Stage 2

User B receives mechanical information.

User B should lead.

### Stage 3

Both receive incomplete information.

They must collaborate equally.

# Experimental Conditions

### Condition A — Fixed Roles

One participant remains leader throughout the task.

### Condition B — User-Controlled Role Switching

Participants manually decide when leadership transfers.

### Condition C — System-Assisted Role Switching

The VR interface recommends which collaborator should lead based on available information.

For example:

"User B currently has more task-relevant information."

# Research Questions

**RQ1:** Does dynamic role switching improve collaborative performance compared with fixed roles?

**RQ2:** Can VR interfaces encourage appropriate leadership transitions?

**RQ3:** How does system-recommended leadership affect trust and perceived equality?

**RQ4:** Do unnecessary leadership transitions produce additional coordination cost?

# Novel Behavioral Metric

## Leadership Transition Cost

Measure the time between:

change in information ownership → change in actual collaborative leadership.

Students can analyze:

- who speaks first;
- who manipulates objects;
- who points;
- who gives instructions;
- who confirms decisions.

# Potential Contribution

**Characterizing leadership transitions and role adaptation during asymmetric collaborative VR tasks.**

This moves beyond conventional expert–novice VR collaboration.

# PROJECT 4 — Predictive Intention Visualization Between Two VR Users

## Research Problem

In collaborative VR, users often see what their partner **is currently doing**, but not what the partner **intends to do next**.

This creates:

- accidental interference;
- duplicated work;
- collisions;
- conflicting actions.

# Core Task

Two participants collaboratively organize or assemble complex virtual objects.

Examples:

- warehouse loading;
- machine assembly;
- disaster cleanup;
- construction planning;
- collaborative puzzle.

Both users manipulate objects simultaneously.

# Proposed VR Mechanism

Before a user performs an action, the system visually indicates their likely intended action.

Examples:

- intended object highlighted;
- predicted destination displayed;
- translucent future hand trajectory;
- planned manipulation arrow;
- temporary "reserved" object indication.

# Experimental Conditions

### Condition 1 — Standard Collaboration

Only current avatar movements are visible.

### Condition 2 — Explicit Intention

Users manually indicate:

"I am going to move this object here."

### Condition 3 — Predictive Intention Visualization

The system predicts the intended object/destination from controller movement or pointing direction.

A sophisticated AI model is not required.

Rule-based prediction is sufficient for a student project.

# Research Questions

**RQ1:** Does visualization of collaborator intention reduce interference between users?

**RQ2:** Does predictive information improve coordination without requiring additional speech?

**RQ3:** What happens when the displayed intention is incorrect?

**RQ4:** How does prediction reliability influence trust?

# Particularly Interesting Manipulation

Students could introduce:

### Reliable Prediction

90% correct.

versus

### Imperfect Prediction

70% correct.

Then investigate:

At what point does predictive assistance become harmful?

# Measurements

- simultaneous object-selection conflicts;
- collision events;
- duplicated actions;
- task completion time;
- verbal coordination;
- prediction acceptance;
- correction behavior;
- trust;
- workload;
- social presence.

# Potential Contribution

**Understanding how predictive visualization of collaborator intent affects coordination, trust, and interference in shared immersive workspaces.**

This is a substantially stronger contribution than another collaborative assembly study.

# PROJECT 5 — Mutual Error Awareness in Collaborative VR

## Research Problem

Collaborators frequently make errors.

However, the other user may not know:

- whether an action was intentional;
- whether the collaborator noticed the error;
- whether intervention is necessary.

# Core Scenario

Two users collaboratively inspect or assemble a complex system.

The system creates situations where one participant makes or is induced to make an error.

Example:

User A installs the wrong component.

User B may:

- immediately intervene;
- wait;
- provide a hint;
- correct the component themselves.

# Experimental Conditions

### Condition A — No Error Awareness Support

Users rely on natural observation.

### Condition B — Explicit Error Alert

System identifies an error:

"Potential error detected."

### Condition C — Socially-Aware Error Visualization

The system indicates:

User A may have made an error  
User A has / has not noticed the problem.

For example:

If User A repeatedly inspects the component, the system can infer that awareness has occurred.

# Research Questions

**RQ1:** Does showing a collaborator's error-awareness state improve intervention timing?

**RQ2:** When should VR systems expose collaborator mistakes?

**RQ3:** Does automatically highlighting mistakes undermine interpersonal trust?

**RQ4:** Do users unnecessarily intervene when collaborator awareness is ambiguous?

# New Metrics

### Intervention Latency

Time between:

**error occurrence → collaborator intervention**

### Unnecessary Intervention Rate

Number of times one user intervenes even though the other participant was already correcting the problem.

# Potential Contribution

**Design principles for communicating errors and error awareness in collaborative immersive systems.**

This has possible relevance for:

- medical collaboration;
- maintenance;
- industrial safety;
- collaborative training.

# PROJECT 6 — Adaptive Shared Attention Without Eye Tracking

## Research Motivation

Shared gaze is already receiving considerable attention in XR research. Recent studies show that gaze visualization can increase shared attention, although it does not necessarily improve completion time.

Therefore, simply implementing:

"show my collaborator's gaze"

would not be sufficiently novel.

Instead investigate whether **low-cost behavioral information can approximate shared attention without eye tracking.**

# Core Task

Two users collaboratively search a complex environment.

Examples:

- industrial hazard inspection;
- aircraft inspection;
- warehouse anomaly detection;
- crime-scene analysis;
- equipment fault detection.

# Proposed Mechanism

Estimate attention from:

- head orientation;
- controller pointing;
- object interaction;
- dwell duration.

Then calculate whether users are attending to the same object.

# Experimental Conditions

### Condition 1 — No Attention Visualization

Normal collaboration.

### Condition 2 — Continuous Partner Attention Visualization

Partner's estimated focus is continuously visible.

### Condition 3 — Adaptive Attention Visualization

The focus indicator appears only when users' attention diverges for a defined period.

# Research Questions

**RQ1:** Can head/controller behavior provide useful collaborative-attention awareness without eye-tracking hardware?

**RQ2:** Is continuous attention sharing unnecessarily distracting?

**RQ3:** Can adaptive attention cues restore joint attention more efficiently?

**RQ4:** Does adaptive visualization reduce verbal clarification?

# Proposed Metric

## Attention Divergence

Define:

\[ D(t)=|P_A(t)-P_B(t)| \]

where:

- (P_A(t)) = object or spatial region attended by User A;
- (P_B(t)) = corresponding attention location of User B.

The group can measure:

- duration of attention divergence;
- number of convergence events;
- time required to establish joint attention.

# Potential Contribution

**A low-cost approach for adaptive shared-attention support in collaborative VR using behavioral proxies instead of dedicated eye tracking.**

This is especially suitable for your available Quest/Vive hardware.

# PROJECT 7 — Collaborative VR Under Communication Constraints

## Research Problem

VR collaboration research often assumes reliable voice communication.

Real environments can contain:

- noise;
- delayed communication;
- language differences;
- incomplete messages;
- high cognitive workload.

Can spatial VR communication compensate?

# Core Task

Two users solve a spatial construction, routing, or emergency-planning problem.

# Experimental Conditions

### Condition A

Full natural voice communication.

### Condition B

Restricted voice communication.

For example, voice can only be used periodically.

### Condition C

Restricted voice + rich spatial communication.

Provide:

- pointing;
- arrows;
- spatial annotations;
- object highlighting;
- persistent markers.

# Research Questions

**RQ1:** Can spatial communication replace part of verbal communication in collaborative VR?

**RQ2:** Which information is better communicated spatially versus verbally?

**RQ3:** Does communication restriction increase development of non-verbal coordination strategies?

**RQ4:** Does spatial annotation reduce ambiguity when verbal communication becomes difficult?

# Measurements

- words or utterances;
- pointing events;
- annotation usage;
- misunderstandings;
- task errors;
- task completion time;
- clarification requests;
- communication workload;
- collaboration quality.

# Potential Contribution

**Understanding the division of labor between verbal and spatial communication channels during immersive collaboration.**

This is stronger than simply comparing voice versus no voice.

# PROJECT 8 — Single-User Adaptive VR Based on Behavioral Uncertainty

This project should remain **single-user** so the course contains at least one distinctly different research direction.

# Research Problem

Traditional VR systems provide assistance based on errors.

But an intelligent interface should ideally provide help:

**before the error happens.**

# Core Task

Participant performs:

- industrial inspection;
- maintenance;
- assembly;
- navigation;
- hazard detection.

The system estimates uncertainty from behavior.

# Behavioral Indicators of Uncertainty

For example:

- repeated head movement between two objects;
- repeated selection/deselection;
- long hesitation;
- controller oscillation;
- revisiting previous areas;
- incomplete movements.

# Experimental Conditions

### Condition A — No Assistance

### Condition B — Error-Based Assistance

Help appears after an incorrect action.

### Condition C — Uncertainty-Based Assistance

Help appears when behavioral uncertainty is detected before an error occurs.

# Research Questions

**RQ1:** Can simple behavioral signals predict upcoming user errors?

**RQ2:** Does anticipatory assistance reduce errors compared with traditional reactive assistance?

**RQ3:** Does premature assistance reduce user autonomy?

**RQ4:** What is the optimal trade-off between assistance accuracy and intervention frequency?

# Important Contribution

The paper would not focus mainly on classification accuracy.

The HCI question is:

**When should an immersive system intervene?**

# Measurements

- prediction accuracy;
- errors prevented;
- errors committed;
- false interventions;
- task time;
- hesitation time;
- assistance dependency;
- NASA-TLX;
- perceived control;
- trust.

# PROJECT 9 — Collaborative Workload Balancing in VR

## Research Problem

In collaborative work, one user can unintentionally perform most of the work.

Traditional collaborative systems rarely dynamically redistribute tasks.

# Core Task

Two participants collaboratively manage multiple simultaneous VR activities.

For example:

- monitor equipment;
- repair failures;
- organize materials;
- respond to alarms;
- inspect hazards.

Tasks continuously appear.

# Experimental Conditions

### Condition A — Self-Allocation

Users choose tasks themselves.

### Condition B — Equal Allocation

The system assigns the same number of tasks to each user.

### Condition C — Adaptive Allocation

Tasks are allocated according to:

- current workload;
- recent task performance;
- number of pending actions;
- spatial proximity.

# Research Questions

**RQ1:** Does adaptive workload distribution improve team efficiency compared with equal task allocation?

**RQ2:** Does equal workload necessarily produce better collaboration?

**RQ3:** How does automated task allocation affect perceived fairness?

**RQ4:** What happens when an algorithm prioritizes efficiency over equality?

# Strong Dependent Variables

### Contribution Imbalance

\[ CI= \]

where:

- (W_A) = amount of work completed by User A;
- (W_B) = amount of work completed by User B.

Higher (CI) indicates greater inequality.

Also measure:

- team completion time;
- missed events;
- individual workload;
- idle time;
- task switching;
- perceived fairness;
- trust;
- team satisfaction.

# Potential Contribution

**Understanding the efficiency–fairness trade-off produced by adaptive task allocation in collaborative VR.**

This could become a particularly interesting HCI study.

# PROJECT 10 — Human–Human Trust Recovery After VR Collaboration Failure

## Research Problem

Most collaborative VR research measures trust after successful collaboration.

A more interesting question is:

**What happens after collaboration fails?**

# Core Task

Two participants collaboratively complete a safety-critical or precision task.

During selected trials, the system secretly introduces a failure attributed ambiguously to collaboration.

Example:

- object unexpectedly moves;
- instruction becomes incorrect;
- system introduces positioning error;
- action performed by one participant appears delayed.

The participants may believe:

"My partner caused the error."

# Experimental Conditions

After failure:

### Condition A — No Explanation

### Condition B — System Explanation

"The failure resulted from system latency."

### Condition C — Shared Replay

The system visually replays both collaborators' actions before the failure.

# Research Questions

**RQ1:** How do unexplained system failures affect interpersonal trust in collaborative VR?

**RQ2:** Can transparent replay prevent incorrect blame attribution?

**RQ3:** Does explaining system uncertainty help restore trust?

**RQ4:** Which is more damaging—system failure or uncertainty about responsibility?

# Measurements

- interpersonal trust;
- system trust;
- blame attribution;
- willingness to collaborate;
- subsequent communication;
- task performance;
- intervention behavior;
- interpersonal distance;
- verbal disagreement.
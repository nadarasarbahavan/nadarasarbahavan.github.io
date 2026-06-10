---
title: "Bio-signals for the Objective Measurement of Presence in Virtual Reality (Final Year Project)"
excerpt: "A 2×2 factorial within-subjects VR experiment using EEG and ECG to identify bio-signal correlates of Presence, Place Illusion, and Plausibility Illusion."
collection: portfolio
category: "ml"
date: 2021-02-15
---

**Final Year Project** — Department of Electronic & Telecommunication Engineering, University of Moratuwa (February 2021).  
**Group:** T.T.N. Bahavan, N. Suman, S.A.D.O. Wickramasooriya, K.I. Akalanka · **Supervisors:** Dr. Anjula De Silva; Dr. Roshan Peiris (RIT, USA).  
**My contributions:** Experiment design, statistical analysis, EEG biosignal analysis, paper writing.  
**Published** in *Springer Virtual Reality* (Q1). → [Read Paper](https://link.springer.com/article/10.1007/s10055-023-00815-x) 

---

## Overview

**Presence** is the mental state in which a VR user reacts to events as if they were real. Traditional measurement methods — questionnaires and behavioural tasks — are intrusive, retrospective, and non-continuous. This project identified *bio-signal correlates* of Presence and its two sub-components, **Place Illusion (PI)** and **Plausibility Illusion (PSI)**, grounded in Slater's Theory of Presence.

<!-- IMAGE: Slater's Theory diagram (Figure 1.1 from report) → /images/slater_theory.png 
![Slater's Theory of Presence](/images/slater_theory.png)-->
<p align="center">
<img src="/images/slater_theory.png" width="50%">
</p> <br>
Slater's framework defines two controllable system factors: **Immersion** (producing PI — the illusion of *being* somewhere) and **Coherence** (producing PSI — the feeling that events are plausible). Their combination gives rise to Presence.

---

## Experiment Design

A **2×2 factorial within-subjects** design crossed high/low Immersion with high/low Coherence, producing four VR scenarios experienced by each participant in randomised order, with simultaneous EEG and ECG recording.

<!-- IMAGE: 2×2 experiment design tree diagram (Figure 2.1) → /images/experiment_design.png 
![experiment_design](/images/experiment_design.png)-->
<p align="center">
<img src="/images/experiment_design.png" width="50%">
</p> <br>
**20 subjects** · Ethics approval: ERN/2020/002 · Scenarios built in Unity on Oculus Go with teleportation locomotion (to minimise simulator sickness).

### Immersion sub-factors controlled
Field of view · Display resolution · Stereo sound · Environmental dynamism · Range of valid actions (teleportation range)

<!-- IMAGE: Side-by-side FOV comparison — High vs. Low Immersion (Figure 2.2) → /images/immersion_fov.png -->

### Coherence sub-factors controlled
- **Correlational** — avatars/animals responding to the player (high) vs. unresponsive (low)
- **Narrative** — contextually appropriate objects (high) vs. incongruous objects, e.g. a toilet in a living room (low)
- **Physical** — realistic physics (high) vs. floating/moving objects (low)

<!-- IMAGE: Side-by-side Coherence comparison — e.g. Narrative High vs. Low (Figure 2.7) → /images/coherence_narrative.png -->

Questionnaires were administered **inside VR** after each scenario (Unity UI + XR toolkit), reducing disorientation and improving response consistency.

<!-- IMAGE: In-VR questionnaire screenshot (Figure 2.9) → /images/inVR_questionnaire.png -->

A **pilot study** (n=6) identified weaknesses in the coherence manipulation — VR characters were ignored, audio was too quiet, voices were robotic — and informed scene redesign before the main experiment.

<!-- IMAGE: Pilot study lab photo (Figure 2.11) → /images/pilot_study.jpg 
![pilot_study](/images/pilot_study.png) -->
<p align="center">
<img src="/images/pilot_study.png" width="50%">
</p><br>
---

## Data Acquisition & Processing

**EEG:** g.Tec HI.amp, 32-electrode 10–20 montage, 256 Hz. Pipeline: band-pass (1–100 Hz) + notch filter → noisy channel rejection + spherical interpolation + average re-reference → Artifact Subspace Reconstruction (burst correction) → AMICA ICA decomposition → ICLabel artifact removal.

<!-- IMAGE: EEG montage diagram (Figure 2.10) → /images/eeg_montage.png -->
<!-- IMAGE: EEG pre-processing pipeline flowchart (Figure 2.12) → /images/eeg_pipeline.png 
![eeg_pipeline](/images/eeg_pipeline.png) -->
<p align="center">
<img src="/images/eeg_pipeline.png" width="50%">
</p> <br>
**ECG:** Biopac MP36, Lead II configuration. Pre-processing: 10th-order Butterworth low-pass (18 Hz) then high-pass (4 Hz) to remove muscle artifacts and baseline drift. Final dataset: 17 usable subjects.

<!-- IMAGE: ECG noise artifact plot — raw, after LP, after HP filter (Figure 2.24) → /images/ecg_artifacts.png -->

---

## Features Extracted

| Category | Features |
|---|---|
| Statistical | Sample Entropy, Mean, Standard Deviation |
| Band-power | Absolute & relative power (Delta/Theta/Alpha/Beta/Gamma); hemispheric asymmetry |
| Functional Connectivity | Spectral Coherence; Envelope Amplitude Correlation (Surface Laplacian for volume conduction) |
| Source Localisation | Dipole fitting → K-means clustering (10 clusters) |
| ECG (HRV) | Mean HR, RR interval, SDNN, RMSSD, VLF/LF/HF/VHF band powers, LF/HF ratio |

---

## Results

### Questionnaire validation (Friedman's test + Wilcoxon post-hoc, Holm correction)

All three manipulated states showed statistically significant differences across scenarios (all p < 0.05), confirming the experimental design was effective.

### EEG findings

Friedman's test at p < 0.01 identified numerous significant features:

- **Right frontal ↔ left parieto-occipital theta connectivity** (F8–PO7, EAC + Spectral Coherence) — higher in high-coherence scenarios; implicates social awareness and episodic memory.
- **Transcallosal central connectivity** (C3–C4, FC2–C3) — elevated in the optimal (HiI-HiC) scenario; reflects sensory-motor integration.
- **Right pre-frontal band-power** (Fp2, all bands) — elevated in mismatched scenarios; corroborates Bouchard et al.'s finding that the dorsolateral PFC modulates presence.
- **Right parietal theta** (P4) — stronger in mismatched scenarios; consistent with spatial disorientation.
- **Mid-parietal alpha** (Pz) — elevated in low-immersion conditions.

<!-- IMAGE: EAC feature bar charts across conditions A–D (Figure 3.2) → /images/eac_features.png -->
<!-- IMAGE: Absolute band-power feature bar charts (Figure 3.4) → /images/bandpower_features.png -->

These findings are consistent with prior EEG/fMRI literature (Baumgartner, Bouchard, Kober et al.), adding a controlled factorial design that distinguishes PI from PSI.

### ECG findings

No statistically significant HRV differences were found. The scenarios lacked strong emotional or stress triggers — highlighting that cardiac measures are scenario-dependent and may not generalise to neutral VR experiences.

---

## Conclusion & Future Work

The project confirmed that EEG bio-signals carry statistically significant information about Presence, Place Illusion, and Plausibility Illusion in VR. ECG did not show significant effects under neutral scenarios, clarifying the boundary conditions of physiological presence measurement.

**Future directions:** dry-contact EEG for robustness during head movement · full-body tracking for richer immersion · haptic feedback · larger cohorts to enable ML-based feature selection.

---

<!-- *Accepted: Springer Virtual Reality (Q1) · Report: [Download PDF](/files/presence.pdf)* -->

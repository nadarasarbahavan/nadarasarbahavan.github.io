---
title: "IEEE Signal Processing Cup"
excerpt: "Self-supervised deep learning to detect anomalies in heterogeneous autonomous systems using frontal-camera video and IMU readings — runners-up at the IEEE Signal Processing Cup 2020."
collection: portfolio
category: "ml"
date: 2020-06-25
---

**IEEE Signal Processing Cup 2020 — Anomaly Detection Challenge.**
**Result:** Runners-up. → [Read Paper](https://arxiv.org/abs/2006.14556)

---

## Overview

Autonomous systems must recognise when something has gone wrong in their environment without being explicitly told what "wrong" looks like. This project tackled **anomaly detection in heterogeneous autonomous systems** using two unsynchronised data streams from the platform: **frontal-camera video** and **IMU (inertial measurement unit) readings**.

The core idea was to learn the system's *normal* behaviour in a **self-supervised** manner — without anomaly labels — and then flag deviations from that learned model as anomalies. Because the video and IMU streams were not time-synchronised, each was analysed by a separate, purpose-built pipeline.

---

## Approach

Two independent subsystems classify each input as either a **normal** or an **anomalous** case. In both, the model is trained only on normal data, and a thresholded error signal at inference time separates anomalies from normal behaviour.

### Vision-based subsystem

The vision pipeline uses a **conditional GAN** that observes the immediate-past three frames and predicts the next frame. At inference, the **prediction error** between the predicted frame and the actual frame is compared against a threshold: a large discrepancy indicates the scene has departed from learned normal dynamics and is classified as anomalous.

### IMU-based subsystem

The IMU pipeline combines two complementary approaches to classify each timestamp:

- **LSTM autoencoder** — reconstructs three consecutive IMU vectors; a high **reconstruction error** signals an anomaly.
- **LSTM forecaster** — predicts the next IMU vector from the previous three; a high **prediction error** signals an anomaly.

The timestamp is classified as normal or anomalous based on the reconstruction error, the prediction error, and a threshold.

---

## Results

On the competition dataset:

| Stream | Metric | Score |
|---|---|---|
| Camera frames (normal + anomalous) | Test accuracy | 94% |
| Camera frames (normal + anomalous) | F1-score | 0.95 |
| IMU (normal test set) | Accuracy | 100% |
| IMU (abnormal test set) | F1-score | 0.98 |

The combined system earned **runners-up** at the IEEE Signal Processing Cup anomaly detection challenge 2020.

---

## Takeaways

The project demonstrated that self-supervised, prediction- and reconstruction-based models can detect anomalies across fundamentally different sensor modalities without anomaly labels — handling unsynchronised video and inertial data by treating each stream with an architecture suited to its structure, then thresholding the resulting error signal. I was involved in the entire Computer Vision aspect of the project. 

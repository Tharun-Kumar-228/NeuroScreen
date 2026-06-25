# NeuroScreen-DG
### Uncertainty-Aware Domain-Generalized Multimodal Screening for Early Detection of Dyslexia and Dysgraphia

NeuroScreen-DG is a smartphone-based AI screening framework for teachers to identify early risk signals of dyslexia and dysgraphia from handwriting images and short reading speech samples. The system is designed for low-resource school environments and focuses on referral-level screening, not medical diagnosis [web:78][web:71].

---

## Problem Statement

Early signs of dyslexia and dysgraphia are often missed in public and underfunded schools because formal screening is expensive, specialist-dependent, and not scalable. Existing AI studies often perform well only in controlled datasets, but real school environments are noisy and variable: audio may be unclear, handwriting may be blurry, devices differ, and children may come from different language backgrounds [web:59][web:68][web:71].

This creates a deployment gap between research performance and real-world usefulness. A practical screening system must remain reliable under noise, missing inputs, and domain shift across schools, devices, and languages [web:61][web:82].

---

## Proposed Solution

NeuroScreen-DG uses two input streams:
- **Handwriting branch**: analyzes a smartphone photo of a child’s written work.
- **Speech branch**: analyzes a short audio recording of the child reading aloud.

Instead of using a fixed fusion rule, the model estimates the reliability of each modality and combines them with uncertainty-aware weighting. If handwriting is low quality, speech contributes more; if speech is noisy, handwriting contributes more. The final output is a screening risk score for early intervention support [web:76][web:82].

---

## Domain Document

### 1. Application Domain
This project belongs to the **educational AI** and **assistive screening** domain. Its goal is to support teachers in identifying learning-disability risk early, especially in under-resourced schools where access to specialists is limited [web:59][web:68].

### 2. Target Users
- Primary and middle school teachers.
- School support staff.
- Special education coordinators.
- Early intervention teams.

### 3. Target Environment
- Public and low-resource schools.
- Smartphone-based classroom use.
- Noisy, variable, real-world capture conditions.
- Multi-language or second-language learning environments [web:59][web:71].

### 4. Problem Characteristics
- Noise in audio recordings.
- Blurry or uneven handwriting images.
- Differences in paper, lighting, camera quality, and dialect.
- Missing modality cases, where only one input is available.
- Need for low-cost and fast screening rather than clinical diagnosis [web:61][web:82].

### 5. Functional Scope
- Capture handwriting image.
- Record reading speech.
- Preprocess both inputs.
- Extract modality-specific features.
- Combine outputs using adaptive multimodal fusion.
- Return a low/moderate/high screening risk.
- Provide a referral-oriented result for teachers.

### 6. Non-Functional Requirements
- Must run on a smartphone or low-cost device.
- Must be easy for teachers to use.
- Must be robust to noise and missing data.
- Must support multiple classroom conditions.
- Must avoid overconfident predictions through uncertainty-aware scoring [web:66][web:82].

### 7. Research Scope
The research focuses on:
- Domain generalization across schools, devices, and languages.
- Uncertainty-aware multimodal fusion.
- Missing-modality robustness.
- Cross-domain validation under realistic deployment conditions.

### 8. Out of Scope
- Clinical diagnosis.
- Treatment prescription.
- Full medical-grade assessment.
- Heavy cloud dependency.
- High-cost specialized hardware.

---

## Novelty

The novelty is not multimodal fusion alone, because multimodal dyslexia and dysgraphia screening already appears in recent literature. The stronger contribution is the combination of:
- **domain generalization**,
- **uncertainty-aware fusion**,
- **missing-modality robustness**, and
- **deployment-oriented validation** in real school conditions [web:76][web:82].

This reframes NeuroScreen-DG as a robust screening framework rather than just a classification model.

---

## System Architecture

### Handwriting Branch
- Input: smartphone image of handwritten text.
- Backbone: ResNet18, MobileNetV3, or EfficientNet-Lite.
- Output: handwriting-risk features and confidence score.

### Speech Branch
- Input: short reading audio recorded by a teacher.
- Backbone: Whisper-tiny embeddings, CRNN, or MFCC-based classifier.
- Output: speech-risk features and confidence score.

### Fusion Branch
- Method: uncertainty-aware weighted fusion or confidence-based gating.
- Purpose: adapt the final decision according to input quality and model confidence.

### Domain Generalization Layer
The model is evaluated on unseen:
- schools,
- phone models,
- language backgrounds,
- classroom noise conditions [web:61][web:82].

---

## Dataset Strategy

Public handwriting datasets for dysgraphia and reading-related datasets for dyslexia can be used as the starting point [web:2][web:25][web:16]. Since fully matched multimodal datasets are limited, the project can use:
- transfer learning,
- data augmentation,
- missing-modality masking,
- cross-domain validation,
- and robustness testing across schools and devices.

This allows the novelty to come from the **validation design** and not only from the dataset size [web:5][web:71].

---

## Baseline Models

### Handwriting Baselines
- CNN
- ResNet18
- MobileNetV3
- EfficientNet-Lite

### Speech Baselines
- Whisper-tiny
- CRNN on Mel-spectrograms
- MFCC + SVM
- Lightweight transformer encoder

### Fusion Baselines
- Early fusion
- Late fusion
- Attention fusion
- Confidence-aware fusion
- Uncertainty-aware fusion

### Validation Baselines
- Standard train-test split
- Leave-one-school-out validation
- Leave-one-device-out validation
- Leave-one-language-background-out validation

---

## Evaluation Plan

### Standard Metrics
- Accuracy
- Precision
- Recall
- F1-score
- Sensitivity
- Specificity

### Novel Metrics
- Cross-school generalization
- Cross-device robustness
- Cross-language fairness
- Missing-modality performance
- Noise robustness
- Confidence calibration

The evaluation should show whether the model is useful in classrooms, not just in controlled lab datasets [web:59][web:61][web:82].

---

## Expected Contribution

This project aims to produce a screening system that is:
- multimodal,
- uncertainty-aware,
- robust to missing inputs,
- generalizable across domains,
- feasible on smartphones,
- and suitable for low-resource educational settings [web:66][web:71].

---

## Implementation Notes

- Use an Android-first or browser-based prototype.
- Keep inference light for school deployment.
- Use offline support where possible.
- Store only the minimum required data for privacy.
- Present the result as a screening recommendation, not a diagnosis.

---

## Conclusion

NeuroScreen-DG is a practical and research-relevant framework for early learning-disability screening. Its main strength is not just combining handwriting and speech, but making the system reliable under real-world school conditions through domain generalization and uncertainty-aware multimodal fusion [web:76][web:82][web:71].

---

## Keywords

NeuroScreen-DG, dyslexia detection, dysgraphia detection, multimodal fusion, uncertainty-aware fusion, domain generalization, missing-modality robustness, smartphone-based screening, low-resource schools, teacher-assisted AI, handwriting analysis, speech analysis, early intervention, cross-school validation, cross-device robustness, confidence calibration

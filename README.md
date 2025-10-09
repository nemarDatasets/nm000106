# handwriting: Handwriting Recognition from EMG

## Overview

**Dataset**: handwriting - Imagined handwriting from wrist-based surface electromyography
**Task**: Air-writing (imagined handwriting without pen)
**Participants**: 100 subjects
**Sessions**: ~700 total (~7 per subject)
**Publication**: Kaifosh et al., 2025 - "A generic non-invasive neuromotor interface for human-computer interaction" (Nature)

### Purpose

This dataset captures wrist-based sEMG signals during imagined handwriting motions for text entry. Participants "write" prompted text with fingers together (as if holding an invisible pen) without any physical writing surface. Applications include AR/VR text input, mobile computing, and hands-free communication.

## Dataset Details

### Participants
- **Sample size**: 100 participants
- **Demographics**: Not available (marked as n/a)
- **Recording side**: Dominant wrist
- **Sessions**: Average 7 per participant

### Hardware
- **Device**: sEMG-RD (single wristband)
- **Channels**: 16 (EMG0-EMG15)
- **Sampling rate**: 2000 Hz
- **Reference**: Bipolar differential

### Recording Protocol
1. Participant holds fingers together (as if holding pen)
2. Prompted text appears on screen
3. Participant "writes" the text in air
4. Session duration: ~11 minutes
5. Prompts per session: 96 phrases

## Data Contents

### Files per Session
```
sub-XXX/ses-XXX/emg/
├── sub-XXX_ses-XXX_task-handwriting_emg.edf
├── sub-XXX_ses-XXX_task-handwriting_emg.json
├── sub-XXX_ses-XXX_task-handwriting_channels.tsv
├── sub-XXX_ses-XXX_task-handwriting_events.tsv
└── sub-XXX_ses-XXX_electrodes.tsv
```

### Events
- **Handwriting prompts**: Text to be written
  - `prompt_text`: Displayed phrase
- **Stage boundaries**: Posture changes (sitting/standing), session phases

### Coordinate System
Single coordinate system at root (dominant wrist, percent units, no decimals)

## Baseline Performance

### Published Results (Kaifosh et al., 2025)

**Generic Model** (6,527 training participants):
- Offline CER: >90% classification accuracy on held-out participants
- Online performance: 20.9 words per minute (WPM)
- Online CER: Median improvement from ~35% (practice) to ~25% (evaluation)

**Personalized Model** (20 min fine-tuning):
- 16% improvement over generic model
- Better performance for users with higher generic CER
- Diminishing returns with more pretraining data

**Comparison**:
- Open-loop handwriting (no pen): 25.1 WPM
- sEMG handwriting: 20.9 WPM (83% of baseline)
- Mobile phone keyboard: 36 WPM

**Model architecture**: MPF features + Conformer (attention mechanism)

## Use Cases
- **Keyboard-free text entry**: AR/VR, mobile devices
- **Silent communication**: Private text input in public spaces
- **Personalization research**: Few-shot learning, transfer learning
- **Sequence modeling**: Character-level prediction with attention

## Known Limitations
- Single wrist (dominant hand only)
- Handedness not recorded
- Learning curve: Users improve with practice/coaching
- Lower WPM than physical writing or typing

## Citation
```
Kaifosh, P., Reardon, T.R., & CTRL-labs at Reality Labs. (2025).
A generic non-invasive neuromotor interface for human-computer interaction.
Nature, 586, https://doi.org/10.1038/s41586-025-09255-w
```

## Data Curator
**Yahya Shirazi**
SCCN (Swartz Center for Computational Neuroscience)
INC (Institute for Neural Computation)
University of California San Diego

## Version History
**v1.0** (2025-10-01): Initial BIDS conversion

---
**BIDS Version**: 1.11 | **EMG-BIDS**: BEP-042 | **Updated**: Oct 1, 2025

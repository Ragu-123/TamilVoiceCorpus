---
dataset_info:
- config_name: AmbientVox
  features:
  - name: duration
    dtype: float64
  - name: file_name
    dtype: string
  - name: start_time
    dtype: string
  - name: video_id
    dtype: string
  - name: text
    dtype: string
  - name: end_time
    dtype: string
  - name: file_path
    dtype: audio
  splits:
  - name: train
    num_bytes: 26436690851
    num_examples: 22057
  - name: test
    num_bytes: 6607285282
    num_examples: 5515
  download_size: 43304415939
  dataset_size: 33043976133
- config_name: PureVox
  features:
  - name: file_name
    dtype: string
  - name: start_time
    dtype: float64
  - name: end_time
    dtype: float64
  - name: duration
    dtype: string
  - name: text
    dtype: string
  - name: file_path
    dtype: audio
  - name: __index_level_0__
    dtype: int64
  splits:
  - name: train
    num_bytes: 4300069520.211
    num_examples: 12371
  - name: test
    num_bytes: 1071233451.068
    num_examples: 3093
  download_size: 5348371976
  dataset_size: 5371302971.279


extra_gated_prompt: "This Tamil Conversational ASR Dataset is intended for research and educational purposes only. By requesting access, you agree to use this dataset solely for non-commercial research activities and to properly cite it in any resulting publications."
---



# Tamil Conversational ASR Dataset

This is a dataset for Automatic Speech Recognition (ASR) focused on **conversational Tamil**, collected from various public sources on the web. Each sample is a short audio clip (averaging 10 seconds) paired with its corresponding transcription.

## Dataset Summary

- **Language:** Tamil (`ta`)
- **Domain:** Conversational speech
- **Average Duration per Clip:** ~10 seconds
- **Format:** Audio (.wav) + text
- **Sample Rate:** 16kHz recommended
- **Total Examples:**
  - **PureVox:**
    - Train: 12,371
    - Test: 3,093
  - **AmbientVox:**
    - Train: 22,057
    - Test: 5,515

## Dataset Structure

The dataset is organized into two subsets:

### PureVox
The PureVox subset contains cleaner audio with minimal background noise, making it ideal for baseline ASR model training and evaluation.

Each example contains the following fields:

| Field         | Type     | Description                                  |
|---------------|----------|----------------------------------------------|
| `file_name`   | `string` | Name of the original audio file              |
| `start_time`  | `float`  | Start time of the segment in seconds         |
| `end_time`    | `float`  | End time of the segment in seconds           |
| `duration`    | `string` | Duration of the segment                      |
| `text`        | `string` | Ground truth transcription in Tamil          |
| `file_path`   | `audio`  | The audio data itself                        |
| `__index_level_0__` | `int64` | Index identifier                        |

### AmbientVox
The AmbientVox subset contains conversational Tamil with realistic background noise and varying acoustic conditions, making it suitable for training robust ASR models for real-world applications.

Each example contains the following fields:

| Field         | Type     | Description                                  |
|---------------|----------|----------------------------------------------|
| `duration`    | `float64`| Duration of the segment in seconds           |
| `file_name`   | `string` | Name of the original audio file              |
| `start_time`  | `string` | Start time of the segment                    |
| `video_id`    | `string` | ID of the source video                       |
| `text`        | `string` | Ground truth transcription in Tamil          |
| `end_time`    | `string` | End time of the segment                      |
| `file_path`   | `audio`  | The audio data itself                        |

## Usage

This dataset can be used for training or evaluating ASR models, especially those based on architectures like [Whisper](https://github.com/openai/whisper) or [Wav2Vec2](https://huggingface.co/models?pipeline_tag=automatic-speech-recognition&sort=downloads).

You can load each subset individually:

```python
from datasets import load_dataset

# Load PureVox subset (cleaner audio)
purevox_dataset = load_dataset("ragunath-ravi/TamilVoiceCorpus", name="PureVox")

# Load AmbientVox subset (with background noise)
ambientvox_dataset = load_dataset("ragunath-ravi/TamilVoiceCorpus", name="AmbientVox")
```

## Comparison of Subsets

| Feature | PureVox | AmbientVox |
|---------|---------|------------|
| Background Noise | Minimal | Present |
| Size (Train) | 12,371 examples | 22,057 examples |
| Size (Test) | 3,093 examples | 5,515 examples |
| Total Dataset Size | ~5.4 GB | ~33 GB |
| Best Use Case | Baseline model training, Controlled evaluations | Robust model training, Real-world applications |

## Licensing

The dataset is compiled from public web sources and is available under the Apache 2.0 license. It is intended for research and educational purposes only. Ensure that you comply with the copyright terms of individual sources if redistributing or using commercially.

## Citation

If you use this dataset in your research, please cite it appropriately or include the Hugging Face link to this dataset card.

## Contributions

This dataset was curated and preprocessed by [Ragunath-Ravi](https://huggingface.co/ragunath-ravi).

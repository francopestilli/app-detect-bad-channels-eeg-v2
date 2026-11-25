# app-detect-bad-channels-eeg-v2

<!-- brainlife-app:begin (generated from the App manifest; edit the manifest, not this block) -->

> **Detects bad EEG channels in epoched data from baseline variance (MAD z-score, dead and flat channels) with MNE-Python and marks them in info['bads'] without interpolation.**

Designed to run before ICA: variance is computed in the pre-stimulus window to avoid flagging channels with strong evoked responses. Channels are flagged if their MAD z-score exceeds z_thresh, their variance is under 1/100 of the median, or they are flat in over half of the epochs; extra channels can be added by name. Epochs are saved unchanged except for the bads list; interpolate after ICA.

| | |
|---|---|
| 📥 **Inputs** | `neuro/meeg/mne/epochs` |
| 📤 **Outputs** | `neuro/meeg/mne/epochs` |
| 🐳 **Container** | `brainlife/mne:1.0.2` |
| ⚙️ **Resources** | 1 CPUs · 20 GB memory · 0.5 h walltime |
| 🔗 **Run it** | [doi.org/10.25663/brainlife.app.897](https://doi.org/10.25663/brainlife.app.897) |

#### 📥 Inputs

| Input | Datatype | Required | Description |
|---|---|---|---|
| `epochs` | `neuro/meeg/mne/epochs` | yes | Epoched EEG data (MNE -epo.fif). |

#### 📤 Outputs

| Output | Datatype | Description |
|---|---|---|
| `out_dir` | `neuro/meeg/mne/epochs` | The same epochs with detected bad channels listed in info['bads']. |

<details>
<summary><b>⚙️ Parameters</b> (2)</summary>

| Parameter | Type | Default | Description |
|---|---|---|---|
| `z_thresh` | number | `5` | MAD z-score threshold. Channels flagged if variance deviates more than this many robust SDs from median |
| `extra_bads` | string |  | Comma-separated channel names to mark bad in addition to those detected. |

</details>

<!-- brainlife-app:end -->


# Machine Sound Anomaly Detection (MIMII Dataset)

Audio-based anomaly detection for industrial machines (valve, pump, fan, slide rail) under factory-noise conditions,
as a basis for predictive maintenance.

## Dataset
[MIMII Dataset](https://zenodo.org/record/3384388) (Hitachi): normal and anomalous machine sounds mixed with real factory noise
at -6 dB, 0 dB, and 6 dB SNR.
Reference: Purohit et al., *MIMII Dataset: Sound Dataset for Malfunctioning Industrial Machine Investigation and Inspection*, 2019.

## Methods compared
| Method | Details |
|---|---|
| FFT | Frequency features with boxplot (Q1) thresholding |
| STFT | Time-frequency features with Harmonic-Percussive Source Separation (HPSS) to suppress percussive factory noise |
| Wavelet | Wavelet features with boxplot thresholding (upper and lower whisker) |

HPSS keeps the harmonic (stationary machine) component and removes the percussive (noise/impulse) component using
median filtering and masking. Main parameters: `n_fft`, `hop_length`, `kernel_size`, `margin`.

## Evaluation
AUC per machine type, model ID, and SNR level, compared against baseline results.
Example: wavelet-based detection on pump ID02 at -6 dB improved AUC from 0.55 to 0.97.
Full results: [MIMII Output spreadsheet](https://docs.google.com/spreadsheets/d/1kwKFYjNBWOFcWQlGncoSShyyk1_tTA_TTrBYQqeDcHM/edit?gid=615279865).

## Run
Open the notebook in Google Colab (`notebook.ipynb`), mount the dataset, and run all cells.

## Author
Jeremi Saragih, Politeknik Elektronika Negeri Surabaya

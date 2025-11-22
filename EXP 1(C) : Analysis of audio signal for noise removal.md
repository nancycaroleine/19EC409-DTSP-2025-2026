# EXP 1(C) : Analysis of audio signal for noise removal

# AIM: 

To analyse an audio signal and remove noise

# APPARATUS REQUIRED:  
PC installed with SCILAB. 

# PROGRAM: 
// DISCRETE FOURIER TRANSFORM 
```
import numpy as np
import soundfile as sf
import matplotlib.pyplot as plt
from scipy.fft import fft, ifft
from IPython.display import Audio

# ============================================================
# 1. LOAD AUDIO + NOISE
# ============================================================
audio, fs = sf.read("audio.wav")
noise, fs_n = sf.read("noise.wav")

# Convert stereo → mono if needed
if audio.ndim > 1:
    audio = np.mean(audio, axis=1)

if noise.ndim > 1:
    noise = np.mean(noise, axis=1)

# Ensure same length
L = min(len(audio), len(noise))
audio = audio[:L]
noise = noise[:L]

# ============================================================
# 2. COMBINE SIGNAL
# ============================================================
combined = audio + noise

# ============================================================
# 3. DFT / FFT NOISE REMOVAL
# ============================================================
AudioFFT = fft(audio)
NoiseFFT = fft(noise)
CombinedFFT = fft(combined)

RecoveredFFT = CombinedFFT - NoiseFFT
recovered = np.real(ifft(RecoveredFFT))

# Normalize audio for playback
recovered = recovered / np.max(np.abs(recovered))

# ============================================================
# 4. PLOT ALL SIGNALS
# ============================================================
plt.figure(figsize=(14, 10))

plt.subplot(4,1,1)
plt.title("Original Audio Signal")
plt.plot(audio)

plt.subplot(4,1,2)
plt.title("Noise Signal")
plt.plot(noise, color='orange')

plt.subplot(4,1,3)
plt.title("Combined Signal (Audio + Noise)")
plt.plot(combined, color='red')

plt.subplot(4,1,4)
plt.title("Recovered Signal (DFT-Based)")
plt.plot(recovered, color='green')

plt.tight_layout()
plt.show()

# ============================================================
# 5. PLAY AUDIO OUTPUTS
# ============================================================
print("🔊 Original Audio:")
display(Audio(audio, rate=fs))

print("🔊 Noise Audio:")
display(Audio(noise, rate=fs))

print("🔊 Combined Audio:")
display(Audio(combined, rate=fs))

print("🔊 Recovered Audio (DFT):")
display(Audio(recovered, rate=fs))

# ============================================================
# 6. SAVE RECOVERED AUDIO
# ============================================================
sf.write("recovered.wav", recovered, fs)
print("Saved recovered.wav")
```

# RESULT: 
<img width="1389" height="989" alt="image" src="https://github.com/user-attachments/assets/1457eca8-0fb0-47f8-a68b-092c34aacd39" />

![WhatsApp Image 2025-11-22 at 12 04 06_372885a4](https://github.com/user-attachments/assets/b142a5f4-a7b2-4026-9de8-1243ef59e806)
Thus the analysis of audio signal and noise removal using DFT is perfomed.


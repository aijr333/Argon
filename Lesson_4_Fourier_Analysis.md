# 🎶 Lesson 4: Fourier Analysis — Turning Complexity into Cycles

## ✅ What It Is — Plain English

**Fourier analysis** breaks down any complex, messy signal into a bunch of simple sine and cosine waves.

- It’s like discovering that every chaotic sound, light wave, or trend is secretly made of **repeating patterns**.
- This is the core idea behind sound compression, signal processing, and trend forecasting.

**Fourier Transform:**
\[
F(k) = \int_{-\infty}^{\infty} f(x) e^{-2\pi ikx} dx
\]
(In practice, we use **Fast Fourier Transform (FFT)** — a digital shortcut!)

---

## ⚙️ Google Colab Setup (First Cell)
To ensure all code runs in Google Colab, begin with this:
```python
# ✅ Run this cell first in Google Colab
!pip install matplotlib numpy scipy --quiet

import numpy as np
import matplotlib.pyplot as plt
from scipy.fft import fft
```

---

## 🌍 Real-World Examples

| Domain       | Use Case                                    | Description                                         |
|--------------|----------------------------------------------|-----------------------------------------------------|
| Audio        | MP3 compression, noise removal               | Breaks music/sound into frequency components         |
| Business     | Market cycles, customer behavior             | Reveals repeating trends in data                    |
| Engineering  | Vibration/stress diagnostics                 | Detects faults via harmonic signals                 |
| Physics      | Light & wave behavior                        | Models particles/waves as frequency spectrums       |
| Medicine     | EEG, heart rate monitors                     | Signal processing for diagnostics                   |

---

## 🧪 Basic FFT Example in Python
```python
x = np.linspace(0, 2 * np.pi, 1000)
signal = np.sin(3 * x) + 0.5 * np.sin(5 * x) + 0.2 * np.sin(9 * x)

F = fft(signal)
frequencies = np.abs(F[:500])  # Only half needed (real part)

plt.figure(figsize=(12, 5))
plt.subplot(1, 2, 1)
plt.plot(x, signal)
plt.title('Original Signal')

plt.subplot(1, 2, 2)
plt.stem(frequencies[:50])
plt.title('Fourier Transform (Frequencies)')
plt.tight_layout()
plt.show()
```

---

## 🧠 Problem-Solving & Practice

### 🎧 Detect Dominant Frequencies in a Market Signal
```python
t = np.linspace(0, 10, 1000)
data = 2 * np.sin(2 * np.pi * 1.5 * t) + 0.5 * np.sin(2 * np.pi * 4.5 * t)
noise = 0.3 * np.random.randn(len(t))
signal = data + noise

F = fft(signal)
frequencies = np.abs(F[:500])

plt.figure(figsize=(14, 5))
plt.subplot(1, 2, 1)
plt.plot(t, signal)
plt.title("Market Signal with Noise")

plt.subplot(1, 2, 2)
plt.stem(frequencies[:50])
plt.title("FFT Frequency Spectrum")
plt.tight_layout()
plt.show()
```

### 💼 Use Case: Find Weekly Patterns in Website Traffic
```python
days = np.linspace(0, 30, 300)
data = 100 + 20 * np.sin(2 * np.pi * days / 7) + 10 * np.sin(2 * np.pi * days / 3.5)
F = fft(data)
frequencies = np.abs(F[:150])

plt.plot(frequencies[:30])
plt.title("Detected Frequency Patterns in Website Traffic")
plt.xlabel("Frequency Index")
plt.ylabel("Magnitude")
plt.grid(True)
plt.show()
```

### 🧪 Combine Fourier with Trend Forecasting
```python
def synth_signal(t):
    return 10 + 3*np.sin(2*np.pi*0.5*t) + 2*np.sin(2*np.pi*1.5*t)

t = np.linspace(0, 20, 1000)
signal = synth_signal(t)
noisy_signal = signal + 2*np.random.randn(len(t))

F = fft(noisy_signal)
mag = np.abs(F[:500])

plt.plot(t, noisy_signal, label='Noisy Signal')
plt.plot(t, signal, label='Original Signal')
plt.legend()
plt.title("Time Series Forecasting with Fourier Insight")
plt.show()
```

---

## 🎛️ Interactive Demo (Build a Custom Signal)
```python
from ipywidgets import interact, FloatSlider

def custom_signal(freq1=3, freq2=6, freq3=9):
    x = np.linspace(0, 2 * np.pi, 1000)
    signal = np.sin(freq1 * x) + 0.5 * np.sin(freq2 * x) + 0.2 * np.sin(freq3 * x)
    plt.plot(x, signal)
    plt.title('Generated Signal with Mixed Frequencies')
    plt.grid(True)
    plt.show()

interact(custom_signal,
         freq1=FloatSlider(1, 1, 10, 1),
         freq2=FloatSlider(3, 1, 15, 1),
         freq3=FloatSlider(5, 1, 20, 1))
```

---

## 🖼️ Diagram Description
- Visualize a messy squiggle on a graph.
- Fourier reveals it’s made of clean, smooth waves stacked together.
- Each wave = a frequency; the stack = the full signal.

---

## 🧠 Slide Deck Summary

**Slide 1:** Title – Fourier Analysis: Pattern Beneath the Noise  
**Slide 2:** Visual: One complex wave = sum of simpler waves  
**Slide 3:** Use cases in audio, business, diagnostics  
**Slide 4:** Python code for FFT + graph output  
**Slide 5:** Interactive sliders to build your own wave combo  
**Slide 6:** Real-world scenario: forecast market cycles or detect audio patterns  
**Slide 7:** Key takeaway: Fourier transforms = decoding complexity into harmony

---


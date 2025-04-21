# 🧠 Lesson 5: Full Simulation — Combining Waves, Motion, and Change

## ✅ Goal:
To build a **real-world simulation** by combining:  
- Sine/Cosine (oscillations)  
- Derivatives (rate of change)  
- Projectile motion (physical pathing)  
- Fourier analysis (pattern detection)

We'll simulate a **product launch campaign** as a projectile in motion with:
- Customer attention = a sine wave
- Conversion rate change = derivative of growth
- Arc = trajectory of campaign effectiveness
- Trend feedback = Fourier to find cyclical success

---

## ⚙️ Google Colab Setup (First Cell)
```python
# ✅ Run this cell first in Google Colab
!pip install matplotlib numpy scipy --quiet

import numpy as np
import matplotlib.pyplot as plt
from scipy.fft import fft
```

---

## 🌐 Simulation Scenario: AI Product Launch

**Description:** You are launching a new AI tool. You want to:
- Predict how interest rises and falls
- Simulate performance based on angle (strategy) and velocity (budget)
- Analyze engagement signal to find repeating patterns

---

## 📐 Math Breakdown:
| Concept       | Formula/Tool                          | Use                           |
|---------------|----------------------------------------|-------------------------------|
| Wave modeling | \( y = A \sin(Bx + C) \)               | Simulate attention span       |
| Derivative    | \( \frac{df}{dx} \)                    | Growth rate of conversion     |
| Trajectory    | \( y = x \tan(\theta) - \frac{gx^2}{2v^2 \cos^2(\theta)} \) | Campaign arc                   |
| Fourier       | `fft(signal)`                         | Detect feedback & loops       |

---

## 🧪 Core Code: Combined Simulation in Python
```python
x = np.linspace(0, 10, 1000)
attention = np.sin(2 * np.pi * 0.5 * x) * np.exp(-0.1 * x)
conversion = x**2 * np.exp(-0.3 * x)
conversion_rate = np.gradient(conversion, x)
signal = attention + conversion
frequencies = np.abs(fft(signal)[:500])

plt.figure(figsize=(14, 6))
plt.subplot(1, 2, 1)
plt.plot(x, attention, label='Customer Attention')
plt.plot(x, conversion, label='Conversion')
plt.plot(x, conversion_rate, label='Conversion Rate')
plt.legend()
plt.title('Campaign Dynamics')

plt.subplot(1, 2, 2)
plt.stem(frequencies[:50])
plt.title('Fourier Analysis of Engagement')
plt.tight_layout()
plt.show()
```

---

## 🧠 More Practice Problems

### 🎯 Optimize Launch Angle and Budget
```python
def campaign_trajectory(v=40, theta_deg=45):
    g = 9.81
    theta = np.radians(theta_deg)
    t_flight = (2 * v * np.sin(theta)) / g
    t = np.linspace(0, t_flight, 500)
    x = v * np.cos(theta) * t
    y = v * np.sin(theta) * t - 0.5 * g * t**2

    plt.plot(x, y)
    plt.title(f'Campaign Reach (v={v}, θ={theta_deg}°)')
    plt.xlabel('Market Reach')
    plt.ylabel('Customer Height')
    plt.grid(True)
    plt.show()

campaign_trajectory()
```

### 📊 Track Engagement Peaks Over Time
```python
t = np.linspace(0, 30, 1000)
attention = 100 * np.sin(2 * np.pi * t / 7) + 500  # Weekly cycles
trend = 50 * np.exp(-0.05 * t)
signal = attention + trend

plt.plot(t, signal)
plt.title('Simulated Attention Over Time')
plt.xlabel('Days')
plt.ylabel('Interest Level')
plt.grid(True)
plt.show()
```

### 📈 Forecast Trends Using FFT Insights
```python
F = fft(signal)
freqs = np.abs(F[:150])

plt.stem(freqs[:30])
plt.title('Fourier Frequency Map of Engagement')
plt.xlabel('Frequency Index')
plt.ylabel('Magnitude')
plt.grid(True)
plt.show()
```

---

## 🎛️ Optional Interactive Sliders
```python
from ipywidgets import interact, FloatSlider

def simulate_combo(v=30, theta_deg=45, freq=0.5):
    x = np.linspace(0, 10, 1000)
    attention = np.sin(2 * np.pi * freq * x) * np.exp(-0.1 * x)
    conversion = x**2 * np.exp(-0.3 * x)
    conversion_rate = np.gradient(conversion, x)

    plt.figure(figsize=(10, 5))
    plt.plot(x, attention, label='Attention')
    plt.plot(x, conversion, label='Conversion')
    plt.plot(

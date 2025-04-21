# 📈 Lesson 1: Sine & Cosine — Cycles, Motion, and Real-World Rhythm

## ✅ What It Is — Plain English

**Sine and cosine** are functions that describe **repeating patterns** — like waves. They show how something moves in cycles over time: up, down, then back again.

- **Sine** tells you how high something is going (vertical).
- **Cosine** tells you how far across it's moving (horizontal).
- Both are linked to circles, like the hands of a clock.

They are foundational for modeling **any oscillation**, such as:
- Sound waves
- Light waves
- Economic cycles
- Motion loops in animations

---

## 🌍 Real-World Examples

| Domain       | Use Case                                 | Description                                      |
|--------------|-------------------------------------------|--------------------------------------------------|
| Business     | Seasonal sales patterns                   | Demand rises and falls over time like a wave     |
| Physics      | A swinging pendulum                       | The motion repeats: up-down-up-down              |
| Engineering  | Electrical currents (AC)                  | Currents switch direction in a sinusoidal pattern|
| Game Dev     | Bobbing character animations              | Use sine for smooth bounce loops                 |
| UI/UX Design | Button pulse or animation easing          | Use cosine to simulate ease-in-out motion        |

---

## 🧠 How to Read & Manipulate the Formula

General Sine Wave Formula:
\[ y = A \sin(Bx + C) + D \]

| Symbol | Meaning                      | What It Does                                |
|--------|-------------------------------|----------------------------------------------|
| A      | Amplitude                    | Controls wave **height** (louder, taller)    |
| B      | Frequency                    | Controls **tightness** of waves (faster cycle) |
| C      | Phase Shift                  | Shifts the wave **left or right**            |
| D      | Vertical Shift               | Moves the whole wave **up or down**          |

---

## 🛠️ Python Practice: Solving Sine/Cosine Problems

### 🔍 Task: Predict attention peak during a 4-week marketing cycle
```python
import numpy as np
import matplotlib.pyplot as plt

weeks = np.linspace(0, 4, 1000)
attention = 50 * np.sin(2 * np.pi * 0.25 * weeks) + 70

plt.plot(weeks, attention)
plt.title("Predicted Customer Attention")
plt.xlabel("Weeks")
plt.ylabel("Attention Level")
plt.grid(True)
plt.show()
```

### 🔍 Task: Find max and min values in a cosine-based pattern
```python
from scipy.optimize import minimize_scalar

f = lambda x: -np.cos(x)  # Flip to find maximum
result = minimize_scalar(f, bounds=(0, 2*np.pi), method='bounded')
print("Max at x =", result.x, "with value =", -result.fun)
```

### 🔍 Task: Phase Shift Comparison (Show multiple waves)
```python
x = np.linspace(0, 2 * np.pi, 500)
plt.plot(x, np.sin(x), label='sin(x)')
plt.plot(x, np.sin(x + np.pi/4), label='sin(x + π/4)')
plt.plot(x, np.sin(x + np.pi/2), label='sin(x + π/2)')
plt.legend()
plt.grid(True)
plt.title("Sine Waves with Phase Shift")
plt.show()
```

---

## ✅ More Practice Examples

### 🧪 Animate a Floating Object
```python
import matplotlib.animation as animation

x = np.linspace(0, 2*np.pi, 100)
y = np.sin(x)
fig, ax = plt.subplots()
line, = ax.plot(x, y)

def update(frame):
    line.set_ydata(np.sin(x + frame/10))
    return line,

ani = animation.FuncAnimation(fig, update, frames=100, interval=50)
plt.show()
```

### 💼 Business Forecasting with Sine Fitting
```python
from scipy.optimize import curve_fit

def model(x, A, B, C, D):
    return A * np.sin(B * x + C) + D

# Fake 12-month trend
x = np.linspace(0, 12, 100)
y = 2000 + 300 * np.sin(2 * np.pi * x/12 + 1.5)  # true function
noise = np.random.normal(0, 100, size=y.shape)
y_noisy = y + noise

# Fit the noisy data
params, _ = curve_fit(model, x, y_noisy)
plt.plot(x, y_noisy, 'o', label='Noisy Sales')
plt.plot(x, model(x, *params), label='Fitted Sine Model')
plt.legend()
plt.title("Seasonal Sales Forecasting")
plt.show()
```

---

## 🖼️ Diagram Description
- Picture a **circle** with a point moving around the edge.
- Draw a line from the center to the point.
- The height of the point = **sine** of the angle
- The distance along the bottom = **cosine** of the angle
- Watch how the point’s motion maps out a sine wave if you track it over time

---

## 🧠 Slide Deck Summary

**Slide 1:** Title – Sine & Cosine: Motion in Cycles  
**Slide 2:** Visual – Unit Circle and Sine/Cosine definitions  
**Slide 3:** Graphs – Compare sine and cosine curves  
**Slide 4:** Real-world use cases across domains  
**Slide 5:** Code example and interactive sliders  
**Slide 6:** Simulation preview using sine in UI/motion  
**Slide 7:** Key takeaway: Sine and cosine are the heartbeat of rhythmic systems

---



x = np.linspace(0, 2 * np.pi, 500)
sine = np.sin(x)
cosine = np.cos(x)

plt.figure(figsize=(10, 4))
plt.plot(x, sine, label='sin(x)')
plt.plot(x, cosine, label='cos(x)', linestyle='--')
plt.title('Sine and Cosine Waves')
plt.xlabel('x')
plt.ylabel('Amplitude')
plt.grid(True)
plt.legend()
plt.show()
```

...

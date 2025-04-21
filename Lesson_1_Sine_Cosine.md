# 📈 Lesson 1: Sine & Cosine — Cycles, Motion, and Real-World Rhythm

## ✅ What It Is — Plain English

**Sine and cosine** are functions that describe **repeating patterns** — like waves. They show how something moves in cycles over time: up, down, then back again.

- **Sine** tells you how high something is going.
- **Cosine** tells you how far across it's moving.
- Both are linked to circles, like the hands of a clock.

---

## 🌍 Real-World Examples

| Domain       | Use Case                                 | Description                                      |
|--------------|-------------------------------------------|--------------------------------------------------|
| Business     | Seasonal sales patterns                   | Demand rises and falls over time like a wave     |
| Physics      | A swinging pendulum                       | The motion repeats: up-down-up-down              |
| Engineering  | Electrical currents (AC)                  | Currents switch direction in a sinusoidal pattern|
| Game Dev     | Bobbing character animations              | Use sine for smooth bounce loops                 |

---

## 🧪 Code Example (Python: Basic Graph)
```python
import numpy as np
import matplotlib.pyplot as plt

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
# 📉 Lesson 2: Derivatives — Measuring Change in Motion, Money, and More

## ✅ What It Is — Plain English

A **derivative** tells you how fast something is changing *right now*.

- It’s like asking, “What’s your speed *at this exact moment*?”
- It measures the **slope** of a curve at a single point — like the steepness of a hill.

Symbolically:
\[ f'(x) = \frac{df}{dx} \]

---

## ⚙️ Google Colab Setup (First Cell)
To ensure all code in this notebook runs in Google Colab, start with this:
```python
# ✅ Run this cell first in Google Colab
!pip install sympy matplotlib numpy scipy

import numpy as np
import matplotlib.pyplot as plt
from scipy.misc import derivative
from sympy import symbols, diff, sin
```

---

## 🌍 Real-World Examples

| Domain       | Use Case                            | Description                                         |
|--------------|--------------------------------------|-----------------------------------------------------|
| Business     | Marginal profit                     | How much more profit per extra sale                 |
| AI/ML        | Gradient descent                    | Finds the best path to minimize error               |
| Physics      | Velocity & Acceleration             | Speed = rate of change of position                  |
| Engineering  | Stress/strain rate                  | Tracks change in material deformation               |

---

## 🧠 Python Derivative Tools

### 1. Symbolic Derivative with SymPy
```python
x = symbols('x')
f = x**2 * sin(x)

# Calculate the derivative
f_prime = diff(f, x)
print("Function:", f)
print("Derivative:", f_prime)
```

### 2. Numerical Derivative with SciPy
```python
def f(x):
    return x**2 * np.sin(x)

# Approximate derivative at x = 1
print("df/dx at x=1:", derivative(f, 1.0, dx=1e-6))
```

---

## 🧪 Applied Examples

### 🧮 Profit Growth Over Time
```python
x = np.linspace(0, 10, 100)
profit = 5 * x**2 - 20 * x + 50
profit_rate = np.gradient(profit, x)

plt.plot(x, profit, label='Profit')
plt.plot(x, profit_rate, label='dProfit/dx', linestyle='--')
plt.title('Profit and Its Derivative')
plt.legend()
plt.grid(True)
plt.show()
```

### 🚗 Velocity from Position
```python
time = np.linspace(0, 10, 100)
position = 3 * time**2 + 2 * time
velocity = np.gradient(position, time)

plt.plot(time, position, label='Position')
plt.plot(time, velocity, label='Velocity (Derivative)', linestyle='--')
plt.title('Position vs Velocity')
plt.legend()
plt.grid(True)
plt.show()
```

### 🎯 Tangent Line Viewer
```python
x = np.linspace(-10, 10, 1000)
y = x**2
x0 = 2
slope = 2 * x0

tangent = slope * (x - x0) + x0**2

plt.plot(x, y, label='y = x^2')
plt.plot(x, tangent, '--', label='Tangent at x=2')
plt.scatter([x0], [x0**2], color='red')
plt.title('Visualizing the Derivative as a Tangent Line')
plt.legend()
plt.grid(True)
plt.show()
```

---

## 📊 Business Intelligence Example: Customer Growth Rate
```python
days = np.linspace(0, 30, 100)
customers = 1000 / (1 + np.exp(-0.2 * (days - 15)))  # Logistic growth
rate = np.gradient(customers, days)

plt.plot(days, customers, label='Total Customers')
plt.plot(days, rate, label='Growth Rate (Derivative)', linestyle='--')
plt.title('Customer Base vs Growth Rate')
plt.legend()
plt.grid(True)
plt.show()
```

---

## 🖼️ Diagram Description
- Imagine a curve of a mountain.
- A **derivative** is like putting a straight stick (tangent) on the slope at a single point.
- The **steeper** the stick, the **faster** the change.

---

## 🧠 Slide Deck Summary

**Slide 1:** Title – Derivatives: The Speed of Change  
**Slide 2:** Tangent line visual over a curve  
**Slide 3:** Business and physics applications  
**Slide 4:** Symbolic and numeric code examples  
**Slide 5:** Gradient and growth graph scenarios  
**Slide 6:** Real-world scenario: AI, velocity, or business ROI  
**Slide 7:** Key takeaway: Derivatives are about understanding how *fast* things evolve in real time

---

# 🎯 Lesson 3: Projectile Motion — The Parabolic Path of Forces in Motion

## ✅ What It Is — Plain English

**Projectile motion** describes the curved path an object follows when launched into the air, under the influence of gravity.

- The path is a **parabola** (like a rainbow or a ball arc).
- It combines **horizontal motion** (constant speed) and **vertical motion** (changing due to gravity).

Formula:
\[
y = x \tan(\theta) - \frac{g x^2}{2 v^2 \cos^2(\theta)}
\]

---

## ⚙️ Google Colab Setup (First Cell)
To ensure all code in this notebook runs in Google Colab, start with this:
```python
# ✅ Run this cell first in Google Colab
!pip install matplotlib numpy --quiet

import numpy as np
import matplotlib.pyplot as plt
```

---

## 🌍 Real-World Examples

| Domain       | Use Case                                 | Description                                       |
|--------------|-------------------------------------------|---------------------------------------------------|
| Physics      | Ballistics, throwing a ball              | Models curved path of any launched object         |
| Engineering  | Designing arcs (e.g., bridges, tunnels)  | Predicts force load distribution                 |
| Game Dev     | Simulating jumping or launching effects  | Trajectory control for animation or logic         |
| Space Tech   | Rocket launching angles                  | Gravity-based path modeling beyond atmosphere     |
| Sports       | Football passes, basketball shots        | Trajectory tuning for maximum performance         |

---

## 🧪 Python Code: Simulate and Plot a Trajectory
```python
def projectile(v=30, theta_deg=45):
    g = 9.81  # gravity in m/s²
    theta = np.radians(theta_deg)
    t_flight = (2 * v * np.sin(theta)) / g
    t = np.linspace(0, t_flight, num=500)

    x = v * np.cos(theta) * t
    y = v * np.sin(theta) * t - 0.5 * g * t**2

    plt.figure(figsize=(10, 5))
    plt.plot(x, y)
    plt.title(f'Trajectory: v={v} m/s, θ={theta_deg}°')
    plt.xlabel('Distance (m)')
    plt.ylabel('Height (m)')
    plt.grid(True)
    plt.show()

projectile()
```

---

## 🎛️ Interactive Visualization with Sliders (Jupyter only)
```python
from ipywidgets import interact, FloatSlider

interact(projectile,
         v=FloatSlider(value=30, min=5, max=100, step=1),
         theta_deg=FloatSlider(value=45, min=10, max=80, step=1))
```

---

## 🧠 Practice Problems with Code

### 🚀 Launch a Cannonball from 3 Different Angles
```python
angles = [30, 45, 60]
v = 40

def plot_multiple_angles():
    g = 9.81
    t = np.linspace(0, 6, 500)
    plt.figure(figsize=(10, 6))
    for theta_deg in angles:
        theta = np.radians(theta_deg)
        x = v * np.cos(theta) * t
        y = v * np.sin(theta) * t - 0.5 * g * t**2
        plt.plot(x, y, label=f'{theta_deg}°')

    plt.title("Comparison of Trajectories at Different Angles")
    plt.xlabel("Distance (m)")
    plt.ylabel("Height (m)")
    plt.grid(True)
    plt.legend()
    plt.show()

plot_multiple_angles()
```

### 🧮 Calculate Maximum Height and Range
```python
def get_max_height_range(v, theta_deg):
    g = 9.81
    theta = np.radians(theta_deg)
    max_height = (v**2) * (np.sin(theta)**2) / (2 * g)
    range_distance = (v**2) * np.sin(2 * theta) / g
    return max_hei

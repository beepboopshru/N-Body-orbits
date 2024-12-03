# **Gravitational Orbit Simulation**

This project is a **gravitational orbit simulator** that numerically models the motion of celestial bodies using Newtonian mechanics. The program can simulate various scenarios such as the motion of planets, comets, and perturbations caused by external forces. It also provides a visual representation of the system and mathematical insights into the orbital mechanics.

---

## **Features**

1. **N-Body Simulation**: Simulates gravitational interactions between multiple celestial bodies.
2. **Dynamic Visualization**: 
   - Real-time animation of orbits.
   - Trajectory tracking for each body.
3. **Energy Analysis**:
   - Classifies orbits as circular, elliptical, parabolic, or hyperbolic based on specific orbital energy.
4. **Collision Detection**: Detects when two bodies collide or come too close.
5. **Customizable Parameters**:
   - Initial positions, velocities, and masses of bodies.
   - Time step (\( \Delta t \)) for numerical integration.
6. **Keplerian Mechanics**: Incorporates calculations for orbital elements like true anomaly, eccentricity, and semi-major axis.

---

 Observe the simulation in the **Pygame window**, with real-time updates of:
   - Orbital trajectories.
   - Key orbital parameters in the top-left corner.

---

## **Mathematical Concepts**

1. **Newton's Law of Gravitation**:
   \[
   \vec{F} = \frac{G \cdot m_1 \cdot m_2}{r^3} \cdot (\vec{r}_2 - \vec{r}_1)
   \]

2. **Numerical Integration**:
   - Velocity update:
     \[
     \vec{v}_{\text{new}} = \vec{v}_{\text{old}} + \vec{a} \cdot \Delta t
     \]
   - Position update:
     \[
     \vec{r}_{\text{new}} = \vec{r}_{\text{old}} + \vec{v}_{\text{new}} \cdot \Delta t
     \]

3. **Orbital Energy**:
   \[
   \epsilon = \frac{v^2}{2} - \frac{G \cdot M}{r}
   \]

4. **Kepler's Equation**:
   Solves for the true anomaly (\( \nu \)) numerically.

---

## **Customization**

1. **Adding New Bodies**:
   Modify the initialization in `main.py`:
   ```python
   bodies = [
       CelestialBody(mass=1.989e30, pos=[0, 0], vel=[0, 0], name="Sun"),
       CelestialBody(mass=5.972e24, pos=[1.496e11, 0], vel=[0, 29780], name="Earth"),
       CelestialBody(mass=1e14, pos=[2e11, 0], vel=[0, 25000], name="Comet"),
   ]
   ```

2. **Adjusting Time Step**:
   Change the `dt` value in `main.py`:
   ```python
   dt = 3600  # Time step in seconds
   ```

3. **Visual Enhancements**:
   Customize the `pygame` display for enhanced aesthetics.

---

## **Possible Enhancements**

1. **Add Relativistic Effects**: Include general relativity for higher accuracy near massive bodies.
2. **Implement Adaptive Time Stepping**: Improve simulation efficiency.
3. **3D Simulation**: Extend the simulation to three dimensions.
4. **Interactive UI**: Allow users to dynamically modify parameters during the simulation.

---

## **Contributing**

Contributions are welcome! If you find a bug or have a feature request, feel free to open an issue or a pull request.

1. Fork the repository.
2. Create a new branch:
   ```bash
   git checkout -b feature-name
   ```
3. Commit changes:
   ```bash
   git commit -m "Add your message here"
   ```
4. Push to your branch and create a pull request.

---

## **Acknowledgments**

- This project is inspired by classical mechanics and Keplerian orbital mechanics.
- Thanks to the open-source Python community for providing incredible libraries like `numpy`, `pygame`, and `matplotlib`.

---

Let me know if you'd like to refine this further or if additional sections are needed! 🚀

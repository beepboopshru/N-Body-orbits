The mathematical foundation for this simulation is rooted in Newtonian mechanics and gravitational dynamics.
---

## 1. **Newton's Law of Gravitation**

The gravitational force between two bodies is given by:

\[
F = \frac{G \cdot m_1 \cdot m_2}{r^2}
\]

- \( G \): Gravitational constant (\(6.67430 \times 10^{-11} \, \text{m}^3 \text{kg}^{-1} \text{s}^{-2}\)).
- \( m_1, m_2 \): Masses of the two bodies.
- \( r \): Distance between the two bodies.

In vector form, the force on body \( i \) due to body \( j \) is:

\[
\vec{F}_{ij} = \frac{G \cdot m_i \cdot m_j}{r^3} (\vec{r}_j - \vec{r}_i)
\]

where \( \vec{r}_j - \vec{r}_i \) is the displacement vector from \( i \) to \( j \).

---

### Code Implementation

```python
r = np.linalg.norm(body2.pos - body1.pos)  # Distance between bodies
force_magnitude = G * body1.mass * body2.mass / r**2  # Magnitude of force
force_direction = (body2.pos - body1.pos) / r  # Unit vector
forces[body1] += force_magnitude * force_direction  # Add to net force
```

This calculates the force on `body1` due to `body2` and accumulates it in a dictionary for each body.

---

## 2. **Newton's Second Law**

The acceleration of a body due to a net force is:

\[
\vec{a} = \frac{\vec{F}}{m}
\]

Given acceleration, the velocity and position of the body are updated using numerical integration (Euler's method):

\[
\vec{v}_{\text{new}} = \vec{v}_{\text{old}} + \vec{a} \cdot \Delta t
\]

\[
\vec{r}_{\text{new}} = \vec{r}_{\text{old}} + \vec{v}_{\text{new}} \cdot \Delta t
\]

---

### Code Implementation

```python
acceleration = force / self.mass
self.vel += acceleration * dt  # Update velocity
self.pos += self.vel * dt  # Update position
```

Each body’s velocity and position are updated iteratively over small time steps, \( \Delta t \).

---

## 3. **Keplerian Dynamics**

To check if a comet or other body becomes bound to the system or escapes, we compute the **specific orbital energy** (\( \epsilon \)):

\[
\epsilon = \frac{v^2}{2} - \frac{G \cdot M}{r}
\]

- \( v \): Magnitude of velocity.
- \( r \): Distance from the central body (e.g., the Sun).
- \( M \): Mass of the central body.

- If \( \epsilon < 0 \), the body is **bound** and will follow an elliptical or circular orbit.
- If \( \epsilon = 0 \), the body is on a **parabolic trajectory**.
- If \( \epsilon > 0 \), the body is **unbound** and escapes on a hyperbolic trajectory.

---

### Code Implementation

```python
r = np.linalg.norm(comet.pos)
v = np.linalg.norm(comet.vel)
energy = 0.5 * v**2 - G * M_sun / r

if energy < 0:
    print("Comet is bound to the system.")
elif energy == 0:
    print("Comet is on a parabolic escape trajectory.")
else:
    print("Comet will escape the system.")
```

---

## 4. **Orbit Plotting**

To visualize the motion, we track the positions of bodies over time. The trajectory reflects the numerical solution of their equations of motion under gravitational forces.

---

### Graphical Interpretation

- The **shape of the orbit** (circle, ellipse, parabola, or hyperbola) depends on the eccentricity:

\[
e = \sqrt{1 + \frac{2 \epsilon h^2}{(G \cdot M)^2}}
\]

where \( h = r \cdot v \cdot \sin(\theta) \) is the angular momentum per unit mass.

This is not explicitly coded here, but the simulation inherently resolves these dynamics based on initial conditions.


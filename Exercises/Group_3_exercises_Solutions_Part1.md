# Group 3 Exercises - Complete Solutions (Part 1: Exercise Sets 1-6)

This document provides detailed solutions to Exercise Sets 1-6 from Group_3_exercises.md.

---

## Exercise Set 1: Phase Modulation (PM)

### Solution 1.1 (Basic)

**Given:** $s(t) = 8\cos[2\pi \cdot 1 \times 10^6 t + 0.5\sin(2\pi \cdot 5 \times 10^3 t)]$

**Solution:**

Comparing with PM form: $s(t) = A_c\cos[\omega_c t + \theta(t)]$

a) **Carrier amplitude:**
   - $A_c = 8$ V

b) **Carrier frequency:**
   - $\omega_c = 2\pi \cdot 1 \times 10^6$ rad/s
   - $f_c = 1 \times 10^6$ Hz = **1 MHz**

c) **Phase function:**
   - $\theta(t) = 0.5\sin(2\pi \cdot 5 \times 10^3 t)$

d) **Modulating signal:**
   
   For PM: $\theta(t) = D_p m(t)$
   
   Therefore: $m(t) = \frac{\theta(t)}{D_p} = \frac{0.5\sin(2\pi \cdot 5 \times 10^3 t)}{0.5}$
   
   $$m(t) = \sin(2\pi \cdot 5 \times 10^3 t)$$

e) **Real envelope:**
   
   For angle modulation: $g(t) = A_c e^{j\theta(t)}$
   
   $$R(t) = |g(t)| = |A_c e^{j\theta(t)}| = A_c|e^{j\theta(t)}| = A_c \times 1 = 8 \text{ V}$$
   
   **Constant envelope!**

---

### Solution 1.2 (Intermediate)

**Given:** $A_c = 10$ V, $f_c = 100$ kHz, $D_p = 2$ rad/V, $m(t) = 3\cos(2\pi \cdot 4 \times 10^3 t)$

**Solution:**

a) **Phase function:**
   $$\theta(t) = D_p m(t) = 2 \times 3\cos(2\pi \cdot 4 \times 10^3 t) = 6\cos(2\pi \cdot 4 \times 10^3 t)$$

b) **Modulated signal:**
   $$s(t) = A_c\cos[\omega_c t + \theta(t)] = 10\cos[2\pi \cdot 100 \times 10^3 t + 6\cos(2\pi \cdot 4 \times 10^3 t)]$$

c) **Complex envelope:**
   $$g(t) = A_c e^{j\theta(t)} = 10e^{j6\cos(2\pi \cdot 4 \times 10^3 t)}$$

d) **Instantaneous frequency:**
   $$f_i(t) = f_c + \frac{1}{2\pi}\frac{d\theta(t)}{dt}$$
   
   $$\frac{d\theta(t)}{dt} = \frac{d}{dt}[6\cos(2\pi \cdot 4 \times 10^3 t)] = -6 \times 2\pi \times 4 \times 10^3 \sin(2\pi \cdot 4 \times 10^3 t)$$
   
   $$\frac{d\theta(t)}{dt} = -48\pi \times 10^3 \sin(2\pi \cdot 4 \times 10^3 t)$$
   
   $$f_i(t) = 100 \times 10^3 + \frac{1}{2\pi}(-48\pi \times 10^3)\sin(2\pi \cdot 4 \times 10^3 t)$$
   
   $$f_i(t) = 100 \times 10^3 - 24 \times 10^3 \sin(2\pi \cdot 4 \times 10^3 t)$$
   
   $$f_i(t) = 100,000 - 24,000\sin(2\pi \cdot 4 \times 10^3 t) \text{ Hz}$$

e) **Peak frequency deviation:**
   $$\Delta F = \max|f_i(t) - f_c| = \max|24,000\sin(2\pi \cdot 4 \times 10^3 t)| = 24,000 \text{ Hz} = 24 \text{ kHz}$$
   
   Or using formula:
   $$\Delta F = \frac{D_p}{2\pi}\max\left|\frac{dm(t)}{dt}\right| = \frac{2}{2\pi} \times 3 \times 2\pi \times 4 \times 10^3 = 24 \times 10^3 = 24 \text{ kHz}$$

---

### Solution 1.3 (Advanced)

**Given:** $s(t) = A_c\cos[\omega_c t + D_p m(t)]$

**Proof:**

a) **Instantaneous frequency:**
   
   The phase is: $\theta(t) = D_p m(t)$
   
   Instantaneous frequency:
   $$f_i(t) = f_c + \frac{1}{2\pi}\frac{d\theta(t)}{dt} = f_c + \frac{1}{2\pi}\frac{d[D_p m(t)]}{dt}$$
   
   $$f_i(t) = f_c + \frac{D_p}{2\pi}\frac{dm(t)}{dt} \quad \square$$

b) **Frequency deviation:**
   $$f_d(t) = f_i(t) - f_c = \frac{D_p}{2\pi}\frac{dm(t)}{dt} \quad \square$$

c) **Peak frequency deviation:**
   $$\Delta F = \max|f_d(t)| = \max\left|\frac{D_p}{2\pi}\frac{dm(t)}{dt}\right| = \frac{D_p}{2\pi}\max\left|\frac{dm(t)}{dt}\right| \quad \square$$

d) **For sinusoidal modulation:**
   
   If $m(t) = A_m\cos(\omega_m t)$:
   $$\frac{dm(t)}{dt} = -A_m \omega_m \sin(\omega_m t)$$
   
   $$\max\left|\frac{dm(t)}{dt}\right| = A_m \omega_m$$
   
   Therefore:
   $$\Delta F = \frac{D_p}{2\pi} \times A_m \omega_m = \frac{D_p A_m \omega_m}{2\pi} = D_p A_m f_m \quad \square$$

---

## Exercise Set 2: Frequency Modulation (FM)

### Solution 2.1 (Basic)

**Given:** $s(t) = 6\cos\left[2\pi \cdot 500 \times 10^3 t + 4\int_0^t \cos(2\pi \cdot 2 \times 10^3 \tau) d\tau\right]$

**Solution:**

Comparing with FM form: $s(t) = A_c\cos[\omega_c t + D_f \int m(t) dt]$

a) **Carrier amplitude:**
   - $A_c = 6$ V

b) **Carrier frequency:**
   - $\omega_c = 2\pi \cdot 500 \times 10^3$ rad/s
   - $f_c = 500 \times 10^3$ Hz = **500 kHz**

c) **Frequency sensitivity:**
   
   From the form: $D_f \int m(t) dt = 4\int_0^t \cos(2\pi \cdot 2 \times 10^3 \tau) d\tau$
   
   Therefore: $D_f = 4$ (units: rad/s per unit of $m(t)$)

d) **Modulating signal:**
   
   Since $D_f \int m(t) dt = 4\int_0^t \cos(2\pi \cdot 2 \times 10^3 \tau) d\tau$:
   
   $$D_f m(t) = 4\cos(2\pi \cdot 2 \times 10^3 t)$$
   
   $$m(t) = \frac{4}{D_f}\cos(2\pi \cdot 2 \times 10^3 t) = \frac{4}{4}\cos(2\pi \cdot 2 \times 10^3 t)$$
   
   $$m(t) = \cos(2\pi \cdot 2 \times 10^3 t)$$

e) **Phase function:**
   $$\theta(t) = D_f \int m(t) dt = 4\int_0^t \cos(2\pi \cdot 2 \times 10^3 \tau) d\tau$$
   
   $$\theta(t) = 4 \times \frac{1}{2\pi \cdot 2 \times 10^3}\sin(2\pi \cdot 2 \times 10^3 t)$$
   
   $$\theta(t) = \frac{4}{4\pi \times 10^3}\sin(2\pi \cdot 2 \times 10^3 t) = \frac{1}{\pi \times 10^3}\sin(2\pi \cdot 2 \times 10^3 t)$$

---

### Solution 2.2 (Intermediate)

**Given:** $A_c = 12$ V, $f_c = 1$ MHz, $D_f = 2\pi \times 10^4$ rad/s per unit, $m(t) = 2\cos(2\pi \cdot 3 \times 10^3 t)$

**Solution:**

a) **Phase function:**
   
   For FM: $\theta(t) = D_f \int m(t) dt$
   
   $$\theta(t) = D_f \int 2\cos(2\pi \cdot 3 \times 10^3 t) dt = D_f \times 2 \times \frac{1}{2\pi \times 3 \times 10^3}\sin(2\pi \times 3 \times 10^3 t)$$
   
   $$\theta(t) = \frac{D_f \times 2}{2\pi \times 3 \times 10^3}\sin(2\pi \cdot 3 \times 10^3 t) = \frac{D_f}{\pi \times 3 \times 10^3}\sin(2\pi \cdot 3 \times 10^3 t)$$
   
   Substituting $D_f = 2\pi \times 10^4$:
   $$\theta(t) = \frac{2\pi \times 10^4}{\pi \times 3 \times 10^3}\sin(2\pi \cdot 3 \times 10^3 t) = \frac{2 \times 10^4}{3 \times 10^3}\sin(2\pi \cdot 3 \times 10^3 t)$$
   
   $$\theta(t) = \frac{20}{3}\sin(2\pi \cdot 3 \times 10^3 t)$$

b) **Modulated signal:**
   $$s(t) = A_c\cos[\omega_c t + \theta(t)] = 12\cos\left[2\pi \cdot 10^6 t + \frac{20}{3}\sin(2\pi \cdot 3 \times 10^3 t)\right]$$

c) **Instantaneous frequency:**
   $$f_i(t) = f_c + \frac{1}{2\pi}\frac{d\theta(t)}{dt}$$
   
   $$\frac{d\theta(t)}{dt} = \frac{20}{3} \times 2\pi \times 3 \times 10^3 \cos(2\pi \cdot 3 \times 10^3 t) = \frac{20}{3} \times 6\pi \times 10^3 \cos(2\pi \cdot 3 \times 10^3 t)$$
   
   $$\frac{d\theta(t)}{dt} = 40\pi \times 10^3 \cos(2\pi \cdot 3 \times 10^3 t)$$
   
   $$f_i(t) = 10^6 + \frac{1}{2\pi} \times 40\pi \times 10^3 \cos(2\pi \cdot 3 \times 10^3 t)$$
   
   $$f_i(t) = 10^6 + 20 \times 10^3 \cos(2\pi \cdot 3 \times 10^3 t)$$
   
   $$f_i(t) = 1,000,000 + 20,000\cos(2\pi \cdot 3 \times 10^3 t) \text{ Hz}$$
   
   Or using the direct formula for FM:
   $$f_i(t) = f_c + \frac{D_f}{2\pi}m(t) = 10^6 + \frac{2\pi \times 10^4}{2\pi} \times 2\cos(2\pi \cdot 3 \times 10^3 t)$$
   
   $$f_i(t) = 10^6 + 2 \times 10^4 \cos(2\pi \cdot 3 \times 10^3 t) \text{ Hz}$$

d) **Peak frequency deviation:**
   $$\Delta F = \max|f_i(t) - f_c| = \max|20,000\cos(2\pi \cdot 3 \times 10^3 t)| = 20,000 \text{ Hz} = 20 \text{ kHz}$$
   
   Or using formula:
   $$\Delta F = \frac{D_f}{2\pi}\max|m(t)| = \frac{2\pi \times 10^4}{2\pi} \times 2 = 2 \times 10^4 = 20 \text{ kHz}$$

e) **Modulation index:**
   $$\beta = \frac{\Delta F}{f_m} = \frac{20 \times 10^3}{3 \times 10^3} = \frac{20}{3} \approx 6.67$$
   
   Or using formula:
   $$\beta = \frac{D_f A_m}{\omega_m} = \frac{2\pi \times 10^4 \times 2}{2\pi \times 3 \times 10^3} = \frac{4 \times 10^4}{6 \times 10^3} = \frac{20}{3} \approx 6.67$$

---

### Solution 2.3 (Advanced)

**Given:** $s(t) = A_c\cos[\omega_c t + D_f \int m(t) dt]$

**Proof:**

a) **Instantaneous frequency:**
   
   The phase is: $\theta(t) = D_f \int m(t) dt$
   
   Instantaneous frequency:
   $$f_i(t) = f_c + \frac{1}{2\pi}\frac{d\theta(t)}{dt} = f_c + \frac{1}{2\pi}\frac{d}{dt}\left[D_f \int m(t) dt\right]$$
   
   Using the fundamental theorem of calculus:
   $$f_i(t) = f_c + \frac{1}{2\pi}D_f m(t) = f_c + \frac{D_f}{2\pi}m(t) \quad \square$$

b) **Frequency deviation:**
   $$f_d(t) = f_i(t) - f_c = \frac{D_f}{2\pi}m(t) \quad \square$$

c) **Peak frequency deviation:**
   $$\Delta F = \max|f_d(t)| = \max\left|\frac{D_f}{2\pi}m(t)\right| = \frac{D_f}{2\pi}\max|m(t)| \quad \square$$

d) **For sinusoidal modulation:**
   
   If $m(t) = A_m\cos(\omega_m t)$:
   $$\Delta F = \frac{D_f}{2\pi}A_m$$
   
   The modulation index is:
   $$\beta = \frac{D_f A_m}{\omega_m} = \frac{D_f A_m}{2\pi f_m} = \frac{\Delta F}{f_m} \quad \square$$

---

## Exercise Set 3: Relationship Between PM and FM

### Solution 3.1 (Basic)

**Given:** $\theta(t) = 2\cos(2\pi \cdot 1 \times 10^3 t)$, $f_c = 100$ kHz, $A_c = 5$ V

**Solution:**

a) **Instantaneous frequency:**
   $$f_i(t) = f_c + \frac{1}{2\pi}\frac{d\theta(t)}{dt}$$
   
   $$\frac{d\theta(t)}{dt} = \frac{d}{dt}[2\cos(2\pi \cdot 10^3 t)] = -2 \times 2\pi \times 10^3 \sin(2\pi \cdot 10^3 t)$$
   
   $$\frac{d\theta(t)}{dt} = -4\pi \times 10^3 \sin(2\pi \cdot 10^3 t)$$
   
   $$f_i(t) = 100 \times 10^3 + \frac{1}{2\pi}(-4\pi \times 10^3)\sin(2\pi \cdot 10^3 t)$$
   
   $$f_i(t) = 100,000 - 2,000\sin(2\pi \cdot 10^3 t) \text{ Hz}$$

b) **Equivalent FM signal:**
   
   For the PM signal, the phase is: $\theta_{PM}(t) = 2\cos(2\pi \cdot 10^3 t)$
   
   For an equivalent FM signal, we need the same phase:
   $$\theta_{FM}(t) = D_f \int m_f(t) dt = 2\cos(2\pi \cdot 10^3 t)$$
   
   Taking derivative:
   $$D_f m_f(t) = \frac{d}{dt}[2\cos(2\pi \cdot 10^3 t)] = -4\pi \times 10^3 \sin(2\pi \cdot 10^3 t)$$
   
   Therefore:
   $$m_f(t) = \frac{-4\pi \times 10^3}{D_f}\sin(2\pi \cdot 10^3 t)$$
   
   If we want $m_f(t) = -4\pi \times 10^3\sin(2\pi \cdot 10^3 t)$ (as given in part c), then:
   $$D_f = 1 \text{ rad/s per unit}$$

c) **Frequency sensitivity:**
   
   If $m_f(t) = -4\pi \times 10^3\sin(2\pi \cdot 10^3 t)$:
   
   From part b: $D_f m_f(t) = -4\pi \times 10^3 \sin(2\pi \cdot 10^3 t)$
   
   Therefore: $D_f = 1$ rad/s per unit

---

### Solution 3.2 (Intermediate)

**Given:** PM signal with $m_p(t) = A_m\cos(\omega_m t)$

**Solution:**

**PM Signal:**
- Phase: $\theta_{PM}(t) = D_p m_p(t) = D_p A_m\cos(\omega_m t)$
- Instantaneous frequency: $f_i(t) = f_c + \frac{D_p}{2\pi}\frac{dm_p(t)}{dt} = f_c - \frac{D_p A_m \omega_m}{2\pi}\sin(\omega_m t)$

**Equivalent FM Signal:**
- For same $f_i(t)$: $f_i(t) = f_c + \frac{D_f}{2\pi}m_f(t)$
- Therefore: $\frac{D_f}{2\pi}m_f(t) = -\frac{D_p A_m \omega_m}{2\pi}\sin(\omega_m t)$
- So: $D_f m_f(t) = -D_p A_m \omega_m \sin(\omega_m t)$

a) **FM message:**
   $$m_f(t) = -\frac{D_p A_m \omega_m}{D_f}\sin(\omega_m t)$$

b) **Relationship between $D_p$ and $D_f$:**
   
   For the FM phase to equal PM phase:
   $$\theta_{FM}(t) = D_f \int m_f(t) dt = D_p A_m\cos(\omega_m t)$$
   
   $$\theta_{FM}(t) = D_f \int \left[-\frac{D_p A_m \omega_m}{D_f}\sin(\omega_m t)\right] dt = D_f \times \frac{D_p A_m \omega_m}{D_f \omega_m}\cos(\omega_m t)$$
   
   $$\theta_{FM}(t) = D_p A_m\cos(\omega_m t)$$
   
   This works for any $D_f$! The relationship is:
   $$D_f m_f(t) = -D_p A_m \omega_m \sin(\omega_m t)$$
   
   Or: $D_f = \frac{D_p A_m \omega_m}{-m_f(t)/\sin(\omega_m t)}$

c) **Phase functions:**
   - **PM:** $\theta_{PM}(t) = D_p A_m\cos(\omega_m t)$
   - **FM:** $\theta_{FM}(t) = D_p A_m\cos(\omega_m t)$ (same!)

---

### Solution 3.3 (Advanced)

**Proof:**

a) **PM with $m(t)$ equivalent to FM with $\frac{dm(t)}{dt}$:**
   
   PM phase: $\theta_{PM}(t) = D_p m(t)$
   
   Instantaneous frequency: $f_i(t) = f_c + \frac{D_p}{2\pi}\frac{dm(t)}{dt}$
   
   For equivalent FM: $f_i(t) = f_c + \frac{D_f}{2\pi}m_f(t)$
   
   Therefore: $\frac{D_f}{2\pi}m_f(t) = \frac{D_p}{2\pi}\frac{dm(t)}{dt}$
   
   So: $D_f m_f(t) = D_p \frac{dm(t)}{dt}$
   
   If we choose $m_f(t) = \frac{dm(t)}{dt}$, then: $D_f = D_p$
   
   **PM with $m(t)$ is equivalent to FM with $\frac{dm(t)}{dt}$** $\square$

b) **FM with $m(t)$ equivalent to PM with $\int m(t) dt$:**
   
   FM phase: $\theta_{FM}(t) = D_f \int m(t) dt$
   
   For equivalent PM: $\theta_{PM}(t) = D_p m_p(t) = D_f \int m(t) dt$
   
   Therefore: $m_p(t) = \frac{D_f}{D_p} \int m(t) dt$
   
   If we choose $D_p = D_f$, then: $m_p(t) = \int m(t) dt$
   
   **FM with $m(t)$ is equivalent to PM with $\int m(t) dt$** $\square$

c) **Relationship:**
   
   When signals are equivalent, they have the same instantaneous frequency:
   $$f_i = f_c + \frac{D_p}{2\pi}\frac{dm_{PM}}{dt} = f_c + \frac{D_f}{2\pi}m_{FM}$$
   
   Therefore:
   $$\frac{D_p}{2\pi}\frac{dm_{PM}}{dt} = \frac{D_f}{2\pi}m_{FM}$$
   
   $$D_p \frac{dm_{PM}(t)}{dt} = D_f m_{FM}(t) \quad \square$$

---

## Exercise Set 4: Instantaneous Frequency

### Solution 4.1 (Basic)

**Given:** $\theta(t) = 0.3\sin(2\pi \cdot 5 \times 10^3 t)$, $f_c = 200$ kHz

**Solution:**

a) **Instantaneous frequency:**
   $$f_i(t) = f_c + \frac{1}{2\pi}\frac{d\theta(t)}{dt}$$
   
   $$\frac{d\theta(t)}{dt} = 0.3 \times 2\pi \times 5 \times 10^3 \cos(2\pi \cdot 5 \times 10^3 t) = 3\pi \times 10^3 \cos(2\pi \cdot 5 \times 10^3 t)$$
   
   $$f_i(t) = 200 \times 10^3 + \frac{1}{2\pi} \times 3\pi \times 10^3 \cos(2\pi \cdot 5 \times 10^3 t)$$
   
   $$f_i(t) = 200,000 + 1,500\cos(2\pi \cdot 5 \times 10^3 t) \text{ Hz}$$

b) **Frequency deviation:**
   $$f_d(t) = f_i(t) - f_c = 1,500\cos(2\pi \cdot 5 \times 10^3 t) \text{ Hz}$$

c) **Maximum and minimum frequencies:**
   - **Maximum:** $f_{i,max} = 200,000 + 1,500 = 201,500$ Hz = 201.5 kHz
   - **Minimum:** $f_{i,min} = 200,000 - 1,500 = 198,500$ Hz = 198.5 kHz

d) **Peak frequency deviation:**
   $$\Delta F = \max|f_d(t)| = 1,500 \text{ Hz} = 1.5 \text{ kHz}$$

---

### Solution 4.2 (Intermediate)

**Given:** $D_p = 1$ rad/V, $m(t) = 4\cos(2\pi \cdot 2 \times 10^3 t)$, $f_c = 500$ kHz

**Solution:**

a) **Phase function:**
   $$\theta(t) = D_p m(t) = 1 \times 4\cos(2\pi \cdot 2 \times 10^3 t) = 4\cos(2\pi \cdot 2 \times 10^3 t)$$

b) **Instantaneous frequency:**
   $$f_i(t) = f_c + \frac{1}{2\pi}\frac{d\theta(t)}{dt}$$
   
   $$\frac{d\theta(t)}{dt} = -4 \times 2\pi \times 2 \times 10^3 \sin(2\pi \cdot 2 \times 10^3 t) = -16\pi \times 10^3 \sin(2\pi \cdot 2 \times 10^3 t)$$
   
   $$f_i(t) = 500 \times 10^3 + \frac{1}{2\pi}(-16\pi \times 10^3)\sin(2\pi \cdot 2 \times 10^3 t)$$
   
   $$f_i(t) = 500,000 - 8,000\sin(2\pi \cdot 2 \times 10^3 t) \text{ Hz}$$

c) **Frequency deviation:**
   $$f_d(t) = f_i(t) - f_c = -8,000\sin(2\pi \cdot 2 \times 10^3 t) \text{ Hz}$$

d) **Sketch of $f_i(t)$:**
   ```
   f_i(t) (kHz)
     508 |        /‾‾‾\        /‾‾‾\
         |       /     \      /     \
     500 |______/       \____/       \____
         |                           
     492 |        \___/        \___/
         |
     0   0.25ms  0.5ms  0.75ms  1ms  t
   ```
   - Period: $T_m = \frac{1}{2 \times 10^3} = 0.5$ ms
   - Maximum: 508 kHz (when $\sin = -1$)
   - Minimum: 492 kHz (when $\sin = +1$)

---

### Solution 4.3 (Advanced)

**Proof:**

a) **Instantaneous frequency is always positive:**
   
   For FM: $f_i(t) = f_c + \frac{D_f}{2\pi}m(t)$
   
   For $f_i(t) > 0$, we need:
   $$f_c + \frac{D_f}{2\pi}m(t) > 0$$
   
   Since $f_c > 0$ and $\frac{D_f}{2\pi} > 0$, if $m(t) \geq 0$, then $f_i(t) > 0$.
   
   However, if $m(t) < 0$ and large in magnitude, we could have $f_i(t) < 0$.
   
   Actually, the condition is: $f_c > \left|\frac{D_f}{2\pi}m(t)\right|$ for all $t$.
   
   But in practice, we ensure $f_c \gg \Delta F$ so $f_i(t) > 0$ always. $\square$

b) **Condition for $f_i(t) > 0$:**
   
   $$f_i(t) = f_c + \frac{D_f}{2\pi}m(t) > 0$$
   
   For the worst case (minimum $f_i$):
   $$f_c + \frac{D_f}{2\pi}\min m(t) > 0$$
   
   If $\min m(t) = -\max|m(t)|$:
   $$f_c - \frac{D_f}{2\pi}\max|m(t)| > 0$$
   
   $$f_c > \frac{D_f}{2\pi}\max|m(t)| = \Delta F \quad \square$$

c) **If $f_c < \Delta F$:**
   
   Then $f_i(t) = f_c + \frac{D_f}{2\pi}m(t)$ can become negative when $m(t) < 0$.
   
   Negative frequencies are **not physically realizable** (they would require time reversal).
   
   This violates causality and physical realizability. $\square$

d) **Practical requirement:**
   
   For practical systems, we need a **safety margin**:
   $$f_c \gg \Delta F$$
   
   Typically: $f_c \geq 10 \times \Delta F$ or more.
   
   This ensures:
   - $f_i(t) > 0$ always
   - No overlap with negative frequency components
   - Proper bandpass filtering possible
   - Good separation from baseband $\square$

---

## Exercise Set 5: Complex Envelope and Power

### Solution 5.1 (Basic)

**Given:** $g(t) = 10e^{j0.2\sin(2\pi \cdot 3 \times 10^3 t)}$, $f_c = 1$ MHz

**Solution:**

a) **Carrier amplitude:**
   - From $g(t) = A_c e^{j\theta(t)}$, we have $A_c = 10$ V

b) **Real envelope:**
   $$R(t) = |g(t)| = |10e^{j0.2\sin(2\pi \cdot 3 \times 10^3 t)}| = 10|e^{j0.2\sin(...)}| = 10 \times 1 = 10 \text{ V}$$
   
   **Constant!**

c) **Phase function:**
   $$\theta(t) = 0.2\sin(2\pi \cdot 3 \times 10^3 t)$$

d) **Average power:**
   $$P_s = \frac{1}{2}A_c^2 = \frac{1}{2}(10)^2 = 50 \text{ W}$$
   
   **Power is constant and independent of modulation!**

---

### Solution 5.2 (Intermediate)

**Given:** $A_c = 8$ V, $\theta(t) = 5\sin(2\pi \cdot 4 \times 10^3 t)$

**Solution:**

a) **Complex envelope:**
   $$g(t) = A_c e^{j\theta(t)} = 8e^{j5\sin(2\pi \cdot 4 \times 10^3 t)}$$

b) **In-phase component:**
   $$x(t) = \text{Re}\{g(t)\} = A_c\cos(\theta(t)) = 8\cos[5\sin(2\pi \cdot 4 \times 10^3 t)]$$

c) **Quadrature component:**
   $$y(t) = \text{Im}\{g(t)\} = A_c\sin(\theta(t)) = 8\sin[5\sin(2\pi \cdot 4 \times 10^3 t)]$$

d) **Average power:**
   $$P_s = \frac{1}{2}A_c^2 = \frac{1}{2}(8)^2 = 32 \text{ W}$$

e) **Verification:**
   
   $$x^2(t) + y^2(t) = A_c^2[\cos^2(\theta(t)) + \sin^2(\theta(t))] = A_c^2 \times 1 = A_c^2 = 64$$
   
   Time average:
   $$\langle x^2(t) + y^2(t) \rangle = \langle A_c^2 \rangle = A_c^2 = 64$$
   
   Therefore:
   $$P_s = \frac{1}{2}\langle x^2(t) + y^2(t) \rangle = \frac{1}{2} \times 64 = 32 \text{ W} \quad \checkmark$$

---

### Solution 5.3 (Advanced)

**Given:** $g(t) = A_c e^{j\theta(t)}$

**Proof:**

a) **Average power:**
   $$P_s = \frac{1}{2}\langle |g(t)|^2 \rangle = \frac{1}{2}\langle |A_c e^{j\theta(t)}|^2 \rangle$$
   
   $$P_s = \frac{1}{2}\langle A_c^2|e^{j\theta(t)}|^2 \rangle = \frac{1}{2}\langle A_c^2 \times 1 \rangle = \frac{1}{2}A_c^2$$
   
   **Independent of $\theta(t)$!** $\square$

b) **Peak envelope power:**
   
   The envelope is: $R(t) = |g(t)| = A_c$ (constant)
   
   Peak envelope power:
   $$P_{PEP} = \frac{1}{2}[\max R(t)]^2 = \frac{1}{2}A_c^2 = P_s$$
   
   **PEP equals average power!** $\square$

c) **Power is constant:**
   
   Since $P_s = \frac{1}{2}A_c^2$ and $A_c$ is constant, the power is **constant regardless of modulation depth** (unlike AM where power depends on $m(t)$). $\square$

d) **Comparison with AM:**
   
   **AM:** $P_s = \frac{1}{2}A_c^2[1 + P_m]$ - depends on modulation
   - Varies with $P_m$
   - PEP > average power
   
   **FM/PM:** $P_s = \frac{1}{2}A_c^2$ - constant
   - Independent of modulation
   - PEP = average power
   
   **This is a key advantage of angle modulation!** $\square$

---

## Exercise Set 6: Modulation Index and Bessel Functions

### Solution 6.1 (Basic)

**Given:** $m(t) = 3\cos(2\pi \cdot 5 \times 10^3 t)$, $D_f = 2\pi \times 10^4$ rad/s per unit, $f_m = 5$ kHz

**Solution:**

a) **Modulation index:**
   $$\beta = \frac{D_f A_m}{\omega_m} = \frac{D_f A_m}{2\pi f_m} = \frac{2\pi \times 10^4 \times 3}{2\pi \times 5 \times 10^3} = \frac{3 \times 10^4}{5 \times 10^3} = 6$$

b) **Peak frequency deviation:**
   $$\Delta F = \frac{D_f A_m}{2\pi} = \frac{2\pi \times 10^4 \times 3}{2\pi} = 3 \times 10^4 = 30 \text{ kHz}$$

c) **Verification:**
   $$\beta = \frac{\Delta F}{f_m} = \frac{30 \times 10^3}{5 \times 10^3} = 6 \quad \checkmark$$

d) **Narrowband or wideband:**
   
   Since $\beta = 6 \gg 1$, this is **wideband FM**
   
   - Many sidebands will be significant
   - Bandwidth will be much larger than $2f_m$

---

### Solution 6.2 (Intermediate)

**Given:** $A_m = 2$ V, $f_m = 10$ kHz, $\beta = 5$

**Solution:**

a) **Frequency sensitivity:**
   
   From: $\beta = \frac{D_f A_m}{\omega_m} = \frac{D_f A_m}{2\pi f_m}$
   
   $$D_f = \frac{\beta \times 2\pi f_m}{A_m} = \frac{5 \times 2\pi \times 10 \times 10^3}{2} = 5\pi \times 10^4 \text{ rad/s per unit}$$
   
   $$D_f = 50\pi \times 10^3 \approx 157,080 \text{ rad/s per unit}$$

b) **Peak frequency deviation:**
   $$\Delta F = \beta f_m = 5 \times 10 \times 10^3 = 50 \times 10^3 = 50 \text{ kHz}$$
   
   Or: $\Delta F = \frac{D_f A_m}{2\pi} = \frac{50\pi \times 10^3 \times 2}{2\pi} = 50 \times 10^3 = 50 \text{ kHz}$ ✓

c) **Number of significant sidebands:**
   
   For $\beta = 5$, approximately $\beta + 1 = 6$ sidebands on each side contain most of the power.
   
   **Total:** About 13 components (carrier + 6 pairs of sidebands)

d) **Bandwidth using Carson's rule:**
   $$B_T \approx 2(\Delta F + f_m) = 2(50 \times 10^3 + 10 \times 10^3) = 2 \times 60 \times 10^3 = 120 \text{ kHz}$$
   
   Or: $B_T \approx 2(\beta + 1)f_m = 2(5 + 1) \times 10 \times 10^3 = 120 \text{ kHz}$ ✓

---

### Solution 6.3 (Advanced)

**Proof:**

a) **Modulation index determines sidebands:**
   
   The spectrum is: $S(f) = \frac{A_c}{2}\sum_{n=-\infty}^{+\infty} J_n(\beta)[\delta(f - f_c - nf_m) + \delta(f + f_c - nf_m)]$
   
   The amplitude of the $n$-th sideband is proportional to $J_n(\beta)$.
   
   - For small $\beta$: Only $J_0(\beta)$ and $J_1(\beta)$ are significant
   - For large $\beta$: Many $J_n(\beta)$ are significant
   
   Therefore, **$\beta$ determines the number of significant sidebands**. $\square$

b) **For $\beta \ll 1$:**
   
   Using small-argument approximations:
   - $J_0(\beta) \approx 1$
   - $J_1(\beta) \approx \beta/2$
   - $J_n(\beta) \approx 0$ for $n \geq 2$
   
   Therefore, only **carrier and first sidebands** are significant. $\square$

c) **For $\beta \gg 1$:**
   
   For large $\beta$, Bessel functions are significant for $n$ up to approximately $\beta$.
   
   **Rule of thumb:** Approximately $\beta + 1$ sidebands on each side contain most of the power.
   
   This is because $J_n(\beta)$ is significant when $|n| \lesssim \beta$. $\square$

d) **Carrier null:**
   
   The carrier component has amplitude $\frac{A_c}{2}J_0(\beta)$.
   
   When $J_0(\beta) = 0$, the carrier disappears.
   
   **First null:** $J_0(2.405) = 0$ (approximately)
   
   At $\beta = 2.405$, all power is in the sidebands! $\square$

e) **Power conservation:**
   
   The total power is:
   $$P_s = \frac{A_c^2}{2}\sum_{n=-\infty}^{+\infty} J_n^2(\beta) = \frac{A_c^2}{2}$$
   
   Therefore:
   $$\sum_{n=-\infty}^{+\infty} J_n^2(\beta) = 1$$
   
   This is a **fundamental property** of Bessel functions! $\square$

---

*End of Part 1 - Solutions for Exercise Sets 1-6*



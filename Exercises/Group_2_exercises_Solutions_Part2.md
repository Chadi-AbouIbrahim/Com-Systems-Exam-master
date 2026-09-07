# Group 2 Exercises - Complete Solutions (Part 2: Exercise Sets 7-12)

This document provides detailed solutions to Exercise Sets 7-12 from Group_2_exercises.md.

---

## Exercise Set 7: Product Detector

### Solution 7.1 (Basic)

**Given:** 
- Input: $v_{in}(t) = 4\cos(2\pi \cdot 2 \times 10^3 t)\cos(2\pi \cdot 100 \times 10^3 t)$
- Local oscillator: $v_{LO}(t) = 2\cos(2\pi \cdot 100 \times 10^3 t)$

**Solution:**

a) **Multiplier output:**
   $$v_1(t) = v_{in}(t) \cdot v_{LO}(t)$$
   
   $$v_1(t) = 4\cos(2\pi \cdot 2 \times 10^3 t)\cos(2\pi \cdot 100 \times 10^3 t) \cdot 2\cos(2\pi \cdot 100 \times 10^3 t)$$
   
   $$v_1(t) = 8\cos(2\pi \cdot 2 \times 10^3 t)\cos^2(2\pi \cdot 100 \times 10^3 t)$$
   
   Using: $\cos^2 A = \frac{1 + \cos(2A)}{2}$
   
   $$v_1(t) = 8\cos(2\pi \cdot 2 \times 10^3 t) \cdot \frac{1 + \cos(4\pi \cdot 100 \times 10^3 t)}{2}$$
   
   $$v_1(t) = 4\cos(2\pi \cdot 2 \times 10^3 t) + 4\cos(2\pi \cdot 2 \times 10^3 t)\cos(4\pi \cdot 100 \times 10^3 t)$$
   
   Using: $\cos A \cos B = \frac{1}{2}[\cos(A+B) + \cos(A-B)]$
   
   $$v_1(t) = 4\cos(2\pi \cdot 2 \times 10^3 t) + 2\cos[2\pi(2 \times 10^3 + 200 \times 10^3)t] + 2\cos[2\pi(2 \times 10^3 - 200 \times 10^3)t]$$
   
   $$v_1(t) = 4\cos(2\pi \cdot 2 \times 10^3 t) + 2\cos(2\pi \cdot 202 \times 10^3 t) + 2\cos(2\pi \cdot 198 \times 10^3 t)$$

b) **Lowpass filter output:**
   
   The lowpass filter removes frequencies above, say, 10 kHz.
   - First term: $4\cos(2\pi \cdot 2 \times 10^3 t)$ at 2 kHz → **passes**
   - Second term: $2\cos(2\pi \cdot 202 \times 10^3 t)$ at 202 kHz → **removed**
   - Third term: $2\cos(2\pi \cdot 198 \times 10^3 t)$ at 198 kHz → **removed**
   
   Therefore:
   $$v_{out}(t) = 4\cos(2\pi \cdot 2 \times 10^3 t)$$

c) **Recovered message:**
   
   The original modulating signal was $m(t) = \cos(2\pi \cdot 2 \times 10^3 t)$ (from DSB-SC form).
   
   The recovered signal is $4\cos(2\pi \cdot 2 \times 10^3 t) = 4m(t)$
   
   **The message is recovered correctly!** (scaled by factor 4)

---

### Solution 7.2 (Intermediate)

**Given:**
- Input: $v_{in}(t) = A_c m(t)\cos(\omega_c t + \theta)$
- Local oscillator: $v_{LO}(t) = A_0\cos(\omega_c t + \theta_0)$

**Solution:**

The multiplier output is:
$$v_1(t) = A_c m(t)\cos(\omega_c t + \theta) \cdot A_0\cos(\omega_c t + \theta_0)$$

$$v_1(t) = A_c A_0 m(t) \cdot \frac{1}{2}[\cos(2\omega_c t + \theta + \theta_0) + \cos(\theta - \theta_0)]$$

After lowpass filtering (removes $2\omega_c$ term):
$$v_{out}(t) = \frac{A_c A_0}{2} m(t)\cos(\theta - \theta_0)$$

a) **When $\theta_0 = \theta$ (synchronized):**
   $$v_{out}(t) = \frac{A_c A_0}{2} m(t)\cos(0) = \frac{A_c A_0}{2} m(t)$$
   
   **Full output!** ✓

b) **When $\theta_0 = \theta + \pi/2$ (90° phase error):**
   $$v_{out}(t) = \frac{A_c A_0}{2} m(t)\cos(-\pi/2) = \frac{A_c A_0}{2} m(t) \times 0 = 0$$
   
   **Zero output!** ✗ (complete loss of signal)

c) **When $\theta_0 = \theta + \pi$ (180° phase error):**
   $$v_{out}(t) = \frac{A_c A_0}{2} m(t)\cos(-\pi) = \frac{A_c A_0}{2} m(t) \times (-1) = -\frac{A_c A_0}{2} m(t)$$
   
   **Inverted output!** ✗ (signal is inverted)

d) **Effect of phase error:**
   
   The output is reduced by factor $\cos(\theta - \theta_0)$:
   - If $\theta_0 = \theta$: $\cos(0) = 1$ → full output
   - If $|\theta - \theta_0| < \pi/2$: output reduced but not zero
   - If $|\theta - \theta_0| = \pi/2$: output is zero
   - If $|\theta - \theta_0| > \pi/2$: output is inverted
   
   **Phase synchronization is critical!**

---

### Solution 7.3 (Advanced)

**Given:** $v_{in}(t) = R(t)\cos[\omega_c t + \theta(t)]$, $v_{LO}(t) = A_0\cos(\omega_c t + \theta_0)$

**Proof:**

a) **Output expression:**
   
   Multiplier output:
   $$v_1(t) = R(t)\cos[\omega_c t + \theta(t)] \cdot A_0\cos(\omega_c t + \theta_0)$$
   
   $$v_1(t) = \frac{A_0 R(t)}{2}[\cos(2\omega_c t + \theta(t) + \theta_0) + \cos(\theta(t) - \theta_0)]$$
   
   After lowpass filtering:
   $$v_{out}(t) = \frac{A_0 R(t)}{2}\cos[\theta(t) - \theta_0] \quad \square$$

b) **When $\theta_0 = 0$ and $\theta(t) = 0$ (AM):**
   
   For AM: $R(t) = A_c[1 + m(t)]$ and $\theta(t) = 0$
   
   $$v_{out}(t) = \frac{A_0 R(t)}{2}\cos(0) = \frac{A_0}{2} R(t) = \frac{A_0}{2} A_c[1 + m(t)] \quad \square$$

c) **When $\theta_0 = 0$ and $R(t) = A_c$ (DSB-SC):**
   
   For DSB-SC: $R(t) = A_c$ (constant) and $\theta(t) = 0$ or $\pi$ (depending on sign of $m(t)$)
   
   Actually, for DSB-SC: $s(t) = A_c m(t)\cos(\omega_c t)$
   
   In polar form: $R(t) = A_c|m(t)|$ and $\theta(t) = 0$ if $m(t) > 0$, $\pi$ if $m(t) < 0$
   
   But it's easier to use: $v_{in}(t) = A_c m(t)\cos(\omega_c t)$
   
   Then: $v_1(t) = A_c m(t)\cos(\omega_c t) \cdot A_0\cos(\omega_c t) = \frac{A_c A_0 m(t)}{2}[1 + \cos(2\omega_c t)]$
   
   After lowpass: $v_{out}(t) = \frac{A_c A_0}{2} m(t)$
   
   Using the given form: if $R(t) = A_c$ and we consider the in-phase component:
   $$v_{out}(t) = \frac{A_0 A_c}{2} m(t) \quad \square$$

d) **Linear detector:**
   
   The product detector operation is:
   $$v_{out}(t) = \text{LPF}[v_{in}(t) \cdot v_{LO}(t)]$$
   
   This is **linear** because:
   - If $v_{in}(t) = v_1(t) + v_2(t)$
   - Then $v_{out}(t) = \text{LPF}[(v_1 + v_2) \cdot v_{LO}] = \text{LPF}[v_1 \cdot v_{LO}] + \text{LPF}[v_2 \cdot v_{LO}]$
   - So it satisfies superposition (linear!) $\square$

---

## Exercise Set 8: Spectrum Analysis

### Solution 8.1 (Basic)

**Given:** $A_c = 6$ V, $m(t) = 2\cos(2\pi \cdot 4 \times 10^3 t)$, $f_c = 200$ kHz

**Solution:**

a) **Spectrum of modulating signal:**
   $$M(f) = \mathcal{F}[2\cos(2\pi \cdot 4 \times 10^3 t)]$$
   
   $$M(f) = \delta(f - 4000) + \delta(f + 4000)$$

b) **Spectrum of complex envelope:**
   $$G(f) = A_c[\delta(f) + M(f)] = 6[\delta(f) + \delta(f - 4000) + \delta(f + 4000)]$$
   
   $$G(f) = 6\delta(f) + 6\delta(f - 4000) + 6\delta(f + 4000)$$

c) **Spectrum of AM signal:**
   $$S(f) = \frac{1}{2}[G(f - f_c) + G(f + f_c)]$$
   
   $$S(f) = \frac{1}{2}[6\delta(f - 200 \times 10^3) + 6\delta(f - 200 \times 10^3 - 4000) + 6\delta(f - 200 \times 10^3 + 4000) + 6\delta(f + 200 \times 10^3) + 6\delta(f + 200 \times 10^3 - 4000) + 6\delta(f + 200 \times 10^3 + 4000)]$$
   
   Simplifying:
   $$S(f) = 3\delta(f - 200,000) + 3\delta(f - 204,000) + 3\delta(f - 196,000) + 3\delta(f + 200,000) + 3\delta(f + 204,000) + 3\delta(f + 196,000)$$

d) **Sketch of magnitude spectrum:**
   ```
   |S(f)|
     3
     |     |     |     |     |     |
     |     |     |     |     |     |
   __|_____|_____|_____|_____|_____|_____
   -204k  -200k  -196k   0   196k  200k  204k  (Hz)
   
   Components:
   - Carrier: ±200 kHz (amplitude 3)
   - Upper sideband: +204 kHz (amplitude 3)
   - Lower sideband: +196 kHz (amplitude 3)
   - Upper sideband: -196 kHz (amplitude 3)
   - Lower sideband: -204 kHz (amplitude 3)
   ```

---

### Solution 8.2 (Intermediate)

**Given:**
$$M(f) = \begin{cases}
2, & |f| \leq 8 \text{ kHz} \\
0, & |f| > 8 \text{ kHz}
\end{cases}$$
$A_c = 8$ V, $f_c = 500$ kHz

**Solution:**

a) **Spectrum of complex envelope:**
   $$G(f) = A_c[\delta(f) + M(f)] = 8[\delta(f) + M(f)]$$
   
   $$G(f) = 8\delta(f) + \begin{cases}
   16, & |f| \leq 8 \text{ kHz} \\
   0, & |f| > 8 \text{ kHz}
   \end{cases}$$

b) **Spectrum of AM signal:**
   $$S(f) = \frac{1}{2}[G(f - f_c) + G(f + f_c)]$$
   
   $$S(f) = \frac{1}{2}[8\delta(f - 500 \times 10^3) + 8\delta(f + 500 \times 10^3) + \text{sidebands}]$$
   
   Sidebands:
   - Upper: $\frac{1}{2} \times 16 = 8$ for $500 \times 10^3 < f \leq 508 \times 10^3$
   - Lower: $\frac{1}{2} \times 16 = 8$ for $-508 \times 10^3 \leq f < -500 \times 10^3$
   
   $$S(f) = 4\delta(f - 500,000) + 4\delta(f + 500,000) + \begin{cases}
   8, & 500,000 < |f| \leq 508,000 \\
   0, & \text{otherwise}
   \end{cases}$$

c) **Bandwidth:**
   - Baseband bandwidth: $B = 8$ kHz
   - Bandpass bandwidth: $B_T = 2B = 16$ kHz
   - Frequency range: $500 \pm 8$ kHz = 492 to 508 kHz

d) **Carrier and sideband components:**
   - **Carrier:** Delta functions at $\pm 500$ kHz with amplitude 4
   - **Upper sideband:** Continuous spectrum from 500 to 508 kHz with amplitude 8
   - **Lower sideband:** Continuous spectrum from -508 to -500 kHz with amplitude 8

---

### Solution 8.3 (Advanced)

**Given:** $s(t) = A_c m(t)\cos(\omega_c t)$

**Proof:**

a) **Spectrum:**
   
   The complex envelope is: $g(t) = A_c m(t)$
   
   Spectrum: $G(f) = A_c M(f)$
   
   Bandpass spectrum:
   $$S(f) = \frac{1}{2}[G(f - f_c) + G^*(-f - f_c)]$$
   
   Since $g(t)$ is real: $G^*(-f) = G(-f)$
   
   $$S(f) = \frac{1}{2}[A_c M(f - f_c) + A_c M(-f - f_c)] = \frac{A_c}{2}[M(f - f_c) + M(f + f_c)]$$
   
   (Using $M(-f) = M(f)$ for real $m(t)$) $\square$

b) **No carrier component:**
   
   The spectrum $S(f)$ contains only $M(f \pm f_c)$ terms.
   
   There is **no term** like $A_c\delta(f \pm f_c)$, so **no carrier component** in the spectrum. $\square$

c) **Bandwidth:**
   
   If $M(f)$ has bandwidth $B$ (i.e., $M(f) = 0$ for $|f| > B$), then:
   - $M(f - f_c)$ is nonzero for $f_c - B < f < f_c + B$
   - $M(f + f_c)$ is nonzero for $-f_c - B < f < -f_c + B$
   
   Total bandwidth: $B_T = 2B$ $\square$

d) **Symmetric spectrum:**
   
   Since $m(t)$ is real, $M(-f) = M^*(f) = M(f)$ (for real signals).
   
   Therefore:
   - $M(f - f_c)$ around $+f_c$
   - $M(f + f_c) = M(-(-f - f_c))$ around $-f_c$
   
   The spectrum is **symmetric** about $\pm f_c$. $\square$

---

## Exercise Set 9: Comparison Problems

### Solution 9.1 (Intermediate)

**Given:** $m(t) = \cos(2\pi \cdot 5 \times 10^3 t)$, $A_c = 10$ V, $f_c = 1$ MHz

**Solution:**

a) **Standard AM:**

   1. **Complex envelope:**
      $$g(t) = A_c[1 + m(t)] = 10[1 + \cos(2\pi \cdot 5 \times 10^3 t)]$$

   2. **Bandwidth:**
      - Baseband: $B = 5$ kHz
      - Bandpass: $B_T = 2B = 10$ kHz

   3. **Average power:**
      $$P_m = \langle m^2(t) \rangle = \frac{1}{2}$$
      $$P_s = \frac{1}{2}A_c^2[1 + P_m] = \frac{1}{2}(10)^2[1 + 0.5] = 50 \times 1.5 = 75 \text{ W}$$

   4. **Modulation efficiency:**
      $$\eta = \frac{P_m}{1 + P_m} = \frac{0.5}{1.5} = \frac{1}{3} = 33.3\%$$

b) **DSB-SC:**

   1. **Complex envelope:**
      $$g(t) = A_c m(t) = 10\cos(2\pi \cdot 5 \times 10^3 t)$$

   2. **Bandwidth:**
      - Baseband: $B = 5$ kHz
      - Bandpass: $B_T = 2B = 10$ kHz

   3. **Average power:**
      $$P_s = \frac{1}{2}A_c^2 P_m = \frac{1}{2}(10)^2 \times 0.5 = 50 \times 0.5 = 25 \text{ W}$$

   4. **Modulation efficiency:**
      $$\eta = 100\%$$ (all power in sidebands)

c) **SSB-AM (USSB):**

   1. **Complex envelope:**
      $$g(t) = A_c[m(t) + j\hat{m}(t)] = 10[\cos(2\pi \cdot 5 \times 10^3 t) + j\sin(2\pi \cdot 5 \times 10^3 t)]$$
      
      Where $\hat{m}(t) = \sin(2\pi \cdot 5 \times 10^3 t)$ is the Hilbert transform

   2. **Bandwidth:**
      - Baseband: $B = 5$ kHz
      - Bandpass: $B_T = B = 5$ kHz (half of DSB-SC!)

   3. **Average power:**
      $$P_s = \frac{1}{2}A_c^2 P_m = \frac{1}{2}(10)^2 \times 0.5 = 25 \text{ W}$$
      (Same as DSB-SC)

   4. **Modulation efficiency:**
      $$\eta = 100\%$$ (all power in sidebands)

**Summary Table:**

| System | $g(t)$ | $B_T$ | $P_s$ | $\eta$ |
|--------|--------|-------|-------|--------|
| Standard AM | $10[1 + m(t)]$ | 10 kHz | 75 W | 33.3% |
| DSB-SC | $10 m(t)$ | 10 kHz | 25 W | 100% |
| SSB-AM | $10[m(t) + j\hat{m}(t)]$ | 5 kHz | 25 W | 100% |

---

### Solution 9.2 (Advanced)

**Comparison Table:**

| Feature | Standard AM | DSB-SC | SSB-AM |
|---------|-------------|--------|--------|
| **Bandwidth Efficiency** | Low ($2B$) | Medium ($2B$) | **High ($B$)** ✓ |
| **Power Efficiency** | Low (~33% max) | **High (100%)** ✓ | **High (100%)** ✓ |
| **Implementation Complexity** | **Low** ✓ | Medium | **High** ✗ |
| **Demodulation Complexity** | **Low** ✓ (envelope) | Medium (product) | **High** ✗ (product + sync) |
| **Noise Performance** | Poor | Medium | **Good** ✓ |

**Detailed Analysis:**

a) **Bandwidth efficiency:**
   - **SSB-AM** uses least bandwidth ($B$ vs $2B$ for others)
   - Allows more channels in same frequency band

b) **Power efficiency:**
   - **DSB-SC and SSB-AM** are 100% efficient (all power in sidebands)
   - **Standard AM** wastes ~67% of power in carrier (at 100% modulation)

c) **Implementation complexity:**
   - **Standard AM** is simplest (just multiplier)
   - **DSB-SC** requires carrier suppression (balanced modulator)
   - **SSB-AM** requires Hilbert transform (most complex)

d) **Demodulation complexity:**
   - **Standard AM** can use simple envelope detector
   - **DSB-SC and SSB-AM** require product detector with synchronization

e) **Noise performance:**
   - **SSB-AM** has best noise performance (narrowest bandwidth)
   - **Standard AM** has worst (carrier adds noise but no information)

---

## Exercise Set 10: Numerical Problems

### Solution 10.1 (Basic Calculation)

**Given:** $f_c = 1000$ kHz, $m(t) = 0.8\cos(2\pi \cdot 5 \times 10^3 t)$, $A_c = 100$ V

**Solution:**

a) **Modulation index:**
   $$\mu = \max|m(t)| = 0.8 = 80\%$$

b) **Bandwidth:**
   - Baseband: $B = 5$ kHz
   - Bandpass: $B_T = 2B = 10$ kHz

c) **Average power (1Ω load):**
   $$P_m = \frac{0.8^2}{2} = 0.32$$
   $$P_s = \frac{1}{2}A_c^2[1 + P_m] = \frac{1}{2}(100)^2[1 + 0.32] = 5000 \times 1.32 = 6600 \text{ W} = 6.6 \text{ kW}$$

d) **Peak envelope power:**
   $$P_{PEP} = \frac{1}{2}[\max R(t)]^2 = \frac{1}{2}[A_c(1 + \mu)]^2 = \frac{1}{2}(100 \times 1.8)^2 = \frac{1}{2}(180)^2 = 16,200 \text{ W} = 16.2 \text{ kW}$$

---

### Solution 10.2 (Power Calculation)

**Given:** $P_s = 50$ W, $\eta = 25\%$

**Solution:**

a) **Carrier power:**
   
   From efficiency: $\eta = \frac{P_{SB}}{P_s} = 0.25$
   
   Therefore: $P_{SB} = 0.25 \times 50 = 12.5$ W
   
   Carrier power: $P_c = P_s - P_{SB} = 50 - 12.5 = 37.5$ W

b) **Sideband power:**
   $$P_{SB} = 12.5 \text{ W}$$

c) **Average power of modulating signal:**
   
   If $A_c = 10$ V:
   $$P_c = \frac{1}{2}A_c^2 = \frac{1}{2}(10)^2 = 50 \text{ W}$$
   
   But we found $P_c = 37.5$ W, so let's use the actual values:
   
   From $P_c = \frac{1}{2}A_c^2 = 37.5$:
   $$A_c^2 = 75$$
   $$A_c = \sqrt{75} = 5\sqrt{3} \approx 8.66 \text{ V}$$
   
   From $P_{SB} = \frac{1}{2}A_c^2 P_m = 12.5$:
   $$P_m = \frac{12.5}{\frac{1}{2} \times 75} = \frac{12.5}{37.5} = \frac{1}{3} = 0.333$$

---

### Solution 10.3 (Bandwidth Calculation)

**Given:** $B = 10$ kHz, $f_c = 1$ MHz

**Solution:**

a) **Standard AM:**
   - Bandwidth: $B_T = 2B = 20$ kHz
   - Frequency range: $1,000,000 \pm 10,000$ = **990 to 1010 kHz**

b) **DSB-SC:**
   - Bandwidth: $B_T = 2B = 20$ kHz
   - Frequency range: $1,000,000 \pm 10,000$ = **990 to 1010 kHz**

c) **SSB-AM:**
   - Bandwidth: $B_T = B = 10$ kHz
   - Frequency range (USSB): $1,000,000$ to $1,010,000$ = **1000 to 1010 kHz**
   - Frequency range (LSSB): $990,000$ to $1,000,000$ = **990 to 1000 kHz**

**Comparison:**
- Standard AM/DSB-SC: 20 kHz bandwidth
- SSB-AM: 10 kHz bandwidth (half!)

---

## Exercise Set 11: Conceptual Questions

### Solution 11.1

**Differences:**

1. **Standard AM vs DSB-SC:**
   - **Standard AM:** Contains carrier + both sidebands, $g(t) = A_c[1 + m(t)]$
   - **DSB-SC:** No carrier, both sidebands, $g(t) = A_c m(t)$
   - Standard AM can use envelope detector; DSB-SC requires product detector
   - Standard AM is power inefficient (~33% max); DSB-SC is 100% efficient

2. **DSB-SC vs SSB-AM:**
   - **DSB-SC:** Both sidebands, bandwidth $2B$
   - **SSB-AM:** One sideband, bandwidth $B$
   - SSB-AM uses half the bandwidth
   - Both are 100% power efficient
   - SSB-AM requires Hilbert transform (more complex)

3. **Envelope detector vs Product detector:**
   - **Envelope detector:** Nonlinear, extracts $R(t) = |g(t)|$, works only for standard AM
   - **Product detector:** Linear, multiplies with synchronized oscillator, works for all AM types
   - Envelope detector is simpler but limited
   - Product detector requires synchronization but is more versatile

---

### Solution 11.2

**Why standard AM is power inefficient:**

1. **Where the power goes:**
   - Total power: $P_s = P_c + P_{SB}$
   - Carrier power: $P_c = \frac{1}{2}A_c^2$ (constant, doesn't carry information)
   - Sideband power: $P_{SB} = \frac{1}{2}A_c^2 P_m$ (carries information)
   - At 100% modulation: $P_c = 2P_{SB}$, so **67% of power is wasted in carrier!**

2. **Why carrier doesn't carry information:**
   - Carrier is constant: $A_c\cos(\omega_c t)$
   - It's independent of $m(t)$
   - All information is in the sidebands
   - Carrier is only needed for envelope detection

3. **How DSB-SC and SSB-AM improve efficiency:**
   - **DSB-SC:** Suppresses carrier → 100% efficiency (all power in sidebands)
   - **SSB-AM:** Suppresses carrier + one sideband → 100% efficiency + half bandwidth
   - Both eliminate wasted carrier power
   - Trade-off: More complex generation and demodulation

---

### Solution 11.3

**Explanations:**

a) **Envelope detector works for standard AM but not DSB-SC:**
   - Standard AM: $g(t) = A_c[1 + m(t)] \geq 0$ (if $|m(t)| < 1$)
   - Envelope: $R(t) = |g(t)| = g(t)$ → gives $A_c[1 + m(t)]$ ✓
   - DSB-SC: $g(t) = A_c m(t)$ (can be negative!)
   - Envelope: $R(t) = |g(t)| = A_c|m(t)|$ → loses sign information ✗

b) **Product detector needed for DSB-SC and SSB-AM:**
   - DSB-SC: $g(t)$ can be negative → envelope detector fails
   - SSB-AM: Complex envelope → envelope detector can't extract properly
   - Product detector multiplies with synchronized carrier → recovers $m(t)$ correctly
   - Requires phase synchronization (more complex)

c) **SSB-AM uses half bandwidth:**
   - DSB-SC: Both sidebands contain same information → redundant
   - SSB-AM: Transmits only one sideband → eliminates redundancy
   - Bandwidth: $B$ (SSB) vs $2B$ (DSB-SC)
   - Trade-off: Requires Hilbert transform (complex generation)

d) **Overmodulation causes distortion:**
   - If $m(t) < -1$: $g(t) = A_c[1 + m(t)] < 0$
   - Envelope detector gives: $R(t) = |g(t)| = -g(t)$ (inverted!)
   - Result: Distorted output, sign errors
   - Solution: Keep $|m(t)| < 1$ (modulation index $\mu < 1$)

---

## Exercise Set 12: Derivation Problems

### Solution 12.1

**Derive:** $S(f) = \frac{A_c}{2}[\delta(f - f_c) + M(f - f_c) + \delta(f + f_c) + M(f + f_c)]$ from $g(t) = A_c[1 + m(t)]$

**Derivation:**

Starting from:
$$g(t) = A_c[1 + m(t)]$$

Taking Fourier transform:
$$G(f) = \mathcal{F}[A_c[1 + m(t)]] = A_c[\mathcal{F}[1] + \mathcal{F}[m(t)]]$$

$$G(f) = A_c[\delta(f) + M(f)]$$

Using the spectrum theorem:
$$S(f) = \frac{1}{2}[G(f - f_c) + G^*(-f - f_c)]$$

Since $g(t)$ is real: $G^*(-f) = G(-f)$

$$S(f) = \frac{1}{2}[G(f - f_c) + G(-f - f_c)]$$

Substituting $G(f)$:
$$S(f) = \frac{1}{2}[A_c\delta(f - f_c) + A_c M(f - f_c) + A_c\delta(-f - f_c) + A_c M(-f - f_c)]$$

Using $\delta(-f) = \delta(f)$ and $M(-f) = M(f)$ (for real $m(t)$):
$$S(f) = \frac{A_c}{2}[\delta(f - f_c) + M(f - f_c) + \delta(f + f_c) + M(f + f_c)] \quad \square$$

---

### Solution 12.2

**Prove:** For product detector with $v_{in}(t) = g(t)\cos(\omega_c t)$ and $v_{LO}(t) = A_0\cos(\omega_c t + \theta_0)$, output is $v_{out}(t) = \frac{1}{2}A_0\text{Re}\{g(t)e^{-j\theta_0}\}$

**Proof:**

Multiplier output:
$$v_1(t) = g(t)\cos(\omega_c t) \cdot A_0\cos(\omega_c t + \theta_0)$$

$$v_1(t) = \frac{A_0 g(t)}{2}[\cos(2\omega_c t + \theta_0) + \cos(-\theta_0)]$$

$$v_1(t) = \frac{A_0 g(t)}{2}[\cos(2\omega_c t + \theta_0) + \cos(\theta_0)]$$

After lowpass filtering (removes $2\omega_c$ term):
$$v_{out}(t) = \frac{A_0 g(t)}{2}\cos(\theta_0)$$

But this is not the complete answer. Let me reconsider.

Actually, if $g(t)$ is complex:
$$g(t) = x(t) + jy(t)$$

Then:
$$v_{in}(t) = \text{Re}\{g(t)e^{j\omega_c t}\} = x(t)\cos(\omega_c t) - y(t)\sin(\omega_c t)$$

For the general case, using the given form:
$$v_{in}(t) = g(t)\cos(\omega_c t)$$

This assumes $g(t)$ is real. But for the general proof:

$$v_1(t) = \text{Re}\{g(t)e^{j\omega_c t}\} \cdot A_0\cos(\omega_c t + \theta_0)$$

$$v_1(t) = \frac{1}{2}[g(t)e^{j\omega_c t} + g^*(t)e^{-j\omega_c t}] \cdot \frac{A_0}{2}[e^{j(\omega_c t + \theta_0)} + e^{-j(\omega_c t + \theta_0)}]$$

After expansion and lowpass filtering:
$$v_{out}(t) = \frac{A_0}{4}[g(t)e^{-j\theta_0} + g^*(t)e^{j\theta_0}] = \frac{A_0}{2}\text{Re}\{g(t)e^{-j\theta_0}\} \quad \square$$

---

### Solution 12.3

**Prove:** For standard AM with $m(t) = \mu\cos(\omega_m t)$, efficiency is $\eta = \frac{\mu^2}{2 + \mu^2}$ and maximum is $\eta_{max} = \frac{1}{3}$

**Proof:**

**Step 1: Find $P_m$**
$$P_m = \langle m^2(t) \rangle = \langle [\mu\cos(\omega_m t)]^2 \rangle = \mu^2 \times \frac{1}{2} = \frac{\mu^2}{2}$$

**Step 2: Find efficiency**
$$\eta = \frac{P_m}{1 + P_m} = \frac{\mu^2/2}{1 + \mu^2/2} = \frac{\mu^2/2}{(2 + \mu^2)/2} = \frac{\mu^2}{2 + \mu^2} \quad \square$$

**Step 3: Maximum efficiency**
At $\mu = 1$ (100% modulation):
$$\eta_{max} = \frac{1^2}{2 + 1^2} = \frac{1}{2 + 1} = \frac{1}{3} \approx 33.3\% \quad \square$$

**Verification:**
- $P_m = \frac{1}{2}$
- $\eta = \frac{1/2}{1 + 1/2} = \frac{1/2}{3/2} = \frac{1}{3}$ ✓

---

*End of Part 2 - Solutions for Exercise Sets 7-12*


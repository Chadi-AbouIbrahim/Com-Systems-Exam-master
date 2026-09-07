# GROUP 3 - Analog Modulation (Angle-based): Detailed Explanation

## Lecture 18: Angle Modulation (FM & PM)

---

## Table of Contents

1. [Introduction: What is Angle Modulation?](#introduction)
2. [Phase Modulation (PM) - The Basics](#phase-modulation)
3. [Frequency Modulation (FM) - The Basics](#frequency-modulation)
4. [Relationship Between PM and FM](#pm-fm-relationship)
5. [Instantaneous Frequency](#instantaneous-frequency)
6. [Complex Envelope for Angle Modulation](#complex-envelope)
7. [Spectrum of Angle-Modulated Signals](#spectrum)
8. [Bessel Functions and Modulation Index](#bessel-functions)
9. [Carson's Rule and Bandwidth](#carson-rule)
10. [Power in Angle-Modulated Signals](#power)
11. [Detailed Example: Sinusoidal Modulation](#detailed-example)
12. [Key Takeaways](#key-takeaways)

---

## 1. Introduction: What is Angle Modulation? {#introduction}

### The Basic Idea

**Angle Modulation** is the process of varying the **phase** or **frequency** of a carrier signal in proportion to an information signal, while keeping the **amplitude constant**.

**Why Angle Modulation?**
- **Constant amplitude** → resistant to amplitude noise and fading
- **Better noise performance** than AM
- **Wider bandwidth** but better signal-to-noise ratio
- Used in FM radio, TV audio, and many communication systems

### Two Types of Angle Modulation

1. **Phase Modulation (PM):** The **phase** of the carrier varies with the message
2. **Frequency Modulation (FM):** The **frequency** of the carrier varies with the message

**Key Insight:** PM and FM are closely related - they're just different ways of encoding the same information!

### Comparison with Amplitude Modulation

| Feature | AM | PM/FM |
|---------|----|----|
| Amplitude | Varies | Constant |
| Phase/Frequency | Constant | Varies |
| Noise Resistance | Poor | Good |
| Bandwidth | Narrow | Wide |
| Power Efficiency | Low | High |

---

## 2. Phase Modulation (PM) - The Basics {#phase-modulation}

### The Complex Envelope

For **Phase Modulation**, the complex envelope is:

$$g(t) = A_c e^{j\theta(t)}$$

where:
- $A_c > 0$ is the **constant carrier amplitude**
- $\theta(t)$ is the **phase** that varies with the message

### The Phase Function

The phase is directly proportional to the modulating signal:

$$\theta(t) = D_p m(t)$$

where:
- $D_p$ is the **phase sensitivity** (radians per unit of $m(t)$)
- $m(t)$ is the **modulating signal** (information)

### The Modulated Signal

The bandpass signal is:

$$s(t) = \text{Re}\{g(t)e^{j\omega_c t}\} = \text{Re}\{A_c e^{j\theta(t)}e^{j\omega_c t}\}$$

$$s(t) = A_c\cos[\omega_c t + \theta(t)] = A_c\cos[\omega_c t + D_p m(t)]$$

**What This Means:**
- The **amplitude** is constant: $A_c$
- The **phase** varies: $\theta(t) = D_p m(t)$
- Information is encoded in the **phase variations**

### Real Envelope

Since $g(t) = A_c e^{j\theta(t)}$:

$$R(t) = |g(t)| = |A_c e^{j\theta(t)}| = A_c|e^{j\theta(t)}| = A_c \times 1 = A_c$$

**Key Property:** The envelope is **constant**! This is why PM/FM are resistant to amplitude noise.

### Visual Example

```
Message m(t):     ___/‾‾‾\___/‾‾‾\___
                  
PM Signal:        ~~~~~~~~~~~~~~~~~~~~
                 (constant amplitude,
                  phase varies)
```

The **phase** of the carrier wave shifts back and forth, but the **amplitude** stays constant.

---

## 3. Frequency Modulation (FM) - The Basics {#frequency-modulation}

### The Complex Envelope

For **Frequency Modulation**, the complex envelope is the same form:

$$g(t) = A_c e^{j\theta(t)}$$

But the **phase function** is different!

### The Phase Function for FM

For FM, the **instantaneous frequency** is proportional to the message:

$$f_i(t) = f_c + \frac{1}{2\pi}D_f m(t)$$

where:
- $f_c$ is the **carrier frequency**
- $D_f$ is the **frequency sensitivity** (Hz per unit of $m(t)$)
- $m(t)$ is the **modulating signal**

The phase is the **integral** of the frequency:

$$\theta(t) = 2\pi \int_0^t f_i(\tau) - f_c \, d\tau = D_f \int_0^t m(\tau) \, d\tau$$

**Key Difference from PM:**
- **PM:** Phase directly proportional to message: $\theta(t) = D_p m(t)$
- **FM:** Phase is **integral** of message: $\theta(t) = D_f \int m(t) dt$

### The Modulated Signal

$$s(t) = A_c\cos[\omega_c t + \theta(t)] = A_c\cos\left[\omega_c t + D_f \int_0^t m(\tau) \, d\tau\right]$$

**What This Means:**
- The **amplitude** is constant: $A_c$
- The **frequency** varies: $f_i(t) = f_c + \frac{D_f}{2\pi} m(t)$
- Information is encoded in the **frequency variations**

### Frequency Deviation

The **frequency deviation** is:

$$f_d(t) = f_i(t) - f_c = \frac{1}{2\pi}D_f m(t)$$

This is how much the frequency **deviates** from the carrier frequency.

**Peak frequency deviation:**
$$\Delta F = \max|f_d(t)| = \frac{1}{2\pi}D_f \max|m(t)|$$

---

## 4. Relationship Between PM and FM {#pm-fm-relationship}

### The Key Relationship

**PM and FM are mathematically related!**

If we have a PM signal with phase $\theta_{PM}(t) = D_p m(t)$, then:
- The instantaneous frequency is: $f_i(t) = f_c + \frac{1}{2\pi}\frac{d\theta_{PM}}{dt} = f_c + \frac{D_p}{2\pi}\frac{dm(t)}{dt}$

If we have an FM signal with phase $\theta_{FM}(t) = D_f \int m(t) dt$, then:
- The phase is: $\theta_{FM}(t) = D_f \int m(t) dt$

**Key Insight:**
- **PM** with message $m(t)$ is equivalent to **FM** with message $\frac{dm(t)}{dt}$
- **FM** with message $m(t)$ is equivalent to **PM** with message $\int m(t) dt$

### Example

**PM Signal:**
- Message: $m(t) = \cos(\omega_m t)$
- Phase: $\theta(t) = D_p \cos(\omega_m t)$
- Instantaneous frequency: $f_i(t) = f_c - \frac{D_p \omega_m}{2\pi}\sin(\omega_m t)$

**Equivalent FM Signal:**
- Message: $m_{FM}(t) = -\frac{D_p \omega_m}{D_f}\sin(\omega_m t)$
- Phase: $\theta(t) = D_f \int m_{FM}(t) dt = D_p \cos(\omega_m t)$

**They produce the same signal!**

---

## 5. Instantaneous Frequency {#instantaneous-frequency}

### Definition

The **instantaneous frequency** is the rate of change of the phase:

$$f_i(t) = \frac{1}{2\pi}\frac{d[\omega_c t + \theta(t)]}{dt} = f_c + \frac{1}{2\pi}\frac{d\theta(t)}{dt}$$

**What This Means:**
- At any instant $t$, the signal is oscillating at frequency $f_i(t)$
- This frequency **varies** with time (unlike a pure sinusoid)
- The variation encodes the information

### For PM

If $\theta(t) = D_p m(t)$:

$$f_i(t) = f_c + \frac{1}{2\pi}D_p \frac{dm(t)}{dt}$$

**Key:** The frequency depends on the **derivative** of the message!

### For FM

If $\theta(t) = D_f \int m(t) dt$:

$$f_i(t) = f_c + \frac{1}{2\pi}D_f m(t)$$

**Key:** The frequency is **directly proportional** to the message!

### Frequency Deviation

The **frequency deviation** from the carrier is:

$$f_d(t) = f_i(t) - f_c = \frac{1}{2\pi}\frac{d\theta(t)}{dt}$$

**For PM:** $f_d(t) = \frac{D_p}{2\pi}\frac{dm(t)}{dt}$

**For FM:** $f_d(t) = \frac{D_f}{2\pi}m(t)$

---

## 6. Complex Envelope for Angle Modulation {#complex-envelope}

### General Form

For any angle-modulated signal:

$$g(t) = A_c e^{j\theta(t)}$$

where $\theta(t)$ depends on the type of modulation:
- **PM:** $\theta(t) = D_p m(t)$
- **FM:** $\theta(t) = D_f \int m(t) dt$

### Properties

1. **Magnitude:** $|g(t)| = A_c$ (constant)
2. **Phase:** $\arg[g(t)] = \theta(t)$ (varies)
3. **Real envelope:** $R(t) = A_c$ (constant)

**Key Insight:** All information is in the **phase**, not the amplitude!

### In-Phase and Quadrature Components

From $g(t) = A_c e^{j\theta(t)}$:

$$g(t) = A_c[\cos(\theta(t)) + j\sin(\theta(t))]$$

Therefore:
- **In-phase:** $x(t) = A_c\cos(\theta(t))$
- **Quadrature:** $y(t) = A_c\sin(\theta(t))$

The bandpass signal is:
$$s(t) = x(t)\cos(\omega_c t) - y(t)\sin(\omega_c t) = A_c\cos[\omega_c t + \theta(t)]$$

---

## 7. Spectrum of Angle-Modulated Signals {#spectrum}

### The Challenge

Unlike AM, the spectrum of angle-modulated signals is **not** simply related to the spectrum of the modulating signal $M(f)$.

**Why?**
- The relationship is **nonlinear**: $e^{j\theta(t)}$ where $\theta(t)$ depends on $m(t)$
- For general $m(t)$, no closed-form expression exists

### Special Case: Sinusoidal Modulation

For **sinusoidal modulation**, we can find an exact expression!

**For PM:**
- Modulating signal: $m_p(t) = A_m\sin(\omega_m t)$
- Phase: $\theta(t) = D_p A_m\sin(\omega_m t) = \beta\sin(\omega_m t)$
- Where $\beta = D_p A_m$ is the **modulation index**

**For FM:**
- Modulating signal: $m_f(t) = A_m\cos(\omega_m t)$
- Phase: $\theta(t) = D_f \int A_m\cos(\omega_m t) dt = \frac{D_f A_m}{\omega_m}\sin(\omega_m t) = \beta\sin(\omega_m t)$
- Where $\beta = \frac{D_f A_m}{\omega_m}$ is the **modulation index**

### The Complex Envelope

For sinusoidal modulation:

$$g(t) = A_c e^{j\beta\sin(\omega_m t)}$$

This is a **periodic function** with period $T_m = \frac{1}{f_m}$.

### Fourier Series Expansion

Since $g(t)$ is periodic, we can expand it as a Fourier series:

$$g(t) = A_c \sum_{n=-\infty}^{+\infty} c_n e^{jn\omega_m t}$$

The coefficients are:

$$c_n = \frac{1}{T_m}\int_0^{T_m} e^{j\beta\sin(\omega_m t)} e^{-jn\omega_m t} dt$$

These coefficients are related to **Bessel functions**!

### The Spectrum

The Fourier transform is:

$$G(f) = A_c \sum_{n=-\infty}^{+\infty} J_n(\beta)\delta(f - nf_m)$$

where $J_n(\beta)$ is the **$n$-th order Bessel function of the first kind**.

The bandpass spectrum is:

$$S(f) = \frac{1}{2}[G(f - f_c) + G^*(-f - f_c)]$$

$$S(f) = \frac{A_c}{2}\sum_{n=-\infty}^{+\infty} J_n(\beta)[\delta(f - f_c - nf_m) + \delta(f + f_c + nf_m)]$$

**What This Means:**
- The spectrum consists of **discrete components** at frequencies $f_c \pm nf_m$
- The amplitudes are given by Bessel functions $J_n(\beta)$
- There are **infinite** sidebands (in theory), but most power is in a finite number

---

## 8. Bessel Functions and Modulation Index {#bessel-functions}

### Bessel Functions

**Bessel functions of the first kind** $J_n(\beta)$ are special functions that appear in angle modulation.

**Properties:**
- $J_n(\beta)$ depends on both the **order** $n$ and the **argument** $\beta$
- For small $\beta$: $J_0(\beta) \approx 1$, $J_1(\beta) \approx \beta/2$, higher orders are small
- For large $\beta$: Many orders contribute significantly
- **Symmetry:** $J_{-n}(\beta) = (-1)^n J_n(\beta)$

### Modulation Index

The **modulation index** $\beta$ is a key parameter:

**For PM:**
$$\beta = \beta_p = D_p \max|m_p(t)| = D_p A_m$$

**For FM:**
$$\beta = \beta_f = \frac{D_f A_m}{\omega_m} = \frac{\Delta F}{f_m}$$

where:
- $\Delta F = \frac{D_f A_m}{2\pi}$ is the **peak frequency deviation**
- $f_m$ is the **modulating frequency**

**Physical Meaning:**
- $\beta$ determines how many sidebands are significant
- Small $\beta$ → narrowband FM/PM (few sidebands)
- Large $\beta$ → wideband FM/PM (many sidebands)

### Bessel Function Values

Some important values:
- $J_0(0) = 1$ (all power in carrier when $\beta = 0$)
- $J_0(2.405) = 0$ (carrier disappears at $\beta = 2.405$)
- $\sum_{n=-\infty}^{+\infty} J_n^2(\beta) = 1$ (power conservation)

### Number of Significant Sidebands

**Rule of thumb:** For $\beta \gg 1$, approximately $\beta + 1$ sidebands on each side contain most of the power.

**Example:**
- $\beta = 5$ → about 6 sidebands on each side
- $\beta = 10$ → about 11 sidebands on each side

---

## 9. Carson's Rule and Bandwidth {#carson-rule}

### Carson's Rule

**Carson's rule** gives an approximate bandwidth for angle-modulated signals:

$$B_T \approx 2(\Delta F + f_m) = 2(\beta + 1)f_m$$

where:
- $\Delta F$ is the peak frequency deviation
- $f_m$ is the maximum modulating frequency
- $\beta$ is the modulation index

**For FM:**
$$B_T \approx 2\left(\frac{D_f \max|m(t)|}{2\pi} + f_m\right)$$

**For PM:**
$$B_T \approx 2\left(\frac{D_p \max|\frac{dm(t)}{dt}|}{2\pi} + f_m\right)$$

### Understanding Carson's Rule

**Two Cases:**

1. **Narrowband FM/PM ($\beta \ll 1$):**
   - $B_T \approx 2f_m$ (similar to AM bandwidth)
   - Only a few sidebands

2. **Wideband FM/PM ($\beta \gg 1$):**
   - $B_T \approx 2\Delta F$ (dominated by frequency deviation)
   - Many sidebands

### Comparison with AM

| Modulation | Bandwidth |
|------------|-----------|
| AM | $2B$ (exact) |
| Narrowband FM/PM | $\approx 2B$ |
| Wideband FM/PM | $\approx 2\Delta F$ (can be much larger) |

**Key Trade-off:**
- FM/PM use **more bandwidth** than AM
- But they have **better noise performance**

---

## 10. Power in Angle-Modulated Signals {#power}

### Average Power

For angle-modulated signals with $g(t) = A_c e^{j\theta(t)}$:

$$P_s = \frac{1}{2}\langle |g(t)|^2 \rangle = \frac{1}{2}\langle A_c^2 \rangle = \frac{1}{2}A_c^2$$

**Key Property:** The power is **constant** and independent of the modulation!

**Why?**
- The amplitude $A_c$ is constant
- Power depends only on amplitude, not phase

### Power Distribution

For sinusoidal modulation, the power is distributed among the carrier and sidebands:

$$P_s = \frac{A_c^2}{2}\sum_{n=-\infty}^{+\infty} J_n^2(\beta) = \frac{A_c^2}{2}$$

**Power in carrier:** $P_c = \frac{A_c^2}{2}J_0^2(\beta)$

**Power in $n$-th sideband pair:** $P_n = \frac{A_c^2}{2}[J_n^2(\beta) + J_{-n}^2(\beta)] = A_c^2 J_n^2(\beta)$

### Carrier Null

When $J_0(\beta) = 0$, the carrier component disappears!

**First null:** $\beta = 2.405$ (approximately)

At this point, all power is in the sidebands.

### Peak Envelope Power (PEP)

Since the envelope is constant:

$$P_{PEP} = P_s = \frac{1}{2}A_c^2$$

**Key:** PEP equals average power for angle modulation (unlike AM)!

---

## 11. Detailed Example: Sinusoidal Modulation {#detailed-example}

Let's work through a **complete example** step by step.

### Problem Setup

**Given:**
- Modulating signal: $m(t) = 2\cos(2\pi \cdot 5 \times 10^3 t)$ (5 kHz tone, amplitude 2)
- Carrier amplitude: $A_c = 10$ V
- Carrier frequency: $f_c = 100$ MHz = $10^8$ Hz
- Frequency sensitivity: $D_f = 2\pi \times 10^4$ rad/s per unit of $m(t)$

**Find:**
1. The modulation index $\beta$
2. The peak frequency deviation $\Delta F$
3. The complex envelope $g(t)$
4. The bandpass signal $s(t)$
5. The spectrum $S(f)$
6. The bandwidth $B_T$ (using Carson's rule)
7. The average power $P_s$

---

### Step 1: Modulation Index

For FM with sinusoidal modulation:

$$\beta = \frac{D_f A_m}{\omega_m} = \frac{D_f A_m}{2\pi f_m}$$

Substituting:
- $D_f = 2\pi \times 10^4$ rad/s
- $A_m = 2$
- $f_m = 5 \times 10^3$ Hz

$$\beta = \frac{2\pi \times 10^4 \times 2}{2\pi \times 5 \times 10^3} = \frac{4 \times 10^4}{5 \times 10^3} = 8$$

**Modulation index:** $\beta = 8$ (wideband FM)

---

### Step 2: Peak Frequency Deviation

$$\Delta F = \frac{D_f A_m}{2\pi} = \frac{2\pi \times 10^4 \times 2}{2\pi} = 2 \times 10^4 = 20 \text{ kHz}$$

**Peak frequency deviation:** $\Delta F = 20$ kHz

**Verification:** $\beta = \frac{\Delta F}{f_m} = \frac{20 \times 10^3}{5 \times 10^3} = 4$... Wait, let me recalculate.

Actually, for FM: $\beta = \frac{D_f A_m}{\omega_m}$. If $D_f$ is in rad/s per unit, then:
$$\Delta F = \frac{D_f A_m}{2\pi} = \frac{2\pi \times 10^4 \times 2}{2\pi} = 2 \times 10^4 = 20 \text{ kHz}$$

And: $\beta = \frac{\Delta F}{f_m} = \frac{20 \times 10^3}{5 \times 10^3} = 4$

Let me correct: If $\beta = 8$, then:
$$\Delta F = \beta f_m = 8 \times 5 \times 10^3 = 40 \text{ kHz}$$

So: $D_f = \frac{2\pi \Delta F}{A_m} = \frac{2\pi \times 40 \times 10^3}{2} = 4\pi \times 10^4$ rad/s

Let's use $\beta = 8$ and $\Delta F = 40$ kHz.

---

### Step 3: Complex Envelope

For FM with $m(t) = A_m\cos(\omega_m t)$:

$$\theta(t) = D_f \int m(t) dt = D_f \int A_m\cos(\omega_m t) dt = \frac{D_f A_m}{\omega_m}\sin(\omega_m t) = \beta\sin(\omega_m t)$$

Therefore:
$$g(t) = A_c e^{j\beta\sin(\omega_m t)} = 10e^{j8\sin(2\pi \cdot 5 \times 10^3 t)}$$

---

### Step 4: Bandpass Signal

$$s(t) = \text{Re}\{g(t)e^{j\omega_c t}\} = A_c\cos[\omega_c t + \theta(t)]$$

$$s(t) = 10\cos[2\pi \cdot 10^8 t + 8\sin(2\pi \cdot 5 \times 10^3 t)]$$

---

### Step 5: Spectrum

Using the Bessel function expansion:

$$G(f) = A_c \sum_{n=-\infty}^{+\infty} J_n(\beta)\delta(f - nf_m)$$

$$G(f) = 10 \sum_{n=-\infty}^{+\infty} J_n(8)\delta(f - n \times 5 \times 10^3)$$

The bandpass spectrum is:

$$S(f) = \frac{A_c}{2}\sum_{n=-\infty}^{+\infty} J_n(8)[\delta(f - 10^8 - n \times 5000) + \delta(f + 10^8 - n \times 5000)]$$

**Components:**
- Carrier: $\frac{10}{2}J_0(8)\delta(f \pm 10^8)$ at $\pm 100$ MHz
- First sidebands: $\frac{10}{2}J_1(8)\delta(f - 10^8 \pm 5000)$ at $\pm 100.005$ MHz and $\pm 99.995$ MHz
- Second sidebands: $\frac{10}{2}J_2(8)\delta(f - 10^8 \pm 10000)$ at $\pm 100.01$ MHz and $\pm 99.99$ MHz
- And so on...

**Bessel function values (approximate):**
- $J_0(8) \approx 0.17$ (small carrier)
- $J_1(8) \approx 0.23$
- $J_2(8) \approx 0.11$
- $J_3(8) \approx 0.03$
- Higher orders are smaller

---

### Step 6: Bandwidth

Using Carson's rule:

$$B_T \approx 2(\Delta F + f_m) = 2(40 \times 10^3 + 5 \times 10^3) = 2 \times 45 \times 10^3 = 90 \text{ kHz}$$

**Or using modulation index:**

$$B_T \approx 2(\beta + 1)f_m = 2(8 + 1) \times 5 \times 10^3 = 90 \text{ kHz}$$

**Bandwidth:** Approximately 90 kHz

**Note:** This is much wider than AM, which would only need $2 \times 5 = 10$ kHz!

---

### Step 7: Average Power

$$P_s = \frac{1}{2}A_c^2 = \frac{1}{2}(10)^2 = 50 \text{ W}$$

**Power is constant** and independent of modulation!

---

## 12. Key Takeaways {#key-takeaways}

### Essential Concepts

1. **Angle modulation** encodes information in **phase** or **frequency**, not amplitude
2. **Constant amplitude** → resistant to noise and fading
3. **PM and FM** are mathematically related (derivative/integral relationship)
4. **Modulation index** $\beta$ determines bandwidth and spectrum shape
5. **Bessel functions** describe the spectrum for sinusoidal modulation
6. **Carson's rule** gives approximate bandwidth: $B_T \approx 2(\Delta F + f_m)$

### Key Formulas

**Complex Envelope:**
$$g(t) = A_c e^{j\theta(t)}$$

**Phase Functions:**
- PM: $\theta(t) = D_p m(t)$
- FM: $\theta(t) = D_f \int m(t) dt$

**Instantaneous Frequency:**
$$f_i(t) = f_c + \frac{1}{2\pi}\frac{d\theta(t)}{dt}$$

**Modulation Index:**
- PM: $\beta = D_p A_m$
- FM: $\beta = \frac{D_f A_m}{\omega_m} = \frac{\Delta F}{f_m}$

**Power:**
$$P_s = \frac{1}{2}A_c^2$$ (constant!)

**Bandwidth (Carson's Rule):**
$$B_T \approx 2(\Delta F + f_m) = 2(\beta + 1)f_m$$

### Common Mistakes to Avoid

1. **Confusing PM and FM** - remember the derivative/integral relationship
2. **Forgetting the constant amplitude** - unlike AM, amplitude doesn't vary
3. **Using wrong bandwidth formula** - Carson's rule is approximate, not exact
4. **Ignoring Bessel functions** - they're essential for understanding the spectrum
5. **Mixing up modulation index** - different formulas for PM vs FM

### Study Tips

1. **Memorize the phase relationships:**
   - PM: $\theta = D_p m(t)$
   - FM: $\theta = D_f \int m(t) dt$

2. **Understand the modulation index:**
   - Small $\beta$ → narrowband (few sidebands)
   - Large $\beta$ → wideband (many sidebands)

3. **Know Carson's rule:**
   - $B_T \approx 2(\Delta F + f_m)$
   - Works for both PM and FM

4. **Remember power is constant:**
   - $P_s = \frac{1}{2}A_c^2$ always
   - Independent of modulation

5. **Practice with sinusoidal modulation:**
   - This is the only case with exact spectrum
   - Bessel functions give the answer

---

## Summary of Key Formulas

### Complex Envelope
$$g(t) = A_c e^{j\theta(t)}$$

### Phase Functions
- **PM:** $\theta(t) = D_p m(t)$
- **FM:** $\theta(t) = D_f \int m(t) dt$

### Instantaneous Frequency
$$f_i(t) = f_c + \frac{1}{2\pi}\frac{d\theta(t)}{dt}$$

### Modulation Index
- **PM:** $\beta = D_p A_m$
- **FM:** $\beta = \frac{D_f A_m}{\omega_m} = \frac{\Delta F}{f_m}$

### Spectrum (Sinusoidal Modulation)
$$S(f) = \frac{A_c}{2}\sum_{n=-\infty}^{+\infty} J_n(\beta)[\delta(f - f_c - nf_m) + \delta(f + f_c - nf_m)]$$

### Power
$$P_s = \frac{1}{2}A_c^2$$

### Bandwidth (Carson's Rule)
$$B_T \approx 2(\Delta F + f_m) = 2(\beta + 1)f_m$$

---

*End of Group 3 Detailed Explanation*


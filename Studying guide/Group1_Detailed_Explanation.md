# GROUP 1 - Foundations of Modulation: Detailed Explanation

## Lecture 13: Bandpass Signals

---

## Table of Contents

1. [Introduction: Why Do We Need This?](#introduction)
2. [Complex Envelope Representation - The Core Concept](#complex-envelope)
3. [Three Equivalent Representations](#three-representations)
4. [Modulation Process Explained](#modulation-process)
5. [Spectrum of Bandpass Signals](#spectrum)
6. [Power Spectral Density (PSD)](#psd)
7. [Power Calculations](#power)
8. [Detailed Example: Amplitude-Modulated Signal](#detailed-example)
9. [Key Takeaways](#key-takeaways)

---

## 1. Introduction: Why Do We Need This? {#introduction}

### The Problem

Imagine you want to send music (audio signal) through the air. The audio signal has frequencies from 20 Hz to 20 kHz - these are **baseband** (low frequency) signals. However, to transmit through the air efficiently, we need to use **high frequencies** (like radio frequencies in MHz or GHz range).

**Why?**
- Low frequencies don't travel well through air
- We need high frequencies for efficient transmission
- Multiple signals can share the airwaves by using different carrier frequencies

### The Solution: Complex Envelope Representation

Instead of working directly with high-frequency signals (which is mathematically complex and computationally expensive), we can:

1. **Work with the "envelope"** - the low-frequency information signal
2. **Shift it to high frequency** when we need to transmit
3. **Process everything at baseband** (0 to B Hz) instead of around $f_c$ (carrier frequency)

**Analogy:** Think of it like mailing a letter:
- The **letter** (message $m(t)$) = your information
- The **envelope** ($g(t)$) = how you package it
- The **carrier** ($e^{j\omega_c t}$) = the postal service that delivers it
- The **final signal** ($v(t)$) = the delivered package

---

## 2. Complex Envelope Representation - The Core Concept {#complex-envelope}

### The Fundamental Theorem

**Any physical bandpass waveform centered around $\pm f_c$ can be represented as:**

$$v(t) = \text{Re}\{g(t)e^{j\omega_c t}\}$$

### Breaking Down the Formula

Let's understand each component:

#### $v(t)$ - The Bandpass Signal
- This is the **actual signal** we transmit or receive
- It's **real-valued** (we can measure it with physical instruments)
- It oscillates at **high frequency** (around $f_c$)
- Example: Radio signal at 101.5 MHz

#### $g(t)$ - The Complex Envelope
- This is the **baseband signal** containing our information
- It's **complex-valued** (has real and imaginary parts)
- It oscillates at **low frequency** (0 to B Hz, where B is the bandwidth)
- This is what we actually process and manipulate

#### $e^{j\omega_c t}$ - The Carrier
- This is the **high-frequency carrier wave**
- $\omega_c = 2\pi f_c$ is the carrier frequency in radians/second
- $f_c$ is the carrier frequency in Hz
- This "carries" our information to high frequencies

#### $\text{Re}\{\cdot\}$ - Taking the Real Part
- Since $g(t)$ is complex and $e^{j\omega_c t}$ is complex, their product is complex
- But physical signals must be real, so we take the **real part**
- This extracts the actual signal we can transmit

### Why "Complex" Envelope?

The envelope is complex because it has two components:
- **Real part** $x(t)$ - in-phase component
- **Imaginary part** $y(t)$ - quadrature component (90° out of phase)

Together, they can represent **any** type of modulation (AM, FM, PM, etc.)

---

## 3. Three Equivalent Representations {#three-representations}

The complex envelope $g(t)$ can be written in three different but **equivalent** ways. Each is useful for different purposes.

### Representation 1: Complex Form (Rectangular)

$$g(t) = x(t) + jy(t)$$

This gives us the bandpass signal as:

$$v(t) = x(t)\cos(\omega_c t) - y(t)\sin(\omega_c t)$$

**What This Means:**
- $x(t)$ = **in-phase component** - modulates the cosine wave
- $y(t)$ = **quadrature component** - modulates the sine wave (90° out of phase)
- The cosine and sine are **orthogonal** (perpendicular), so they don't interfere
- Together, they can represent **any** modulation scheme!

**When to Use:**
- Digital signal processing
- Software-defined radio
- When you need to separate I and Q components

**Example:**
If $x(t) = A_c[1 + m(t)]$ and $y(t) = 0$, we get:
$$v(t) = A_c[1 + m(t)]\cos(\omega_c t)$$
This is **Amplitude Modulation (AM)**!

---

### Representation 2: Polar Form

$$g(t) = R(t)e^{j\theta(t)}$$

This gives us:

$$v(t) = R(t)\cos[\omega_c t + \theta(t)]$$

**What This Means:**
- $R(t)$ = **amplitude modulation** - controls how "loud" the signal is
- $\theta(t)$ = **phase modulation** - controls the phase/angle of the signal
- This is the most **intuitive** form - amplitude and phase!

**When to Use:**
- Understanding modulation concepts
- Analyzing amplitude and phase separately
- When working with angle modulation (FM/PM)

**Example:**
- If $R(t)$ varies and $\theta(t) = 0$ → **Amplitude Modulation**
- If $R(t)$ is constant and $\theta(t)$ varies → **Phase/Frequency Modulation**

---

### Representation 3: Magnitude-Phase Form

$$g(t) = |g(t)|e^{j\arg[g(t)]} = R(t)e^{j\theta(t)}$$

This is just another way to write the polar form, emphasizing:
- $|g(t)| = R(t)$ = magnitude (always positive)
- $\arg[g(t)] = \theta(t)$ = phase angle

### Key Relationships Between Representations

**From Complex to Polar:**
- $R(t) = |g(t)| = \sqrt{x^2(t) + y^2(t)}$ (magnitude)
- $\theta(t) = \arg[g(t)] = \tan^{-1}\left(\frac{y(t)}{x(t)}\right)$ (phase)

**From Polar to Complex:**
- $x(t) = R(t)\cos[\theta(t)]$ (in-phase from polar)
- $y(t) = R(t)\sin[\theta(t)]$ (quadrature from polar)

### Important Properties Summary

| Signal | Type | Frequency Range |
|--------|------|----------------|
| $v(t)$ (bandpass) | **Real** | High (around $f_c$) |
| $g(t)$ (complex envelope) | **Complex** | Low (0 to B Hz) |
| $x(t)$, $y(t)$ | **Real** | Low (0 to B Hz) |
| $R(t)$, $\theta(t)$ | **Real** | Low (0 to B Hz) |

**Key Insight:** All the information is in the low-frequency components ($g(t)$, $x(t)$, $y(t)$, $R(t)$, $\theta(t)$). The carrier $e^{j\omega_c t}$ just shifts it to high frequency for transmission!

---

## 4. Modulation Process Explained {#modulation-process}

### What is Modulation?

**Modulation** is the process of encoding information $m(t)$ (the message) into a bandpass signal $s(t)$ (the transmitted signal).

### The Modulation Process (Step by Step)

**Step 1:** Start with information signal $m(t)$
- This is your **message** (voice, music, data, etc.)
- It's **baseband** (low frequency, 0 to B Hz)
- Example: Audio signal from 20 Hz to 20 kHz

**Step 2:** Create complex envelope $g(t) = g[m(t)]$
- This is a **mapping function** that encodes $m(t)$ into $g(t)$
- The mapping depends on the **type of modulation** you want
- Example: For AM, $g(t) = A_c[1 + m(t)]$

**Step 3:** Generate bandpass signal $s(t) = \text{Re}\{g(t)e^{j\omega_c t}\}$
- Multiply the envelope by the carrier
- Take the real part
- Result: High-frequency signal ready for transmission!

### Example: Amplitude Modulation (AM)

For **Amplitude Modulation**, the mapping is simple:

$$g(t) = A_c[1 + m(t)]$$

where:
- $A_c > 0$ is a constant (carrier amplitude)
- We require $m(t) \geq -1$ to keep $g(t) \geq 0$

**What This Means:**
- $R(t) = A_c[1 + m(t)]$ (amplitude varies with message)
- $\theta(t) = 0$ (no phase modulation)
- Information is **only** in the amplitude!

**The resulting bandpass signal:**
$$s(t) = \text{Re}\{A_c[1 + m(t)]e^{j\omega_c t}\} = A_c[1 + m(t)]\cos(\omega_c t)$$

### Why This Mapping?

The mapping $g[m]$ must satisfy four important criteria:

1. **Easy to implement** - simple circuits (multipliers, adders)
2. **Good spectral properties** - efficient bandwidth use
3. **Invertible** - receiver can recover $m(t)$ from $g(t)$ uniquely
4. **Noise resistant** - minimizes the effects of noise

Different modulation schemes (AM, FM, PM, etc.) use different mappings, each optimized for different trade-offs!

---

## 5. Spectrum of Bandpass Signals {#spectrum}

### The Spectrum Theorem

**If $v(t) = \text{Re}\{g(t)e^{j\omega_c t}\}$, then the spectrum is:**

$$V(f) = \frac{1}{2}[G(f - f_c) + G^*(-f - f_c)]$$

### Understanding This Formula

**What This Means:**
- The spectrum of $v(t)$ is the spectrum of $g(t)$ **shifted** to $\pm f_c$
- $G(f - f_c)$ = spectrum shifted to the **right** (positive frequencies around $f_c$)
- $G^*(-f - f_c)$ = complex conjugate, shifted to the **left** (negative frequencies around $-f_c$)
- The $\frac{1}{2}$ factor comes from taking the real part

**Visual Representation:**
```
Baseband spectrum G(f):        [----g(t)----]
                              0    B

Bandpass spectrum V(f):   [----]        [----]
                         -fc            +fc
```

### Special Case: Real $g(t)$

If $g(t)$ is real (like in AM), then $G^*(f) = G(-f)$, and:

$$V(f) = \frac{1}{2}[G(f - f_c) + G(f + f_c)]$$

The spectrum is **symmetric** around $\pm f_c$!

### Proof (Simplified)

We can write:
$$v(t) = \text{Re}\{g(t)e^{j\omega_c t}\} = \frac{1}{2}g(t)e^{j\omega_c t} + \frac{1}{2}g^*(t)e^{-j\omega_c t}$$

Taking Fourier transform and using the **frequency shifting property**:
- $g(t)e^{j\omega_c t} \rightarrow G(f - f_c)$ (shift right by $f_c$)
- $g^*(t)e^{-j\omega_c t} \rightarrow G^*(-f - f_c)$ (shift left by $f_c$, with conjugation)

**Key Insight:** The spectrum is just the baseband spectrum, copied and shifted to $\pm f_c$!

---

## 6. Power Spectral Density (PSD) {#psd}

### The PSD Theorem

**If $v(t) = \text{Re}\{g(t)e^{j\omega_c t}\}$, then:**

$$P_v(f) = \frac{1}{4}[P_g(f - f_c) + P_g(-f - f_c)]$$

where $P_g(f)$ is the PSD of $g(t)$.

### Understanding PSD

**Power Spectral Density (PSD)** tells us how power is distributed across frequencies.

**Key Points:**
- PSD of bandpass signal = PSD of envelope, shifted to $\pm f_c$
- The $\frac{1}{4}$ factor (instead of $\frac{1}{2}$) accounts for power distribution
- If $g(t)$ is real: $P_v(f) = \frac{1}{4}[P_g(f - f_c) + P_g(f + f_c)]$

**Why $\frac{1}{4}$ instead of $\frac{1}{2}$?**
- When we take $\text{Re}\{\cdot\}$, we're using "half" the complex signal
- Power is proportional to the square of amplitude
- So: $(\frac{1}{2})^2 = \frac{1}{4}$

### Autocorrelation Function

The autocorrelation function of $v(t)$ is:

$$R_v(\tau) = \frac{1}{2}\text{Re}\{R_g(\tau)e^{j\omega_c \tau}\}$$

where $R_g(\tau)$ is the autocorrelation of $g(t)$.

The PSD is the Fourier transform of the autocorrelation:
$$P_v(f) = \mathcal{F}[R_v(\tau)]$$

---

## 7. Power Calculations {#power}

### Average Power

The average power of a bandpass signal can be calculated in **three equivalent ways**:

$$P_v = \langle v^2(t) \rangle = \int_{-\infty}^{+\infty} P_v(f)df = R_v(0) = \frac{1}{2}\langle |g(t)|^2 \rangle$$

### Understanding Each Term

1. **$\langle v^2(t) \rangle$** = time average of squared signal
   - Square the signal, then average over time
   - Direct measurement approach

2. **$\int P_v(f)df$** = total power from frequency domain
   - Integrate the PSD over all frequencies
   - Frequency domain approach

3. **$R_v(0)$** = autocorrelation at zero delay
   - Autocorrelation at $\tau = 0$ gives total power
   - Statistical approach

4. **$\frac{1}{2}\langle |g(t)|^2 \rangle$** = **half** the average power of the envelope
   - This is the **most useful** formula!
   - Work with the envelope, then divide by 2

### Why the $\frac{1}{2}$ Factor?

When we take $\text{Re}\{g(t)e^{j\omega_c t}\}$, we're only using "half" the complex signal, so we get half the power.

**Mathematical Explanation:**
- $|g(t)e^{j\omega_c t}|^2 = |g(t)|^2$ (magnitude of product = product of magnitudes)
- But $\text{Re}\{g(t)e^{j\omega_c t}\}$ has half the power of the full complex signal
- Hence: $P_v = \frac{1}{2}\langle |g(t)|^2 \rangle$

### Peak Envelope Power (PEP)

**PEP** is the power if the envelope stayed at its maximum:

$$P_{PEP} = \frac{1}{2}[\max|g(t)|]^2$$

**Why This Matters:**
- Transmitters must be designed to handle the **peak power**
- PEP determines the required transmitter power rating
- Important for system design!

**Example:**
If $\max|g(t)| = 2A_c$, then:
$$P_{PEP} = \frac{1}{2}(2A_c)^2 = 2A_c^2$$

---

## 8. Detailed Example: Amplitude-Modulated Signal {#detailed-example}

Let's work through a **complete example** step by step.

### Problem Setup

**Given:**
- Information message: $m(t) = 0.5\cos(2\pi \cdot 1000t)$ (1 kHz tone, 50% modulation)
- Carrier amplitude: $A_c = 1$ V
- Carrier frequency: $f_c = 1$ MHz = $10^6$ Hz
- Bandwidth of $m(t)$: $B = 1$ kHz

**Find:**
1. The complex envelope $g(t)$
2. The bandpass signal $s(t)$
3. The spectrum $S(f)$
4. The average power $P_s$
5. The peak envelope power $P_{PEP}$

---

### Step 1: Find the Complex Envelope $g(t)$

For AM, the complex envelope is:
$$g(t) = A_c[1 + m(t)]$$

Substituting values:
$$g(t) = 1 \cdot [1 + 0.5\cos(2\pi \cdot 1000t)]$$
$$g(t) = 1 + 0.5\cos(2\pi \cdot 1000t)$$

**What This Means:**
- DC component: $1$ (the carrier)
- AC component: $0.5\cos(2\pi \cdot 1000t)$ (the message)
- The envelope varies between $0.5$ and $1.5$ (50% modulation)

**In Polar Form:**
- $R(t) = |g(t)| = 1 + 0.5\cos(2\pi \cdot 1000t)$ (since it's always positive)
- $\theta(t) = 0$ (no phase modulation)

---

### Step 2: Find the Bandpass Signal $s(t)$

The bandpass signal is:
$$s(t) = \text{Re}\{g(t)e^{j\omega_c t}\}$$

Since $g(t)$ is real:
$$s(t) = g(t)\cos(\omega_c t)$$

Substituting:
$$s(t) = [1 + 0.5\cos(2\pi \cdot 1000t)]\cos(2\pi \cdot 10^6 t)$$

**Expanding using trigonometric identity:**
$$\cos(A)\cos(B) = \frac{1}{2}[\cos(A+B) + \cos(A-B)]$$

$$s(t) = \cos(2\pi \cdot 10^6 t) + 0.5\cos(2\pi \cdot 1000t)\cos(2\pi \cdot 10^6 t)$$

$$s(t) = \cos(2\pi \cdot 10^6 t) + \frac{0.5}{2}[\cos(2\pi(10^6 + 1000)t) + \cos(2\pi(10^6 - 1000)t)]$$

$$s(t) = \cos(2\pi \cdot 10^6 t) + 0.25\cos(2\pi \cdot 1,001,000t) + 0.25\cos(2\pi \cdot 999,000t)$$

**What This Means:**
- **Carrier component:** $\cos(2\pi \cdot 10^6 t)$ at 1 MHz
- **Upper sideband:** $0.25\cos(2\pi \cdot 1,001,000t)$ at 1.001 MHz
- **Lower sideband:** $0.25\cos(2\pi \cdot 999,000t)$ at 0.999 MHz

---

### Step 3: Find the Spectrum $S(f)$

**Method 1: Using the Spectrum Theorem**

First, find $G(f)$ (spectrum of $g(t)$):

$$g(t) = 1 + 0.5\cos(2\pi \cdot 1000t)$$

Using Fourier transform properties:
- $\mathcal{F}[1] = \delta(f)$ (DC component)
- $\mathcal{F}[\cos(2\pi f_0 t)] = \frac{1}{2}[\delta(f - f_0) + \delta(f + f_0)]$

$$G(f) = \delta(f) + 0.5 \cdot \frac{1}{2}[\delta(f - 1000) + \delta(f + 1000)]$$

$$G(f) = \delta(f) + 0.25\delta(f - 1000) + 0.25\delta(f + 1000)$$

Now, using the spectrum theorem:
$$S(f) = \frac{1}{2}[G(f - f_c) + G^*(-f - f_c)]$$

Since $g(t)$ is real, $G^*(f) = G(-f)$:
$$S(f) = \frac{1}{2}[G(f - f_c) + G(f + f_c)]$$

Substituting $G(f)$:
$$S(f) = \frac{1}{2}[\delta(f - f_c) + 0.25\delta(f - f_c - 1000) + 0.25\delta(f - f_c + 1000) + \delta(f + f_c) + 0.25\delta(f + f_c - 1000) + 0.25\delta(f + f_c + 1000)]$$

With $f_c = 10^6$:
$$S(f) = \frac{1}{2}[\delta(f - 10^6) + 0.25\delta(f - 1,001,000) + 0.25\delta(f - 999,000) + \delta(f + 10^6) + 0.25\delta(f + 1,001,000) + 0.25\delta(f + 999,000)]$$

**What This Means:**
- **Carrier:** $\frac{1}{2}\delta(f - 10^6)$ and $\frac{1}{2}\delta(f + 10^6)$ at $\pm 1$ MHz
- **Upper sideband:** $\frac{0.25}{2}\delta(f - 1,001,000)$ and $\frac{0.25}{2}\delta(f + 1,001,000)$ at $\pm 1.001$ MHz
- **Lower sideband:** $\frac{0.25}{2}\delta(f - 999,000)$ and $\frac{0.25}{2}\delta(f + 999,000)$ at $\pm 0.999$ MHz

**Bandwidth:** $2B = 2 \times 1000 = 2000$ Hz (from 999 kHz to 1001 kHz)

---

### Step 4: Calculate Average Power $P_s$

**Method 1: Using the envelope formula**

$$P_s = \frac{1}{2}\langle |g(t)|^2 \rangle$$

Since $g(t)$ is real: $|g(t)|^2 = g^2(t)$

$$g^2(t) = [1 + 0.5\cos(2\pi \cdot 1000t)]^2$$

$$g^2(t) = 1 + 2 \cdot 0.5\cos(2\pi \cdot 1000t) + [0.5\cos(2\pi \cdot 1000t)]^2$$

$$g^2(t) = 1 + \cos(2\pi \cdot 1000t) + 0.25\cos^2(2\pi \cdot 1000t)$$

Using identity: $\cos^2(\theta) = \frac{1 + \cos(2\theta)}{2}$

$$g^2(t) = 1 + \cos(2\pi \cdot 1000t) + 0.25 \cdot \frac{1 + \cos(4\pi \cdot 1000t)}{2}$$

$$g^2(t) = 1 + \cos(2\pi \cdot 1000t) + 0.125 + 0.125\cos(4\pi \cdot 1000t)$$

$$g^2(t) = 1.125 + \cos(2\pi \cdot 1000t) + 0.125\cos(4\pi \cdot 1000t)$$

Taking time average:
- $\langle 1.125 \rangle = 1.125$ (DC term)
- $\langle \cos(2\pi \cdot 1000t) \rangle = 0$ (average of cosine = 0)
- $\langle 0.125\cos(4\pi \cdot 1000t) \rangle = 0$ (average of cosine = 0)

Therefore:
$$\langle g^2(t) \rangle = 1.125$$

**Average Power:**
$$P_s = \frac{1}{2} \times 1.125 = 0.5625 \text{ W}$$

**Power Breakdown:**
- **Carrier power:** $P_c = \frac{1}{2}A_c^2 = \frac{1}{2}(1)^2 = 0.5$ W
- **Sideband power:** $P_{SB} = P_s - P_c = 0.5625 - 0.5 = 0.0625$ W
- **Total power:** $P_s = 0.5625$ W

**Modulation Efficiency:**
$$\eta = \frac{P_{SB}}{P_s} = \frac{0.0625}{0.5625} = 0.111 = 11.1\%$$

Only 11.1% of the power carries information! (This is why DSB-SC and SSB are more efficient)

---

### Step 5: Calculate Peak Envelope Power (PEP)

**Find $\max|g(t)|$:**

$$g(t) = 1 + 0.5\cos(2\pi \cdot 1000t)$$

The maximum occurs when $\cos(2\pi \cdot 1000t) = 1$:
$$\max|g(t)| = 1 + 0.5(1) = 1.5 \text{ V}$$

**Peak Envelope Power:**
$$P_{PEP} = \frac{1}{2}[\max|g(t)|]^2 = \frac{1}{2}(1.5)^2 = \frac{1}{2} \times 2.25 = 1.125 \text{ W}$$

**What This Means:**
- The transmitter must handle **1.125 W** at peak
- Average power is **0.5625 W**
- Peak-to-average ratio: $\frac{1.125}{0.5625} = 2$ (or 3 dB)

---

## 9. Key Takeaways {#key-takeaways}

### Essential Concepts

1. **Complex envelope** allows us to work with baseband signals (0 to B Hz) instead of high-frequency bandpass signals (around $f_c$)

2. **Three representations** are equivalent:
   - Complex: $g(t) = x(t) + jy(t)$
   - Polar: $g(t) = R(t)e^{j\theta(t)}$
   - Magnitude-phase: $g(t) = |g(t)|e^{j\arg[g(t)]}$

3. **Spectrum** of bandpass signal = envelope spectrum shifted to $\pm f_c$:
   $$V(f) = \frac{1}{2}[G(f - f_c) + G^*(-f - f_c)]$$

4. **Power** = half the average power of the envelope magnitude squared:
   $$P_v = \frac{1}{2}\langle |g(t)|^2 \rangle$$

5. **Modulation** maps information $m(t)$ to complex envelope $g(t)$, which is then shifted to carrier frequency

### Common Mistakes to Avoid

1. **Forgetting the $\frac{1}{2}$ factor** in power calculations
2. **Confusing $g(t)$ (complex) with $v(t)$ (real)**
3. **Not accounting for the $\frac{1}{2}$ or $\frac{1}{4}$ factors** in spectrum/PSD formulas
4. **Mixing up frequency and angular frequency** ($f$ vs $\omega = 2\pi f$)

### Study Tips

1. **Visualize** the spectrum shifting from baseband to bandpass
2. **Practice** converting between the three representations
3. **Work through examples** step by step
4. **Remember** the physical meaning: envelope = information, carrier = transmission frequency

---

## Summary of Key Formulas

### Core Representation
$$v(t) = \text{Re}\{g(t)e^{j\omega_c t}\}$$

### Three Forms
1. $v(t) = x(t)\cos(\omega_c t) - y(t)\sin(\omega_c t)$
2. $v(t) = R(t)\cos[\omega_c t + \theta(t)]$
3. $g(t) = x(t) + jy(t) = R(t)e^{j\theta(t)}$

### Spectrum
$$V(f) = \frac{1}{2}[G(f - f_c) + G^*(-f - f_c)]$$

### Power
$$P_v = \frac{1}{2}\langle |g(t)|^2 \rangle$$

### Peak Envelope Power
$$P_{PEP} = \frac{1}{2}[\max|g(t)|]^2$$

---

*End of Group 1 Detailed Explanation*


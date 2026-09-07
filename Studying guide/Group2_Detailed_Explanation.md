# GROUP 2 - Analog Modulation (Amplitude-based): Detailed Explanation

## Lectures 15 & 17: Amplitude Modulation and Detector Circuits

---

## Table of Contents

1. [Introduction: What is Amplitude Modulation?](#introduction)
2. [Standard AM (Double-Sideband with Carrier)](#standard-am)
3. [DSB-SC (Double-Sideband Suppressed Carrier)](#dsb-sc)
4. [SSB-AM (Single-Sideband AM)](#ssb-am)
5. [Spectrum Analysis of AM Signals](#spectrum-analysis)
6. [Power Calculations for AM](#power-calculations)
7. [Modulation Index and Efficiency](#modulation-index)
8. [Envelope Detector](#envelope-detector)
9. [Product Detector](#product-detector)
10. [Detailed Examples](#detailed-examples)
11. [Key Takeaways](#key-takeaways)

---

## 1. Introduction: What is Amplitude Modulation? {#introduction}

### The Basic Idea

**Amplitude Modulation (AM)** is the process of varying the **amplitude** of a high-frequency carrier signal in proportion to a low-frequency information signal (the message).

**Why Amplitude Modulation?**
- Simple to implement (just a multiplier circuit)
- Easy to demodulate (can use simple envelope detector)
- Widely used in AM radio broadcasting
- Good for analog voice transmission

### The Modulation Process

**Step 1:** Start with information signal $m(t)$
- Baseband signal (0 to B Hz)
- Contains the information we want to transmit
- Example: Audio signal from microphone

**Step 2:** Create modulated signal $s(t)$
- Multiply $m(t)$ (or a function of it) with carrier $\cos(\omega_c t)$
- Result: High-frequency signal ready for transmission

**Step 3:** Transmit through channel
- Signal travels through air (radio) or cable
- Receiver picks up the signal

**Step 4:** Demodulate to recover $m(t)$
- Extract the original information signal
- Use detector circuit (envelope or product detector)

### Types of Amplitude Modulation

There are **three main types** of AM:

1. **Standard AM (DSB-FC)** - Double-Sideband Full Carrier
   - Contains carrier + both sidebands
   - Easiest to demodulate
   - Least power efficient

2. **DSB-SC** - Double-Sideband Suppressed Carrier
   - No carrier, both sidebands present
   - More power efficient
   - Requires product detector

3. **SSB-AM** - Single-Sideband AM
   - No carrier, only one sideband
   - Most power and bandwidth efficient
   - Most complex to generate and demodulate

---

## 2. Standard AM (Double-Sideband with Carrier) {#standard-am}

### The Complex Envelope

For **standard AM**, the complex envelope is:

$$g(t) = A_c[1 + m(t)]$$

where:
- $A_c > 0$ is the **carrier amplitude** (constant)
- $m(t)$ is the **modulating signal** (information)
- We require $m(t) \geq -1$ to ensure $g(t) \geq 0$

### The Modulated Signal

The bandpass signal is:

$$s(t) = \text{Re}\{g(t)e^{j\omega_c t}\} = A_c[1 + m(t)]\cos(\omega_c t)$$

**Breaking Down the Formula:**
- $A_c\cos(\omega_c t)$ = **carrier component** (constant amplitude)
- $A_c m(t)\cos(\omega_c t)$ = **sideband components** (varying amplitude)
- The amplitude varies as $A_c[1 + m(t)]$

### Real Envelope

Since $g(t)$ is real and positive:

$$R(t) = |g(t)| = A_c[1 + m(t)]$$

**Key Property:** The real envelope **directly contains** the information signal $m(t)$!

### In-Phase and Quadrature Components

For standard AM:
- **In-phase component:** $x(t) = A_c[1 + m(t)]$
- **Quadrature component:** $y(t) = 0$ (no quadrature component)
- **Phase:** $\theta(t) = 0$ (no phase modulation)

**Why?** All information is in the **amplitude**, not the phase!

### Physical Interpretation

**Visual Example:**
```
Message m(t):     ___/‾‾‾\___/‾‾‾\___
                  
Carrier:          ~~~~~~~~~~~~~~~~~~~~
                  
AM Signal:        ___/‾‾‾\___/‾‾‾\___
                 ~~~~~~~~~~~~~~~~~~~~
                 (amplitude follows m(t))
```

The **envelope** (the outline) of the AM signal follows the shape of $m(t)$!

### Requirements for Undistorted AM

For the envelope to accurately represent $m(t)$, we need:

1. **$m(t) \geq -1$** (to keep $g(t) \geq 0$)
2. **$|m(t)| < 1$** (for proper envelope detection)

If $m(t) < -1$, then $g(t) < 0$, which causes **overmodulation** and distortion!

---

## 3. DSB-SC (Double-Sideband Suppressed Carrier) {#dsb-sc}

### The Complex Envelope

For **DSB-SC**, the complex envelope is simply:

$$g(t) = A_c m(t)$$

**Key Difference:** No "1 +" term! The carrier is **suppressed** (removed).

### The Modulated Signal

$$s(t) = A_c m(t)\cos(\omega_c t)$$

**What This Means:**
- **No carrier component** - only sidebands
- The amplitude varies as $A_c|m(t)|$
- More **power efficient** than standard AM

### Real Envelope

$$R(t) = |g(t)| = A_c|m(t)|$$

**Important:** The envelope is $|m(t)|$, not $m(t)$ itself!

**Problem:** If $m(t)$ changes sign, the envelope detector will give $|m(t)|$, which loses the sign information!

**Solution:** Use a **product detector** instead of envelope detector.

### Why Suppress the Carrier?

**Advantages:**
1. **Power Efficiency:** All power goes to sidebands (which contain information)
2. **No Carrier Waste:** In standard AM, carrier power doesn't carry information
3. **Better SNR:** More power available for information

**Disadvantages:**
1. **More Complex Demodulation:** Requires product detector (synchronized oscillator)
2. **Synchronization Required:** Need to know exact carrier frequency and phase

### Comparison: Standard AM vs DSB-SC

| Feature | Standard AM | DSB-SC |
|---------|-------------|--------|
| Complex Envelope | $A_c[1 + m(t)]$ | $A_c m(t)$ |
| Carrier Present? | Yes | No |
| Demodulation | Envelope detector | Product detector |
| Power Efficiency | Low (~33% max) | High (100%) |
| Complexity | Simple | Moderate |

---

## 4. SSB-AM (Single-Sideband AM) {#ssb-am}

### The Concept

**Single-Sideband AM** uses only **one sideband** (upper or lower), eliminating:
- The carrier (like DSB-SC)
- One of the sidebands (bandwidth savings!)

**Why?** Both sidebands contain the **same information** (they're mirror images), so we only need one!

### Complex Envelope for USSB-AM

For **Upper Single-Sideband (USSB-AM)**:

$$g(t) = A_c[m(t) + j\hat{m}(t)]$$

where $\hat{m}(t)$ is the **Hilbert transform** of $m(t)$.

### Hilbert Transform

The Hilbert transform $\hat{m}(t)$ is defined as:

$$\hat{m}(t) = m(t) * h(t) = m(t) * \frac{1}{\pi t}$$

In frequency domain:

$$H(f) = \mathcal{F}[h(t)] = \begin{cases}
-j, & f > 0 \\
+j, & f < 0
\end{cases}$$

**What It Does:**
- Applies a **-90° phase shift** to positive frequencies
- Applies a **+90° phase shift** to negative frequencies
- Creates a **quadrature component** that cancels one sideband

### Frequency Domain Representation

The spectrum of the complex envelope is:

$$G(f) = A_c[M(f) + j\mathcal{F}[\hat{m}(t)]] = A_c M(f)[1 + jH(f)]$$

This simplifies to:

$$G(f) = \begin{cases}
2A_c M(f), & f > 0 \\
0, & f < 0
\end{cases}$$

**What This Means:**
- **Only positive frequencies** in the complex envelope
- When shifted to carrier frequency, we get **only upper sideband**
- Bandwidth = $B$ (half of DSB-SC!)

### Complex Envelope for LSSB-AM

For **Lower Single-Sideband (LSSB-AM)**:

$$g(t) = A_c[m(t) - j\hat{m}(t)]$$

This gives:

$$G(f) = \begin{cases}
0, & f > 0 \\
2A_c M(f), & f < 0
\end{cases}$$

### The Modulated Signal

For USSB-AM:
$$s(t) = A_c[m(t)\cos(\omega_c t) - \hat{m}(t)\sin(\omega_c t)]$$

For LSSB-AM:
$$s(t) = A_c[m(t)\cos(\omega_c t) + \hat{m}(t)\sin(\omega_c t)]$$

**Key Insight:** The quadrature component ($\hat{m}(t)$) modulates the **sine** carrier, creating the sideband cancellation!

### Advantages of SSB-AM

1. **Bandwidth Efficiency:** Uses only $B$ Hz (half of DSB-SC)
2. **Power Efficiency:** No carrier, only one sideband
3. **Spectrum Efficiency:** More channels can fit in same frequency band

### Disadvantages of SSB-AM

1. **Complex Generation:** Requires Hilbert transform (difficult to implement)
2. **Complex Demodulation:** Requires product detector with precise synchronization
3. **Cost:** More expensive equipment

### Comparison of All Three Types

| Feature | Standard AM | DSB-SC | SSB-AM |
|---------|-------------|--------|--------|
| Bandwidth | $2B$ | $2B$ | $B$ |
| Carrier | Yes | No | No |
| Sidebands | Both | Both | One |
| Power Efficiency | Low | Medium | High |
| Complexity | Low | Medium | High |
| Demodulation | Envelope | Product | Product |

---

## 5. Spectrum Analysis of AM Signals {#spectrum-analysis}

### Standard AM Spectrum

For standard AM with $g(t) = A_c[1 + m(t)]$:

The spectrum of the complex envelope is:
$$G(f) = A_c[\delta(f) + M(f)]$$

Using the spectrum theorem from Group 1:
$$S(f) = \frac{1}{2}[G(f - f_c) + G^*(-f - f_c)]$$

Since $g(t)$ is real, $G^*(f) = G(-f)$:
$$S(f) = \frac{1}{2}[G(f - f_c) + G(f + f_c)]$$

Substituting $G(f)$:
$$S(f) = \frac{A_c}{2}[\delta(f - f_c) + M(f - f_c) + \delta(f + f_c) + M(f + f_c)]$$

**Breaking Down the Spectrum:**

1. **Carrier Components:**
   - $\frac{A_c}{2}\delta(f - f_c)$ at $+f_c$
   - $\frac{A_c}{2}\delta(f + f_c)$ at $-f_c$

2. **Upper Sideband:**
   - $\frac{A_c}{2}M(f - f_c)$ around $+f_c$ (shifted right)

3. **Lower Sideband:**
   - $\frac{A_c}{2}M(f + f_c)$ around $-f_c$ (shifted left)

**Visual Representation:**
```
Spectrum S(f):

        Lower Sideband    Carrier    Upper Sideband
            |M|              |            |M|
    ────────┴────────────────┴────────────┴────────
   -fc-B   -fc           0  +fc        +fc+B
```

**Bandwidth:** $2B$ (from $f_c - B$ to $f_c + B$)

### DSB-SC Spectrum

For DSB-SC with $g(t) = A_c m(t)$:

$$G(f) = A_c M(f)$$

$$S(f) = \frac{A_c}{2}[M(f - f_c) + M(f + f_c)]$$

**Key Difference:** No carrier components (delta functions)!

**Bandwidth:** Still $2B$ (both sidebands present)

### SSB-AM Spectrum

For USSB-AM:
$$G(f) = \begin{cases}
2A_c M(f), & f > 0 \\
0, & f < 0
\end{cases}$$

$$S(f) = \frac{1}{2}[G(f - f_c) + G^*(-f - f_c)]$$

This results in spectrum only around $+f_c$ (upper sideband only).

**Bandwidth:** Only $B$ (half of DSB-SC)!

---

## 6. Power Calculations for AM {#power-calculations}

### Standard AM Power

From Group 1, we know:
$$P_s = \frac{1}{2}\langle |g(t)|^2 \rangle$$

For standard AM: $g(t) = A_c[1 + m(t)]$

$$|g(t)|^2 = A_c^2[1 + m(t)]^2 = A_c^2[1 + 2m(t) + m^2(t)]$$

Taking time average:
$$\langle |g(t)|^2 \rangle = A_c^2[1 + 2\langle m(t) \rangle + \langle m^2(t) \rangle]$$

If $m(t)$ has zero mean ($\langle m(t) \rangle = 0$):
$$\langle |g(t)|^2 \rangle = A_c^2[1 + P_m]$$

where $P_m = \langle m^2(t) \rangle$ is the **average power of the modulating signal**.

**Average Power:**
$$P_s = \frac{1}{2}A_c^2[1 + P_m]$$

### Power Breakdown

**Carrier Power:**
$$P_c = \frac{1}{2}A_c^2$$

**Sideband Power:**
$$P_{SB} = \frac{1}{2}A_c^2 P_m$$

**Total Power:**
$$P_s = P_c + P_{SB} = \frac{1}{2}A_c^2[1 + P_m]$$

### Modulation Efficiency

**Modulation Efficiency** is the fraction of total power that carries information:

$$\eta = \frac{P_{SB}}{P_s} = \frac{P_m}{1 + P_m}$$

**Key Insight:** 
- Maximum efficiency occurs when $P_m$ is large
- For sinusoidal modulation with $m(t) = \mu\cos(\omega_m t)$:
  - $P_m = \frac{\mu^2}{2}$
  - Maximum $\eta = \frac{\mu^2/2}{1 + \mu^2/2}$
  - When $\mu = 1$ (100% modulation): $\eta_{max} = \frac{1/2}{3/2} = \frac{1}{3} \approx 33.3\%$

**This is why standard AM is power inefficient!** Most power goes to the carrier, which doesn't carry information.

### DSB-SC Power

For DSB-SC: $g(t) = A_c m(t)$

$$P_s = \frac{1}{2}\langle |g(t)|^2 \rangle = \frac{1}{2}A_c^2 \langle m^2(t) \rangle = \frac{1}{2}A_c^2 P_m$$

**Key Difference:** No carrier power! All power goes to sidebands.

**Efficiency:** $\eta = 100\%$ (all power carries information)

### SSB-AM Power

For SSB-AM, the power is similar to DSB-SC:

$$P_s = \frac{1}{2}A_c^2 P_m$$

**Efficiency:** $\eta = 100\%$ (all power carries information)

**Plus:** Uses only half the bandwidth!

### Peak Envelope Power (PEP)

**PEP** is the power if the envelope stayed at its maximum:

$$P_{PEP} = \frac{1}{2}[\max|g(t)|]^2$$

**For Standard AM:**
$$P_{PEP} = \frac{1}{2}A_c^2[1 + \max m(t)]^2$$

**Why This Matters:**
- Transmitter must handle peak power
- Determines transmitter power rating
- Important for system design

---

## 7. Modulation Index and Efficiency {#modulation-index}

### Modulation Index (Modulation Depth)

For sinusoidal modulation: $m(t) = \mu\cos(\omega_m t)$

The **modulation index** $\mu$ is defined as:

$$\mu = \frac{\max m(t) - \min m(t)}{2}$$

**For Standard AM:**
- $0 \leq \mu \leq 1$
- $\mu = 1$ → **100% modulation** (maximum)
- $\mu > 1$ → **Overmodulation** (distortion!)

### Percent Modulation

**Percent Modulation** = $100 \times \mu\%$

- 0% → No modulation (just carrier)
- 50% → Moderate modulation
- 100% → Maximum modulation (optimal)
- >100% → Overmodulation (distortion)

### Visual Example

```
μ = 0%:     ~~~~~~~~~~~~~~~~~~~~  (constant amplitude)
           
μ = 50%:   ___/‾‾‾\___/‾‾‾\___  (moderate variation)
           ~~~~~~~~~~~~~~~~~~~~
           
μ = 100%:  __/‾‾‾‾\__/‾‾‾‾\__  (maximum variation)
           ~~~~~~~~~~~~~~~~~~~~
           
μ > 100%:  _/‾‾‾‾‾\_/‾‾‾‾‾\_  (overmodulation - distortion!)
           ~~~~~~~~~~~~~~~~~~~~
```

### Power vs Modulation Index

For sinusoidal modulation with $\mu$:

$$P_m = \frac{\mu^2}{2}$$

$$P_s = \frac{1}{2}A_c^2\left[1 + \frac{\mu^2}{2}\right]$$

**Modulation Efficiency:**
$$\eta = \frac{\mu^2/2}{1 + \mu^2/2} = \frac{\mu^2}{2 + \mu^2}$$

**At 100% modulation ($\mu = 1$):**
$$\eta = \frac{1}{2 + 1} = \frac{1}{3} \approx 33.3\%$$

**Key Insight:** Even at maximum modulation, only 1/3 of power carries information!

---

## 8. Envelope Detector {#envelope-detector}

### What is an Envelope Detector?

An **envelope detector** is a circuit that extracts the **real envelope** $R(t)$ from a bandpass signal.

### Ideal Envelope Detector

**Ideal Operation:**
$$v_{out}(t) = K R(t) = K|g(t)|$$

where $K$ is a proportionality constant.

### How It Works

**Physical Implementation:**
1. **Diode** - rectifies the signal (allows current in one direction)
2. **RC Lowpass Filter** - smooths the rectified signal
3. **DC Blocking Capacitor** (optional) - removes DC component

**Mathematical Operation:**
- Takes the **magnitude** of the complex envelope
- Filters out high-frequency components
- Output follows the envelope shape

### For Standard AM

If input is: $v_{in}(t) = A_c[1 + m(t)]\cos(\omega_c t)$

Then: $g(t) = A_c[1 + m(t)]$ (real and positive)

Output: $v_{out}(t) = K A_c[1 + m(t)] = K A_c + K A_c m(t)$

**What This Means:**
- **DC component:** $K A_c$ (carrier contribution)
- **AC component:** $K A_c m(t)$ (the information!)

**To recover $m(t)$:** Remove DC component with a capacitor or highpass filter.

### Requirements for Proper Operation

1. **$|m(t)| < 1$** - to avoid overmodulation
2. **$g(t) \geq 0$** - envelope must be positive
3. **RC time constant:** $\frac{1}{2\pi RC} < B$ (filter must be fast enough to follow envelope)

**If RC is too large:** Detector is too slow, can't follow rapid envelope changes (distortion)

**If RC is too small:** Too much ripple from carrier frequency (noise)

### Advantages

1. **Simple:** Just a diode and RC circuit
2. **No synchronization needed:** Works without knowing carrier phase
3. **Inexpensive:** Very cheap to implement
4. **Robust:** Works even with some phase/frequency errors

### Disadvantages

1. **Nonlinear:** Not a linear detector
2. **Only for AM:** Doesn't work for DSB-SC or SSB-AM
3. **Sensitive to noise:** Performance degrades with noise
4. **Requires positive envelope:** Only works when $g(t) \geq 0$

### When to Use

- **Standard AM** signals
- When simplicity and cost are important
- When synchronization is difficult
- Consumer AM radio receivers

---

## 9. Product Detector {#product-detector}

### What is a Product Detector?

A **product detector** (also called **coherent detector** or **synchronous detector**) is a **mixer circuit** that multiplies the input signal with a **synchronized local oscillator**.

### Ideal Product Detector

**Operation:**
1. Multiply input with local oscillator: $v_1(t) = v_{in}(t) \cdot A_0\cos(\omega_c t + \theta_0)$
2. Lowpass filter to remove high-frequency components
3. Output is proportional to the complex envelope

### Mathematical Analysis

**Input Signal:**
$$v_{in}(t) = R(t)\cos[\omega_c t + \theta(t)] = \text{Re}\{g(t)e^{j\omega_c t}\}$$

**Local Oscillator:**
$$v_{LO}(t) = A_0\cos(\omega_c t + \theta_0)$$

**Multiplier Output:**
$$v_1(t) = v_{in}(t) \cdot v_{LO}(t)$$

$$v_1(t) = R(t)\cos[\omega_c t + \theta(t)] \cdot A_0\cos(\omega_c t + \theta_0)$$

Using trigonometric identity:
$$\cos(A)\cos(B) = \frac{1}{2}[\cos(A+B) + \cos(A-B)]$$

$$v_1(t) = \frac{1}{2}A_0 R(t)\cos[2\omega_c t + \theta(t) + \theta_0] + \frac{1}{2}A_0 R(t)\cos[\theta(t) - \theta_0]$$

**After Lowpass Filtering:**
- High-frequency term ($2\omega_c$) is removed
- Only low-frequency term remains

**Output:**
$$v_{out}(t) = \frac{1}{2}A_0 R(t)\cos[\theta(t) - \theta_0] = \frac{1}{2}A_0\text{Re}\{g(t)e^{-j\theta_0}\}$$

### Case 1: Synchronized ($\theta_0 = 0$)

If the local oscillator is **synchronized** with the carrier ($\theta_0 = 0$):

$$v_{out}(t) = \frac{1}{2}A_0 R(t)\cos[\theta(t)] = \frac{1}{2}A_0\text{Re}\{g(t)\} = \frac{1}{2}A_0 x(t)$$

**For Standard AM:** $x(t) = A_c[1 + m(t)]$, so:
$$v_{out}(t) = \frac{1}{2}A_0 A_c[1 + m(t)]$$

**For DSB-SC:** $x(t) = A_c m(t)$, so:
$$v_{out}(t) = \frac{1}{2}A_0 A_c m(t)$$

**Key:** We recover the **in-phase component** directly!

### Case 2: Quadrature ($\theta_0 = \pi/2$)

If the local oscillator is **90° out of phase** ($\theta_0 = \pi/2$):

$$v_{out}(t) = \frac{1}{2}A_0 R(t)\cos[\theta(t) - \pi/2] = \frac{1}{2}A_0 R(t)\sin[\theta(t)] = \frac{1}{2}A_0 y(t)$$

**Key:** We recover the **quadrature component**!

### Case 3: Phase Error

If there's a **phase error** $\theta_0 \neq 0$:

$$v_{out}(t) = \frac{1}{2}A_0 R(t)\cos[\theta(t) - \theta_0]$$

**Problem:** Output depends on phase error!

**For AM:** If $\theta(t) = 0$ (no phase modulation):
$$v_{out}(t) = \frac{1}{2}A_0 R(t)\cos(\theta_0)$$

**Effect:** Output is **reduced** by factor $\cos(\theta_0)$
- If $\theta_0 = 0$: Full output
- If $\theta_0 = \pi/2$: Zero output!
- If $\theta_0 = \pi$: Inverted output

### Advantages

1. **Linear:** Linear detector (no distortion)
2. **Works for all AM types:** AM, DSB-SC, SSB-AM
3. **Better performance:** Superior to envelope detector
4. **Flexible:** Can extract I or Q components by adjusting phase

### Disadvantages

1. **Requires synchronization:** Need to know carrier frequency and phase
2. **More complex:** Requires local oscillator and phase-locked loop (PLL)
3. **More expensive:** More components needed
4. **Sensitive to phase errors:** Performance degrades with phase mismatch

### When to Use

- **DSB-SC** signals (required!)
- **SSB-AM** signals (required!)
- **Standard AM** when better performance is needed
- Professional/commercial receivers
- Digital communication systems

### Comparison: Envelope vs Product Detector

| Feature | Envelope Detector | Product Detector |
|---------|-------------------|------------------|
| Type | Nonlinear | Linear |
| Works with AM? | Yes | Yes |
| Works with DSB-SC? | No | Yes |
| Works with SSB-AM? | No | Yes |
| Synchronization | Not needed | Required |
| Complexity | Low | High |
| Cost | Low | High |
| Performance | Good for AM | Superior |
| Phase sensitivity | Low | High |

---

## 10. Detailed Examples {#detailed-examples}

### Example 1: Standard AM with Sinusoidal Modulation

**Given:**
- Modulating signal: $m(t) = 0.8\cos(2\pi \cdot 5 \times 10^3 t)$
- Carrier amplitude: $A_c = 10$ V
- Carrier frequency: $f_c = 1$ MHz = $10^6$ Hz

**Find:**
1. The complex envelope $g(t)$
2. The modulated signal $s(t)$
3. The spectrum $S(f)$
4. The average power $P_s$
5. The modulation efficiency $\eta$
6. The peak envelope power $P_{PEP}$

---

#### Solution 1: Complex Envelope

$$g(t) = A_c[1 + m(t)] = 10[1 + 0.8\cos(2\pi \cdot 5 \times 10^3 t)]$$

$$g(t) = 10 + 8\cos(2\pi \cdot 5 \times 10^3 t)$$

**Real Envelope:**
$$R(t) = |g(t)| = 10 + 8\cos(2\pi \cdot 5 \times 10^3 t)$$

**Modulation Index:**
$$\mu = 0.8 = 80\% \text{ modulation}$$

---

#### Solution 2: Modulated Signal

$$s(t) = A_c[1 + m(t)]\cos(\omega_c t)$$

$$s(t) = [10 + 8\cos(2\pi \cdot 5 \times 10^3 t)]\cos(2\pi \cdot 10^6 t)$$

**Expanding:**
$$s(t) = 10\cos(2\pi \cdot 10^6 t) + 8\cos(2\pi \cdot 5 \times 10^3 t)\cos(2\pi \cdot 10^6 t)$$

Using: $\cos(A)\cos(B) = \frac{1}{2}[\cos(A+B) + \cos(A-B)]$

$$s(t) = 10\cos(2\pi \cdot 10^6 t) + 4\cos[2\pi(10^6 + 5000)t] + 4\cos[2\pi(10^6 - 5000)t]$$

**Components:**
- **Carrier:** $10\cos(2\pi \cdot 10^6 t)$ at 1 MHz
- **Upper sideband:** $4\cos[2\pi \cdot 1,005,000 t]$ at 1.005 MHz
- **Lower sideband:** $4\cos[2\pi \cdot 995,000 t]$ at 0.995 MHz

---

#### Solution 3: Spectrum

**Complex Envelope Spectrum:**
$$G(f) = 10\delta(f) + 8 \cdot \frac{1}{2}[\delta(f - 5000) + \delta(f + 5000)]$$

$$G(f) = 10\delta(f) + 4\delta(f - 5000) + 4\delta(f + 5000)$$

**Bandpass Spectrum:**
$$S(f) = \frac{1}{2}[G(f - f_c) + G(f + f_c)]$$

$$S(f) = \frac{1}{2}[10\delta(f - f_c) + 4\delta(f - f_c - 5000) + 4\delta(f - f_c + 5000) + 10\delta(f + f_c) + 4\delta(f + f_c - 5000) + 4\delta(f + f_c + 5000)]$$

With $f_c = 10^6$:
$$S(f) = 5\delta(f - 10^6) + 2\delta(f - 1,005,000) + 2\delta(f - 995,000) + 5\delta(f + 10^6) + 2\delta(f + 1,005,000) + 2\delta(f + 995,000)$$

**Bandwidth:** $2B = 2 \times 5000 = 10,000$ Hz = 10 kHz

---

#### Solution 4: Average Power

**Power of Modulating Signal:**
$$P_m = \langle m^2(t) \rangle = \langle [0.8\cos(2\pi \cdot 5 \times 10^3 t)]^2 \rangle$$

$$P_m = 0.64 \times \frac{1}{2} = 0.32$$

**Average Power:**
$$P_s = \frac{1}{2}A_c^2[1 + P_m] = \frac{1}{2}(10)^2[1 + 0.32] = 50 \times 1.32 = 66 \text{ W}$$

**Power Breakdown:**
- **Carrier power:** $P_c = \frac{1}{2}(10)^2 = 50$ W
- **Sideband power:** $P_{SB} = 66 - 50 = 16$ W

---

#### Solution 5: Modulation Efficiency

$$\eta = \frac{P_{SB}}{P_s} = \frac{16}{66} = 0.2424 = 24.24\%$$

**Or using formula:**
$$\eta = \frac{P_m}{1 + P_m} = \frac{0.32}{1.32} = 0.2424 = 24.24\%$$

---

#### Solution 6: Peak Envelope Power

**Maximum Envelope:**
$$\max|g(t)| = 10 + 8(1) = 18 \text{ V}$$

**PEP:**
$$P_{PEP} = \frac{1}{2}(18)^2 = \frac{1}{2} \times 324 = 162 \text{ W}$$

**Peak-to-Average Ratio:**
$$\frac{P_{PEP}}{P_s} = \frac{162}{66} = 2.45 \text{ (or } 3.9 \text{ dB)}$$

---

### Example 2: DSB-SC Signal

**Given:**
- Modulating signal: $m(t) = 2\cos(2\pi \cdot 3 \times 10^3 t)$
- Carrier amplitude: $A_c = 5$ V
- Carrier frequency: $f_c = 100$ kHz

**Find:**
1. The complex envelope $g(t)$
2. The modulated signal $s(t)$
3. The average power $P_s$
4. Why envelope detector won't work

---

#### Solution 1: Complex Envelope

$$g(t) = A_c m(t) = 5 \times 2\cos(2\pi \cdot 3 \times 10^3 t) = 10\cos(2\pi \cdot 3 \times 10^3 t)$$

**Real Envelope:**
$$R(t) = |g(t)| = 10|\cos(2\pi \cdot 3 \times 10^3 t)|$$

**Problem:** $g(t)$ can be **negative**! The envelope is $|m(t)|$, not $m(t)$.

---

#### Solution 2: Modulated Signal

$$s(t) = A_c m(t)\cos(\omega_c t) = 10\cos(2\pi \cdot 3 \times 10^3 t)\cos(2\pi \cdot 10^5 t)$$

$$s(t) = 5\cos[2\pi(10^5 + 3000)t] + 5\cos[2\pi(10^5 - 3000)t]$$

**No carrier component!** Only sidebands.

---

#### Solution 3: Average Power

$$P_m = \langle m^2(t) \rangle = \langle [2\cos(2\pi \cdot 3 \times 10^3 t)]^2 \rangle = 4 \times \frac{1}{2} = 2$$

$$P_s = \frac{1}{2}A_c^2 P_m = \frac{1}{2}(5)^2 \times 2 = 25 \text{ W}$$

**All power in sidebands!** Efficiency = 100%

---

#### Solution 4: Why Envelope Detector Fails

If we use envelope detector:
$$v_{out}(t) = K|g(t)| = K \times 10|\cos(2\pi \cdot 3 \times 10^3 t)|$$

**Problem:** We get $|m(t)|$ instead of $m(t)$!

**The sign information is lost!** The envelope detector gives:
```
|cos|:  ___/‾‾‾\___/‾‾‾\___
```

But we need:
```
cos:   /‾‾‾\___/‾‾‾\___/‾‾
```

**Solution:** Use product detector to recover $m(t)$ correctly!

---

## 11. Key Takeaways {#key-takeaways}

### Essential Concepts

1. **Standard AM:**
   - Complex envelope: $g(t) = A_c[1 + m(t)]$
   - Contains carrier + both sidebands
   - Can use simple envelope detector
   - Power inefficient (~33% max efficiency)

2. **DSB-SC:**
   - Complex envelope: $g(t) = A_c m(t)$
   - No carrier, both sidebands
   - Requires product detector
   - 100% power efficient

3. **SSB-AM:**
   - Complex envelope: $g(t) = A_c[m(t) \pm j\hat{m}(t)]$
   - No carrier, one sideband
   - Requires product detector
   - Most bandwidth and power efficient

4. **Envelope Detector:**
   - Extracts $R(t) = |g(t)|$
   - Simple, nonlinear
   - Only works for standard AM
   - No synchronization needed

5. **Product Detector:**
   - Extracts $x(t)$ or $y(t)$
   - Linear, superior performance
   - Works for all AM types
   - Requires synchronization

### Common Mistakes to Avoid

1. **Using envelope detector for DSB-SC** - will lose sign information
2. **Forgetting the $\frac{1}{2}$ factor** in power calculations
3. **Confusing bandwidth** - SSB uses $B$, others use $2B$
4. **Overmodulation** - $m(t) < -1$ causes distortion
5. **Phase errors in product detector** - reduces output

### Study Tips

1. **Memorize the complex envelopes:**
   - AM: $A_c[1 + m(t)]$
   - DSB-SC: $A_c m(t)$
   - SSB: $A_c[m(t) \pm j\hat{m}(t)]$

2. **Understand the trade-offs:**
   - Simplicity vs Efficiency
   - Bandwidth vs Complexity
   - Cost vs Performance

3. **Practice power calculations:**
   - Always start from $P_s = \frac{1}{2}\langle |g(t)|^2 \rangle$
   - Break down into carrier and sideband power

4. **Know when to use which detector:**
   - Envelope: Standard AM only
   - Product: All types, better performance

---

## Summary of Key Formulas

### Complex Envelopes
- **Standard AM:** $g(t) = A_c[1 + m(t)]$
- **DSB-SC:** $g(t) = A_c m(t)$
- **USSB-AM:** $g(t) = A_c[m(t) + j\hat{m}(t)]$
- **LSSB-AM:** $g(t) = A_c[m(t) - j\hat{m}(t)]$

### Modulated Signals
- **Standard AM:** $s(t) = A_c[1 + m(t)]\cos(\omega_c t)$
- **DSB-SC:** $s(t) = A_c m(t)\cos(\omega_c t)$
- **SSB-AM:** $s(t) = A_c[m(t)\cos(\omega_c t) \mp \hat{m}(t)\sin(\omega_c t)]$

### Power
- **Standard AM:** $P_s = \frac{1}{2}A_c^2[1 + P_m]$
- **DSB-SC/SSB:** $P_s = \frac{1}{2}A_c^2 P_m$
- **Efficiency:** $\eta = \frac{P_{SB}}{P_s}$

### Detectors
- **Envelope:** $v_{out}(t) = K R(t) = K|g(t)|$
- **Product:** $v_{out}(t) = \frac{1}{2}A_0 x(t)$ (when $\theta_0 = 0$)

### Bandwidth
- **Standard AM/DSB-SC:** $2B$
- **SSB-AM:** $B$

---

*End of Group 2 Detailed Explanation*


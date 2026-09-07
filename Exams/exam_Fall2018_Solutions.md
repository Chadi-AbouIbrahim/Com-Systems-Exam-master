# Communication Systems - Fall 2018 Final Exam Solutions

**Instructor:** Dr. Chadi Abou-Rjeily  
**Total Points:** 100 points

---

## Problem 1: (10 points: 5×2)

### Part (a): Delta Modulation Sampling Frequency

**Question:** Comment on one advantage and one disadvantage that follow from increasing the sampling frequency in Delta Modulation (DM) systems.

**Solution:**

**Advantage:**
- **Reduced slope overload noise:** Higher sampling frequency allows the DM system to track rapid changes in the input signal more accurately. The step-size can follow steeper slopes without causing slope overload distortion.

**Disadvantage:**
- **Increased bandwidth requirement:** Higher sampling frequency means more samples per second, which requires more transmission bandwidth. For a given step-size, doubling the sampling rate doubles the bit rate and bandwidth.

**Additional Notes:**
- Sampling frequency $f_s$ determines the bit rate: $R_b = f_s$ (assuming 1 bit per sample)
- Higher $f_s$ → better tracking but more bandwidth
- Trade-off between slope overload and granular noise

---

### Part (b): TDM Synchronization Word Length

**Question:** Consider a TDM system and denote by $K$ the length of the synchronization word. Comment on one advantage and one disadvantage that follow from increasing $K$.

**Solution:**

**Advantage:**
- **Better synchronization reliability:** Longer synchronization words provide more unique patterns, making it easier to distinguish the sync word from data. This reduces the probability of false synchronization and improves frame alignment accuracy.

**Disadvantage:**
- **Reduced efficiency:** Longer synchronization words consume more bits in each frame, reducing the percentage of frame capacity available for actual data transmission. This overhead reduces the overall system efficiency.

**Additional Notes:**
- Sync word length affects frame overhead: $\text{Overhead} = \frac{K}{N}$ where $N$ is total frame length
- Longer $K$ → better sync reliability but more overhead
- Typical sync word lengths: 7-16 bits depending on application

---

### Part (c): Adaptive Delta Modulation (ADM)

**Question:** Comment on one advantage and one disadvantage associated with Adaptive Delta Modulation (ADM).

**Solution:**

**Advantage:**
- **Automatic step-size adjustment:** ADM adapts the step-size based on the input signal characteristics. When the signal changes rapidly, the step-size increases to prevent slope overload. When the signal is relatively constant, the step-size decreases to reduce granular noise. This provides better overall performance than fixed-step DM.

**Disadvantage:**
- **Increased complexity:** ADM requires additional circuitry and logic to monitor the signal and adjust the step-size dynamically. This makes the system more complex, expensive, and potentially more susceptible to errors in the adaptation algorithm.

**Additional Notes:**
- ADM uses variable step-size: $\Delta(n) = \Delta(n-1) \times M$ or $\Delta(n-1) \times \frac{1}{M}$
- Adaptation based on consecutive same-direction steps
- Better SQNR than fixed-step DM

---

### Part (d): DSB-SC-AM vs Conventional AM

**Question:** Comment on one advantage and one disadvantage of DSB-SC-AM compared to conventional AM.

**Solution:**

**Advantage:**
- **Higher power efficiency:** DSB-SC-AM suppresses the carrier, so all transmitted power goes into the sidebands containing information. For a given total power, DSB-SC delivers more power to the information-bearing sidebands compared to conventional AM, where a significant portion of power (often 50% or more) is wasted in the carrier.

**Disadvantage:**
- **Requires coherent detection:** DSB-SC-AM cannot be demodulated using a simple envelope detector. It requires a product detector (coherent detector) that needs a local oscillator synchronized in phase and frequency with the carrier. This makes the receiver more complex and expensive.

**Additional Notes:**
- DSB-SC: $s(t) = A_c m(t)\cos(\omega_c t)$ (no carrier)
- Conventional AM: $s(t) = A_c[1 + \mu m(t)]\cos(\omega_c t)$ (with carrier)
- Power efficiency: DSB-SC can achieve up to 100% efficiency, while AM typically has 33% efficiency for $\mu = 1$

---

### Part (e): Product Detector vs Envelope Detector

**Question:** Comment on one advantage and one disadvantage of product detectors (used as AM demodulators) compared to envelope detectors.

**Solution:**

**Advantage:**
- **Works with DSB-SC signals:** Product detectors can demodulate both conventional AM and DSB-SC-AM signals, while envelope detectors only work with AM signals that have a carrier. Product detectors are more versatile.

**Disadvantage:**
- **Requires carrier synchronization:** Product detectors need a local oscillator that is synchronized in both phase and frequency with the carrier. This requires carrier recovery circuitry (PLL, Costas loop, etc.), making the receiver more complex and expensive than envelope detectors.

**Additional Notes:**
- Product detector: $y(t) = s(t) \times A_{LO}\cos(\omega_c t + \phi)$
- Envelope detector: Simple diode + RC circuit (non-coherent)
- Product detector: Coherent, more complex, works for DSB-SC
- Envelope detector: Non-coherent, simple, only for AM with carrier

---

## Problem 2: (5 points: 2,3)

### Part (a): Inter-Symbol Interference (ISI)

**Question:** A signal of bandwidth 1 MHz is transmitted over a channel of bandwidth 2 MHz. Will the communication system suffer from Inter-Symbol Interference (ISI) in this case? Why?

**Solution:**

**Answer: No, the system will NOT suffer from ISI.**

**Reasoning:**
- The channel bandwidth (2 MHz) is **greater than** the signal bandwidth (1 MHz)
- For ISI to occur, the channel must be **bandwidth-limited**, meaning the channel bandwidth is less than or equal to the signal bandwidth
- Since the channel can accommodate the full signal spectrum without distortion, all frequency components of the signal pass through without interference
- The Nyquist criterion for zero ISI requires: Channel bandwidth ≥ Signal bandwidth (for ideal case)

**Mathematical Explanation:**
- Signal bandwidth: $B_{signal} = 1$ MHz
- Channel bandwidth: $B_{channel} = 2$ MHz
- Since $B_{channel} > B_{signal}$, the channel is not bandwidth-limited
- No frequency components are lost or distorted → No ISI

---

### Part (b): Nyquist First Method

**Question:** A communication system has the equivalent impulse response given by $h_e(t) = \text{sinc}^2(200t)$. Find the maximum baud rate at which the system will satisfy the Nyquist first method for eliminating the ISI.

**Solution:**

**Given:**
$$h_e(t) = \text{sinc}^2(200t)$$

**Nyquist First Method:** For zero ISI, the impulse response must satisfy:
$$h_e(nT) = \begin{cases} 
1 & \text{if } n = 0 \\
0 & \text{if } n \neq 0
\end{cases}$$

where $T$ is the symbol period.

**Finding the zero-crossings:**

The function $\text{sinc}^2(200t)$ has zeros when:
$$200t = k\pi \quad \text{for } k = \pm 1, \pm 2, \pm 3, \ldots$$

Therefore: $t = \frac{k\pi}{200}$ for $k = \pm 1, \pm 2, \ldots$

**For the first zero-crossing (k = 1):**
$$t_1 = \frac{\pi}{200}$$

**To satisfy Nyquist criterion:**
The symbol period $T$ must be equal to the first zero-crossing time:
$$T = \frac{\pi}{200} \text{ seconds}$$

**Maximum baud rate:**
$$R_{max} = \frac{1}{T} = \frac{200}{\pi} \approx 63.66 \text{ baud}$$

**Answer:** Maximum baud rate = $\frac{200}{\pi}$ baud ≈ **63.66 baud**

---

## Problem 3: (5 points) - Delta Modulation Step-Size

**Question:** Delta Modulation (DM) is applied on the signal $w(t) = 10\cos(200\pi t)$. Find the value of the step-size that eliminates the slope overload noise while minimizing the granular noise if the DM system transmits at the rate of 10 kbits/s.

**Solution:**

**Given:**
- Signal: $w(t) = 10\cos(200\pi t)$
- Transmission rate: $R_b = 10$ kbits/s = $10,000$ bits/s
- Sampling frequency: $f_s = R_b = 10,000$ Hz (assuming 1 bit per sample)

**Step 1: Find the maximum slope of the signal**

$$w(t) = 10\cos(200\pi t)$$

$$\frac{dw(t)}{dt} = -10 \times 200\pi \sin(200\pi t) = -2000\pi \sin(200\pi t)$$

**Maximum slope occurs when $|\sin(200\pi t)| = 1$:**

$$\left|\frac{dw(t)}{dt}\right|_{max} = 2000\pi \text{ V/s}$$

**Step 2: Condition to avoid slope overload**

For DM, to avoid slope overload:
$$\Delta \times f_s \geq \left|\frac{dw(t)}{dt}\right|_{max}$$

where:
- $\Delta$ = step-size
- $f_s$ = sampling frequency

**Substituting:**
$$\Delta \times 10,000 \geq 2000\pi$$

$$\Delta \geq \frac{2000\pi}{10,000} = \frac{\pi}{5} = 0.628 \text{ V}$$

**Step 3: Minimize granular noise**

To minimize granular noise, we want the **smallest** step-size that still prevents slope overload.

**Answer:** Step-size = $\frac{\pi}{5}$ V ≈ **0.628 V**

**Verification:**
- Slope overload condition: $\Delta f_s = 0.628 \times 10,000 = 6280$ V/s ≥ $2000\pi = 6283$ V/s ✓
- This is the minimum step-size that prevents slope overload while minimizing granular noise.

---

## Problem 4: (10 points: 7,3) - TDM System Design

### Part (a): TDM System Design

**Question:** Design a TDM system that allows to accommodate the following sources:
- One analog source having a bandwidth of 100 Hz
- One analog source having a bandwidth of 300 Hz
- Three digital sources having a data rate of 235 bits/s each

**Constraints:**
- Pulse stuffing is allowed and only two commutators can be used
- The analog samples will be encoded into 3-bit PCM codewords
- No synchronization bits are required

Draw a block diagram for your design indicating the data rates at various points of your diagram.

**Solution:**

**Step 1: Determine sampling rates**

**Analog Source 1:** Bandwidth = 100 Hz
- Nyquist rate: $f_{s1} = 2 \times 100 = 200$ Hz
- Use: $f_{s1} = 200$ Hz

**Analog Source 2:** Bandwidth = 300 Hz
- Nyquist rate: $f_{s2} = 2 \times 300 = 600$ Hz
- Use: $f_{s2} = 600$ Hz

**Digital Sources:** 3 sources at 235 bits/s each
- Total digital rate: $3 \times 235 = 705$ bits/s

**Step 2: PCM encoding**

Each analog sample encoded into 3-bit PCM:
- Bits per sample: 3 bits
- Source 1 bit rate: $200 \times 3 = 600$ bits/s
- Source 2 bit rate: $600 \times 3 = 1800$ bits/s

**Step 3: First commutator (Analog sources)**

Combine the two analog sources:
- Input 1: 600 bits/s (from Source 1)
- Input 2: 1800 bits/s (from Source 2)
- **Output of Commutator 1:** 2400 bits/s

**Step 4: Second commutator (Final TDM)**

Combine analog TDM output with digital sources:
- Input 1: 2400 bits/s (from Commutator 1)
- Input 2: 705 bits/s (from 3 digital sources)
- **Output of Commutator 2 (Final TDM):** 2400 + 705 = **3105 bits/s**

**Block Diagram:**

```
Analog Source 1          Analog Source 2
(100 Hz BW)              (300 Hz BW)
     |                         |
     v                         v
[Sampler]                  [Sampler]
fs1 = 200 Hz              fs2 = 600 Hz
     |                         |
     v                         v
[3-bit PCM]               [3-bit PCM]
     |                         |
     v                         v
  600 b/s                 1800 b/s
     |                         |
     +-----[Commutator 1]------+
                    |
                    v
              2400 b/s
                    |
     +--------------+
     |              |
     v              v
Digital Sources  [Commutator 2]
(3 × 235 b/s)         |
= 705 b/s              v
               [Final TDM Output]
                   3105 b/s
```

**Data Rates Summary:**
- Analog Source 1 output: **600 bits/s**
- Analog Source 2 output: **1800 bits/s**
- Commutator 1 output: **2400 bits/s**
- Digital sources total: **705 bits/s**
- Final TDM output: **3105 bits/s**

---

### Part (b): Channel Bandwidth

**Question:** The TDM signal is transmitted over a channel with overall raised cosine-rolloff Nyquist filter characteristics with $r = 0.5$. Find the absolute bandwidth required for the channel.

**Solution:**

**Given:**
- TDM bit rate: $R_b = 3105$ bits/s
- Rolloff factor: $r = 0.5$

**Raised cosine filter bandwidth:**
$$B = \frac{R_b}{2}(1 + r)$$

**Substituting:**
$$B = \frac{3105}{2}(1 + 0.5) = \frac{3105}{2} \times 1.5 = 1552.5 \times 1.5 = 2328.75 \text{ Hz}$$

**Answer:** Absolute bandwidth required = **2328.75 Hz** ≈ **2.33 kHz**

---

## Problem 5: (10 points: 2,2,3,3) - Modulation Power Calculations

**Given:** $m(t) = \cos(200\pi t)$, $A_c = 10$

Find the normalized average power of the modulated signal in each case.

---

### Part (a): DSB-SC AM Power (2 points)

**Solution:**

**DSB-SC AM signal:**
$$s(t) = A_c m(t)\cos(\omega_c t) = 10\cos(200\pi t)\cos(\omega_c t)$$

**Normalized average power:**
$$P_s = \frac{A_c^2}{2}P_m$$

where $P_m$ is the power of $m(t)$.

**Power of $m(t) = \cos(200\pi t)$:**
$$P_m = \frac{1}{2}$$

**Therefore:**
$$P_s = \frac{10^2}{2} \times \frac{1}{2} = \frac{100}{4} = 25$$

**Answer:** Normalized average power = **25**

---

### Part (b): FM Power (2 points)

**Solution:**

**FM signal:**
$$s(t) = A_c\cos\left[\omega_c t + 2\pi D_f \int_{-\infty}^{t} m(\tau) d\tau\right]$$

**Key property:** The power in an angle-modulated (FM/PM) signal is **constant** and independent of the modulation.

**Normalized average power:**
$$P_s = \frac{A_c^2}{2} = \frac{10^2}{2} = \frac{100}{2} = 50$$

**Answer:** Normalized average power = **50**

**Note:** This is true regardless of the modulation index or modulating signal.

---

### Part (c): AM Power (3 points)

**Solution:**

**Standard AM signal:**
$$s(t) = A_c[1 + \mu m(t)]\cos(\omega_c t)$$

**Modulation index:** For $m(t) = \cos(200\pi t)$ with peak value 1, and assuming $\mu = 1$ (100% modulation):

$$s(t) = 10[1 + \cos(200\pi t)]\cos(\omega_c t)$$

**Normalized average power:**
$$P_s = \frac{A_c^2}{2}\left(1 + \frac{\mu^2}{2}P_m\right)$$

**With $\mu = 1$ and $P_m = \frac{1}{2}$:**
$$P_s = \frac{10^2}{2}\left(1 + \frac{1^2}{2} \times \frac{1}{2}\right) = 50\left(1 + \frac{1}{4}\right) = 50 \times \frac{5}{4} = 62.5$$

**Answer:** Normalized average power = **62.5**

**Breakdown:**
- Carrier power: $P_c = \frac{A_c^2}{2} = 50$
- Sideband power: $P_{SB} = \frac{A_c^2 \mu^2}{4}P_m = \frac{100 \times 1}{4} \times \frac{1}{2} = 12.5$
- Total: $P_s = 50 + 12.5 = 62.5$

---

### Part (d): USSB AM Power (3 points)

**Solution:**

**Upper Single-Sideband AM signal:**
$$s(t) = A_c[m(t)\cos(\omega_c t) - \hat{m}(t)\sin(\omega_c t)]$$

where $\hat{m}(t)$ is the Hilbert transform of $m(t)$.

**For $m(t) = \cos(200\pi t)$:**
- Hilbert transform: $\hat{m}(t) = \sin(200\pi t)$

**USSB signal:**
$$s(t) = 10[\cos(200\pi t)\cos(\omega_c t) - \sin(200\pi t)\sin(\omega_c t)]$$
$$= 10\cos(\omega_c t + 200\pi t)$$

**Normalized average power:**
$$P_s = \frac{A_c^2}{4}P_m = \frac{10^2}{4} \times \frac{1}{2} = \frac{100}{8} = 12.5$$

**Answer:** Normalized average power = **12.5**

**Note:** SSB uses only one sideband, so power is half of DSB-SC.

---

## Problem 6: (10 points: 3,3,4) - AM Detection

**Given:** 
- $m(t) = 2\sin(2\pi f_1 t)$
- $A_c = 1$
- Carrier frequency: $f_c$

---

### Part (a): Product Detector Output (3 points)

**Question:** The AM signal is applied to the input of a product detector. Write down the expression of the signal at the output of the detector. Is the detection successful? (Hint: the signal at the output of the local oscillator is given by $A_{LO}\cos(2\pi f_c t)$)

**Solution:**

**AM signal:**
$$s(t) = A_c[1 + \mu m(t)]\cos(2\pi f_c t)$$

**With $A_c = 1$ and assuming $\mu = 1$:**
$$s(t) = [1 + 2\sin(2\pi f_1 t)]\cos(2\pi f_c t)$$

**Product detector:**
$$y(t) = s(t) \times A_{LO}\cos(2\pi f_c t)$$

**Assuming $A_{LO} = 1$ for simplicity:**
$$y(t) = [1 + 2\sin(2\pi f_1 t)]\cos(2\pi f_c t) \times \cos(2\pi f_c t)$$

**Using identity:** $\cos^2(\theta) = \frac{1}{2}[1 + \cos(2\theta)]$

$$y(t) = [1 + 2\sin(2\pi f_1 t)] \times \frac{1}{2}[1 + \cos(4\pi f_c t)]$$

$$y(t) = \frac{1}{2}[1 + 2\sin(2\pi f_1 t)] + \frac{1}{2}[1 + 2\sin(2\pi f_1 t)]\cos(4\pi f_c t)$$

**After low-pass filtering (removing $2f_c$ component):**
$$y_{LPF}(t) = \frac{1}{2}[1 + 2\sin(2\pi f_1 t)] = \frac{1}{2} + \sin(2\pi f_1 t)$$

**Answer:**
- Output expression: $y(t) = \frac{1}{2} + \sin(2\pi f_1 t)$ (after LPF)
- **Detection is successful** - The modulating signal $m(t) = 2\sin(2\pi f_1 t)$ is recovered (scaled by $\frac{1}{2}$), plus a DC component that can be removed with a capacitor.

---

### Part (b): Envelope Detector Output (3 points)

**Question:** The AM signal is applied to the input of an envelope detector. Write down the expression of the signal at the output of the detector. Is the detection successful?

**Solution:**

**AM signal:**
$$s(t) = [1 + 2\sin(2\pi f_1 t)]\cos(2\pi f_c t)$$

**Envelope of AM signal:**
The envelope is the magnitude of the complex envelope:
$$|g(t)| = |1 + 2\sin(2\pi f_1 t)|$$

**Envelope detector output:**
$$y(t) = |1 + 2\sin(2\pi f_1 t)|$$

**Analysis:**
- When $1 + 2\sin(2\pi f_1 t) \geq 0$: $y(t) = 1 + 2\sin(2\pi f_1 t)$
- When $1 + 2\sin(2\pi f_1 t) < 0$: $y(t) = -(1 + 2\sin(2\pi f_1 t))$ (rectified)

**Since the peak value of $2\sin(2\pi f_1 t)$ is 2, and $1 + 2\sin(2\pi f_1 t)$ ranges from -1 to 3:**
- The envelope becomes negative for part of the cycle
- This means **overmodulation** ($\mu > 1$)

**Answer:**
- Output expression: $y(t) = |1 + 2\sin(2\pi f_1 t)|$
- **Detection is NOT fully successful** - Due to overmodulation, the envelope detector will produce distortion. The recovered signal will not be a perfect replica of $m(t)$.

**Note:** For successful envelope detection, we need $\mu \leq 1$, which requires the modulating signal to have peak value $\leq 1$.

---

### Part (c): Sketch AM Signal and Envelope Detector Output (4 points)

**Solution:**

**AM Signal Sketch:**

The AM signal is:
$$s(t) = [1 + 2\sin(2\pi f_1 t)]\cos(2\pi f_c t)$$

**Key features:**
- Carrier frequency: $f_c$ (high frequency oscillation)
- Envelope: $1 + 2\sin(2\pi f_1 t)$ (varies slowly at rate $f_1$)
- The envelope goes negative (overmodulation), causing phase reversals

**Envelope Detector Output:**

After envelope detection:
$$y(t) = |1 + 2\sin(2\pi f_1 t)|$$

**Sketch description:**
- The output follows the positive envelope
- When the envelope is negative, it's rectified to positive
- Shows distortion due to overmodulation
- DC component present

**Note:** A proper sketch would show:
1. High-frequency carrier oscillations
2. Envelope that goes below zero (overmodulation)
3. Envelope detector output showing rectified waveform with distortion

---

## Problem 7: (5 points) - LSSB AM Spectrum

**Question:** Lower Single-Sideband (LSSB) Amplitude Modulation is applied on the signal whose spectrum is shown in the figure below with $f_c = 1$ MHz and $A_c = 100$. Provide a labeled sketch of the spectrum of the LSSB signal. (Hint: find and plot $G(f)$ first)

**Solution:**

**Step 1: Find the complex envelope $G(f)$**

For LSSB-AM, the complex envelope is:
$$g(t) = A_c[m(t) + j\hat{m}(t)]$$

where $\hat{m}(t)$ is the Hilbert transform of $m(t)$.

**In frequency domain:**
$$G(f) = A_c[M(f) + j(-j\text{sgn}(f))M(f)] = A_c[M(f) + \text{sgn}(f)M(f)]$$

For positive frequencies: $G(f) = 2A_c M(f)$ for $f > 0$  
For negative frequencies: $G(f) = 0$ for $f < 0$

**Given:** $A_c = 100$ and baseband spectrum $M(f)$ from the figure

**Step 2: Spectrum of LSSB signal**

The bandpass spectrum is:
$$S(f) = \frac{1}{2}[G(f - f_c) + G^*(-f - f_c)]$$

**For LSSB:**
- Lower sideband: $f_c - B \leq |f| \leq f_c$ (where $B$ is baseband bandwidth)
- Upper sideband: Suppressed
- Carrier: Suppressed (assuming DSB-SC LSSB) or present (if AM LSSB)

**Sketch Description:**

**$G(f)$ (Complex Envelope):**
- For $f > 0$: $G(f) = 200 \times M(f)$ (scaled version of baseband)
- For $f < 0$: $G(f) = 0$

**$S(f)$ (LSSB Spectrum):**
- **Lower sideband:** Around $f = -f_c$ to $f = -f_c + B$ and $f = f_c - B$ to $f = f_c$
- **Upper sideband:** Absent (suppressed)
- **Carrier:** At $f = \pm f_c$ (if present) or suppressed (if DSB-SC)

**Answer:** The LSSB spectrum shows only the lower sideband components, with the upper sideband completely suppressed.

---

## Problem 8: (5 points) - Nonlinear System Harmonic Distortion

**Question:** A nonlinear system $x(t) \to y(t)$ is described by the relation $y(t) = x^3(t)$. Find the total harmonic distortion of the system. (Hint: let $x(t) = \cos(\omega_c t)$)

**Solution:**

**Given:**
$$y(t) = x^3(t)$$

**Input:** $x(t) = \cos(\omega_c t)$

**Output:**
$$y(t) = \cos^3(\omega_c t)$$

**Using trigonometric identity:**
$$\cos^3(\theta) = \frac{1}{4}[3\cos(\theta) + \cos(3\theta)]$$

**Therefore:**
$$y(t) = \frac{3}{4}\cos(\omega_c t) + \frac{1}{4}\cos(3\omega_c t)$$

**Harmonic components:**
- **Fundamental (1st harmonic):** $\frac{3}{4}\cos(\omega_c t)$ - Amplitude: $\frac{3}{4}$
- **3rd harmonic:** $\frac{1}{4}\cos(3\omega_c t)$ - Amplitude: $\frac{1}{4}$

**Total Harmonic Distortion (THD):**

THD is defined as:
$$\text{THD} = \frac{\sqrt{\sum_{n=2}^{\infty} A_n^2}}{A_1}$$

where:
- $A_1$ = amplitude of fundamental
- $A_n$ = amplitude of $n$-th harmonic

**In this case:**
- $A_1 = \frac{3}{4}$ (fundamental)
- $A_3 = \frac{1}{4}$ (3rd harmonic)
- All other harmonics: $A_n = 0$ for $n \neq 1, 3$

**THD calculation:**
$$\text{THD} = \frac{A_3}{A_1} = \frac{\frac{1}{4}}{\frac{3}{4}} = \frac{1}{3} = 0.3333...$$

**As percentage:**
$$\text{THD} = 33.33\%$$

**Answer:** Total Harmonic Distortion = **$\frac{1}{3}$** or **33.33%**

---

## Problem 9: (5 points) - Peak Envelope Power (PEP)

**Question:** Find the normalized peak envelope power (PEP) of the RF signal $s(t) = 5\cos((\omega_c - \omega_a)t) + 5\cos((\omega_c + \omega_a)t)$ where $\omega_c \gg \omega_a$.

**Solution:**

**Given:**
$$s(t) = 5\cos((\omega_c - \omega_a)t) + 5\cos((\omega_c + \omega_a)t)$$

**Step 1: Express in complex envelope form**

Using Euler's formula:
$$s(t) = \text{Re}\{5e^{j(\omega_c - \omega_a)t} + 5e^{j(\omega_c + \omega_a)t}\}$$

$$= \text{Re}\{5e^{j\omega_c t}(e^{-j\omega_a t} + e^{j\omega_a t})\}$$

$$= \text{Re}\{5e^{j\omega_c t} \times 2\cos(\omega_a t)\}$$

$$= \text{Re}\{10\cos(\omega_a t) e^{j\omega_c t}\}$$

**Complex envelope:**
$$g(t) = 10\cos(\omega_a t)$$

**Step 2: Find peak envelope power**

**Peak Envelope Power (PEP):**
$$\text{PEP} = \frac{1}{2}\max|g(t)|^2$$

**Maximum of $|g(t)|$:**
$$|g(t)| = |10\cos(\omega_a t)| = 10|\cos(\omega_a t)|$$

Maximum occurs when $|\cos(\omega_a t)| = 1$:
$$\max|g(t)| = 10$$

**PEP:**
$$\text{PEP} = \frac{1}{2} \times 10^2 = \frac{100}{2} = 50$$

**Answer:** Normalized Peak Envelope Power = **50**

**Verification:**
The signal can be written as:
$$s(t) = 10\cos(\omega_a t)\cos(\omega_c t)$$

This is a DSB-SC signal with carrier amplitude effectively 10, confirming PEP = 50.

---

## Problem 10: (6 points: 2,2,2) - Superheterodyne Receiver

**Question:** An FM radio is tuned to receive an FM broadcasting station of frequency 100 MHz. The radio is of the superheterodyne type with the local oscillator operating on the high side of the 100 MHz and using a 10 MHz intermediate frequency (IF).

---

### Part (a): Local Oscillator Frequency (2 points)

**Solution:**

**Given:**
- Carrier frequency: $f_c = 100$ MHz
- IF frequency: $f_{IF} = 10$ MHz
- High-side injection: LO frequency > carrier frequency

**For high-side injection:**
$$f_{LO} = f_c + f_{IF}$$

**Substituting:**
$$f_{LO} = 100 + 10 = 110 \text{ MHz}$$

**Answer:** Local oscillator frequency = **110 MHz**

---

### Part (b): Image Frequency (2 points)

**Solution:**

**Image frequency formula:**
$$f_{image} = f_{LO} + f_{IF}$$

**Substituting:**
$$f_{image} = 110 + 10 = 120 \text{ MHz}$$

**Answer:** Image frequency = **120 MHz**

**Verification:**
- Desired signal: $f_c = 100$ MHz → Mixer output: $|f_{LO} - f_c| = |110 - 100| = 10$ MHz ✓
- Image signal: $f_{image} = 120$ MHz → Mixer output: $|f_{LO} - f_{image}| = |110 - 120| = 10$ MHz ✓

Both produce the same IF frequency, which is why the image frequency is a problem.

---

### Part (c): IF Filter Requirements (2 points)

**Solution:**

**Given:**
- FM signal bandwidth: $B_{FM} = 200$ kHz = 0.2 MHz

**IF filter requirements:**
- **Center frequency:** $f_{IF} = 10$ MHz
- **Bandwidth:** Must pass the FM signal bandwidth
- **Bandwidth:** $B_{IF} \geq 200$ kHz

**Typical design:**
- IF filter bandwidth: $B_{IF} = 200$ kHz to 250 kHz (slightly wider than signal bandwidth)
- **Passband:** 9.9 MHz to 10.1 MHz (approximately)
- **Stopband:** Must reject frequencies outside the passband

**Answer:**
- IF filter center frequency: **10 MHz**
- IF filter bandwidth: **≥ 200 kHz** (typically 200-250 kHz)
- Must provide sufficient rejection of out-of-band signals

---

## Problem 11: (9 points: 3,3,3) - PM and FM Analysis

**Given:** A modulated RF waveform is given by:
$$s(t) = 100\cos(2\pi \cdot 10^8 t + 4\cos(300\pi t))$$

---

### Part (a): Average Power (3 points)

**Question:** Determine the average power dissipated in a 50-Ω resistor.

**Solution:**

**Given signal:**
$$s(t) = 100\cos(2\pi \cdot 10^8 t + 4\cos(300\pi t))$$

**Carrier amplitude:** $A_c = 100$ V

**For angle-modulated signals (PM or FM), the power is constant:**
$$P_{avg} = \frac{A_c^2}{2}$$

**Substituting:**
$$P_{avg} = \frac{100^2}{2} = \frac{10,000}{2} = 5000 \text{ W}$$

**Power in 50-Ω resistor:**
$$P_R = \frac{V_{rms}^2}{R} = \frac{(A_c/\sqrt{2})^2}{R} = \frac{A_c^2}{2R}$$

$$P_R = \frac{100^2}{2 \times 50} = \frac{10,000}{100} = 100 \text{ W}$$

**Answer:** Average power dissipated in 50-Ω resistor = **100 W**

**Note:** The normalized power is 5000, but the actual power in the resistor is 100 W.

---

### Part (b): Modulating Signal for PM (3 points)

**Question:** Phase Modulation (PM) is applied with a phase deviation constant of 100 rad/V. Find the expression of the modulating signal.

**Solution:**

**PM signal:**
$$s(t) = A_c\cos[\omega_c t + D_p m(t)]$$

**Given:**
- $s(t) = 100\cos(2\pi \cdot 10^8 t + 4\cos(300\pi t))$
- Phase deviation constant: $D_p = 100$ rad/V

**Comparing:**
$$D_p m(t) = 4\cos(300\pi t)$$

**Therefore:**
$$m(t) = \frac{4\cos(300\pi t)}{D_p} = \frac{4\cos(300\pi t)}{100} = 0.04\cos(300\pi t)$$

**Answer:** Modulating signal = **$m(t) = 0.04\cos(300\pi t)$** V

---

### Part (c): Modulating Signal for FM (3 points)

**Question:** Frequency Modulation (FM) is applied with a frequency deviation constant of $10^4$ rad/(V·s). Find the expression of the modulating signal.

**Solution:**

**FM signal:**
$$s(t) = A_c\cos\left[\omega_c t + 2\pi D_f \int_{-\infty}^{t} m(\tau) d\tau\right]$$

**Given:**
- $s(t) = 100\cos(2\pi \cdot 10^8 t + 4\cos(300\pi t))$
- Frequency deviation constant: $D_f = 10^4$ rad/(V·s)

**Comparing:**
$$2\pi D_f \int_{-\infty}^{t} m(\tau) d\tau = 4\cos(300\pi t)$$

**Differentiating both sides:**
$$2\pi D_f m(t) = -4 \times 300\pi \sin(300\pi t) = -1200\pi \sin(300\pi t)$$

**Therefore:**
$$m(t) = \frac{-1200\pi \sin(300\pi t)}{2\pi D_f} = \frac{-1200\pi \sin(300\pi t)}{2\pi \times 10^4}$$

$$m(t) = \frac{-1200 \sin(300\pi t)}{2 \times 10^4} = \frac{-1200 \sin(300\pi t)}{20,000} = -0.06\sin(300\pi t)$$

**Answer:** Modulating signal = **$m(t) = -0.06\sin(300\pi t)$** V

**Note:** Using the identity $\cos(\theta) = \sin(\theta + \pi/2)$, we can also write:
$$m(t) = 0.06\cos(300\pi t + \pi/2)$$

---

## Problem 12: (5 points) - PM Spectrum

**Question:** A phase-modulated (PM) waveform is given by:
$$s(t) = 10\cos(2\pi \cdot 10^6 t + \sin(2000\pi t))$$

Provide a labeled sketch of the magnitude spectrum $|S(f)|$ for positive frequencies showing only the part of the spectrum included in the Carson's bandwidth.

**Solution:**

**Given:**
$$s(t) = 10\cos(2\pi \cdot 10^6 t + \sin(2000\pi t))$$

**Parameters:**
- Carrier amplitude: $A_c = 10$
- Carrier frequency: $f_c = 10^6$ Hz = 1 MHz
- Phase deviation: $\phi(t) = \sin(2000\pi t)$
- Modulating frequency: $f_m = \frac{2000\pi}{2\pi} = 1000$ Hz = 1 kHz

**Modulation index:**
$$\beta = \max|\phi(t)| = \max|\sin(2000\pi t)| = 1$$

**Carson's Rule bandwidth:**
$$B_T \approx 2(\Delta F + B)$$

For sinusoidal modulation:
- Peak frequency deviation: $\Delta F = \beta f_m = 1 \times 1000 = 1000$ Hz
- Modulating signal bandwidth: $B = f_m = 1000$ Hz

$$B_T \approx 2(1000 + 1000) = 4000 \text{ Hz} = 4 \text{ kHz}$$

**Spectrum using Bessel functions:**

For PM with $\beta = 1$:
$$s(t) = 10\sum_{n=-\infty}^{\infty} J_n(1)\cos[2\pi(f_c + nf_m)t]$$

**Bessel function values for $\beta = 1$:**
- $J_0(1) \approx 0.765$
- $J_1(1) \approx 0.440$
- $J_2(1) \approx 0.115$
- $J_3(1) \approx 0.020$
- Higher order terms are negligible

**Spectrum components:**
- Carrier: $f_c = 1$ MHz, Amplitude: $10J_0(1) = 7.65$
- 1st sidebands: $f_c \pm f_m = 1 \text{ MHz} \pm 1 \text{ kHz}$, Amplitude: $10J_1(1) = 4.40$
- 2nd sidebands: $f_c \pm 2f_m = 1 \text{ MHz} \pm 2 \text{ kHz}$, Amplitude: $10J_2(1) = 1.15$
- 3rd sidebands: $f_c \pm 3f_m = 1 \text{ MHz} \pm 3 \text{ kHz}$, Amplitude: $10J_3(1) = 0.20$

**Sketch Description:**

**Magnitude Spectrum $|S(f)|$ for $f > 0$:**

```
Amplitude
  |
10 |                    *
  |                   * *
  |                  *   *
  |                 *     *
  |                *       *
  |               *         *
  |              *           *
  |             *             *
  |            *               *
  |           *                 *
  |          *                   *
  |         *                     *
  |        *                       *
  |       *                         *
  |      *                           *
  |     *                             *
  |    *                               *
  |   *                                 *
  |  *                                   *
  | *                                     *
  |*                                       *
  +----------------------------------------+--------> f (Hz)
  0.996M  0.997M  0.998M  0.999M  1.000M  1.001M  1.002M  1.003M  1.004M
                              f_c
```

**Key frequencies:**
- $f_c - 3f_m = 997$ kHz: Amplitude ≈ 0.20
- $f_c - 2f_m = 998$ kHz: Amplitude ≈ 1.15
- $f_c - f_m = 999$ kHz: Amplitude ≈ 4.40
- $f_c = 1000$ kHz: Amplitude ≈ 7.65 (carrier)
- $f_c + f_m = 1001$ kHz: Amplitude ≈ 4.40
- $f_c + 2f_m = 1002$ kHz: Amplitude ≈ 1.15
- $f_c + 3f_m = 1003$ kHz: Amplitude ≈ 0.20

**Carson's bandwidth:** 996 kHz to 1004 kHz (4 kHz total)

**Answer:** The spectrum shows the carrier and sidebands within Carson's bandwidth, with amplitudes determined by Bessel functions $J_n(1)$.

---

## Problem 13: (5 points) - Envelope Detector Design

**Question:** Consider a diode envelope detector consisting of a diode, resistance $R$ (Ohms) and capacitance $C$ (Farads) that is used for AM demodulation. Assume that the carrier frequency is 1 MHz and that the modulating signal is bandlimited to 5 kHz. Find an appropriate range of values for $RC$.

**Solution:**

**Given:**
- Carrier frequency: $f_c = 1$ MHz = $10^6$ Hz
- Modulating signal bandwidth: $B = 5$ kHz = $5 \times 10^3$ Hz

**Envelope detector requirements:**

**1. RC must be much larger than carrier period (to smooth carrier):**
$$RC \gg \frac{1}{f_c}$$

$$RC \gg \frac{1}{10^6} = 10^{-6} \text{ s}$$

**2. RC must be much smaller than modulating signal period (to follow envelope):**
$$RC \ll \frac{1}{B}$$

$$RC \ll \frac{1}{5 \times 10^3} = 2 \times 10^{-4} \text{ s} = 200 \mu\text{s}$$

**Combining both conditions:**
$$10^{-6} \text{ s} \ll RC \ll 2 \times 10^{-4} \text{ s}$$

**Typical design rule (using factors of 10):**
$$10 \times \frac{1}{f_c} < RC < \frac{1}{10B}$$

$$10 \times 10^{-6} < RC < \frac{1}{10 \times 5 \times 10^3}$$

$$10^{-5} < RC < 2 \times 10^{-5}$$

**More practical range:**
$$RC = (1 \text{ to } 10) \times 10^{-5} \text{ s}$$

**Answer:** Appropriate range for $RC$:
$$10^{-5} \text{ s} < RC < 2 \times 10^{-5} \text{ s}$$

Or: **10 μs < RC < 20 μs**

**Example values:**
- $R = 10$ kΩ, $C = 1$ nF → $RC = 10$ μs ✓
- $R = 5$ kΩ, $C = 2$ nF → $RC = 10$ μs ✓
- $R = 10$ kΩ, $C = 1.5$ nF → $RC = 15$ μs ✓

---

## Problem 14: (10 points: 4,2,4) - FM/PM Instantaneous Frequency

**Given:** A modulated signal is given by:
$$s(t) = \cos\left(2\pi f_c t + 5\int_{-\infty}^{t} m(\sigma) d\sigma\right)$$

where $f_c$ is the carrier frequency and $m(t)$ is shown in the figure below.

---

### Part (a): Instantaneous Frequency Sketch (4 points)

**Question:** Provide a labeled sketch of the instantaneous frequency.

**Solution:**

**Given signal:**
$$s(t) = \cos\left(2\pi f_c t + 5\int_{-\infty}^{t} m(\sigma) d\sigma\right)$$

**Phase:**
$$\phi(t) = 2\pi f_c t + 5\int_{-\infty}^{t} m(\sigma) d\sigma$$

**Instantaneous frequency:**
$$f_i(t) = \frac{1}{2\pi}\frac{d\phi(t)}{dt} = f_c + \frac{5}{2\pi}m(t)$$

**From the figure, $m(t)$ appears to be a periodic signal. The instantaneous frequency will be:**
$$f_i(t) = f_c + \frac{5}{2\pi}m(t)$$

**Sketch Description:**

The instantaneous frequency follows the shape of $m(t)$ scaled by $\frac{5}{2\pi}$ and shifted by $f_c$.

**Key features:**
- Base frequency: $f_c$
- Variation: Proportional to $m(t)$
- Peak frequency deviation: $\Delta F = \frac{5}{2\pi} \times \max|m(t)|$

**Answer:** The instantaneous frequency sketch shows $f_i(t) = f_c + \frac{5}{2\pi}m(t)$, following the shape of $m(t)$ around the carrier frequency $f_c$.

---

### Part (b): Peak Frequency Deviation (2 points)

**Question:** Find the peak frequency deviation.

**Solution:**

**Peak frequency deviation:**
$$\Delta F = \max|f_i(t) - f_c| = \max\left|\frac{5}{2\pi}m(t)\right| = \frac{5}{2\pi}\max|m(t)|$$

**From the figure, if $m(t)$ has peak value $A_m$:**
$$\Delta F = \frac{5A_m}{2\pi}$$

**Answer:** Peak frequency deviation = **$\frac{5}{2\pi}\max|m(t)|$** Hz

**Note:** The exact value depends on the peak value of $m(t)$ shown in the figure.

---

### Part (c): Best Figure Description (4 points)

**Question:** Which one of the below figures best describes the variation of $s(t)$? Justify your answer.

**Solution:**

**Analysis of $s(t)$:**

The signal is:
$$s(t) = \cos\left(2\pi f_c t + 5\int_{-\infty}^{t} m(\sigma) d\sigma\right)$$

**Key observations:**

1. **This is an FM signal** (frequency modulation via integration)
2. **Amplitude is constant** (cosine function has constant amplitude = 1)
3. **Frequency varies** according to $m(t)$
4. **Phase varies** according to the integral of $m(t)$

**Characteristics to look for in the figures:**

- **Constant amplitude** (envelope should be flat)
- **Frequency variation** (spacing between zero-crossings changes)
- **No amplitude modulation** (should not show envelope following $m(t)$)

**Answer:** The figure that best describes $s(t)$ would be one that shows:
- **Constant amplitude** (flat envelope)
- **Variable frequency** (changing zero-crossing spacing)
- **Frequency following the pattern of $m(t)$** (faster when $m(t)$ is positive, slower when negative)

**Justification:**
- Since $s(t)$ is a pure FM signal, it has constant amplitude
- The frequency deviation is proportional to $m(t)$
- The signal should show frequency modulation, not amplitude modulation
- Figures showing amplitude variation (envelope following $m(t)$) are incorrect
- The correct figure should show constant amplitude with frequency that varies according to $m(t)$

**Note:** Without seeing the actual figures, the correct answer would be the one showing constant amplitude with variable frequency spacing.

---

## Summary

**Total Points:** 100 points

| Problem | Points | Main Topics |
|---------|--------|-------------|
| 1 | 10 | DM, TDM, ADM, DSB-SC, Detectors |
| 2 | 5 | ISI, Nyquist Criterion |
| 3 | 5 | Delta Modulation |
| 4 | 10 | TDM System Design |
| 5 | 10 | Power Calculations (DSB-SC, FM, AM, SSB) |
| 6 | 10 | AM Detection |
| 7 | 5 | LSSB Spectrum |
| 8 | 5 | Harmonic Distortion |
| 9 | 5 | Peak Envelope Power |
| 10 | 6 | Superheterodyne Receiver |
| 11 | 9 | PM/FM Analysis |
| 12 | 5 | PM Spectrum |
| 13 | 5 | Envelope Detector |
| 14 | 10 | FM Instantaneous Frequency |

---

*End of Solutions*

*Good luck with your studies!*


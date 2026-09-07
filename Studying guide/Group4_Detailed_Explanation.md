# GROUP 4 - Digital & Pulse Modulation: Detailed Explanation

## Lecture 12: Pulse Modulation Techniques

---

## Table of Contents

1. [Introduction: What is Pulse Modulation?](#introduction)
2. [Sampling Theorem - The Foundation](#sampling-theorem)
3. [Pulse Amplitude Modulation (PAM)](#pam)
4. [Pulse Width Modulation (PWM)](#pwm)
5. [Pulse Position Modulation (PPM)](#ppm)
6. [Delta Modulation (DM)](#delta-modulation)
7. [Quantization and Quantization Noise](#quantization)
8. [Comparison of Pulse Modulation Schemes](#comparison)
9. [Detailed Examples](#detailed-examples)
10. [Key Takeaways](#key-takeaways)

---

## 1. Introduction: What is Pulse Modulation? {#introduction}

### The Basic Idea

**Pulse Modulation** is a technique where an analog signal is converted into a series of pulses, where some characteristic of the pulses (amplitude, width, or position) varies according to the analog signal.

**Why Pulse Modulation?**
- Allows **time-division multiplexing** (multiple signals on one channel)
- Enables **digital transmission** (can quantize pulse parameters)
- **Noise resistance** - pulses are easier to regenerate than analog signals
- **Efficient bandwidth usage** - can interleave multiple signals

### Types of Pulse Modulation

There are **three main types** of pulse modulation:

1. **PAM (Pulse Amplitude Modulation)** - Pulse **amplitude** varies
2. **PWM (Pulse Width Modulation)** - Pulse **width** varies
3. **PPM (Pulse Position Modulation)** - Pulse **position** varies

**Plus:**
4. **Delta Modulation (DM)** - Special case using 1-bit quantization

### The Modulation Process

**Step 1:** Sample the analog signal at regular intervals
- Sample at rate $f_s$ (samples per second)
- Get discrete-time samples

**Step 2:** Modulate a pulse train
- Create pulses at sampling instants
- Vary pulse characteristic (amplitude/width/position) according to sample value

**Step 3:** Transmit the pulse train
- Pulses can be transmitted over channel
- Multiple signals can be interleaved (TDM)

**Step 4:** Demodulate at receiver
- Extract sample values from pulses
- Reconstruct analog signal using lowpass filter

---

## 2. Sampling Theorem - The Foundation {#sampling-theorem}

### Nyquist-Shannon Sampling Theorem

**The fundamental theorem of digital signal processing:**

> An analog signal with bandwidth $B$ can be perfectly reconstructed from its samples if the sampling rate $f_s$ satisfies:
> $$f_s \geq 2B$$

**What This Means:**
- Must sample at **at least twice** the highest frequency
- $f_s = 2B$ is called the **Nyquist rate**
- $f_s > 2B$ provides margin for practical filters

### Aliasing

**What happens if $f_s < 2B$?**

**Aliasing** occurs - high frequencies "fold back" into lower frequencies, causing distortion.

**Visual Example:**
```
Original signal:     /‾‾‾\___/‾‾‾\___/‾‾‾\___
                    (high frequency)
                    
Undersampled:       /‾‾‾\___/‾‾‾\___
                    (appears as lower frequency - aliasing!)
```

### Anti-Aliasing Filter

Before sampling, we use an **anti-aliasing filter**:
- Lowpass filter with cutoff at $B$
- Removes frequencies above $B$
- Prevents aliasing

### Sampling Process

**Mathematical Representation:**

The sampled signal is:

$$x_s(t) = x(t) \cdot \sum_{n=-\infty}^{+\infty} \delta(t - nT_s)$$

where:
- $T_s = \frac{1}{f_s}$ is the **sampling period**
- $\delta(t)$ is the Dirac delta function (impulse)

**In Frequency Domain:**

The spectrum of the sampled signal is:
$$X_s(f) = f_s \sum_{k=-\infty}^{+\infty} X(f - kf_s)$$

**What This Means:**
- Original spectrum $X(f)$ is **replicated** at multiples of $f_s$
- If $f_s \geq 2B$, replicas don't overlap
- Can recover original by lowpass filtering

---

## 3. Pulse Amplitude Modulation (PAM) {#pam}

### The Concept

**Pulse Amplitude Modulation (PAM)** is where the **amplitude** of regularly-spaced pulses varies according to the instantaneous value of the analog signal.

### Generation Process

**Step 1:** Sample the analog signal
- Sample $m(t)$ at rate $f_s$
- Get samples: $m(nT_s)$ where $n = 0, 1, 2, \ldots$

**Step 2:** Create pulse train
- Generate pulses at sampling instants
- Pulse amplitude = sample value
- Pulse width = $\tau$ (usually small compared to $T_s$)

**Mathematical Representation:**

$$s_{PAM}(t) = \sum_{n=-\infty}^{+\infty} m(nT_s) p(t - nT_s)$$

where $p(t)$ is the pulse shape (usually rectangular).

### Pulse Shape

**Rectangular Pulse:**

$$p(t) = \begin{cases}
1, & 0 \leq t < \tau \\
0, & \text{otherwise}
\end{cases}$$

**Key Parameters:**
- **Pulse width:** $\tau$
- **Sampling period:** $T_s = \frac{1}{f_s}$
- **Duty cycle:** $\frac{\tau}{T_s}$ (usually small, e.g., 0.1)

### Visual Example

```
Analog signal:      ___/‾‾‾\___/‾‾‾\___
                   
Sampling instants:  |   |   |   |   |
                   
PAM signal:         |‾| |‾‾| |‾| |‾‾|
                    (amplitude varies)
```

### Spectrum of PAM Signal

The spectrum contains:
1. **Baseband component** - the original signal spectrum (scaled)
2. **Harmonic components** - at multiples of $f_s$

**Recovery:**
- Use **lowpass filter** with cutoff at $B$
- Filters out harmonic components
- Recovers the original analog signal

### Advantages

1. **Simple to generate** - just multiply signal by pulse train
2. **Simple to demodulate** - lowpass filter
3. **Time-division multiplexing** - can interleave multiple PAM signals

### Disadvantages

1. **Sensitive to noise** - noise directly affects pulse amplitude
2. **Requires linear amplification** - amplitude must be preserved
3. **Bandwidth** - needs bandwidth for pulse harmonics

---

## 4. Pulse Width Modulation (PWM) {#pwm}

### The Concept

**Pulse Width Modulation (PWM)** is where the **width** (duration) of regularly-spaced pulses varies according to the instantaneous value of the analog signal, while the amplitude remains constant.

### Generation Process

**Step 1:** Sample the analog signal
- Sample $m(t)$ at rate $f_s$
- Get samples: $m(nT_s)$

**Step 2:** Compare with sawtooth/ramp
- Generate sawtooth wave synchronized with sampling
- Compare sample value with sawtooth
- Pulse width = time until sawtooth exceeds sample

**Mathematical Representation:**

For a sample value $m(nT_s)$, the pulse width is:

$$\tau(n) = \tau_0 + k \cdot m(nT_s)$$

where:
- $\tau_0$ is the **minimum pulse width** (for $m = 0$)
- $k$ is the **width sensitivity**

**Constraint:** $0 < \tau(n) < T_s$ (pulse must fit in sampling period)

### Visual Example

```
Analog signal:      ___/‾‾‾\___/‾‾‾\___
                   
Sampling instants:  |   |   |   |   |
                   
PWM signal:        |‾‾‾| |‾‾‾‾‾| |‾| |‾‾‾‾|
                    (width varies, amplitude constant)
```

### Generation Circuit

**Sawtooth Comparison Method:**

1. Generate sawtooth wave: $r(t) = \frac{t \mod T_s}{T_s}$ (0 to 1)
2. Sample analog signal: $m(nT_s)$
3. Compare: If $m(nT_s) > r(t)$, pulse is HIGH; else LOW
4. Result: Pulse width proportional to sample value

### Demodulation

**Method 1: Lowpass Filtering**
- PWM signal has average value proportional to pulse width
- Lowpass filter extracts the average
- Recovers the analog signal

**Method 2: Integration**
- Integrate PWM signal over each period
- Integration result = pulse width
- Proportional to sample value

### Advantages

1. **Constant amplitude** - easier to amplify (can use switching amplifiers)
2. **Noise resistant** - width less sensitive to noise than amplitude
3. **Power efficient** - can use efficient switching circuits

### Disadvantages

1. **More complex generation** - requires sawtooth and comparator
2. **Bandwidth** - needs bandwidth for varying pulse widths
3. **Synchronization** - requires precise timing

### Applications

- **Motor control** - speed control via PWM
- **Power supplies** - voltage regulation
- **LED dimming** - brightness control
- **Audio amplifiers** - Class D amplifiers

---

## 5. Pulse Position Modulation (PPM) {#ppm}

### The Concept

**Pulse Position Modulation (PPM)** is where the **position** (timing) of narrow pulses varies according to the instantaneous value of the analog signal, while both amplitude and width remain constant.

### Generation Process

**Step 1:** Generate PWM signal first
- Create PWM from analog signal
- PWM pulse width varies with signal

**Step 2:** Differentiate PWM signal
- Differentiate the PWM signal
- Get impulses at pulse edges
- Use leading edge (or trailing edge) only

**Step 3:** Result: Narrow pulses at varying positions
- Pulse position = function of sample value
- Pulse width = very narrow (ideally impulse)
- Pulse amplitude = constant

**Mathematical Representation:**

For a sample value $m(nT_s)$, the pulse position is:

$$t_p(n) = nT_s + t_0 + k \cdot m(nT_s)$$

where:
- $t_0$ is the **reference position** (for $m = 0$)
- $k$ is the **position sensitivity**
- Constraint: Pulse must be within $[nT_s, (n+1)T_s]$

### Visual Example

```
Analog signal:      ___/‾‾‾\___/‾‾‾\___
                   
Sampling instants:  |   |   |   |   |
                   
PPM signal:         | |   | |     | |   | |
                    (position varies, width/amplitude constant)
```

### Generation from PWM

**Method:**
1. Generate PWM signal
2. Differentiate: $\frac{d}{dt}$(PWM)
3. Get impulses at edges
4. Filter to get only leading (or trailing) edges
5. Result: PPM signal

### Demodulation

**Method 1: Convert to PWM then to PAM**
1. Convert PPM to PWM (integrate or use monostable)
2. Convert PWM to PAM (lowpass filter)
3. Recover analog signal

**Method 2: Direct conversion**
1. Measure time between pulses
2. Time difference proportional to sample value
3. Reconstruct analog signal

### Advantages

1. **Constant amplitude and width** - very robust
2. **Highly noise resistant** - only position matters
3. **Power efficient** - narrow pulses use less average power

### Disadvantages

1. **Complex generation** - requires PWM first
2. **Requires precise timing** - position must be accurately measured
3. **Bandwidth** - needs bandwidth for position variations

### Applications

- **Optical communication** - fiber optics
- **Remote control systems** - infrared remotes
- **Radar systems** - pulse position encoding

---

## 6. Delta Modulation (DM) {#delta-modulation}

### The Concept

**Delta Modulation (DM)** is a special form of pulse modulation that uses **1-bit quantization** - it only transmits whether the signal is increasing or decreasing.

### How It Works

**Encoder (Transmitter):**

1. **Predictor:** Maintains a predicted value $\hat{x}(n)$
2. **Comparator:** Compares input $x(n)$ with prediction
3. **Quantizer:** Outputs 1-bit:
   - If $x(n) > \hat{x}(n)$ → output = +1 (or HIGH)
   - If $x(n) < \hat{x}(n)$ → output = -1 (or LOW)
4. **Integrator:** Updates prediction:
   - $\hat{x}(n+1) = \hat{x}(n) + \Delta \cdot \text{output}$
   - Where $\Delta$ is the **step size**

**Decoder (Receiver):**

1. Receives 1-bit stream
2. Integrates the bits (same as encoder)
3. Reconstructs signal: $\hat{x}(n)$

### Mathematical Representation

**Encoder:**

$$d(n) = \begin{cases}
+1, & \text{if } x(n) > \hat{x}(n) \\
-1, & \text{if } x(n) < \hat{x}(n)
\end{cases}$$

$$\hat{x}(n+1) = \hat{x}(n) + \Delta \cdot d(n)$$

**Decoder:**
$$\hat{x}(n+1) = \hat{x}(n) + \Delta \cdot d(n)$$

(Same equation - encoder and decoder are identical!)

### Visual Example

```
Analog signal:      ___/‾‾‾\___/‾‾‾\___
                   
Step approximation: |‾|‾|‾|_|_|_|‾|‾|‾|
                    (staircase following signal)
                   
DM output:          + + + - - - + + +
                    (1-bit: up or down)
```

### Step Size

The **step size** $\Delta$ is crucial:

**Too small:**
- **Slope overload** - can't follow rapid changes
- Signal changes faster than step size can track
- Distortion occurs

**Too large:**
- **Granular noise** - large quantization error
- Signal has large "steps"
- Poor signal quality

**Optimal:** Balance between slope overload and granular noise

### Slope Overload

**Condition for slope overload:**

If the signal slope exceeds the maximum tracking rate:
$$\left|\frac{dx(t)}{dt}\right| > \frac{\Delta}{T_s}$$

Then slope overload occurs.

**Solution:**
- Increase step size $\Delta$
- Or increase sampling rate $f_s = \frac{1}{T_s}$

### Granular Noise

Even when tracking correctly, there's **quantization error**:
- Difference between signal and step approximation
- Causes "granular" noise
- Reduces with smaller step size

**Trade-off:**
- Small $\Delta$ → less granular noise, but more slope overload
- Large $\Delta$ → less slope overload, but more granular noise

### Adaptive Delta Modulation (ADM)

**Solution to the trade-off:** Vary step size adaptively!

**Principle:**
- If signal changes rapidly → increase $\Delta$ (prevent slope overload)
- If signal changes slowly → decrease $\Delta$ (reduce granular noise)

**Algorithm:**
- Monitor consecutive bits
- If many same bits → signal changing rapidly → increase $\Delta$
- If alternating bits → signal stable → decrease $\Delta$

### Advantages

1. **Very simple** - only 1 bit per sample
2. **Simple hardware** - just comparator and integrator
3. **Low bit rate** - $R = f_s$ bits/second
4. **Robust** - only needs to detect up/down

### Disadvantages

1. **Slope overload** - can't follow rapid changes
2. **Granular noise** - quantization error
3. **Requires high sampling rate** - typically $f_s > 10B$ (much higher than Nyquist)

### Comparison with PCM

| Feature | Delta Modulation | PCM |
|---------|------------------|-----|
| Bits per sample | 1 | 8-16 |
| Sampling rate | High ($>10B$) | Low ($2B$) |
| Complexity | Low | High |
| Quality | Moderate | High |
| Bit rate | $f_s$ | $8f_s$ to $16f_s$ |

---

## 7. Quantization and Quantization Noise {#quantization}

### What is Quantization?

**Quantization** is the process of converting a continuous (analog) value into a discrete (digital) value.

**Example:**
- Analog voltage: 3.7 V
- Quantized to nearest level: 4 V (if levels are 0, 1, 2, 3, 4, 5, ...)

### Uniform Quantization

**Uniform quantizer** has equal spacing between levels:

**Quantization levels:**
$$q_k = k \cdot \Delta, \quad k = -N/2, \ldots, -1, 0, 1, \ldots, N/2-1$$

where:
- $\Delta$ is the **quantization step size**
- $N$ is the **number of levels**
- Range: $[-N\Delta/2, N\Delta/2]$

### Quantization Error

**Quantization error** (noise) is the difference between actual and quantized value:

$$e(n) = x(n) - Q[x(n)]$$

where $Q[\cdot]$ is the quantization function.

**Properties:**
- Error is bounded: $|e(n)| \leq \frac{\Delta}{2}$
- Error is approximately **uniformly distributed** (for many samples)
- Error is **uncorrelated** with signal (for many samples)

### Quantization Noise Power

**For uniform quantizer with step size $\Delta$:**

The quantization noise power is:

$$N_q = \frac{\Delta^2}{12}$$

**Derivation:**
- Error is uniformly distributed in $[-\Delta/2, \Delta/2]$
- Variance of uniform distribution: $\sigma^2 = \frac{(\Delta)^2}{12}$
- Power = variance for zero-mean process

### Signal-to-Quantization-Noise Ratio (SQNR)

**SQNR** measures the quality of quantization:

$$\text{SQNR} = \frac{\text{Signal Power}}{\text{Quantization Noise Power}} = \frac{S}{N_q}$$

**For uniform quantizer:**

If signal power is $S$ and quantization step is $\Delta$:

$$\text{SQNR} = \frac{S}{\Delta^2/12} = \frac{12S}{\Delta^2}$$

**In decibels:**
$$\text{SQNR (dB)} = 10\log_{10}\left(\frac{12S}{\Delta^2}\right)$$

### SQNR vs Number of Bits

**Relationship:**

If we have $b$ bits, we have $N = 2^b$ quantization levels.

If signal range is $V_{pp}$ (peak-to-peak), then:
$$\Delta = \frac{V_{pp}}{2^b}$$

**SQNR becomes:**
$$\text{SQNR (dB)} = 10\log_{10}\left(\frac{12S \cdot 2^{2b}}{V_{pp}^2}\right)$$

For sinusoidal signal with amplitude $A$:
- Signal power: $S = \frac{A^2}{2}$
- Peak-to-peak: $V_{pp} = 2A$
- SQNR: $\text{SQNR (dB)} \approx 6.02b + 1.76$ dB

**Rule of thumb:** Each additional bit adds **6 dB** to SQNR!

### Example

**8-bit quantizer:**
- SQNR ≈ $6.02 \times 8 + 1.76 = 48.16 + 1.76 = 49.92$ dB

**16-bit quantizer:**
- SQNR ≈ $6.02 \times 16 + 1.76 = 96.32 + 1.76 = 98.08$ dB

**Much better quality!**

---

## 8. Comparison of Pulse Modulation Schemes {#comparison}

### Comparison Table

| Feature | PAM | PWM | PPM | DM |
|---------|-----|-----|-----|-----|
| **Varying Parameter** | Amplitude | Width | Position | 1-bit |
| **Constant Parameters** | Width, Position | Amplitude, Position | Amplitude, Width | - |
| **Noise Resistance** | Low | Medium | High | Medium |
| **Complexity** | Low | Medium | High | Low |
| **Bandwidth** | Medium | Medium | Medium | Low |
| **Power Efficiency** | Low | High | High | Medium |
| **TDM Compatibility** | High | Medium | Low | High |
| **Applications** | Multiplexing | Motor control | Optical comm | Voice |

### When to Use Each

**PAM:**
- Time-division multiplexing
- When simplicity is important
- When linearity can be maintained

**PWM:**
- Motor speed control
- Power supplies
- When constant amplitude is beneficial
- Switching amplifiers

**PPM:**
- Optical communication
- When maximum noise resistance needed
- When power efficiency critical

**DM:**
- Voice communication
- When low bit rate needed
- Simple systems
- When moderate quality acceptable

---

## 9. Detailed Examples {#detailed-examples}

### Example 1: PAM Signal Generation

**Given:**
- Analog signal: $m(t) = 5\cos(2\pi \cdot 1000t)$ (1 kHz, amplitude 5 V)
- Sampling rate: $f_s = 5000$ Hz
- Pulse width: $\tau = 0.1$ ms

**Find:**
1. Sampling period $T_s$
2. Number of samples per period of $m(t)$
3. Sketch the PAM signal
4. Bandwidth required

**Solution:**

1. **Sampling period:**
   $$T_s = \frac{1}{f_s} = \frac{1}{5000} = 0.2 \text{ ms}$$

2. **Period of $m(t)$:**
   $$T_m = \frac{1}{1000} = 1 \text{ ms}$$

   **Samples per period:**
   $$\frac{T_m}{T_s} = \frac{1}{0.2} = 5 \text{ samples}$$

3. **PAM Signal:**
   - Pulses at $t = 0, 0.2, 0.4, 0.6, 0.8, 1.0, \ldots$ ms
   - Pulse amplitudes = $m(nT_s)$ values
   - Pulse width = 0.1 ms

4. **Bandwidth:**
   - Baseband: $B = 1000$ Hz
   - PAM harmonics at $f_s = 5000$ Hz, $2f_s = 10000$ Hz, etc.
   - Need lowpass filter with cutoff ≈ 1000 Hz
   - Bandwidth ≈ $f_s = 5000$ Hz (to accommodate harmonics)

---

### Example 2: Delta Modulation

**Given:**
- Analog signal: $x(t) = 3\sin(2\pi \cdot 500t)$ (500 Hz, amplitude 3 V)
- Sampling rate: $f_s = 10000$ Hz
- Step size: $\Delta = 0.1$ V

**Find:**
1. Check for slope overload
2. Maximum signal slope
3. Maximum tracking rate of DM
4. Determine if slope overload occurs

**Solution:**

1. **Signal slope:**
   $$\frac{dx(t)}{dt} = 3 \cdot 2\pi \cdot 500 \cos(2\pi \cdot 500t) = 3000\pi \cos(2\pi \cdot 500t)$$

2. **Maximum signal slope:**
   $$\max\left|\frac{dx(t)}{dt}\right| = 3000\pi \approx 9425 \text{ V/s}$$

3. **Maximum tracking rate:**
   $$\frac{\Delta}{T_s} = \frac{0.1}{1/10000} = 1000 \text{ V/s}$$

4. **Slope overload check:**
   - Maximum signal slope: 9425 V/s
   - Maximum tracking rate: 1000 V/s
   - **9425 > 1000** → **Slope overload occurs!**

**Solution:** Increase step size or sampling rate
- New step size: $\Delta = 1.0$ V → tracking rate = 10000 V/s (OK)
- Or increase $f_s$ to 100000 Hz → tracking rate = 10000 V/s (OK)

---

### Example 3: Quantization Noise

**Given:**
- Signal: $x(t) = 4\cos(2\pi \cdot 1000t)$ (amplitude 4 V)
- Quantizer: 8-bit uniform quantizer
- Signal range: -5 V to +5 V

**Find:**
1. Quantization step size $\Delta$
2. Quantization noise power $N_q$
3. Signal power $S$
4. SQNR in dB

**Solution:**

1. **Step size:**
   - Number of levels: $N = 2^8 = 256$
   - Range: $V_{pp} = 5 - (-5) = 10$ V
   - Step size: $\Delta = \frac{10}{256} = 0.03906$ V

2. **Quantization noise power:**
   $$N_q = \frac{\Delta^2}{12} = \frac{(0.03906)^2}{12} = \frac{0.001526}{12} = 1.272 \times 10^{-4} \text{ V}^2$$

3. **Signal power:**
   $$S = \frac{A^2}{2} = \frac{4^2}{2} = 8 \text{ V}^2$$

4. **SQNR:**
   $$\text{SQNR} = \frac{S}{N_q} = \frac{8}{1.272 \times 10^{-4}} = 62,893$$

   **In dB:**
   $$\text{SQNR (dB)} = 10\log_{10}(62,893) = 47.99 \text{ dB}$$

   **Using formula:** $\text{SQNR (dB)} \approx 6.02 \times 8 + 1.76 = 48.16 + 1.76 = 49.92$ dB

   (Slight difference due to signal not using full range)

---

## 10. Key Takeaways {#key-takeaways}

### Essential Concepts

1. **Sampling Theorem:** Must sample at $f_s \geq 2B$ to avoid aliasing
2. **PAM:** Amplitude varies, simplest but noise-sensitive
3. **PWM:** Width varies, constant amplitude, good for power applications
4. **PPM:** Position varies, most noise-resistant, constant amplitude/width
5. **Delta Modulation:** 1-bit quantization, simple but limited quality
6. **Quantization Noise:** Inevitable error, power = $\Delta^2/12$
7. **SQNR:** Improves by 6 dB per additional bit

### Key Formulas

**Sampling:**
- Nyquist rate: $f_s \geq 2B$
- Sampling period: $T_s = \frac{1}{f_s}$

**PAM:**
$$s_{PAM}(t) = \sum_{n=-\infty}^{+\infty} m(nT_s) p(t - nT_s)$$

**Delta Modulation:**
$$\hat{x}(n+1) = \hat{x}(n) + \Delta \cdot d(n)$$

**Quantization:**
- Step size: $\Delta = \frac{V_{pp}}{2^b}$
- Noise power: $N_q = \frac{\Delta^2}{12}$
- SQNR (dB): $\approx 6.02b + 1.76$ (for sinusoidal signal)

**Slope Overload (DM):**
$$\left|\frac{dx(t)}{dt}\right| > \frac{\Delta}{T_s}$$

### Common Mistakes to Avoid

1. **Undersampling** - forgetting $f_s \geq 2B$ causes aliasing
2. **Slope overload in DM** - step size too small for signal changes
3. **Confusing PWM and PPM** - width vs position
4. **Quantization noise** - forgetting it's always present
5. **SQNR calculation** - using wrong formula or units

### Study Tips

1. **Understand sampling:**
   - Nyquist theorem is fundamental
   - Aliasing is the main problem to avoid

2. **Know the differences:**
   - PAM: amplitude varies
   - PWM: width varies
   - PPM: position varies
   - DM: 1-bit up/down

3. **Quantization:**
   - Always causes noise
   - More bits = better quality
   - 6 dB per bit rule

4. **Delta Modulation:**
   - Simple but limited
   - Slope overload vs granular noise trade-off
   - Adaptive DM solves the trade-off

5. **Practice calculations:**
   - Sampling rates
   - Quantization step sizes
   - SQNR calculations
   - Slope overload checks

---

## Summary of Key Formulas

### Sampling
- **Nyquist rate:** $f_s \geq 2B$
- **Sampling period:** $T_s = \frac{1}{f_s}$

### PAM
$$s_{PAM}(t) = \sum_{n=-\infty}^{+\infty} m(nT_s) p(t - nT_s)$$

### Delta Modulation
$$\hat{x}(n+1) = \hat{x}(n) + \Delta \cdot d(n)$$
$$\text{Slope overload if: } \left|\frac{dx(t)}{dt}\right| > \frac{\Delta}{T_s}$$

### Quantization
- **Step size:** $\Delta = \frac{V_{pp}}{2^b}$
- **Noise power:** $N_q = \frac{\Delta^2}{12}$
- **SQNR (dB):** $\approx 6.02b + 1.76$ (sinusoidal signal)

---

*End of Group 4 Detailed Explanation*


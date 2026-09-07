# Group 4 Exercises - Solutions Part 1

This document contains solutions for Exercise Sets 1-6 of Group 4 exercises.

---

## Exercise Set 1: Sampling Theorem - Solutions

### Problem 1.1 Solution

**Given:**
- Bandwidth: $B = 4$ kHz

**a) Minimum sampling rate (Nyquist rate):**
$$f_s \geq 2B = 2 \times 4 = 8 \text{ kHz}$$

**Answer:** $f_s = 8$ kHz (minimum)

**b) Sampling period at Nyquist rate:**
$$T_s = \frac{1}{f_s} = \frac{1}{8000} = 0.125 \text{ ms} = 125 \mu\text{s}$$

**c) Sampling period with oversampling ($f_s = 10$ kHz):**
$$T_s = \frac{1}{10000} = 0.1 \text{ ms} = 100 \mu\text{s}$$

---

### Problem 1.2 Solution

**Given:**
$$X(f) = \begin{cases}
A, & |f| \leq 3 \text{ kHz} \\
0, & |f| > 3 \text{ kHz}
\end{cases}$$

**a) Bandwidth:**
$$B = 3 \text{ kHz}$$

**b) Minimum sampling rate:**
$$f_s \geq 2B = 2 \times 3 = 6 \text{ kHz}$$

**Answer:** $f_s = 6$ kHz (minimum)

**c) If $f_s = 4$ kHz:**
- $f_s = 4$ kHz $< 2B = 6$ kHz
- **Aliasing occurs!** The spectrum replicas will overlap
- High frequencies will fold back into the baseband
- Signal cannot be perfectly reconstructed

**d) If $f_s = 8$ kHz:**
- $f_s = 8$ kHz $> 2B = 6$ kHz
- **No aliasing!** The spectrum replicas don't overlap
- Signal can be perfectly reconstructed with a lowpass filter
- This is oversampling (provides margin for practical filters)

---

### Problem 1.3 Solution

**Given:**
- Sampling rate: $f_s = 8$ kHz
- Signal components: $f_1 = 2$ kHz, $f_2 = 3$ kHz, $f_3 = 5$ kHz

**a) Frequencies in sampled signal spectrum:**

The sampled signal spectrum contains replicas at:
- Baseband: $f_1 = 2$ kHz, $f_2 = 3$ kHz, $f_3 = 5$ kHz
- At $f_s = 8$ kHz: $8 \pm 2 = 6, 10$ kHz; $8 \pm 3 = 5, 11$ kHz; $8 \pm 5 = 3, 13$ kHz
- At $2f_s = 16$ kHz: $16 \pm 2, 16 \pm 3, 16 \pm 5$, etc.

**Note:** $f_3 = 5$ kHz is close to $f_s/2 = 4$ kHz, so it's near the Nyquist limit.

**b) If $f_3 = 7$ kHz:**

The Nyquist frequency is $f_s/2 = 4$ kHz.

For $f_3 = 7$ kHz:
- $7 > 4$ kHz, so it will alias
- Aliased frequency: $f_s - f_3 = 8 - 7 = 1$ kHz

**Answer:** Aliased to $1$ kHz

**c) If $f_3 = 9$ kHz:**

For $f_3 = 9$ kHz:
- $9 > 4$ kHz, so it will alias
- First, find which "zone" it's in: $9/4 = 2.25$, so it's in the 2nd zone
- Aliased frequency: $f_s - (f_3 - f_s) = 8 - (9 - 8) = 7$ kHz
- Or more simply: $f_3 - f_s = 9 - 8 = 1$ kHz (folds to baseband)

Actually, let's be more careful:
- $f_3 = 9$ kHz
- $f_s/2 = 4$ kHz
- $f_3$ is in the range $(f_s, 3f_s/2) = (8, 12)$
- Aliased frequency: $f_s - (f_3 - f_s) = 8 - 1 = 7$ kHz

Wait, that's not right. Let me recalculate:
- For frequencies above $f_s/2$, they alias to $f_s - f$
- But $f_3 = 9$ kHz is above $f_s = 8$ kHz
- So it aliases to: $f_3 - kf_s$ where $k$ is chosen so result is in $[0, f_s/2]$
- $9 - 8 = 1$ kHz

**Answer:** Aliased to $1$ kHz (or $7$ kHz depending on convention, but typically folds to $|f_s - f_3| = 1$ kHz in baseband)

---

## Exercise Set 2: Pulse Amplitude Modulation (PAM) - Solutions

### Problem 2.1 Solution

**Given:**
- Analog signal: $m(t) = 3\cos(2\pi \cdot 2000t)$
- Sampling rate: $f_s = 8000$ Hz
- Pulse width: $\tau = 50$ $\mu$s

**a) Sampling period:**
$$T_s = \frac{1}{f_s} = \frac{1}{8000} = 0.125 \text{ ms} = 125 \mu\text{s}$$

**b) Number of samples per period of $m(t)$:**

Period of $m(t)$:
$$T_m = \frac{1}{2000} = 0.5 \text{ ms}$$

Samples per period:
$$\frac{T_m}{T_s} = \frac{0.5}{0.125} = 4 \text{ samples}$$

**c) Duty cycle:**
$$\frac{\tau}{T_s} = \frac{50 \times 10^{-6}}{125 \times 10^{-6}} = \frac{50}{125} = 0.4 = 40\%$$

**d) PAM signal expression:**

$$s_{PAM}(t) = \sum_{n=-\infty}^{+\infty} m(nT_s) p(t - nT_s)$$

where:
- $m(nT_s) = 3\cos(2\pi \cdot 2000 \cdot nT_s) = 3\cos(2\pi \cdot 2000 \cdot n/8000) = 3\cos(\pi n/2)$
- $p(t)$ is a rectangular pulse of width $\tau = 50$ $\mu$s and amplitude 1

$$s_{PAM}(t) = \sum_{n=-\infty}^{+\infty} 3\cos\left(\frac{\pi n}{2}\right) \cdot \text{rect}\left(\frac{t - nT_s}{\tau}\right)$$

where $\text{rect}(t/\tau) = 1$ for $0 \leq t < \tau$, and $0$ otherwise.

---

### Problem 2.2 Solution

**Given:**
- Bandwidth: $B = 5$ kHz
- Sampling rate: $f_s = 15$ kHz
- Pulse width: $\tau = 0.05$ ms
- Amplitude range: $-5$ V to $+5$ V

**a) Check if sampling rate is adequate:**

Nyquist rate: $2B = 2 \times 5 = 10$ kHz

Since $f_s = 15$ kHz $> 10$ kHz, **the sampling rate is adequate** (oversampling by 50%).

**b) Sampling period:**
$$T_s = \frac{1}{f_s} = \frac{1}{15000} = 0.0667 \text{ ms} = 66.7 \mu\text{s}$$

**c) Duty cycle:**
$$\frac{\tau}{T_s} = \frac{0.05}{0.0667} = 0.75 = 75\%$$

**d) Approximate bandwidth of PAM signal:**

The PAM signal spectrum contains:
- Baseband component: up to $B = 5$ kHz
- Harmonic components: at $f_s = 15$ kHz, $2f_s = 30$ kHz, etc.

Approximate bandwidth: $B_{PAM} \approx f_s = 15$ kHz (to include first harmonic)

More precisely, the bandwidth depends on the pulse shape, but typically:
$$B_{PAM} \approx \frac{1}{\tau} = \frac{1}{0.05 \times 10^{-3}} = 20 \text{ kHz}$$

**e) Reconstruction filter cutoff frequency:**

The lowpass filter should have cutoff at:
$$f_c = B = 5 \text{ kHz}$$

This passes the baseband signal and rejects the harmonic components at $f_s$ and above.

---

### Problem 2.3 Solution

**Given:**
$$s_{PAM}(t) = \sum_{n=-\infty}^{+\infty} m(nT_s) p(t - nT_s)$$

**a) Spectrum contains original signal at baseband:**

The PAM signal is the convolution of the sampled signal with the pulse shape:
$$s_{PAM}(t) = \left[\sum_{n=-\infty}^{+\infty} m(nT_s) \delta(t - nT_s)\right] * p(t)$$

In frequency domain:
$$S_{PAM}(f) = \left[f_s \sum_{k=-\infty}^{+\infty} M(f - kf_s)\right] \cdot P(f)$$

where $P(f)$ is the Fourier transform of $p(t)$.

At baseband ($k = 0$):
$$S_{PAM}(f) \text{ (baseband)} = f_s M(f) \cdot P(f)$$

This shows the original spectrum $M(f)$ scaled by $f_s$ and multiplied by $P(f)$.

**b) Spectrum contains replicas at multiples of $f_s$:**

From the expression above:
$$S_{PAM}(f) = f_s \sum_{k=-\infty}^{+\infty} M(f - kf_s) \cdot P(f)$$

The term $\sum_{k=-\infty}^{+\infty} M(f - kf_s)$ creates replicas of $M(f)$ at:
- $k = 0$: baseband
- $k = \pm 1$: at $\pm f_s$
- $k = \pm 2$: at $\pm 2f_s$
- And so on...

**c) Lowpass filter can recover original if $f_s \geq 2B$:**

If $f_s \geq 2B$, then:
- The baseband spectrum ($|f| < B$) doesn't overlap with the first replica (at $f_s - B$)
- A lowpass filter with cutoff $f_c = B$ can:
  - Pass the baseband component: $f_s M(f) \cdot P(f)$ for $|f| < B$
  - Reject all harmonic components at $|f| \geq f_s - B$

The recovered signal is:
$$\hat{M}(f) = \frac{S_{PAM}(f)}{f_s P(f)} = M(f) \text{ for } |f| < B$$

Perfect reconstruction! ✓

---

## Exercise Set 3: Pulse Width Modulation (PWM) - Solutions

### Problem 3.1 Solution

**Given:**
- Pulse amplitude: $A = 10$ V (constant)
- Pulse period: $T_s = 0.1$ ms
- Pulse width: $\tau_{min} = 0.01$ ms to $\tau_{max} = 0.09$ ms

**a) Sampling rate:**
$$f_s = \frac{1}{T_s} = \frac{1}{0.1 \times 10^{-3}} = 10 \text{ kHz}$$

**b) Minimum duty cycle:**
$$\text{Duty}_{min} = \frac{\tau_{min}}{T_s} = \frac{0.01}{0.1} = 0.1 = 10\%$$

**c) Maximum duty cycle:**
$$\text{Duty}_{max} = \frac{\tau_{max}}{T_s} = \frac{0.09}{0.1} = 0.9 = 90\%$$

**d) Relationship between pulse width and modulating signal:**

Typically, the pulse width is linearly related to the modulating signal:
$$\tau(t) = \tau_0 + k \cdot m(t)$$

where:
- $\tau_0$ is the center pulse width
- $k$ is a constant of proportionality
- $m(t)$ is the modulating signal

From the given data:
- When $\tau = \tau_{min} = 0.01$ ms, $m(t)$ is minimum
- When $\tau = \tau_{max} = 0.09$ ms, $m(t)$ is maximum

---

### Problem 3.2 Solution

**Given:**
- Modulating signal range: $-2$ V to $+2$ V
- Pulse period: $T_s = 0.2$ ms
- Pulse width: $\tau(t) = 0.05 + 0.05 \cdot \frac{m(t)}{2}$ ms

**a) Sampling rate:**
$$f_s = \frac{1}{T_s} = \frac{1}{0.2 \times 10^{-3}} = 5 \text{ kHz}$$

**b) Minimum pulse width:**

When $m(t) = -2$ V (minimum):
$$\tau_{min} = 0.05 + 0.05 \cdot \frac{-2}{2} = 0.05 - 0.05 = 0 \text{ ms}$$

Wait, this gives 0, which might not be practical. Let me recalculate:
$$\tau_{min} = 0.05 + 0.05 \times (-1) = 0.05 - 0.05 = 0 \text{ ms}$$

**Answer:** $\tau_{min} = 0$ ms (theoretical minimum)

**c) Maximum pulse width:**

When $m(t) = +2$ V (maximum):
$$\tau_{max} = 0.05 + 0.05 \cdot \frac{+2}{2} = 0.05 + 0.05 = 0.1 \text{ ms}$$

**d) Pulse width when $m(t) = 0$ V:**
$$\tau(0) = 0.05 + 0.05 \cdot \frac{0}{2} = 0.05 \text{ ms}$$

This is the center (bias) pulse width.

**e) Pulse width when $m(t) = +2$ V:**
$$\tau(+2) = 0.05 + 0.05 \cdot \frac{+2}{2} = 0.05 + 0.05 = 0.1 \text{ ms}$$

---

### Problem 3.3 Solution

**a) Using lowpass filter to extract average value:**

A PWM signal has constant amplitude but varying width. The **average value** over one period equals the sample value.

For a PWM pulse with amplitude $A$ and width $\tau$:
$$\text{Average} = \frac{A \cdot \tau}{T_s}$$

If the pulse width is proportional to the sample: $\tau = k \cdot m(nT_s)$, then:
$$\text{Average} = \frac{A \cdot k \cdot m(nT_s)}{T_s} = K \cdot m(nT_s)$$

where $K = Ak/T_s$ is a constant.

**b) Average value over one period equals sample value:**

Mathematically:
$$\frac{1}{T_s} \int_{nT_s}^{(n+1)T_s} s_{PWM}(t) dt = \frac{A \tau(nT_s)}{T_s} = K \cdot m(nT_s)$$

This shows the average is proportional to the sample value.

**c) Relationship between PWM pulse width and recovered PAM sample:**

From above:
$$\text{Recovered PAM sample} = \frac{1}{T_s} \int_{nT_s}^{(n+1)T_s} s_{PWM}(t) dt = \frac{A \tau(nT_s)}{T_s}$$

If $\tau(t) = \tau_0 + k \cdot m(t)$, then:
$$\text{PAM sample} = \frac{A(\tau_0 + k \cdot m(nT_s))}{T_s} = \frac{A\tau_0}{T_s} + \frac{Ak}{T_s} m(nT_s)$$

The DC term $\frac{A\tau_0}{T_s}$ can be removed, leaving:
$$\text{PAM sample} \propto m(nT_s)$$

---

## Exercise Set 4: Pulse Position Modulation (PPM) - Solutions

### Problem 4.1 Solution

**Given:**
- Pulse amplitude: $A = 5$ V (fixed)
- Pulse width: $\tau = 0.02$ ms (fixed)
- Pulse period: $T_s = 0.1$ ms
- Position range: $t_0 = 0.01$ ms to $t_0 = 0.08$ ms

**a) Sampling rate:**
$$f_s = \frac{1}{T_s} = \frac{1}{0.1 \times 10^{-3}} = 10 \text{ kHz}$$

**b) Range of pulse positions:**

The pulse position varies from:
- Minimum: $t_{0,min} = 0.01$ ms
- Maximum: $t_{0,max} = 0.08$ ms

**Range:** $0.08 - 0.01 = 0.07$ ms

**c) Relationship between pulse position and modulating signal:**

Typically:
$$t_{position}(t) = t_0 + k \cdot m(t)$$

where:
- $t_0$ is the reference position (e.g., $0.01$ ms)
- $k$ is a constant
- $m(t)$ is the modulating signal

From the data:
- When $m(t)$ is minimum, $t_{position} = 0.01$ ms
- When $m(t)$ is maximum, $t_{position} = 0.08$ ms

---

### Problem 4.2 Solution

**Given:**
- Clock period: $T_s = 0.05$ ms
- Pulse width: $\tau = 0.005$ ms
- Position range: $0.01$ ms to $0.04$ ms (relative to clock edge)

**a) Sampling rate:**
$$f_s = \frac{1}{T_s} = \frac{1}{0.05 \times 10^{-3}} = 20 \text{ kHz}$$

**b) Minimum time delay from clock edge:**
$$t_{delay,min} = 0.01 \text{ ms}$$

**c) Maximum time delay from clock edge:**
$$t_{delay,max} = 0.04 \text{ ms}$$

**d) Total range of position variation:**
$$\Delta t = t_{delay,max} - t_{delay,min} = 0.04 - 0.01 = 0.03 \text{ ms}$$

**e) Relationship: $t_{position} = t_0 + k \cdot m(t)$:**

From the data:
- $t_0 = 0.01$ ms (minimum position)
- Range: $0.03$ ms
- If $m(t)$ ranges from $-M$ to $+M$, then:
  $$k = \frac{\Delta t}{2M} = \frac{0.03}{2M} \text{ ms/V}$$

So:
$$t_{position}(t) = 0.01 + \frac{0.03}{2M} \cdot m(t) \text{ ms}$$

---

### Problem 4.3 Solution

**a) Which is more resistant to amplitude noise?**

**PPM is more resistant** because:
- PPM uses **fixed amplitude** pulses
- Only the **position** carries information
- Amplitude noise doesn't affect the position measurement
- PWM also has fixed amplitude, but PPM is even more robust

**PAM is least resistant** because:
- Information is in the **amplitude**
- Any amplitude noise directly corrupts the signal

**b) Which requires more bandwidth?**

**PPM requires more bandwidth** because:
- Need to accurately resolve pulse position
- Requires narrow pulses (small $\tau$) for good position resolution
- Narrow pulses have wide spectrum
- Typically: $B_{PPM} > B_{PWM} > B_{PAM}$

**c) Which is easier to generate?**

**PAM is easiest** because:
- Just multiply signal by pulse train
- Simple circuit

**PWM is moderate:**
- Need comparator with sawtooth/triangular wave
- More complex than PAM

**PPM is most complex:**
- Need to generate position-modulated pulses
- Requires precise timing circuits

**d) Which is easier to demodulate?**

**PAM is easiest:**
- Just lowpass filter
- Simple

**PWM:**
- Lowpass filter to get average (like PAM)
- Moderate complexity

**PPM:**
- Need to measure pulse position
- Requires timing circuits
- Most complex

---

## Exercise Set 5: Delta Modulation (DM) - Solutions

### Problem 5.1 Solution

**Given:**
- Step size: $\Delta = 0.1$ V
- Sampling rate: $f_s = 10$ kHz
- Input signal: $x(t) = 2\sin(2\pi \cdot 1000t)$

**a) Sampling period:**
$$T_s = \frac{1}{f_s} = \frac{1}{10000} = 0.1 \text{ ms} = 100 \mu\text{s}$$

**b) Maximum tracking rate:**
$$\frac{\Delta}{T_s} = \frac{0.1}{0.1 \times 10^{-3}} = 1000 \text{ V/s}$$

**c) Maximum slope of input signal:**

The slope is:
$$\frac{dx(t)}{dt} = 2 \cdot 2\pi \cdot 1000 \cos(2\pi \cdot 1000t) = 4000\pi \cos(2\pi \cdot 1000t)$$

Maximum slope:
$$\max\left|\frac{dx(t)}{dt}\right| = 4000\pi \approx 12,566 \text{ V/s}$$

**d) Will slope overload occur?**

**Condition for slope overload:**
$$\left|\frac{dx(t)}{dt}\right| > \frac{\Delta}{T_s}$$

**Check:**
- Maximum signal slope: $12,566$ V/s
- Maximum tracking rate: $1,000$ V/s
- Since $12,566 > 1,000$, **slope overload will occur!** ✗

**To avoid slope overload, we need:**
$$\frac{\Delta}{T_s} \geq 12,566$$
$$\Delta \geq 12,566 \times 0.1 \times 10^{-3} = 1.2566 \text{ V}$$

Or increase $f_s$:
$$f_s \geq \frac{\Delta}{\max|dx/dt|} = \frac{0.1}{12,566} = 79.6 \text{ kHz}$$

---

### Problem 5.2 Solution

**Given:**
- Input: $x(t) = 5\cos(2\pi \cdot 2000t)$
- Step size: $\Delta = 0.2$ V
- Sampling rate: $f_s = 20$ kHz

**a) Maximum signal slope:**

$$\frac{dx(t)}{dt} = 5 \cdot 2\pi \cdot 2000 [-\sin(2\pi \cdot 2000t)] = -20000\pi \sin(2\pi \cdot 2000t)$$

Maximum slope:
$$\max\left|\frac{dx(t)}{dt}\right| = 20000\pi \approx 62,832 \text{ V/s}$$

**b) Maximum tracking rate:**
$$T_s = \frac{1}{20000} = 0.05 \text{ ms}$$

$$\frac{\Delta}{T_s} = \frac{0.2}{0.05 \times 10^{-3}} = 4000 \text{ V/s}$$

**c) Check for slope overload:**

**Condition:**
$$\max\left|\frac{dx(t)}{dt}\right| = 62,832 > 4,000 = \frac{\Delta}{T_s}$$

**Answer: Yes, slope overload will occur!** ✗

**d) What should be changed?**

**Option 1: Increase step size**
$$\Delta \geq 62,832 \times 0.05 \times 10^{-3} = 3.14 \text{ V}$$

**Option 2: Increase sampling rate**
$$f_s \geq \frac{\Delta}{\max|dx/dt|} = \frac{0.2}{62,832} = 318.3 \text{ kHz}$$

**Option 3: Both** - increase both $\Delta$ and $f_s$ proportionally

**e) Bit rate:**

Since DM uses 1 bit per sample:
$$\text{Bit rate} = f_s = 20 \text{ kbps}$$

---

### Problem 5.3 Solution

**a) Derive slope overload condition:**

In delta modulation, the reconstructed signal $\hat{x}(t)$ changes by $\pm\Delta$ every $T_s$ seconds.

**Maximum rate of change:**
$$\frac{d\hat{x}(t)}{dt} \leq \frac{\Delta}{T_s}$$

If the input signal changes faster than this, the modulator cannot track it:
$$\left|\frac{dx(t)}{dt}\right| > \frac{\Delta}{T_s}$$

This is the **slope overload condition**.

**b) For sinusoidal signal $x(t) = A\sin(\omega t)$:**

The slope is:
$$\frac{dx(t)}{dt} = A\omega \cos(\omega t)$$

Maximum slope:
$$\max\left|\frac{dx(t)}{dt}\right| = A\omega$$

Slope overload occurs if:
$$A\omega > \frac{\Delta}{T_s}$$

**c) Find minimum step size:**

**Given:**
- $x(t) = 3\sin(2\pi \cdot 5000t)$
- $f_s = 50$ kHz

**Maximum slope:**
$$A = 3 \text{ V}, \quad \omega = 2\pi \cdot 5000 = 10000\pi \text{ rad/s}$$

$$\max\left|\frac{dx(t)}{dt}\right| = 3 \times 10000\pi = 30000\pi \text{ V/s}$$

**To avoid slope overload:**
$$\frac{\Delta}{T_s} \geq 30000\pi$$

$$T_s = \frac{1}{50000} = 0.02 \text{ ms}$$

$$\Delta \geq 30000\pi \times 0.02 \times 10^{-3} = 600\pi \times 10^{-3} = 1.885 \text{ V}$$

**Answer:** $\Delta_{min} = 1.885$ V

---

## Exercise Set 6: Quantization - Solutions

### Problem 6.1 Solution

**Given:**
- Number of bits: $b = 8$
- Range: $-10$ V to $+10$ V

**a) Number of quantization levels:**
$$L = 2^b = 2^8 = 256 \text{ levels}$$

**b) Quantization step size:**
$$V_{pp} = 10 - (-10) = 20 \text{ V}$$

$$\Delta = \frac{V_{pp}}{L} = \frac{20}{256} = 0.078125 \text{ V} = 78.125 \text{ mV}$$

**c) Quantization noise power:**

Assuming uniform quantization error distribution:
$$N_q = \frac{\Delta^2}{12} = \frac{(0.078125)^2}{12} = \frac{0.0061035}{12} = 5.086 \times 10^{-4} \text{ V}^2$$

**d) Maximum quantization error:**

The quantization error is bounded by:
$$|e| \leq \frac{\Delta}{2} = \frac{0.078125}{2} = 0.0390625 \text{ V} = 39.0625 \text{ mV}$$

---

### Problem 6.2 Solution

**Given:**
- Number of bits: $b = 12$
- Peak-to-peak voltage: $V_{pp} = 8$ V

**a) Number of levels:**
$$L = 2^b = 2^{12} = 4096 \text{ levels}$$

**b) Step size:**
$$\Delta = \frac{V_{pp}}{L} = \frac{8}{4096} = 0.001953125 \text{ V} = 1.953 \text{ mV}$$

**c) Quantization noise power:**
$$N_q = \frac{\Delta^2}{12} = \frac{(0.001953125)^2}{12} = \frac{3.8147 \times 10^{-6}}{12} = 3.179 \times 10^{-7} \text{ V}^2$$

**d) SQNR in dB (sinusoidal signal):**

For a sinusoidal signal with amplitude $A$ and range $[-A, +A]$:
- Signal power: $S = \frac{A^2}{2}$
- If $V_{pp} = 2A = 8$ V, then $A = 4$ V
- $S = \frac{4^2}{2} = 8$ V²

SQNR:
$$\text{SQNR} = \frac{S}{N_q} = \frac{8}{3.179 \times 10^{-7}} = 2.516 \times 10^7$$

In dB:
$$\text{SQNR (dB)} = 10\log_{10}(2.516 \times 10^7) = 10(7.401) = 74.01 \text{ dB}$$

**Using the formula:**
$$\text{SQNR (dB)} \approx 6.02b + 1.76 = 6.02 \times 12 + 1.76 = 72.24 + 1.76 = 74.0 \text{ dB}$$

**e) SQNR with 16 bits:**

$$\text{SQNR (dB)} \approx 6.02 \times 16 + 1.76 = 96.32 + 1.76 = 98.08 \text{ dB}$$

**Improvement:** $98.08 - 74.0 = 24.08$ dB (approximately 4 bits × 6 dB = 24 dB)

---

### Problem 6.3 Solution

**a) Quantization noise power:**

Assume the quantization error $e$ is uniformly distributed in $[-\Delta/2, +\Delta/2]$.

**Probability density function:**
$$f_e(e) = \begin{cases}
\frac{1}{\Delta}, & -\Delta/2 \leq e \leq +\Delta/2 \\
0, & \text{otherwise}
\end{cases}$$

**Mean (expected value):**
$$E[e] = \int_{-\Delta/2}^{+\Delta/2} e \cdot \frac{1}{\Delta} de = \frac{1}{\Delta} \left[\frac{e^2}{2}\right]_{-\Delta/2}^{+\Delta/2} = 0$$

**Variance (noise power):**
$$N_q = E[e^2] = \int_{-\Delta/2}^{+\Delta/2} e^2 \cdot \frac{1}{\Delta} de = \frac{1}{\Delta} \left[\frac{e^3}{3}\right]_{-\Delta/2}^{+\Delta/2}$$

$$N_q = \frac{1}{\Delta} \cdot \frac{1}{3} \left[\left(\frac{\Delta}{2}\right)^3 - \left(-\frac{\Delta}{2}\right)^3\right] = \frac{1}{3\Delta} \cdot 2 \cdot \left(\frac{\Delta}{2}\right)^3$$

$$N_q = \frac{2}{3\Delta} \cdot \frac{\Delta^3}{8} = \frac{\Delta^2}{12}$$

**b) Signal power for sinusoidal signal:**

For $x(t) = A\sin(\omega t)$:
$$S = \frac{1}{T} \int_0^T [A\sin(\omega t)]^2 dt = \frac{A^2}{T} \int_0^T \sin^2(\omega t) dt$$

Using $\sin^2(\theta) = \frac{1 - \cos(2\theta)}{2}$:
$$S = \frac{A^2}{T} \int_0^T \frac{1 - \cos(2\omega t)}{2} dt = \frac{A^2}{2T} \left[T - \frac{\sin(2\omega T)}{2\omega}\right]$$

Since $T = 2\pi/\omega$ (one period), $\sin(2\omega T) = \sin(4\pi) = 0$:
$$S = \frac{A^2}{2}$$

**c) SQNR formula:**

For quantization with $b$ bits and range $[-A, +A]$:
- $V_{pp} = 2A$
- $\Delta = \frac{2A}{2^b} = \frac{A}{2^{b-1}}$
- $N_q = \frac{\Delta^2}{12} = \frac{A^2}{12 \cdot 2^{2(b-1)}} = \frac{A^2}{12 \cdot 2^{2b-2}} = \frac{A^2 \cdot 2^2}{12 \cdot 2^{2b}} = \frac{A^2}{3 \cdot 2^{2b}}$

SQNR:
$$\text{SQNR} = \frac{S}{N_q} = \frac{A^2/2}{A^2/(3 \cdot 2^{2b})} = \frac{3 \cdot 2^{2b}}{2}$$

In dB:
$$\text{SQNR (dB)} = 10\log_{10}\left(\frac{3 \cdot 2^{2b}}{2}\right) = 10\log_{10}(3) + 10\log_{10}(2^{2b}) - 10\log_{10}(2)$$

$$= 4.77 + 20b\log_{10}(2) - 3.01 = 4.77 + 6.02b - 3.01 = 6.02b + 1.76$$

**d) Each additional bit improves SQNR by 6 dB:**

From the formula:
$$\text{SQNR (dB)} = 6.02b + 1.76$$

If we increase $b$ by 1:
$$\text{SQNR}_{new} = 6.02(b+1) + 1.76 = 6.02b + 6.02 + 1.76$$

Improvement:
$$\Delta \text{SQNR} = 6.02 \text{ dB}$$

**Approximately 6 dB per bit!** ✓

---

*End of Part 1 Solutions (Exercise Sets 1-6)*


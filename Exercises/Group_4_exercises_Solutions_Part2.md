# Group 4 Exercises - Solutions Part 2


This document contains solutions for Exercise Sets 7-12 of Group 4 exercises.


---


## Exercise Set 7: Signal-to-Quantization-Noise Ratio (SQNR) - Solutions


### Problem 7.1 Solution


**Given:**

- Signal: $x(t) = 4\sin(2\pi \cdot 1000t)$

- Quantization: 10 bits

- Range: $-5$ V to $+5$ V


**a) Step size:**

$$V_{pp} = 5 - (-5) = 10 \text{ V}$$

$$L = 2^{10} = 1024 \text{ levels}$$

$$\Delta = \frac{V_{pp}}{L} = \frac{10}{1024} = 0.009765625 \text{ V} = 9.766 \text{ mV}$$


**b) Signal power:**


For sinusoidal signal $x(t) = A\sin(\omega t)$ with $A = 4$ V:

$$S = \frac{A^2}{2} = \frac{4^2}{2} = \frac{16}{2} = 8 \text{ V}^2$$


**c) Quantization noise power:**

$$N_q = \frac{\Delta^2}{12} = \frac{(0.009765625)^2}{12} = \frac{9.537 \times 10^{-5}}{12} = 7.947 \times 10^{-6} \text{ V}^2$$


**d) SQNR in linear scale:**

$$\text{SQNR} = \frac{S}{N_q} = \frac{8}{7.947 \times 10^{-6}} = 1.006 \times 10^6$$


**e) SQNR in dB:**

$$\text{SQNR (dB)} = 10\log_{10}(1.006 \times 10^6) = 10(6.003) = 60.03 \text{ dB}$$


**Using the formula:**

$$\text{SQNR (dB)} \approx 6.02b + 1.76 = 6.02 \times 10 + 1.76 = 60.2 + 1.76 = 61.96 \text{ dB}$$


(Note: The slight difference is because the range $[-5, +5]$ doesn't exactly match the signal amplitude $A = 4$ V. The formula assumes $V_{pp} = 2A$.)


---


### Problem 7.2 Solution


**Given:**

- Peak amplitude: $A = 6$ V

- Number of bits: $b = 14$

- Quantization range: $\pm A$ (i.e., $-6$ V to $+6$ V)


**a) Step size:**

$$V_{pp} = 6 - (-6) = 12 \text{ V}$$

$$L = 2^{14} = 16384 \text{ levels}$$

$$\Delta = \frac{V_{pp}}{L} = \frac{12}{16384} = 0.000732421875 \text{ V} = 0.732 \text{ mV}$$


**b) Signal power (sinusoidal):**

$$S = \frac{A^2}{2} = \frac{6^2}{2} = \frac{36}{2} = 18 \text{ V}^2$$


**c) Noise power:**

$$N_q = \frac{\Delta^2}{12} = \frac{(0.000732421875)^2}{12} = \frac{5.364 \times 10^{-7}}{12} = 4.470 \times 10^{-8} \text{ V}^2$$


**d) SQNR in dB:**

$$\text{SQNR} = \frac{S}{N_q} = \frac{18}{4.470 \times 10^{-8}} = 4.026 \times 10^8$$


$$\text{SQNR (dB)} = 10\log_{10}(4.026 \times 10^8) = 10(8.605) = 86.05 \text{ dB}$$


**Using the formula:**

$$\text{SQNR (dB)} \approx 6.02b + 1.76 = 6.02 \times 14 + 1.76 = 84.28 + 1.76 = 86.04 \text{ dB}$$


**e) SQNR with different bit numbers:**


**With 8 bits:**

$$\text{SQNR (dB)} \approx 6.02 \times 8 + 1.76 = 48.16 + 1.76 = 49.92 \text{ dB}$$


**With 16 bits:**

$$\text{SQNR (dB)} \approx 6.02 \times 16 + 1.76 = 96.32 + 1.76 = 98.08 \text{ dB}$$


---


### Problem 7.3 Solution


**a) Derive SQNR formula:**


For sinusoidal signal $x(t) = A\sin(\omega t)$:

- Signal power: $S = \frac{A^2}{2}$


For quantization with range $[-A, +A]$:

- $V_{pp} = 2A$

- With $b$ bits: $L = 2^b$

- Step size: $\Delta = \frac{V_{pp}}{L} = \frac{2A}{2^b} = \frac{A}{2^{b-1}}$

- Noise power: $N_q = \frac{\Delta^2}{12} = \frac{A^2}{12 \cdot 2^{2(b-1)}} = \frac{A^2}{3 \cdot 2^{2b}}$


SQNR:

$$\text{SQNR} = \frac{S}{N_q} = \frac{A^2/2}{A^2/(3 \cdot 2^{2b})} = \frac{3 \cdot 2^{2b}}{2}$$


**b) Show SQNR (dB) = 6.02b + 1.76:**


$$\text{SQNR (dB)} = 10\log_{10}\left(\frac{3 \cdot 2^{2b}}{2}\right)$$


$$= 10[\log_{10}(3) + \log_{10}(2^{2b}) - \log_{10}(2)]$$


$$= 10[0.477 + 2b \log_{10}(2) - 0.301]$$


$$= 10[0.477 + 2b(0.301) - 0.301]$$


$$= 10[0.176 + 0.602b]$$


$$= 1.76 + 6.02b$$


**c) Bits needed for SQNR = 60 dB:**


$$60 = 6.02b + 1.76$$


$$6.02b = 60 - 1.76 = 58.24$$


$$b = \frac{58.24}{6.02} = 9.68$$


**Answer:** Need at least **10 bits** (round up)


**Verification:** With 10 bits: SQNR = 6.02 × 10 + 1.76 = 61.96 dB ✓


**d) Bits needed for SQNR = 80 dB:**


$$80 = 6.02b + 1.76$$


$$6.02b = 80 - 1.76 = 78.24$$


$$b = \frac{78.24}{6.02} = 13.0$$


**Answer:** Need **13 bits**


**Verification:** With 13 bits: SQNR = 6.02 × 13 + 1.76 = 80.02 dB ✓


---


## Exercise Set 8: Comparison of Pulse Modulation Schemes - Solutions


### Problem 8.1 Solution


**a) Which scheme varies pulse amplitude?**

**Answer: PAM (Pulse Amplitude Modulation)**


**b) Which scheme varies pulse width?**

**Answer: PWM (Pulse Width Modulation)**


**c) Which scheme varies pulse position?**

**Answer: PPM (Pulse Position Modulation)**


**d) Which is most sensitive to amplitude noise?**

**Answer: PAM** - because the information is directly encoded in the amplitude, any amplitude noise directly corrupts the signal.


**e) Which is least sensitive to amplitude noise?**

**Answer: PPM** - because it uses fixed amplitude pulses, and only the position carries information. Amplitude noise doesn't affect position measurement.


---


### Problem 8.2 Solution


**Given:** Analog signal $m(t)$ with bandwidth $B = 4$ kHz


**a) Bandwidth requirements:**


**PAM:**

- Baseband: $B = 4$ kHz

- Harmonics at $f_s$ and multiples

- Approximate bandwidth: $B_{PAM} \approx f_s \geq 2B = 8$ kHz


**PWM:**

- Requires wider bandwidth due to pulse width variations

- Need to resolve pulse edges accurately

- $B_{PWM} > B_{PAM}$ (typically 2-3 times)


**PPM:**

- Requires narrow pulses for good position resolution

- Narrow pulses have wide spectrum

- $B_{PPM} > B_{PWM} > B_{PAM}$ (typically widest)


**b) Noise resistance:**


**PAM:** Least resistant - amplitude noise directly affects signal


**PWM:** Moderate - fixed amplitude helps, but width measurement can be affected


**PPM:** Most resistant - fixed amplitude, position measurement is robust


**c) Implementation complexity:**


**PAM:** Simplest - just multiply signal by pulse train


**PWM:** Moderate - need comparator with sawtooth/triangular wave


**PPM:** Most complex - need precise timing circuits for position modulation


**d) Power efficiency:**


**PAM:** Moderate - requires linear amplification


**PWM:** High - can use switching amplifiers (constant amplitude)


**PPM:** High - fixed amplitude, efficient power amplifiers


**e) Demodulation method:**


**PAM:** Lowpass filter (simplest)


**PWM:** Lowpass filter to extract average (moderate)


**PPM:** Position measurement using timing circuits (most complex)


---


### Problem 8.3 Solution


**a) Why is PAM simpler but more noise-sensitive?**


**Simplicity:**

- Generation: Just multiply $m(t)$ by pulse train

- Demodulation: Simple lowpass filter

- No complex timing or comparison circuits needed


**Noise sensitivity:**

- Information is in pulse **amplitude**

- Any amplitude noise (channel noise, amplifier distortion) directly corrupts the signal

- No redundancy or error correction


**b) Why does PWM require constant amplitude amplifiers?**


**PWM uses fixed amplitude:**

- Information is in pulse **width**, not amplitude

- Amplitude variations would add noise

- Constant amplitude allows use of:

  - Switching amplifiers (more efficient)

  - Saturated amplifiers (simpler)

  - Power-efficient designs


**Trade-off:** Need precise width measurement, but amplitude can be non-linear.


**c) Why is PPM more complex but more noise-resistant?**


**Complexity:**

- Need to generate position-modulated pulses

- Requires precise timing circuits

- Demodulation needs position measurement

- More complex than PAM or PWM


**Noise resistance:**

- Fixed amplitude pulses

- Position measurement is robust to amplitude noise

- Can use threshold detection (binary: pulse present/absent)

- Less sensitive to channel impairments


**d) When would you choose each scheme?**


**Choose PAM when:**

- Simplicity is important

- Bandwidth is limited

- Noise is low

- Cost is a concern


**Choose PWM when:**

- Power efficiency is important

- Switching amplifiers available

- Moderate noise resistance needed

- Motor control, power supplies


**Choose PPM when:**

- Maximum noise resistance needed

- Bandwidth is available

- Optical communication

- High-quality transmission required


---


## Exercise Set 9: Numerical Problems - Solutions


### Problem 9.1 Solution


**Given:**

- Voice signal: $B = 3.4$ kHz

- Sampling rate: $f_s = 8$ kHz

- Pulse width: $\tau = 10$ $\mu$s

- Amplitude range: $-2$ V to $+2$ V


**a) Is sampling rate adequate?**


Nyquist rate: $2B = 2 \times 3.4 = 6.8$ kHz


Since $f_s = 8$ kHz $> 6.8$ kHz, **yes, the sampling rate is adequate** (oversampling by ~18%).


**b) Sampling period:**

$$T_s = \frac{1}{f_s} = \frac{1}{8000} = 0.125 \text{ ms} = 125 \mu\text{s}$$


**c) Duty cycle:**

$$\frac{\tau}{T_s} = \frac{10 \times 10^{-6}}{125 \times 10^{-6}} = \frac{10}{125} = 0.08 = 8\%$$


**d) Bandwidth of PAM signal:**


The PAM signal spectrum contains:

- Baseband: up to $B = 3.4$ kHz

- Harmonics: at $f_s = 8$ kHz, $2f_s = 16$ kHz, etc.


Approximate bandwidth: $B_{PAM} \approx f_s = 8$ kHz


More precisely, considering pulse shape:

$$B_{PAM} \approx \frac{1}{\tau} = \frac{1}{10 \times 10^{-6}} = 100 \text{ kHz}$$


But for practical purposes, we need bandwidth to accommodate the first few harmonics: $B_{PAM} \approx 2f_s = 16$ kHz


**e) Reconstruction filter cutoff frequency:**


The lowpass filter should have cutoff at:

$$f_c = B = 3.4 \text{ kHz}$$


This passes the baseband signal and rejects harmonics.


---


### Problem 9.2 Solution


**Given:**

- Input: $x(t) = 3\cos(2\pi \cdot 3000t)$

- Step size: $\Delta = 0.15$ V

- Sampling rate: $f_s = 30$ kHz


**a) Maximum signal slope:**


$$\frac{dx(t)}{dt} = 3 \cdot 2\pi \cdot 3000 [-\sin(2\pi \cdot 3000t)] = -18000\pi \sin(2\pi \cdot 3000t)$$


Maximum slope:

$$\max\left|\frac{dx(t)}{dt}\right| = 18000\pi \approx 56,549 \text{ V/s}$$


**b) Maximum tracking rate:**

$$T_s = \frac{1}{30000} = 0.0333 \text{ ms}$$


$$\frac{\Delta}{T_s} = \frac{0.15}{0.0333 \times 10^{-3}} = 4500 \text{ V/s}$$


**c) Will slope overload occur?**


**Check:**

$$\max\left|\frac{dx(t)}{dt}\right| = 56,549 > 4,500 = \frac{\Delta}{T_s}$$


**Answer: Yes, slope overload will occur!** ✗


**d) Step size needed to avoid slope overload:**


To avoid slope overload:

$$\frac{\Delta}{T_s} \geq 56,549$$


$$\Delta \geq 56,549 \times 0.0333 \times 10^{-3} = 1.885 \text{ V}$$


**Answer:** Need $\Delta \geq 1.885$ V


**e) Bit rate:**


Since DM uses 1 bit per sample:

$$\text{Bit rate} = f_s = 30 \text{ kbps}$$


---


### Problem 9.3 Solution


**Given:**

- Signal: $x(t) = 5\sin(2\pi \cdot 2000t)$

- Quantization: 12 bits

- Range: $-6$ V to $+6$ V

- Sampling rate: $f_s = 8$ kHz


**a) Step size:**

$$V_{pp} = 6 - (-6) = 12 \text{ V}$$

$$L = 2^{12} = 4096 \text{ levels}$$

$$\Delta = \frac{V_{pp}}{L} = \frac{12}{4096} = 0.0029296875 \text{ V} = 2.93 \text{ mV}$$


**b) Signal power:**


For $x(t) = 5\sin(\omega t)$ with $A = 5$ V:

$$S = \frac{A^2}{2} = \frac{5^2}{2} = \frac{25}{2} = 12.5 \text{ V}^2$$


**c) Quantization noise power:**

$$N_q = \frac{\Delta^2}{12} = \frac{(0.0029296875)^2}{12} = \frac{8.583 \times 10^{-6}}{12} = 7.153 \times 10^{-7} \text{ V}^2$$


**d) SQNR in dB:**

$$\text{SQNR} = \frac{S}{N_q} = \frac{12.5}{7.153 \times 10^{-7}} = 1.747 \times 10^7$$


$$\text{SQNR (dB)} = 10\log_{10}(1.747 \times 10^7) = 10(7.242) = 72.42 \text{ dB}$$


**Using the formula:**

$$\text{SQNR (dB)} \approx 6.02b + 1.76 = 6.02 \times 12 + 1.76 = 72.24 + 1.76 = 74.0 \text{ dB}$$


**e) Data rate:**


With 12 bits per sample and $f_s = 8$ kHz:

$$\text{Data rate} = b \times f_s = 12 \times 8000 = 96,000 \text{ bps} = 96 \text{ kbps}$$


---


## Exercise Set 10: Conceptual Questions - Solutions


### Problem 10.1 Solution


**a) What is aliasing and how does it occur?**


**Aliasing** is the phenomenon where high-frequency components of a signal appear as lower frequencies after sampling.


**How it occurs:**

- When a signal is sampled at rate $f_s$, the spectrum is replicated at multiples of $f_s$

- If the signal has frequencies above $f_s/2$ (Nyquist frequency), these frequencies "fold back" into the baseband

- The high frequencies appear as aliased lower frequencies

- Example: A 7 kHz signal sampled at 8 kHz aliases to 1 kHz


**b) Why is the Nyquist rate $f_s = 2B$ the minimum sampling rate?**


**Nyquist-Shannon Theorem:**

- A signal with bandwidth $B$ has no frequency components above $B$

- To avoid aliasing, the spectrum replicas must not overlap

- The first replica starts at $f_s$

- To avoid overlap: $f_s - B \geq B$, so $f_s \geq 2B$

- $f_s = 2B$ is the **minimum** rate (exactly at the limit)

- $f_s > 2B$ provides margin for practical filters


**c) What is the purpose of an anti-aliasing filter?**


**Anti-aliasing filter:**

- **Lowpass filter** placed **before** the sampler

- **Cutoff frequency:** $f_c = B$ (signal bandwidth)

- **Purpose:** Remove frequency components above $B$ before sampling

- **Why:** Prevents these high frequencies from aliasing into baseband

- **Result:** Signal is truly bandlimited, can be sampled without aliasing


**d) What happens if we sample below the Nyquist rate?**


**Consequences:**

- **Aliasing occurs** - high frequencies fold into baseband

- **Distortion** - original signal cannot be perfectly recovered

- **Information loss** - high-frequency information is lost/ corrupted

- **Irreversible** - cannot undo aliasing after sampling

- **Solution:** Must sample at or above Nyquist rate


---


### Problem 10.2 Solution


**a) Why does PAM require linear amplification?**


**PAM encodes information in amplitude:**

- Pulse amplitude = sample value

- Any non-linearity distorts the amplitude

- Distortion = loss of information

- **Linear amplification** preserves the amplitude relationship

- Non-linear amplifiers would introduce distortion


**b) Why is PWM more power-efficient than PAM?**


**PWM uses fixed amplitude:**

- Can use **switching amplifiers** (on/off, not linear)

- Switching amplifiers are more efficient (less power loss)

- Don't need to preserve amplitude linearly

- Can use saturated amplifiers

- **Result:** Higher power efficiency


**PAM requires linear amplification:**

- Must preserve amplitude accurately

- Linear amplifiers less efficient

- More power dissipation


**c) Why is PPM more resistant to noise than PAM?**


**PPM advantages:**

- **Fixed amplitude** pulses - amplitude noise doesn't affect position

- **Position measurement** is robust (binary: pulse present/absent)

- Can use threshold detection

- Less sensitive to channel impairments


**PAM disadvantages:**

- Information in **amplitude** - any amplitude noise corrupts signal

- Direct relationship between noise and error

- More sensitive to channel conditions


**d) What is the main disadvantage of delta modulation?**


**Main disadvantages:**

1. **Slope overload** - cannot track rapid signal changes

2. **Granular noise** - quantization error for slowly varying signals

3. **Trade-off** - large step size avoids slope overload but increases granular noise

4. **Limited quality** - 1-bit quantization limits signal quality

5. **Requires high sampling rate** - to avoid slope overload


**Solution:** Adaptive delta modulation (ADM) adjusts step size dynamically.


---


### Problem 10.3 Solution


**a) What is slope overload in delta modulation?**


**Slope overload:**

- Occurs when the input signal changes **faster** than the modulator can track

- Condition: $\left|\frac{dx(t)}{dt}\right| > \frac{\Delta}{T_s}$

- **Result:** The reconstructed signal cannot follow the input

- **Visual:** Large error, signal "falls behind"

- **Solution:** Increase step size $\Delta$ or sampling rate $f_s$


**b) What is granular noise in delta modulation?**


**Granular noise:**

- Occurs when the signal changes **slowly**

- The step size $\Delta$ is too large relative to signal variations

- **Result:** Quantization error even for small changes

- **Visual:** "Staircase" approximation, quantization error

- **Solution:** Decrease step size $\Delta$


**c) What is the trade-off between slope overload and granular noise?**


**The trade-off:**

- **Large step size ($\Delta$):**

  - ✓ Avoids slope overload

  - ✗ Increases granular noise

  - Good for rapidly varying signals


- **Small step size ($\Delta$):**

  - ✓ Reduces granular noise

  - ✗ Causes slope overload

  - Good for slowly varying signals


**Problem:** Cannot optimize for both simultaneously with fixed step size!


**d) How does adaptive delta modulation solve this trade-off?**


**Adaptive Delta Modulation (ADM):**

- **Variable step size** - adjusts $\Delta$ based on signal characteristics

- **Large steps** when signal changes rapidly (avoid slope overload)

- **Small steps** when signal changes slowly (reduce granular noise)

- **Algorithm:** Monitor signal slope, adjust $\Delta$ accordingly

- **Result:** Better quality than fixed-step DM

- **Trade-off solved!** ✓


---


## Exercise Set 11: Derivation Problems - Solutions


### Problem 11.1 Solution


**Derive the Nyquist-Shannon sampling theorem:**


**a) Start with bandlimited signal:**


Let $x(t)$ be a signal with spectrum:

$$X(f) = 0 \text{ for } |f| > B$$


**b) Sampling creates spectrum replicas:**


Sampling $x(t)$ at rate $f_s$:

$$x_s(t) = x(t) \sum_{n=-\infty}^{+\infty} \delta(t - nT_s)$$


where $T_s = 1/f_s$.


In frequency domain, multiplication in time = convolution in frequency:

$$X_s(f) = X(f) * \left[f_s \sum_{k=-\infty}^{+\infty} \delta(f - kf_s)\right]$$


$$X_s(f) = f_s \sum_{k=-\infty}^{+\infty} X(f - kf_s)$$


**This shows replicas of $X(f)$ at multiples of $f_s$:**

- $k = 0$: baseband $X(f)$

- $k = \pm 1$: $X(f \pm f_s)$

- $k = \pm 2$: $X(f \pm 2f_s)$

- etc.


**c) If $f_s < 2B$, replicas overlap (aliasing):**


The baseband spectrum extends from $-B$ to $+B$.


The first replica (at $k = +1$) is $X(f - f_s)$, centered at $f = f_s$.


**For no overlap:**

$$f_s - B \geq B$$

$$f_s \geq 2B$$


**If $f_s < 2B$:**

- The replica at $f_s$ overlaps with baseband

- Frequencies from $f_s - B$ to $f_s$ fold into baseband

- **Aliasing occurs!** ✗


**d) If $f_s \geq 2B$, original signal can be recovered:**


**If $f_s \geq 2B$:**

- Replicas don't overlap

- Baseband spectrum ($|f| < B$) is isolated

- Can use **lowpass filter** with cutoff $f_c = B$:


$$H(f) = \begin{cases}

1, & |f| < B \\

0, & |f| \geq B

\end{cases}$$


**Filtered spectrum:**

$$\hat{X}(f) = X_s(f) \cdot H(f) = f_s X(f) \text{ for } |f| < B$$


**Recovered signal:**

$$\hat{x}(t) = \text{Inverse FT of } \hat{X}(f) = x(t)$$


**Perfect reconstruction!** ✓


**Conclusion:** $f_s \geq 2B$ is necessary and sufficient for perfect reconstruction.


---


### Problem 11.2 Solution


**Derive quantization noise power:**


**a) Uniform quantization with step size $\Delta$:**


The quantizer divides the range into levels separated by $\Delta$.


**Quantization error $e$:**

- Difference between actual value and quantized value

- $e = x - Q(x)$ where $Q(x)$ is quantized value


**b) Error is uniformly distributed in $[-\Delta/2, +\Delta/2]$:**


Assuming the signal is "busy" (varies significantly), the error is approximately uniformly distributed:


$$f_e(e) = \begin{cases}

\frac{1}{\Delta}, & -\Delta/2 \leq e \leq +\Delta/2 \\

0, & \text{otherwise}

\end{cases}$$


**c) Mean of error:**

$$E[e] = \int_{-\Delta/2}^{+\Delta/2} e \cdot \frac{1}{\Delta} de = \frac{1}{\Delta} \left[\frac{e^2}{2}\right]_{-\Delta/2}^{+\Delta/2}$$


$$= \frac{1}{\Delta} \cdot \frac{1}{2} \left[\left(\frac{\Delta}{2}\right)^2 - \left(-\frac{\Delta}{2}\right)^2\right] = \frac{1}{2\Delta} \cdot 0 = 0$$


**The mean error is zero** (quantizer is unbiased).


**d) Variance (noise power):**

$$N_q = E[e^2] = \int_{-\Delta/2}^{+\Delta/2} e^2 \cdot \frac{1}{\Delta} de$$


$$= \frac{1}{\Delta} \left[\frac{e^3}{3}\right]_{-\Delta/2}^{+\Delta/2} = \frac{1}{\Delta} \cdot \frac{1}{3} \left[\left(\frac{\Delta}{2}\right)^3 - \left(-\frac{\Delta}{2}\right)^3\right]$$


$$= \frac{1}{3\Delta} \cdot 2 \cdot \left(\frac{\Delta}{2}\right)^3 = \frac{2}{3\Delta} \cdot \frac{\Delta^3}{8} = \frac{\Delta^2}{12}$$


**Result:** $N_q = \frac{\Delta^2}{12}$ ✓


---


### Problem 11.3 Solution


**Derive SQNR formula for sinusoidal signal:**


**a) Signal power for $x(t) = A\sin(\omega t)$:**


$$S = \lim_{T \to \infty} \frac{1}{T} \int_{-T/2}^{T/2} [A\sin(\omega t)]^2 dt$$


For one period ($T = 2\pi/\omega$):

$$S = \frac{1}{T} \int_0^T A^2 \sin^2(\omega t) dt$$


Using $\sin^2(\theta) = \frac{1 - \cos(2\theta)}{2}$:

$$S = \frac{A^2}{T} \int_0^T \frac{1 - \cos(2\omega t)}{2} dt = \frac{A^2}{2T} \left[T - \frac{\sin(2\omega T)}{2\omega}\right]$$


Since $T = 2\pi/\omega$, we have $\sin(2\omega T) = \sin(4\pi) = 0$:

$$S = \frac{A^2}{2}$$


**b) Step size for $b$ bits with range $[-A, +A]$:**


$$V_{pp} = A - (-A) = 2A$$

$$L = 2^b$$

$$\Delta = \frac{V_{pp}}{L} = \frac{2A}{2^b} = \frac{A}{2^{b-1}}$$


**c) Noise power:**

$$N_q = \frac{\Delta^2}{12} = \frac{(A/2^{b-1})^2}{12} = \frac{A^2}{12 \cdot 2^{2(b-1)}} = \frac{A^2 \cdot 2^2}{12 \cdot 2^{2b}} = \frac{A^2}{3 \cdot 2^{2b}}$$


**d) SQNR:**

$$\text{SQNR} = \frac{S}{N_q} = \frac{A^2/2}{A^2/(3 \cdot 2^{2b})} = \frac{3 \cdot 2^{2b}}{2}$$


**e) Convert to dB:**

$$\text{SQNR (dB)} = 10\log_{10}\left(\frac{3 \cdot 2^{2b}}{2}\right)$$


$$= 10[\log_{10}(3) + \log_{10}(2^{2b}) - \log_{10}(2)]$$


$$= 10[0.477 + 2b \log_{10}(2) - 0.301]$$


$$= 10[0.477 + 2b(0.301) - 0.301]$$


$$= 10[0.176 + 0.602b]$$


$$= 1.76 + 6.02b$$


**Result:** $\text{SQNR (dB)} = 6.02b + 1.76$ ✓


---


## Exercise Set 12: Combined Problems - Solutions


### Problem 12.1 Solution


**Given:**

- Analog signal: $m(t) = 4\cos(2\pi \cdot 3000t)$

- Sampling rate: $f_s = 10$ kHz

- Quantization: 8 bits, range $[-5, +5]$ V

- Pulse width: $\tau = 0.02$ ms


**a) Check if sampling rate is adequate:**


Bandwidth: $B = 3$ kHz

Nyquist rate: $2B = 6$ kHz


Since $f_s = 10$ kHz $> 6$ kHz, **sampling rate is adequate** ✓


**b) PAM signal parameters:**


- Sampling period: $T_s = 1/10000 = 0.1$ ms

- Pulse width: $\tau = 0.02$ ms

- Duty cycle: $\tau/T_s = 0.02/0.1 = 0.2 = 20\%$

- Pulse amplitude range: $-5$ V to $+5$ V (before quantization)


**c) Quantized PAM signal:**


- Number of bits: $b = 8$

- Levels: $L = 2^8 = 256$

- Range: $V_{pp} = 5 - (-5) = 10$ V

- Step size: $\Delta = 10/256 = 0.0390625$ V = 39.06 mV

- Quantization noise: $N_q = \Delta^2/12 = (0.0390625)^2/12 = 1.271 \times 10^{-4}$ V²


**d) SQNR in dB:**


Signal amplitude: $A = 4$ V (but range is $[-5, +5]$)

Signal power: $S = A^2/2 = 16/2 = 8$ V²


SQNR:

$$\text{SQNR} = \frac{S}{N_q} = \frac{8}{1.271 \times 10^{-4}} = 6.294 \times 10^4$$


$$\text{SQNR (dB)} = 10\log_{10}(6.294 \times 10^4) = 47.99 \text{ dB}$$


**Using formula:**

$$\text{SQNR (dB)} \approx 6.02 \times 8 + 1.76 = 48.16 + 1.76 = 49.92 \text{ dB}$$


**e) Bandwidth required:**


PAM signal bandwidth: $B_{PAM} \approx f_s = 10$ kHz


More precisely, considering pulse shape: $B_{PAM} \approx 1/\tau = 1/0.02 \times 10^{-3} = 50$ kHz


**f) Bit rate:**


With 8 bits per sample and $f_s = 10$ kHz:

$$\text{Bit rate} = b \times f_s = 8 \times 10000 = 80,000 \text{ bps} = 80 \text{ kbps}$$


---


### Problem 12.2 Solution


**Given:**

- Input: $x(t) = 2\sin(2\pi \cdot 4000t)$

- Sampling rate: $f_s = 40$ kHz

- Step size: $\Delta = 0.1$ V


**a) Check for slope overload:**


Maximum signal slope:

$$\max\left|\frac{dx(t)}{dt}\right| = 2 \times 2\pi \times 4000 = 16000\pi \approx 50,265 \text{ V/s}$$


Maximum tracking rate:

$$T_s = 1/40000 = 0.025 \text{ ms}$$

$$\frac{\Delta}{T_s} = \frac{0.1}{0.025 \times 10^{-3}} = 4000 \text{ V/s}$$


Since $50,265 > 4000$, **slope overload will occur!** ✗


**b) Bit rate:**


DM uses 1 bit per sample:

$$\text{Bit rate} = f_s = 40 \text{ kbps}$$


**c) Compare with quantized PAM using 4 bits:**


**PAM with 4 bits:**

- Bits per sample: $b = 4$

- If sampled at same rate: Bit rate = $4 \times 40 = 160$ kbps

- If sampled at Nyquist ($f_s = 8$ kHz): Bit rate = $4 \times 8 = 32$ kbps


**DM:**

- Bit rate = 40 kbps (at $f_s = 40$ kHz)


**d) Which has higher bit rate?**


**DM:** 40 kbps

**PAM (at same $f_s$):** 160 kbps (4× higher)


**PAM has higher bit rate** because it uses more bits per sample.


**e) Which is simpler to implement?**


**DM is simpler:**

- 1-bit quantizer (comparator)

- Simple up/down logic

- No complex ADC needed


**PAM is more complex:**

- Multi-bit ADC required

- More complex quantization

- But provides better quality


---


### Problem 12.3 Solution


**Given:**

- Signal: $x(t) = 6\cos(2\pi \cdot 2000t)$

- Required SQNR: $\geq 50$ dB

- Sampling rate: $f_s = 8$ kHz


**a) Minimum number of bits:**


From SQNR formula:

$$50 = 6.02b + 1.76$$

$$6.02b = 50 - 1.76 = 48.24$$

$$b = \frac{48.24}{6.02} = 8.01$$


**Answer:** Need at least **9 bits** (round up)


**b) Step size:**


With $b = 9$ bits and range $[-6, +6]$ V:

$$V_{pp} = 12 \text{ V}$$

$$L = 2^9 = 512$$

$$\Delta = \frac{12}{512} = 0.0234375 \text{ V} = 23.44 \text{ mV}$$


**c) Quantization noise power:**

$$N_q = \frac{\Delta^2}{12} = \frac{(0.0234375)^2}{12} = \frac{5.493 \times 10^{-4}}{12} = 4.577 \times 10^{-5} \text{ V}^2$$


**d) Actual SQNR achieved:**


Signal power: $S = A^2/2 = 36/2 = 18$ V²


SQNR:

$$\text{SQNR} = \frac{S}{N_q} = \frac{18}{4.577 \times 10^{-5}} = 3.932 \times 10^5$$


$$\text{SQNR (dB)} = 10\log_{10}(3.932 \times 10^5) = 55.95 \text{ dB}$$


**Using formula:**

$$\text{SQNR (dB)} = 6.02 \times 9 + 1.76 = 54.18 + 1.76 = 55.94 \text{ dB}$$


**This exceeds the requirement of 50 dB** ✓


**e) Data rate:**


With 9 bits per sample and $f_s = 8$ kHz:

$$\text{Data rate} = b \times f_s = 9 \times 8000 = 72,000 \text{ bps} = 72 \text{ kbps}$$


---


*End of Part 2 Solutions (Exercise Sets 7-12)*


*Good luck with your exam preparation!*



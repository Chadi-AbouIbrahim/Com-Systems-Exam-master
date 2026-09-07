# Group 2 Exercises - Analog Modulation (Amplitude-based)

This document contains exercises and problems covering amplitude modulation (AM, DSB-SC, SSB-AM) and detector circuits from Lectures 15 and 17.

---

## Exercise Set 1: Standard AM (DSB-FC)

### Problem 1.1 (Basic)
Given a standard AM signal:
$$s(t) = 10[1 + 0.6\cos(2\pi \cdot 5 \times 10^3 t)]\cos(2\pi \cdot 1 \times 10^6 t)$$

Find:
a) The carrier amplitude $A_c$
b) The modulating signal $m(t)$
c) The complex envelope $g(t)$
d) The real envelope $R(t)$
e) The modulation index $\mu$

**Solution Guide:**
- Compare with standard AM form: $s(t) = A_c[1 + m(t)]\cos(\omega_c t)$
- Identify $A_c$ and $m(t)$
- Find $g(t) = A_c[1 + m(t)]$
- Calculate modulation index: $\mu = \max|m(t)|$

---

### Problem 1.2 (Intermediate)
A standard AM signal has:
- Carrier amplitude: $A_c = 8$ V
- Modulating signal: $m(t) = 0.5\cos(2\pi \cdot 3 \times 10^3 t)$
- Carrier frequency: $f_c = 100$ kHz

Find:
a) The modulated signal $s(t)$
b) The spectrum $S(f)$
c) The bandwidth $B_T$
d) The average power $P_s$
e) The modulation efficiency $\eta$

---

### Problem 1.3 (Advanced)
For a standard AM signal with $g(t) = A_c[1 + m(t)]$ where $m(t)$ has zero mean:

Show that:
a) The average power is $P_s = \frac{1}{2}A_c^2[1 + P_m]$ where $P_m = \langle m^2(t) \rangle$
b) The carrier power is $P_c = \frac{1}{2}A_c^2$
c) The sideband power is $P_{SB} = \frac{1}{2}A_c^2 P_m$
d) The modulation efficiency is $\eta = \frac{P_m}{1 + P_m}$

---

## Exercise Set 2: DSB-SC (Double-Sideband Suppressed Carrier)

### Problem 2.1 (Basic)
A DSB-SC signal is given by:
$$s(t) = 5\cos(2\pi \cdot 2 \times 10^3 t)\cos(2\pi \cdot 100 \times 10^3 t)$$

Find:
a) The carrier amplitude $A_c$
b) The modulating signal $m(t)$
c) The complex envelope $g(t)$
d) Express $s(t)$ in terms of sidebands only

**Solution Guide:**
- Compare with DSB-SC form: $s(t) = A_c m(t)\cos(\omega_c t)$
- Use trigonometric identity to find sideband frequencies
- Note: No carrier component!

---

### Problem 2.2 (Intermediate)
Given a DSB-SC system:
- Modulating signal: $m(t) = 3\cos(2\pi \cdot 4 \times 10^3 t)$
- Carrier amplitude: $A_c = 6$ V
- Carrier frequency: $f_c = 500$ kHz

Find:
a) The DSB-SC signal $s(t)$
b) The spectrum $S(f)$
c) The bandwidth $B_T$
d) The average power $P_s$
e) Why envelope detector cannot be used for demodulation

---

### Problem 2.3 (Advanced)
Prove that for a DSB-SC signal $s(t) = A_c m(t)\cos(\omega_c t)$:

a) The spectrum contains no carrier component
b) The average power is $P_s = \frac{1}{2}A_c^2 P_m$ where $P_m = \langle m^2(t) \rangle$
c) All power is in the sidebands (100% efficiency)
d) The real envelope is $R(t) = A_c|m(t)|$, which loses sign information

---

## Exercise Set 3: SSB-AM (Single-Sideband AM)

### Problem 3.1 (Basic)
An upper single-sideband (USSB-AM) signal has complex envelope:
$$g(t) = 4[m(t) + j\hat{m}(t)]$$

where $m(t) = 2\cos(2\pi \cdot 1 \times 10^3 t)$ and $\hat{m}(t)$ is its Hilbert transform.

Find:
a) The Hilbert transform $\hat{m}(t)$
b) The USSB-AM signal $s(t)$
c) The bandwidth compared to DSB-SC

**Solution Guide:**
- For $m(t) = A_m\cos(\omega_m t)$, the Hilbert transform is $\hat{m}(t) = A_m\sin(\omega_m t)$
- USSB-AM: $s(t) = A_c[m(t)\cos(\omega_c t) - \hat{m}(t)\sin(\omega_c t)]$

---

### Problem 3.2 (Intermediate)
Given a modulating signal with spectrum:

$$M(f) = \begin{cases}
1, & |f| \leq 5 \text{ kHz} \\
0, & |f| > 5 \text{ kHz}
\end{cases}$$

and $A_c = 10$ V, $f_c = 1$ MHz:

Find:
a) The spectrum $G(f)$ of the complex envelope for USSB-AM
b) The spectrum $S(f)$ of the USSB-AM signal
c) The bandwidth $B_T$
d) Compare bandwidth with standard AM and DSB-SC

---

### Problem 3.3 (Advanced)
For an SSB-AM signal with $g(t) = A_c[m(t) \pm j\hat{m}(t)]$:

Show that:
a) The spectrum $G(f)$ is zero for negative frequencies (USSB) or positive frequencies (LSSB)
b) The bandwidth is $B$ (half of DSB-SC)
c) The average power is $P_s = \frac{1}{2}A_c^2 P_m$ (same as DSB-SC)
d) The signal can be written as $s(t) = A_c[m(t)\cos(\omega_c t) \mp \hat{m}(t)\sin(\omega_c t)]$

---

## Exercise Set 4: Power Calculations

### Problem 4.1 (Basic)
A standard AM signal has:
- $A_c = 5$ V
- $m(t) = 0.8\cos(2\pi \cdot 2 \times 10^3 t)$

Calculate:
a) The average power of the modulating signal $P_m$
b) The average power of the AM signal $P_s$
c) The carrier power $P_c$
d) The sideband power $P_{SB}$
e) The modulation efficiency $\eta$

**Solution Guide:**
- For cosine: $P_m = \langle m^2(t) \rangle = \frac{A_m^2}{2}$
- Use: $P_s = \frac{1}{2}A_c^2[1 + P_m]$
- Efficiency: $\eta = \frac{P_{SB}}{P_s}$

---

### Problem 4.2 (Intermediate)
Compare the power efficiency of three AM systems transmitting the same message $m(t)$ with $P_m = 0.25$:

a) Standard AM with $A_c = 10$ V
b) DSB-SC with $A_c = 10$ V
c) SSB-AM with $A_c = 10$ V

Calculate the total power and efficiency for each.

---

### Problem 4.3 (Advanced)
For a standard AM signal with sinusoidal modulation $m(t) = \mu\cos(\omega_m t)$:

Show that:
a) The peak envelope power is $P_{PEP} = \frac{1}{2}A_c^2(1 + \mu)^2$
b) The peak-to-average power ratio is $\frac{(1 + \mu)^2}{1 + \mu^2/2}$
c) At 100% modulation ($\mu = 1$), the peak-to-average ratio is 4/3 (or 1.25 dB)
d) The modulation efficiency at 100% modulation is $\eta = \frac{1}{3} \approx 33.3\%$

---

## Exercise Set 5: Modulation Index and Overmodulation

### Problem 5.1 (Basic)
A standard AM signal has modulating signal:
$$m(t) = 0.9\cos(2\pi \cdot 1 \times 10^3 t)$$

Determine:
a) The modulation index $\mu$
b) The percent modulation
c) Whether overmodulation occurs
d) The minimum and maximum envelope values

**Solution Guide:**
- Modulation index: $\mu = \max|m(t)|$
- Percent modulation: $100 \times \mu\%$
- Overmodulation if $\mu > 1$
- Envelope: $R(t) = A_c[1 + m(t)]$

---

### Problem 5.2 (Intermediate)
An AM signal has:
- $A_c = 6$ V
- Envelope varies between 2 V and 10 V

Find:
a) The modulation index $\mu$
b) The modulating signal amplitude $A_m$
c) The percent modulation
d) The minimum value of $m(t)$

---

### Problem 5.3 (Advanced)
For a standard AM signal, show that:

a) To avoid overmodulation, we must have $m(t) \geq -1$ for all $t$
b) If $m(t) < -1$ for some $t$, then $g(t) < 0$ and envelope detection fails
c) The condition $|m(t)| < 1$ ensures proper envelope detection
d) For sinusoidal modulation, 100% modulation ($\mu = 1$) is the maximum

---

## Exercise Set 6: Envelope Detector

### Problem 6.1 (Basic)
An envelope detector receives a standard AM signal:
$$v_{in}(t) = 8[1 + 0.7\cos(2\pi \cdot 3 \times 10^3 t)]\cos(2\pi \cdot 100 \times 10^3 t)$$

If the detector has output $v_{out}(t) = K R(t)$ where $K = 0.5$:

Find:
a) The output signal $v_{out}(t)$
b) The DC component
c) The AC component (the recovered message)
d) How to remove the DC component

**Solution Guide:**
- Envelope: $R(t) = A_c[1 + m(t)]$
- Output: $v_{out}(t) = K A_c[1 + m(t)]$
- DC = $K A_c$, AC = $K A_c m(t)$

---

### Problem 6.2 (Intermediate)
An envelope detector is used to demodulate an AM signal. The input is:
$$v_{in}(t) = 5[1 + 0.5\cos(2\pi \cdot 2 \times 10^3 t)]\cos(2\pi \cdot 50 \times 10^3 t)$$

The detector output is $v_{out}(t) = K|g(t)|$ where $K = 1$.

Find:
a) The output $v_{out}(t)$
b) The recovered message signal
c) Why this works for standard AM but not for DSB-SC

---

### Problem 6.3 (Advanced)
Show that an envelope detector with output $v_{out}(t) = K R(t)$:

a) Works correctly for standard AM when $|m(t)| < 1$
b) Fails for DSB-SC because $R(t) = A_c|m(t)|$ loses sign information
c) Requires $g(t) \geq 0$ for proper operation
d) Is a nonlinear detector (unlike product detector)

---

## Exercise Set 7: Product Detector

### Problem 7.1 (Basic)
A product detector receives a DSB-SC signal:
$$v_{in}(t) = 4\cos(2\pi \cdot 2 \times 10^3 t)\cos(2\pi \cdot 100 \times 10^3 t)$$

The local oscillator is synchronized: $v_{LO}(t) = 2\cos(2\pi \cdot 100 \times 10^3 t)$

Find:
a) The multiplier output $v_1(t)$
b) The lowpass filter output $v_{out}(t)$
c) The recovered message signal

**Solution Guide:**
- Multiply: $v_1(t) = v_{in}(t) \cdot v_{LO}(t)$
- Use: $\cos A \cos B = \frac{1}{2}[\cos(A+B) + \cos(A-B)]$
- Lowpass filter removes high-frequency term

---

### Problem 7.2 (Intermediate)
A product detector is used with:
- Input: $v_{in}(t) = A_c m(t)\cos(\omega_c t + \theta)$ (DSB-SC with phase error)
- Local oscillator: $v_{LO}(t) = A_0\cos(\omega_c t + \theta_0)$

Find:
a) The output when $\theta_0 = \theta$ (synchronized)
b) The output when $\theta_0 = \theta + \pi/2$ (90° phase error)
c) The output when $\theta_0 = \theta + \pi$ (180° phase error)
d) The effect of phase error on the output

---

### Problem 7.3 (Advanced)
Prove that for a product detector with input $v_{in}(t) = R(t)\cos[\omega_c t + \theta(t)]$ and local oscillator $v_{LO}(t) = A_0\cos(\omega_c t + \theta_0)$:

a) The output is $v_{out}(t) = \frac{1}{2}A_0 R(t)\cos[\theta(t) - \theta_0]$
b) When $\theta_0 = 0$ and $\theta(t) = 0$ (AM), output is $v_{out}(t) = \frac{1}{2}A_0 R(t)$
c) When $\theta_0 = 0$ and $R(t) = A_c$ (DSB-SC), output is $v_{out}(t) = \frac{1}{2}A_0 A_c m(t)$
d) The detector is linear (unlike envelope detector)

---

## Exercise Set 8: Spectrum Analysis

### Problem 8.1 (Basic)
A standard AM signal has:
- $A_c = 6$ V
- $m(t) = 2\cos(2\pi \cdot 4 \times 10^3 t)$
- $f_c = 200$ kHz

Find:
a) The spectrum $M(f)$ of the modulating signal
b) The spectrum $G(f)$ of the complex envelope
c) The spectrum $S(f)$ of the AM signal
d) Sketch the magnitude spectrum $|S(f)|$

**Solution Guide:**
- $M(f) = \delta(f - 4000) + \delta(f + 4000)$
- $G(f) = A_c[\delta(f) + M(f)]$
- Use: $S(f) = \frac{1}{2}[G(f - f_c) + G(f + f_c)]$

---

### Problem 8.2 (Intermediate)
Given a modulating signal with spectrum:
$$M(f) = \begin{cases}
2, & |f| \leq 8 \text{ kHz} \\
0, & |f| > 8 \text{ kHz}
\end{cases}$$

and standard AM with $A_c = 8$ V, $f_c = 500$ kHz:

Determine:
a) The spectrum $G(f)$
b) The spectrum $S(f)$
c) The bandwidth $B_T$
d) Identify carrier and sideband components

---

### Problem 8.3 (Advanced)
For a DSB-SC signal with $s(t) = A_c m(t)\cos(\omega_c t)$:

Show that:
a) The spectrum is $S(f) = \frac{A_c}{2}[M(f - f_c) + M(f + f_c)]$
b) There is no carrier component (no delta function at $\pm f_c$)
c) The bandwidth is $2B$ where $B$ is the bandwidth of $m(t)$
d) The spectrum is symmetric about $\pm f_c$

---

## Exercise Set 9: Comparison Problems

### Problem 9.1 (Intermediate)
Three AM systems transmit the same message $m(t) = \cos(2\pi \cdot 5 \times 10^3 t)$ with $A_c = 10$ V, $f_c = 1$ MHz:

a) Standard AM
b) DSB-SC
c) SSB-AM (USSB)

For each, find:
1. The complex envelope $g(t)$
2. The bandwidth $B_T$
3. The average power $P_s$
4. The modulation efficiency $\eta$

---

### Problem 9.2 (Advanced)
Compare standard AM, DSB-SC, and SSB-AM in terms of:

a) **Bandwidth efficiency** - which uses least bandwidth?
b) **Power efficiency** - which wastes least power?
c) **Implementation complexity** - which is simplest?
d) **Demodulation complexity** - which is easiest to demodulate?
e) **Noise performance** - which is most resistant to noise?

Provide a table summarizing the trade-offs.

---

## Exercise Set 10: Numerical Problems

### Problem 10.1 (Basic Calculation)
A standard AM radio station transmits:
- Carrier frequency: $f_c = 1000$ kHz
- Modulating signal: $m(t) = 0.8\cos(2\pi \cdot 5 \times 10^3 t)$
- Carrier amplitude: $A_c = 100$ V

Calculate:
a) The modulation index
b) The bandwidth
c) The average power (assuming 1Ω load)
d) The peak envelope power

---

### Problem 10.2 (Power Calculation)
An AM signal has average power $P_s = 50$ W and modulation efficiency $\eta = 25\%$.

Find:
a) The carrier power $P_c$
b) The sideband power $P_{SB}$
c) The average power of the modulating signal $P_m$ (if $A_c = 10$ V)

---

### Problem 10.3 (Bandwidth Calculation)
A modulating signal has bandwidth $B = 10$ kHz. Compare the bandwidth required for:

a) Standard AM
b) DSB-SC
c) SSB-AM

If the carrier frequency is $f_c = 1$ MHz, what frequency ranges do they occupy?

---

## Exercise Set 11: Conceptual Questions

### Question 11.1
Explain the differences between:
- Standard AM and DSB-SC
- DSB-SC and SSB-AM
- Envelope detector and product detector

---

### Question 11.2
Why is standard AM power inefficient? Discuss:
- Where the power goes
- Why the carrier doesn't carry information
- How DSB-SC and SSB-AM improve efficiency

---

### Question 11.3
Explain why:
a) Envelope detector works for standard AM but not DSB-SC
b) Product detector is needed for DSB-SC and SSB-AM
c) SSB-AM uses half the bandwidth of DSB-SC
d) Overmodulation causes distortion in AM

---

## Exercise Set 12: Derivation Problems

### Problem 12.1
Starting from $g(t) = A_c[1 + m(t)]$ for standard AM, derive:
$$S(f) = \frac{A_c}{2}[\delta(f - f_c) + M(f - f_c) + \delta(f + f_c) + M(f + f_c)]$$

**Hint:** Use the spectrum theorem and Fourier transform properties.

---

### Problem 12.2
Show that for a product detector with input $v_{in}(t) = g(t)\cos(\omega_c t)$ and local oscillator $v_{LO}(t) = A_0\cos(\omega_c t + \theta_0)$:

The output after lowpass filtering is:
$$v_{out}(t) = \frac{1}{2}A_0\text{Re}\{g(t)e^{-j\theta_0}\}$$

---

### Problem 12.3
Prove that the modulation efficiency of standard AM with sinusoidal modulation $m(t) = \mu\cos(\omega_m t)$ is:

$$\eta = \frac{\mu^2}{2 + \mu^2}$$

and show that the maximum efficiency (at $\mu = 1$) is $\eta_{max} = \frac{1}{3}$.

---

## Answer Key (Selected Problems)

### Solution 1.1
a) $A_c = 10$ V  
b) $m(t) = 0.6\cos(2\pi \cdot 5 \times 10^3 t)$  
c) $g(t) = 10[1 + 0.6\cos(2\pi \cdot 5 \times 10^3 t)]$  
d) $R(t) = 10[1 + 0.6\cos(2\pi \cdot 5 \times 10^3 t)]$  
e) $\mu = 0.6 = 60\%$ modulation

### Solution 4.1
a) $P_m = \frac{0.8^2}{2} = 0.32$  
b) $P_s = \frac{1}{2}(5)^2[1 + 0.32] = 12.5 \times 1.32 = 16.5$ W  
c) $P_c = \frac{1}{2}(5)^2 = 12.5$ W  
d) $P_{SB} = 16.5 - 12.5 = 4$ W  
e) $\eta = \frac{4}{16.5} = 0.242 = 24.2\%$

---

## Study Tips

1. **Master the complex envelopes:**
   - Standard AM: $g(t) = A_c[1 + m(t)]$
   - DSB-SC: $g(t) = A_c m(t)$
   - SSB-AM: $g(t) = A_c[m(t) \pm j\hat{m}(t)]$

2. **Power calculations:**
   - Standard AM: $P_s = \frac{1}{2}A_c^2[1 + P_m]$
   - DSB-SC/SSB: $P_s = \frac{1}{2}A_c^2 P_m$
   - Efficiency: $\eta = \frac{P_{SB}}{P_s}$

3. **Bandwidth:**
   - Standard AM/DSB-SC: $2B$
   - SSB-AM: $B$

4. **Detectors:**
   - Envelope: Works for standard AM only
   - Product: Works for all types, requires synchronization

5. **Modulation index:**
   - $\mu = \max|m(t)|$
   - Must have $\mu \leq 1$ to avoid overmodulation

---

*Good luck with your exam preparation!*



# Group 3 Exercises - Analog Modulation (Angle-based)

This document contains exercises and problems covering angle modulation (FM & PM) from Lecture 18.

---

## Exercise Set 1: Phase Modulation (PM)

### Problem 1.1 (Basic)
Given a PM signal:
$$s(t) = 8\cos[2\pi \cdot 1 \times 10^6 t + 0.5\sin(2\pi \cdot 5 \times 10^3 t)]$$

Find:
a) The carrier amplitude $A_c$
b) The carrier frequency $f_c$
c) The phase function $\theta(t)$
d) The modulating signal $m(t)$ if $D_p = 0.5$ rad/V
e) The real envelope $R(t)$

**Solution Guide:**
- Compare with PM form: $s(t) = A_c\cos[\omega_c t + \theta(t)]$
- Identify $A_c$, $\omega_c$, and $\theta(t)$
- For PM: $\theta(t) = D_p m(t)$

---

### Problem 1.2 (Intermediate)
A PM signal has:
- Carrier amplitude: $A_c = 10$ V
- Carrier frequency: $f_c = 100$ kHz
- Phase sensitivity: $D_p = 2$ rad/V
- Modulating signal: $m(t) = 3\cos(2\pi \cdot 4 \times 10^3 t)$

Find:
a) The phase function $\theta(t)$
b) The modulated signal $s(t)$
c) The complex envelope $g(t)$
d) The instantaneous frequency $f_i(t)$
e) The peak frequency deviation $\Delta F$

---

### Problem 1.3 (Advanced)
For a PM signal with $s(t) = A_c\cos[\omega_c t + D_p m(t)]$:

Show that:
a) The instantaneous frequency is $f_i(t) = f_c + \frac{D_p}{2\pi}\frac{dm(t)}{dt}$
b) The frequency deviation is $f_d(t) = \frac{D_p}{2\pi}\frac{dm(t)}{dt}$
c) The peak frequency deviation is $\Delta F = \frac{D_p}{2\pi}\max\left|\frac{dm(t)}{dt}\right|$
d) For sinusoidal modulation $m(t) = A_m\cos(\omega_m t)$, the peak deviation is $\Delta F = \frac{D_p A_m f_m}{2\pi}$

---

## Exercise Set 2: Frequency Modulation (FM)

### Problem 2.1 (Basic)
Given an FM signal:
$$s(t) = 6\cos\left[2\pi \cdot 500 \times 10^3 t + 4\int_0^t \cos(2\pi \cdot 2 \times 10^3 \tau) d\tau\right]$$

Find:
a) The carrier amplitude $A_c$
b) The carrier frequency $f_c$
c) The frequency sensitivity $D_f$
d) The modulating signal $m(t)$
e) The phase function $\theta(t)$

**Solution Guide:**
- Compare with FM form: $s(t) = A_c\cos[\omega_c t + D_f \int m(t) dt]$
- Identify $A_c$, $\omega_c$, and the integral term

---

### Problem 2.2 (Intermediate)
An FM signal has:
- Carrier amplitude: $A_c = 12$ V
- Carrier frequency: $f_c = 1$ MHz
- Frequency sensitivity: $D_f = 2\pi \times 10^4$ rad/s per unit
- Modulating signal: $m(t) = 2\cos(2\pi \cdot 3 \times 10^3 t)$

Find:
a) The phase function $\theta(t)$
b) The modulated signal $s(t)$
c) The instantaneous frequency $f_i(t)$
d) The peak frequency deviation $\Delta F$
e) The modulation index $\beta$

---

### Problem 2.3 (Advanced)
For an FM signal with $s(t) = A_c\cos[\omega_c t + D_f \int m(t) dt]$:

Show that:
a) The instantaneous frequency is $f_i(t) = f_c + \frac{D_f}{2\pi}m(t)$
b) The frequency deviation is $f_d(t) = \frac{D_f}{2\pi}m(t)$
c) The peak frequency deviation is $\Delta F = \frac{D_f}{2\pi}\max|m(t)|$
d) For sinusoidal modulation $m(t) = A_m\cos(\omega_m t)$, the modulation index is $\beta = \frac{D_f A_m}{\omega_m} = \frac{\Delta F}{f_m}$

---

## Exercise Set 3: Relationship Between PM and FM

### Problem 3.1 (Basic)
A PM signal has:
- Phase: $\theta(t) = 2\cos(2\pi \cdot 1 \times 10^3 t)$
- Carrier: $f_c = 100$ kHz, $A_c = 5$ V

Find:
a) The instantaneous frequency $f_i(t)$
b) The equivalent FM signal (find the FM modulating signal that produces the same $s(t)$)
c) The frequency sensitivity $D_f$ if the FM message is $m_f(t) = -4\pi \times 10^3\sin(2\pi \cdot 10^3 t)$

---

### Problem 3.2 (Intermediate)
Show that a PM signal with message $m_p(t) = A_m\cos(\omega_m t)$ is equivalent to an FM signal.

Find:
a) The FM message $m_f(t)$ that produces the same signal
b) The relationship between $D_p$ and $D_f$
c) The phase functions for both PM and FM

---

### Problem 3.3 (Advanced)
Prove that:
a) PM with message $m(t)$ is equivalent to FM with message $\frac{dm(t)}{dt}$
b) FM with message $m(t)$ is equivalent to PM with message $\int m(t) dt$
c) The relationship: $D_p \frac{dm_{PM}(t)}{dt} = D_f m_{FM}(t)$ when signals are equivalent

---

## Exercise Set 4: Instantaneous Frequency

### Problem 4.1 (Basic)
An angle-modulated signal has phase:
$$\theta(t) = 0.3\sin(2\pi \cdot 5 \times 10^3 t)$$

and carrier frequency $f_c = 200$ kHz.

Find:
a) The instantaneous frequency $f_i(t)$
b) The frequency deviation $f_d(t)$
c) The maximum and minimum instantaneous frequencies
d) The peak frequency deviation $\Delta F$

---

### Problem 4.2 (Intermediate)
For a PM signal with:
- $D_p = 1$ rad/V
- $m(t) = 4\cos(2\pi \cdot 2 \times 10^3 t)$
- $f_c = 500$ kHz

Find:
a) The phase function $\theta(t)$
b) The instantaneous frequency $f_i(t)$
c) The frequency deviation $f_d(t)$
d) Sketch $f_i(t)$ vs $t$ for one period of $m(t)$

---

### Problem 4.3 (Advanced)
For an FM signal, show that:
a) The instantaneous frequency is always positive: $f_i(t) > 0$
b) The condition for $f_i(t) > 0$ is: $f_c > \frac{D_f}{2\pi}\max|m(t)| = \Delta F$
c) If $f_c < \Delta F$, the signal has negative frequencies (not physically realizable)
d) The carrier frequency must satisfy: $f_c \gg \Delta F$ for practical systems

---

## Exercise Set 5: Complex Envelope and Power

### Problem 5.1 (Basic)
An angle-modulated signal has:
- Complex envelope: $g(t) = 10e^{j0.2\sin(2\pi \cdot 3 \times 10^3 t)}$
- Carrier frequency: $f_c = 1$ MHz

Find:
a) The carrier amplitude $A_c$
b) The real envelope $R(t)$
c) The phase function $\theta(t)$
d) The average power $P_s$

**Solution Guide:**
- For angle modulation: $g(t) = A_c e^{j\theta(t)}$
- Power: $P_s = \frac{1}{2}A_c^2$ (constant!)

---

### Problem 5.2 (Intermediate)
An FM signal has:
- $A_c = 8$ V
- $\theta(t) = 5\sin(2\pi \cdot 4 \times 10^3 t)$

Find:
a) The complex envelope $g(t)$
b) The in-phase component $x(t)$
c) The quadrature component $y(t)$
d) The average power $P_s$
e) Verify that $P_s = \frac{1}{2}[x^2(t) + y^2(t)]$ (time average)

---

### Problem 5.3 (Advanced)
Prove that for any angle-modulated signal with $g(t) = A_c e^{j\theta(t)}$:

a) The average power is $P_s = \frac{1}{2}A_c^2$ (independent of $\theta(t)$)
b) The peak envelope power equals the average power: $P_{PEP} = P_s$
c) The power is constant regardless of modulation depth
d) Compare this with AM, where power depends on modulation

---

## Exercise Set 6: Modulation Index and Bessel Functions

### Problem 6.1 (Basic)
An FM signal has:
- Modulating signal: $m(t) = 3\cos(2\pi \cdot 5 \times 10^3 t)$
- Frequency sensitivity: $D_f = 2\pi \times 10^4$ rad/s per unit
- Modulating frequency: $f_m = 5$ kHz

Find:
a) The modulation index $\beta$
b) The peak frequency deviation $\Delta F$
c) Verify that $\beta = \frac{\Delta F}{f_m}$
d) Is this narrowband or wideband FM?

**Solution Guide:**
- For FM: $\beta = \frac{D_f A_m}{\omega_m} = \frac{D_f A_m}{2\pi f_m}$
- $\Delta F = \frac{D_f A_m}{2\pi}$
- Narrowband if $\beta \ll 1$, wideband if $\beta \gg 1$

---

### Problem 6.2 (Intermediate)
For an FM signal with sinusoidal modulation:
- $A_m = 2$ V
- $f_m = 10$ kHz
- $\beta = 5$

Find:
a) The frequency sensitivity $D_f$
b) The peak frequency deviation $\Delta F$
c) The approximate number of significant sidebands
d) The bandwidth using Carson's rule

---

### Problem 6.3 (Advanced)
For sinusoidal angle modulation, show that:

a) The modulation index $\beta$ determines the number of significant sidebands
b) For $\beta \ll 1$: Only carrier and first sidebands are significant
c) For $\beta \gg 1$: Approximately $\beta + 1$ sidebands on each side contain most power
d) The carrier component disappears when $J_0(\beta) = 0$ (first null at $\beta \approx 2.405$)
e) Power conservation: $\sum_{n=-\infty}^{+\infty} J_n^2(\beta) = 1$

---

## Exercise Set 7: Spectrum Analysis

### Problem 7.1 (Basic)
An FM signal has:
- $A_c = 6$ V
- $f_c = 100$ kHz
- $\beta = 2$
- $f_m = 5$ kHz

Find:
a) The spectrum $G(f)$ of the complex envelope
b) The spectrum $S(f)$ of the FM signal
c) The frequencies of the carrier and first few sidebands
d) The approximate amplitudes using Bessel function values

**Solution Guide:**
- $G(f) = A_c \sum_{n=-\infty}^{+\infty} J_n(\beta)\delta(f - nf_m)$
- $S(f) = \frac{A_c}{2}\sum_{n=-\infty}^{+\infty} J_n(\beta)[\delta(f - f_c - nf_m) + \delta(f + f_c - nf_m)]$
- Bessel values: $J_0(2) \approx 0.22$, $J_1(2) \approx 0.58$, $J_2(2) \approx 0.35$

---

### Problem 7.2 (Intermediate)
For an FM signal with:
- $A_c = 10$ V
- $f_c = 1$ MHz
- $\beta = 4$
- $f_m = 8$ kHz

Determine:
a) The spectrum $S(f)$
b) The power in the carrier component
c) The power in the first sideband pair
d) The total power (verify it equals $\frac{1}{2}A_c^2$)

---

### Problem 7.3 (Advanced)
Show that for sinusoidal angle modulation:

a) The spectrum consists of discrete components at $f_c \pm nf_m$ for $n = 0, 1, 2, \ldots$
b) The amplitude of the $n$-th sideband pair is $\frac{A_c}{2}J_n(\beta)$
c) The spectrum is symmetric: $|S(f_c + nf_m)| = |S(f_c - nf_m)|$
d) For large $\beta$, the spectrum extends approximately from $f_c - \Delta F - f_m$ to $f_c + \Delta F + f_m$

---

## Exercise Set 8: Carson's Rule and Bandwidth

### Problem 8.1 (Basic)
An FM signal has:
- Peak frequency deviation: $\Delta F = 25$ kHz
- Modulating frequency: $f_m = 5$ kHz

Find:
a) The modulation index $\beta$
b) The bandwidth using Carson's rule
c) Classify as narrowband or wideband FM
d) Compare bandwidth with equivalent AM signal

**Solution Guide:**
- Carson's rule: $B_T \approx 2(\Delta F + f_m) = 2(\beta + 1)f_m$
- Narrowband: $\beta \ll 1$, Wideband: $\beta \gg 1$

---

### Problem 8.2 (Intermediate)
Compare the bandwidth for three FM systems:

a) Narrowband FM: $\beta = 0.5$, $f_m = 10$ kHz
b) Medium FM: $\beta = 5$, $f_m = 10$ kHz
c) Wideband FM: $\beta = 20$, $f_m = 10$ kHz

For each, find:
1. $\Delta F$
2. Bandwidth using Carson's rule
3. Approximate number of significant sidebands

---

### Problem 8.3 (Advanced)
For an FM signal, show that:

a) Carson's rule: $B_T \approx 2(\Delta F + f_m)$ is an approximation
b) For narrowband FM ($\beta \ll 1$): $B_T \approx 2f_m$ (similar to AM)
c) For wideband FM ($\beta \gg 1$): $B_T \approx 2\Delta F$ (dominated by deviation)
d) The exact bandwidth depends on Bessel function values, but Carson's rule gives a good estimate
e) For PM, the bandwidth formula is: $B_T \approx 2\left(\frac{D_p \max|\frac{dm}{dt}|}{2\pi} + f_m\right)$

---

## Exercise Set 9: Power Distribution

### Problem 9.1 (Basic)
An FM signal has:
- $A_c = 8$ V
- $\beta = 3$

Using approximate Bessel function values:
- $J_0(3) \approx 0.26$
- $J_1(3) \approx 0.34$
- $J_2(3) \approx 0.49$
- $J_3(3) \approx 0.31$

Find:
a) The total average power $P_s$
b) The power in the carrier $P_c$
c) The power in the first sideband pair $P_1$
d) The power in the second sideband pair $P_2$
e) Verify power conservation: $P_c + 2\sum_{n=1}^{\infty} P_n = P_s$

---

### Problem 9.2 (Intermediate)
For an FM signal with $\beta = 2.405$ (first carrier null):

Find:
a) The power in the carrier component
b) The total power (should equal $\frac{1}{2}A_c^2$)
c) Where the power goes (all in sidebands)
d) The approximate bandwidth

---

### Problem 9.3 (Advanced)
Show that for sinusoidal angle modulation:

a) The total power is always $P_s = \frac{1}{2}A_c^2$ regardless of $\beta$
b) Power in carrier: $P_c = \frac{A_c^2}{2}J_0^2(\beta)$
c) Power in $n$-th sideband pair: $P_n = A_c^2 J_n^2(\beta)$
d) Power conservation: $\sum_{n=-\infty}^{+\infty} J_n^2(\beta) = 1$
e) As $\beta$ increases, carrier power decreases and sideband power increases

---

## Exercise Set 10: Comparison Problems

### Problem 10.1 (Intermediate)
Compare AM and FM for the same message $m(t) = \cos(2\pi \cdot 5 \times 10^3 t)$:

**AM System:**
- $A_c = 10$ V, $f_c = 1$ MHz, $\mu = 0.8$

**FM System:**
- $A_c = 10$ V, $f_c = 1$ MHz, $\beta = 5$, $f_m = 5$ kHz

For each, find:
1. Bandwidth
2. Average power
3. Power distribution (carrier vs sidebands)
4. Advantages and disadvantages

---

### Problem 10.2 (Advanced)
Compare narrowband FM and wideband FM:

**Narrowband FM:**
- $\beta = 0.5$, $f_m = 10$ kHz, $A_c = 5$ V

**Wideband FM:**
- $\beta = 10$, $f_m = 10$ kHz, $A_c = 5$ V

For each, find:
1. $\Delta F$
2. Bandwidth
3. Number of significant sidebands
4. Power in carrier vs sidebands
5. Applications

---

## Exercise Set 11: Numerical Problems

### Problem 11.1 (Basic Calculation)
An FM radio station transmits:
- Carrier frequency: $f_c = 100$ MHz
- Peak frequency deviation: $\Delta F = 75$ kHz
- Maximum modulating frequency: $f_m = 15$ kHz

Calculate:
a) The modulation index $\beta$
b) The bandwidth using Carson's rule
c) The frequency range occupied by the signal
d) Compare with AM bandwidth for the same $f_m$

---

### Problem 11.2 (Power Calculation)
An FM signal has:
- $A_c = 12$ V
- $\beta = 4$

Calculate:
a) The average power $P_s$
b) The peak envelope power $P_{PEP}$
c) The ratio $P_{PEP}/P_s$ (compare with AM)
d) If the signal is measured across a 50Ω load, find the power in watts

---

### Problem 11.3 (Bandwidth Calculation)
A modulating signal has:
- Maximum frequency: $f_m = 8$ kHz
- Maximum amplitude: $A_m = 3$ V

For FM with $D_f = 2\pi \times 2 \times 10^4$ rad/s per unit:

Find:
a) The peak frequency deviation $\Delta F$
b) The modulation index $\beta$
c) The bandwidth using Carson's rule
d) If $f_c = 90$ MHz, what frequency range does the signal occupy?

---

## Exercise Set 12: Conceptual Questions

### Question 12.1
Explain the differences between:
- Phase Modulation (PM) and Frequency Modulation (FM)
- Angle modulation and Amplitude modulation
- Narrowband FM and Wideband FM

---

### Question 12.2
Why is angle modulation (FM/PM) more resistant to noise than AM? Discuss:
- Constant amplitude property
- Noise characteristics
- Trade-offs (bandwidth vs noise performance)

---

### Question 12.3
Explain:
a) Why the power in angle-modulated signals is constant
b) How the modulation index $\beta$ affects the spectrum
c) Why Carson's rule is an approximation
d) When the carrier component disappears in FM

---

## Exercise Set 13: Derivation Problems

### Problem 13.1
Starting from $s(t) = A_c\cos[\omega_c t + \theta(t)]$ for angle modulation, show that:

a) The instantaneous frequency is $f_i(t) = f_c + \frac{1}{2\pi}\frac{d\theta(t)}{dt}$
b) For PM: $f_i(t) = f_c + \frac{D_p}{2\pi}\frac{dm(t)}{dt}$
c) For FM: $f_i(t) = f_c + \frac{D_f}{2\pi}m(t)$

---

### Problem 13.2
Derive the modulation index formulas:

a) For PM with $m(t) = A_m\sin(\omega_m t)$: $\beta = D_p A_m$
b) For FM with $m(t) = A_m\cos(\omega_m t)$: $\beta = \frac{D_f A_m}{\omega_m} = \frac{\Delta F}{f_m}$
c) Show that $\beta$ represents the peak phase deviation

---

### Problem 13.3
Prove that for sinusoidal angle modulation:

a) The complex envelope is periodic: $g(t) = A_c e^{j\beta\sin(\omega_m t)}$
b) The Fourier series coefficients are Bessel functions: $c_n = J_n(\beta)$
c) The spectrum is: $G(f) = A_c \sum_{n=-\infty}^{+\infty} J_n(\beta)\delta(f - nf_m)$
d) The bandpass spectrum is: $S(f) = \frac{A_c}{2}\sum_{n=-\infty}^{+\infty} J_n(\beta)[\delta(f - f_c - nf_m) + \delta(f + f_c - nf_m)]$

---

## Answer Key (Selected Problems)

### Solution 1.1
a) $A_c = 8$ V  
b) $f_c = 1 \times 10^6$ Hz = 1 MHz  
c) $\theta(t) = 0.5\sin(2\pi \cdot 5 \times 10^3 t)$  
d) $m(t) = \sin(2\pi \cdot 5 \times 10^3 t)$ (since $\theta = D_p m$, so $m = \theta/D_p$)  
e) $R(t) = 8$ (constant)

### Solution 2.2
a) $\theta(t) = \frac{D_f A_m}{\omega_m}\sin(\omega_m t) = \frac{2\pi \times 10^4 \times 2}{2\pi \times 3 \times 10^3}\sin(2\pi \cdot 3 \times 10^3 t) = \frac{20}{3}\sin(2\pi \cdot 3 \times 10^3 t)$  
b) $s(t) = 12\cos[2\pi \cdot 10^6 t + \frac{20}{3}\sin(2\pi \cdot 3 \times 10^3 t)]$  
c) $f_i(t) = 10^6 + \frac{2 \times 10^4}{2\pi} \times 2\cos(2\pi \cdot 3 \times 10^3 t) = 10^6 + \frac{2 \times 10^4}{\pi}\cos(2\pi \cdot 3 \times 10^3 t)$ Hz  
d) $\Delta F = \frac{D_f A_m}{2\pi} = \frac{2\pi \times 10^4 \times 2}{2\pi} = 2 \times 10^4 = 20$ kHz  
e) $\beta = \frac{\Delta F}{f_m} = \frac{20 \times 10^3}{3 \times 10^3} = \frac{20}{3} \approx 6.67$

### Solution 6.1
a) $\beta = \frac{D_f A_m}{2\pi f_m} = \frac{2\pi \times 10^4 \times 3}{2\pi \times 5 \times 10^3} = \frac{3 \times 10^4}{5 \times 10^3} = 6$  
b) $\Delta F = \frac{D_f A_m}{2\pi} = \frac{2\pi \times 10^4 \times 3}{2\pi} = 3 \times 10^4 = 30$ kHz  
c) $\beta = \frac{\Delta F}{f_m} = \frac{30 \times 10^3}{5 \times 10^3} = 6$ ✓  
d) Since $\beta = 6 \gg 1$, this is **wideband FM**

---

## Study Tips

1. **Master the phase relationships:**
   - PM: $\theta(t) = D_p m(t)$
   - FM: $\theta(t) = D_f \int m(t) dt$

2. **Instantaneous frequency:**
   - $f_i(t) = f_c + \frac{1}{2\pi}\frac{d\theta(t)}{dt}$
   - PM: depends on derivative of message
   - FM: depends directly on message

3. **Modulation index:**
   - PM: $\beta = D_p A_m$
   - FM: $\beta = \frac{D_f A_m}{\omega_m} = \frac{\Delta F}{f_m}$
   - Determines bandwidth and spectrum shape

4. **Power:**
   - Always constant: $P_s = \frac{1}{2}A_c^2$
   - Independent of modulation
   - Distributed among carrier and sidebands

5. **Bandwidth (Carson's rule):**
   - $B_T \approx 2(\Delta F + f_m) = 2(\beta + 1)f_m$
   - Narrowband: $\beta \ll 1$ → $B_T \approx 2f_m$
   - Wideband: $\beta \gg 1$ → $B_T \approx 2\Delta F$

6. **Bessel functions:**
   - Describe spectrum for sinusoidal modulation
   - $J_0(\beta)$ gives carrier amplitude
   - $J_n(\beta)$ gives $n$-th sideband amplitude
   - Power conservation: $\sum J_n^2(\beta) = 1$

---

*Good luck with your exam preparation!*



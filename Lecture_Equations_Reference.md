# Communication Systems - Complete Equations Reference

**Comprehensive collection of all key equations from Groups 1-6**

---

## Table of Contents

0. [Lecture 2: Power Spectral Density](#lecture-2)
1. [Lecture 3: Orthogonal Representation of Signals](#lecture-3)
2. [Group 1: Foundations of Modulation](#group-1)
2. [Group 2: Analog Modulation - Amplitude-based](#group-2)
3. [Group 3: Analog Modulation - Angle-based](#group-3)
4. [Group 4: Digital & Pulse Modulation](#group-4)
5. [Group 5: Multiplexing (TDM)](#group-5)
6. [Group 6: Frequency Translation & Receiver Design](#group-6)

---

## Lecture 2: Power Spectral Density {#lecture-2}

### Energy and Power Signals

**Energy of a Signal:**
$$E = \lim_{T \to \infty} \int_{-T/2}^{T/2} w^2(t) dt$$

**Power of a Signal:**
$$P = \lim_{T \to \infty} \frac{1}{T} \int_{-T/2}^{T/2} w^2(t) dt$$

---

### Time Average Operator

**General Definition:**
$$\langle w(t) \rangle = \lim_{T \to \infty} \frac{1}{T} \int_{-T/2}^{T/2} w(t) dt$$

**For Periodic Signals:**
$$\langle w(t) \rangle = \frac{1}{T_0} \int_{T_0} w(t) dt$$

---

### Power Spectral Density (PSD)

**Average Power from PSD:**
$$P = \int_{-\infty}^{\infty} \mathcal{P}_w(f) df$$

**Wiener-Khintchine Theorem:**
$$\mathcal{P}_w(f) = \mathcal{F}[R_w(\tau)]$$

---

### Autocorrelation

**Definition for Power Signals:**
$$R_w(\tau) = \langle w(t)w(t+\tau) \rangle = \lim_{T \to \infty} \frac{1}{T} \int_{-T/2}^{T/2} w(t)w(t+\tau) dt$$

**Average Power:**
$$P = R_w(0)$$

---

## Lecture 3: Orthogonal Representation of Signals {#lecture-3}

### Orthogonal Functions

**Orthogonality Condition:**
$$\int_a^b \phi_n(t)\phi_m^*(t) dt = K_n \delta_{nm} = \begin{cases} 0, & n \neq m \\ K_n, & n = m \end{cases}$$

**Orthonormal Condition:**
$$K_n = 1$$

---

### Orthogonal Series

**Series Representation:**
$$w(t) = \sum_n a_n \phi_n(t)$$

**Coefficients:**
$$a_n = \frac{1}{K_n} \int_a^b w(t)\phi_n^*(t) dt$$

---

### Fourier Series

**Orthogonal Functions:**
$$\phi_n(t) = e^{jn\omega_0 t}$$
where $\omega_0 = 2\pi f_0 = \frac{2\pi}{T_0}$ and $T_0 = b - a$

**Fourier Series Representation:**
$$w(t) = \sum_{n \in \mathbb{Z}} c_n e^{jn\omega_0 t}$$

**Fourier Coefficients:**
$$c_n = \frac{1}{T_0} \int_{a}^{a+T_0} w(t)e^{-jn\omega_0 t} dt$$

**Symmetry Properties (for real $w(t)$):**
- Real: $c_n = c_{-n}^*$
- Real and Even: $\text{Im}[c_n] = 0$
- Real and Odd: $\text{Re}[c_n] = 0$

---

### Spectrum and Power of Periodic Waveforms

**Spectrum:**
$$W(f) = \sum_{n \in \mathbb{Z}} c_n \delta(f - nf_0)$$

**Power Spectral Density (PSD):**
$$\mathcal{P}_w(f) = \sum_{n \in \mathbb{Z}} |c_n|^2 \delta(f - nf_0)$$

**Average Power:**
$$P = R_w(0) = \sum_{n \in \mathbb{Z}} |c_n|^2$$

---

### LTI Systems and Distortion-less Transmission

**Power Transfer Function:**
$$G_h(f) = |H(f)|^2$$

**Output PSD:**
$$\mathcal{P}_y(f) = |H(f)|^2 \mathcal{P}_x(f)$$

**Distortion-less Channel Conditions:**
- Time Domain: $y(t) = A x(t - T_d)$
- Amplitude Response: $|H(f)| = A$
- Phase Response: $\arg[H(f)] = -2\pi T_d f$

---

## Group 1: Foundations of Modulation {#group-1}

### Core Representation

**Fundamental Complex Envelope Representation:**
$$v(t) = \text{Re}\{g(t)e^{j\omega_c t}\}$$

**Where:**
- $v(t)$ = bandpass signal (real-valued, high frequency)
- $g(t)$ = complex envelope (complex-valued, baseband)
- $\omega_c = 2\pi f_c$ = carrier angular frequency
- $f_c$ = carrier frequency (Hz)

**Physical Meaning:** Any bandpass signal can be represented as the real part of a complex envelope multiplied by a carrier.

---

### Three Equivalent Representations

#### 1. Complex Form (Rectangular)
$$g(t) = x(t) + jy(t)$$

**Bandpass signal:**
$$v(t) = x(t)\cos(\omega_c t) - y(t)\sin(\omega_c t)$$

**Where:**
- $x(t)$ = in-phase component (real part)
- $y(t)$ = quadrature component (imaginary part)

#### 2. Polar Form
$$g(t) = R(t)e^{j\theta(t)}$$

**Bandpass signal:**
$$v(t) = R(t)\cos[\omega_c t + \theta(t)]$$

**Where:**
- $R(t) = |g(t)|$ = real envelope (amplitude)
- $\theta(t) = \arg[g(t)]$ = phase

#### 3. Magnitude-Phase Form
$$g(t) = |g(t)|e^{j\arg[g(t)]} = R(t)e^{j\theta(t)}$$

---

### Conversion Between Representations

**From Complex to Polar:**
$$R(t) = |g(t)| = \sqrt{x^2(t) + y^2(t)}$$

$$\theta(t) = \arg[g(t)] = \tan^{-1}\left(\frac{y(t)}{x(t)}\right)$$

**From Polar to Complex:**
$$x(t) = R(t)\cos[\theta(t)]$$

$$y(t) = R(t)\sin[\theta(t)]$$

---

### Spectrum of Bandpass Signals

**Spectrum Theorem:**
$$V(f) = \frac{1}{2}[G(f - f_c) + G^*(-f - f_c)]$$

**Where:**
- $V(f)$ = Fourier transform of $v(t)$
- $G(f)$ = Fourier transform of $g(t)$
- $G^*(f)$ = complex conjugate of $G(f)$

**Special Case (Real $g(t)$):**
$$V(f) = \frac{1}{2}[G(f - f_c) + G(f + f_c)]$$

**Physical Meaning:** The spectrum of the bandpass signal is the baseband spectrum shifted to $\pm f_c$.

---

### Power Spectral Density (PSD)

**PSD of Bandpass Signal:**
$$P_v(f) = \frac{1}{4}[P_g(f - f_c) + P_g(-f - f_c)]$$

**Where:**
- $P_v(f)$ = PSD of $v(t)$
- $P_g(f)$ = PSD of $g(t)$

**Special Case (Real $g(t)$):**
$$P_v(f) = \frac{1}{4}[P_g(f - f_c) + P_g(f + f_c)]$$

**Autocorrelation:**
$$R_v(\tau) = \frac{1}{2}\text{Re}\{R_g(\tau)e^{j\omega_c \tau}\}$$

---

### Power Calculations

**Average Power (Four Equivalent Forms):**
$$P_v = \langle v^2(t) \rangle = \int_{-\infty}^{+\infty} P_v(f)df = R_v(0) = \frac{1}{2}\langle |g(t)|^2 \rangle$$

**Most Useful Form:**
$$P_v = \frac{1}{2}\langle |g(t)|^2 \rangle$$

**For Real $g(t)$:**
$$P_v = \frac{1}{2}\langle g^2(t) \rangle$$

**Peak Envelope Power (PEP):**
$$P_{PEP} = \frac{1}{2}[\max|g(t)|]^2$$

**Physical Meaning:** PEP is the power if the envelope stayed at its maximum value.

---

## Group 2: Analog Modulation - Amplitude-based {#group-2}

### Standard AM (Double-Sideband with Carrier)

**Complex Envelope:**
$$g(t) = A_c[1 + m(t)]$$

**Modulated Signal:**
$$s(t) = A_c[1 + m(t)]\cos(\omega_c t)$$

**Real Envelope:**
$$R(t) = A_c[1 + m(t)]$$

**Constraint:** $m(t) \geq -1$ to ensure $g(t) \geq 0$

**In-Phase and Quadrature Components:**
- $x(t) = A_c[1 + m(t)]$
- $y(t) = 0$
- $\theta(t) = 0$

---

### DSB-SC (Double-Sideband Suppressed Carrier)

**Complex Envelope:**
$$g(t) = A_c m(t)$$

**Modulated Signal:**
$$s(t) = A_c m(t)\cos(\omega_c t)$$

**Real Envelope:**
$$R(t) = A_c|m(t)|$$

**Note:** Envelope is $|m(t)|$, not $m(t)$ itself!

---

### SSB-AM (Single-Sideband AM)

**Upper Single-Sideband (USSB-AM) Complex Envelope:**
$$g(t) = A_c[m(t) + j\hat{m}(t)]$$

**Lower Single-Sideband (LSSB-AM) Complex Envelope:**
$$g(t) = A_c[m(t) - j\hat{m}(t)]$$

**Where:** $\hat{m}(t)$ is the Hilbert transform of $m(t)$

**Modulated Signal (USSB):**
$$s(t) = A_c[m(t)\cos(\omega_c t) - \hat{m}(t)\sin(\omega_c t)]$$

**Modulated Signal (LSSB):**

$$s(t) = A_c[m(t)\cos(\omega_c t) + \hat{m}(t)\sin(\omega_c t)]$$

**Hilbert Transform (Frequency Domain):**

$$\hat{M}(f) = -j\text{sgn}(f)M(f) = \begin{cases}
-jM(f), & f > 0 \\
+jM(f), & f < 0
\end{cases}$$

---

### Spectrum Analysis

**Standard AM Spectrum:**

$$S(f) = \frac{A_c}{2}[\delta(f - f_c) + M(f - f_c) + \delta(f + f_c) + M(f + f_c)]$$

**DSB-SC Spectrum:**

$$S(f) = \frac{A_c}{2}[M(f - f_c) + M(f + f_c)]$$

**SSB-AM Spectrum (USSB):**

$$G(f) = \begin{cases}
2A_c M(f), & f > 0 \\
0, & f < 0
\end{cases}$$

**Bandwidth:**
- Standard AM: $B_T = 2B$
- DSB-SC: $B_T = 2B$
- SSB-AM: $B_T = B$ (half of DSB-SC!)

---

### Power Calculations

**Standard AM Power:**
$$P_s = \frac{1}{2}A_c^2[1 + P_m]$$

**Where:** $P_m = \langle m^2(t) \rangle$ is the power of the modulating signal

**Power Breakdown:**
- **Carrier power:** $P_c = \frac{1}{2}A_c^2$
- **Sideband power:** $P_{SB} = \frac{1}{2}A_c^2 P_m$
- **Total power:** $P_s = P_c + P_{SB}$

**DSB-SC Power:**
$$P_s = \frac{1}{2}A_c^2 P_m$$

**SSB-AM Power:**
$$P_s = \frac{1}{2}A_c^2 P_m$$

**Note:** DSB-SC and SSB-AM have no carrier power!

---

### Modulation Index and Efficiency

**Modulation Index (for sinusoidal $m(t) = \mu\cos(\omega_m t)$):**

$$\mu = \frac{\max m(t) - \min m(t)}{2}$$

**For Standard AM:**
- $0 \leq \mu \leq 1$ (100% modulation when $\mu = 1$)
- $\mu > 1$ → Overmodulation (distortion!)

**Modulation Efficiency:**
$$\eta = \frac{P_{SB}}{P_s} = \frac{P_m}{1 + P_m}$$

**For Sinusoidal Modulation:**
$$P_m = \frac{\mu^2}{2}$$

$$P_s = \frac{1}{2}A_c^2\left[1 + \frac{\mu^2}{2}\right]$$

$$\eta = \frac{\mu^2/2}{1 + \mu^2/2} = \frac{\mu^2}{2 + \mu^2}$$

**Maximum Efficiency (at $\mu = 1$):**
$$\eta_{max} = \frac{1}{3} \approx 33.3\%$$

**Peak Envelope Power (Standard AM):**
$$P_{PEP} = \frac{1}{2}A_c^2[1 + \max m(t)]^2$$

---

### Detectors

#### Envelope Detector

**Ideal Operation:**
$$v_{out}(t) = K R(t) = K|g(t)|$$

**For Standard AM:**
$$v_{out}(t) = K A_c[1 + m(t)] = K A_c + K A_c m(t)$$

**RC Time Constant Requirements:**
$$\frac{1}{f_c} \ll RC \ll \frac{1}{B}$$

**Where:**
- $f_c$ = carrier frequency
- $B$ = modulating signal bandwidth

#### Product Detector

**Operation:**
$$v_1(t) = v_{in}(t) \times A_0\cos(\omega_c t + \theta_0)$$

**After Lowpass Filtering (synchronized, $\theta_0 = 0$):**
$$v_{out}(t) = \frac{1}{2}A_0 x(t) = \frac{1}{2}A_0\text{Re}\{g(t)\}$$

**For Standard AM:**
$$v_{out}(t) = \frac{1}{2}A_0 A_c[1 + m(t)]$$

**For DSB-SC:**
$$v_{out}(t) = \frac{1}{2}A_0 A_c m(t)$$

**With Phase Error ($\theta_0 \neq 0$):**
$$v_{out}(t) = \frac{1}{2}A_0 R(t)\cos[\theta(t) - \theta_0]$$

**For AM ($\theta(t) = 0$):**
$$v_{out}(t) = \frac{1}{2}A_0 R(t)\cos(\theta_0)$$

**Effect:** Output reduced by factor $\cos(\theta_0)$

---

## Group 3: Analog Modulation - Angle-based {#group-3}

### Phase Modulation (PM)

**Complex Envelope:**
$$g(t) = A_c e^{j\theta(t)}$$

**Phase Function:**
$$\theta(t) = D_p m(t)$$

**Where:**
- $D_p$ = phase sensitivity (radians per unit of $m(t)$)
- $m(t)$ = modulating signal

**Modulated Signal:**
$$s(t) = A_c\cos[\omega_c t + D_p m(t)]$$

**Real Envelope:**
$$R(t) = A_c$$ (constant!)

---

### Frequency Modulation (FM)

**Complex Envelope:**
$$g(t) = A_c e^{j\theta(t)}$$

**Phase Function:**
$$\theta(t) = D_f \int_0^t m(\tau) d\tau$$

**Where:**
- $D_f$ = frequency sensitivity (rad/s per unit of $m(t)$)
- $m(t)$ = modulating signal

**Modulated Signal:**
$$s(t) = A_c\cos\left[\omega_c t + D_f \int_0^t m(\tau) d\tau\right]$$

**Real Envelope:**
$$R(t) = A_c$$ (constant!)

---

### Instantaneous Frequency

**Definition:**
$$f_i(t) = \frac{1}{2\pi}\frac{d[\omega_c t + \theta(t)]}{dt} = f_c + \frac{1}{2\pi}\frac{d\theta(t)}{dt}$$

**For PM:**
$$f_i(t) = f_c + \frac{1}{2\pi}D_p \frac{dm(t)}{dt}$$

**For FM:**
$$f_i(t) = f_c + \frac{1}{2\pi}D_f m(t)$$

**Frequency Deviation:**
$$f_d(t) = f_i(t) - f_c = \frac{1}{2\pi}\frac{d\theta(t)}{dt}$$

**Peak Frequency Deviation:**
$$\Delta F = \max|f_d(t)|$$

**For FM:**
$$\Delta F = \frac{1}{2\pi}D_f \max|m(t)|$$

---

### Relationship Between PM and FM

**PM with message $m(t)$ is equivalent to FM with message $\frac{dm(t)}{dt}$**

**FM with message $m(t)$ is equivalent to PM with message $\int m(t) dt$**

**Key Insight:** PM and FM are mathematically related through differentiation/integration!

---

### Modulation Index

**For PM (sinusoidal modulation $m(t) = A_m\sin(\omega_m t)$):**

$$\beta = D_p A_m$$

**For FM (sinusoidal modulation $m(t) = A_m\cos(\omega_m t)$):**

$$\beta = \frac{D_f A_m}{\omega_m} = \frac{\Delta F}{f_m}$$

**Where:**
- $\Delta F = \frac{D_f A_m}{2\pi}$ = peak frequency deviation
- $f_m$ = modulating frequency

**Physical Meaning:** $\beta$ determines how many sidebands are significant in the spectrum.

---

### Spectrum (Sinusoidal Modulation)

**Complex Envelope:**
$$g(t) = A_c e^{j\beta\sin(\omega_m t)}$$

**Fourier Series Expansion:**
$$g(t) = A_c \sum_{n=-\infty}^{+\infty} J_n(\beta)e^{jn\omega_m t}$$

**Where:** $J_n(\beta)$ = $n$-th order Bessel function of the first kind

**Spectrum:**
$$G(f) = A_c \sum_{n=-\infty}^{+\infty} J_n(\beta)\delta(f - nf_m)$$

**Bandpass Spectrum:**
$$S(f) = \frac{A_c}{2}\sum_{n=-\infty}^{+\infty} J_n(\beta)[\delta(f - f_c - nf_m) + \delta(f + f_c - nf_m)]$$

**Bessel Function Properties:**
- $J_{-n}(\beta) = (-1)^n J_n(\beta)$ (symmetry)
- $\sum_{n=-\infty}^{+\infty} J_n^2(\beta) = 1$ (power conservation)
- $J_0(2.405) = 0$ (carrier null)

---

### Carson's Rule (Bandwidth)

**Approximate Bandwidth:**
$$B_T \approx 2(\Delta F + f_m) = 2(\beta + 1)f_m$$

**For FM:**
$$B_T \approx 2\left(\frac{D_f \max|m(t)|}{2\pi} + f_m\right)$$

**For PM:**
$$B_T \approx 2\left(\frac{D_p \max|\frac{dm(t)}{dt}|}{2\pi} + f_m\right)$$

**Two Cases:**
- **Narrowband ($\beta \ll 1$):** $B_T \approx 2f_m$ (similar to AM)
- **Wideband ($\beta \gg 1$):** $B_T \approx 2\Delta F$ (dominated by deviation)

---

### Power in Angle-Modulated Signals

**Average Power:**
$$P_s = \frac{1}{2}A_c^2$$

**Key Property:** Power is **constant** and independent of modulation!

**Power Distribution (Sinusoidal Modulation):**
$$P_s = \frac{A_c^2}{2}\sum_{n=-\infty}^{+\infty} J_n^2(\beta) = \frac{A_c^2}{2}$$

**Power in Carrier:**
$$P_c = \frac{A_c^2}{2}J_0^2(\beta)$$

**Power in $n$-th Sideband Pair:**
$$P_n = A_c^2 J_n^2(\beta)$$

**Peak Envelope Power:**
$$P_{PEP} = P_s = \frac{1}{2}A_c^2$$

**Note:** PEP equals average power for angle modulation (unlike AM)!

---

## Group 4: Digital & Pulse Modulation {#group-4}

### Sampling Theorem

**Nyquist-Shannon Sampling Theorem:**
$$f_s \geq 2B$$

**Where:**
- $f_s$ = sampling frequency
- $B$ = signal bandwidth

**Nyquist Rate:**
$$f_{Nyquist} = 2B$$

**Sampling Period:**
$$T_s = \frac{1}{f_s}$$

**Sampled Signal:**
$$x_s(t) = x(t) \cdot \sum_{n=-\infty}^{+\infty} \delta(t - nT_s)$$

**Spectrum of Sampled Signal:**
$$X_s(f) = f_s \sum_{k=-\infty}^{+\infty} X(f - kf_s)$$

**Aliasing Condition:**
If $f_s < 2B$, aliasing occurs (high frequencies fold back into lower frequencies).

---

### Pulse Amplitude Modulation (PAM)

**PAM Signal:**
$$s_{PAM}(t) = \sum_{n=-\infty}^{+\infty} m(nT_s) p(t - nT_s)$$

**Where:**
- $m(nT_s)$ = sample values
- $p(t)$ = pulse shape (usually rectangular)

**Rectangular Pulse:**

$$p(t) = \begin{cases}
1, & 0 \leq t < \tau \\
0, & \text{otherwise}
\end{cases}$$

**Duty Cycle:**

$$\text{Duty Cycle} = \frac{\tau}{T_s}$$

---

### Delta Modulation (DM)

**Encoder:**

$$d(n) = \begin{cases}
+1, & \text{if } x(n) > \hat{x}(n) \\
-1, & \text{if } x(n) < \hat{x}(n)
\end{cases}$$

**Prediction Update:**
$$\hat{x}(n+1) = \hat{x}(n) + \Delta \cdot d(n)$$

**Where:**
- $\Delta$ = step size
- $d(n)$ = 1-bit output (+1 or -1)

**Decoder (Same as Encoder):**
$$\hat{x}(n+1) = \hat{x}(n) + \Delta \cdot d(n)$$

**Slope Overload Condition:**
$$\left|\frac{dx(t)}{dt}\right| > \frac{\Delta}{T_s}$$

**Maximum Tracking Rate:**
$$\frac{\Delta}{T_s} = \Delta f_s$$

**To Avoid Slope Overload:**
$$\Delta f_s \geq \max\left|\frac{dx(t)}{dt}\right|$$

---

### Quantization

**Quantization Levels:**
$$q_k = k \cdot \Delta, \quad k = -N/2, \ldots, -1, 0, 1, \ldots, N/2-1$$

**Where:**
- $\Delta$ = quantization step size
- $N$ = number of quantization levels

**Step Size (for $b$ bits):**
$$\Delta = \frac{V_{pp}}{2^b} = \frac{V_{pp}}{N}$$

**Where:**
- $V_{pp}$ = peak-to-peak signal range
- $b$ = number of bits
- $N = 2^b$ = number of levels

**Quantization Error:**
$$e(n) = x(n) - Q[x(n)]$$

**Error Bound:**
$$|e(n)| \leq \frac{\Delta}{2}$$

---

### Quantization Noise

**Quantization Noise Power:**
$$N_q = \frac{\Delta^2}{12}$$

**Derivation:** Error is uniformly distributed in $[-\Delta/2, \Delta/2]$, variance = $\Delta^2/12$

**Signal-to-Quantization-Noise Ratio (SQNR):**
$$\text{SQNR} = \frac{S}{N_q} = \frac{S}{\Delta^2/12} = \frac{12S}{\Delta^2}$$

**In Decibels:**
$$\text{SQNR (dB)} = 10\log_{10}\left(\frac{12S}{\Delta^2}\right)$$

**For Sinusoidal Signal (amplitude $A$):**
- Signal power: $S = \frac{A^2}{2}$
- Peak-to-peak: $V_{pp} = 2A$
- Step size: $\Delta = \frac{2A}{2^b}$

**SQNR Formula:**
$$\text{SQNR (dB)} = 10\log_{10}\left(\frac{12 \cdot A^2/2}{(2A/2^b)^2}\right)$$

**Simplified:**
$$\text{SQNR (dB)} \approx 6.02b + 1.76 \text{ dB}$$

**Rule of Thumb:** Each additional bit adds **6 dB** to SQNR!

---

## Group 5: Multiplexing (TDM) {#group-5}

### Frame Structure

**Frame Period:**
$$T_f = \frac{1}{f_s}$$

**Where:**
- $f_s$ = sampling rate per signal

**Slot Duration (without sync word):**
$$T_s = \frac{T_f}{K} = \frac{1}{K f_s}$$

**Where:**
- $K$ = number of signals

**Slot Duration (with sync word):**
$$T_s = \frac{T_f - T_{sync}}{K}$$

**Where:**
- $T_{sync}$ = duration of synchronization word

---

### Sampling and Bandwidth

**Sampling Requirement (per signal):**
$$f_s \geq 2B$$

**Where:**
- $B$ = bandwidth of each signal

**Total TDM Sampling Rate:**
$$f_{TDM} = K f_s$$

**TDM Bandwidth:**
$$B_{TDM} = K \times 2B = K f_s$$

**Key Insight:** TDM uses time to separate signals, all share the same frequency band!

---

### Commutator Operation

**Commutator Frequency:**
$$f_{commutator} = f_s$$

**Time per Frame:**
$$T_f = \frac{1}{f_s}$$

**Time per Slot:**
$$T_s = \frac{T_f}{K}$$

**Slot for Signal $k$ (Frame $n$):**
- Starts at: $t = (k-1)T_s + nT_f$
- Duration: $T_s$

---

### Synchronization

**Coincident Detector (K-input AND gate):**

**Sync Word:** $s = (s_1, s_2, \ldots, s_K)$

**Received Signal:** $r = (r_1, r_2, \ldots, r_K)$

**Detection Logic:**
$$\text{Output} = \prod_{i=1}^{K} [1 - (r_i \oplus s_i)]$$

**Where:** $\oplus$ is XOR (0 if equal, 1 if different)

**Output = 1** when all bits match (sync detected)  
**Output = 0** when any bit mismatches (no sync)

---

### Comparison: TDM vs FDM

**TDM Bandwidth:**
$$B_{TDM} = K \times 2B$$

**FDM Bandwidth:**
$$B_{FDM} = K \times 2B + \text{guard bands}$$

**Key Difference:** TDM has no guard bands, making it more bandwidth efficient!

---

## Group 6: Frequency Translation & Receiver Design {#group-6}

### Mixer Operation

**Input Signal:**
$$v_{in}(t) = R(t)\cos[\omega_c t + \theta(t)]$$

**Local Oscillator:**
$$v_{LO}(t) = A_0\cos(\omega_0 t)$$

**Mixer Output:**
$$v_1(t) = v_{in}(t) \times v_{LO}(t)$$

**Result:**
$$v_1(t) = \frac{A_0 R(t)}{2}\cos[(\omega_c + \omega_0)t + \theta(t)] + \frac{A_0 R(t)}{2}\cos[(\omega_c - \omega_0)t + \theta(t)]$$

**Two Output Frequencies:**
- **Upper sideband:** $f_c + f_0$ (up-conversion)
- **Lower sideband:** $f_c - f_0$ (down-conversion)

**Filter Selection:**
- **Up-conversion:** Select $f_c + f_0$ with bandpass filter
- **Down-conversion:** Select $f_c - f_0$ with bandpass filter

---

### Complex Envelope in Frequency Translation

**Input Complex Envelope:**
$$v_{in}(t) = \text{Re}\{g_{in}(t)e^{j\omega_c t}\}$$

**Mixer Output (Complex Form):**
$$v_1(t) = \frac{A_0}{2}\text{Re}\{g_{in}(t)e^{j(\omega_c + \omega_0)t}\} + \frac{A_0}{2}\text{Re}\{g_{in}(t)e^{j(\omega_c - \omega_0)t}\}$$

**Output Complex Envelope:**
$$g_2(t) = \frac{A_0}{2}g_{in}(t)$$

**Key Result:** Complex envelope is **preserved** (scaled by $\frac{A_0}{2}$), only carrier frequency changes!

---

### Nonlinear Devices

**Nonlinear Relationship:**
$$v_{out}(t) = K_n v_{in}^n(t)$$

**For $n$-th Order Nonlinearity:**
$$v_{out}(t) = C R^n(t)\cos[n\omega_c t + n\theta(t)]$$

**Key Points:**
- Output appears at **$n$-th harmonic**: $nf_c$
- Envelope becomes: $R^n(t)$
- Phase becomes: $n\theta(t)$

**Harmonics Produced:**
- $n = 2$ → $2f_c$ (second harmonic)
- $n = 3$ → $3f_c$ (third harmonic)
- And so on...

**Solution:** Use bandpass filter to select desired frequency, reject harmonics.

---

### Superheterodyne Receiver

**LO Frequency (High-Side Injection):**
$$f_{LO} = f_c + f_{IF}$$

**LO Frequency (Low-Side Injection):**
$$f_{LO} = f_c - f_{IF}$$

**IF Frequency:**
$$f_{IF} = |f_c - f_{LO}|$$

**Common IF Frequencies:**
- AM Broadcast: $f_{IF} = 455$ kHz
- FM Broadcast: $f_{IF} = 10.7$ MHz
- TV: $f_{IF} = 45.75$ MHz

---

### Image Frequency

**Image Frequency (High-Side Injection):**
$$f_{image} = f_c + 2f_{IF}$$

**Image Frequency (Low-Side Injection):**
$$f_{image} = f_c - 2f_{IF}$$

**Image Separation:**
$$\Delta f = f_{image} - f_c = 2f_{IF}$$

**Why It's a Problem:**
- Desired signal: $f_c - f_{LO} = f_{IF}$ ✓
- Image signal: $f_{image} - f_{LO} = f_{IF}$ ✓
- **Both produce IF!** Image causes interference.

**Solution:** RF bandpass filter must reject image frequency.

---

### Image Rejection

**Image Rejection Ratio:**
$$\text{Image Rejection (dB)} = 10\log_{10}\left(\frac{\text{Power at } f_c}{\text{Power at } f_{image}}\right)$$

**Factors:**
- **IF frequency:** Higher $f_{IF}$ → better rejection (easier filtering)
- **Filter quality:** Better filter → better rejection
- **Separation:** $\Delta f = 2f_{IF}$

**Trade-off:**
- Higher $f_{IF}$: Better image rejection, but harder to build IF filters
- Lower $f_{IF}$: Easier IF filters, but poor image rejection

**Standard IF frequencies are chosen as a compromise!**

---

## Quick Reference Summary

### Power Formulas

| Modulation Type | Power Formula |
|----------------|---------------|
| **General Bandpass** |  $P_v = \frac{1}{2}\langle |g(t)|^2 \rangle$  |
| **Standard AM** | $P_s = \frac{1}{2}A_c^2[1 + P_m]$ |
| **DSB-SC/SSB** | $P_s = \frac{1}{2}A_c^2 P_m$ |
| **FM/PM** | $P_s = \frac{1}{2}A_c^2$ (constant!) |
| **PEP (AM)** | $P_{PEP} = \frac{1}{2}[\max|g(t)|]^2$ |
| **PEP (FM/PM)** | $P_{PEP} = P_s = \frac{1}{2}A_c^2$ |

### Bandwidth Formulas

| Modulation Type | Bandwidth |
|----------------|-----------|
| **Standard AM** | $B_T = 2B$ |
| **DSB-SC** | $B_T = 2B$ |
| **SSB-AM** | $B_T = B$ |
| **FM/PM (Carson's)** | $B_T \approx 2(\Delta F + f_m) = 2(\beta + 1)f_m$ |
| **TDM** | $B_{TDM} = K \times 2B$ |

### Key Constants and Relationships

**Angular Frequency:**
$$\omega = 2\pi f$$

**Modulation Index (AM):**

$$\mu = \frac{\max m(t) - \min m(t)}{2}, \quad 0 \leq \mu \leq 1$$

**Modulation Index (FM):**

$$\beta = \frac{D_f A_m}{\omega_m} = \frac{\Delta F}{f_m}$$

**Modulation Index (PM):**

$$\beta = D_p A_m$$

**SQNR (Quantization):**
$$\text{SQNR (dB)} \approx 6.02b + 1.76 \text{ dB}$$

**Sampling Rate:**
$$f_s \geq 2B \text{ (Nyquist)}$$

---

## Important Notes

1. **Always check units:** Frequency in Hz, angular frequency in rad/s
2. **Power formulas:** Remember the $\frac{1}{2}$ factor for bandpass signals
3. **Spectrum formulas:** Remember the $\frac{1}{2}$ or $\frac{1}{4}$ factors
4. **Modulation index:** Different formulas for AM, FM, and PM
5. **Image frequency:** Always consider both high-side and low-side injection
6. **Quantization:** Step size depends on number of bits and signal range
7. **TDM:** Bandwidth is sum of individual signal bandwidths (no guard bands)

---

*End of Equations Reference*

**Last Updated:** Based on Groups 1-6 Detailed Explanations


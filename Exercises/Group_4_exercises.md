# Group 4 Exercises - Digital & Pulse Modulation


This document contains exercises and problems covering pulse modulation techniques from Lecture 12.


---


## Exercise Set 1: Sampling Theorem


### Problem 1.1 (Basic)

An analog signal has a bandwidth of $B = 4$ kHz.


Find:

a) The minimum sampling rate (Nyquist rate) required

b) The sampling period $T_s$ at the Nyquist rate

c) The sampling period if we use $f_s = 10$ kHz (oversampling)


---


### Problem 1.2 (Intermediate)

A signal $x(t)$ has spectrum:

$$X(f) = \begin{cases}

A, & |f| \leq 3 \text{ kHz} \\

0, & |f| > 3 \text{ kHz}

\end{cases}$$


Find:

a) The bandwidth $B$

b) The minimum sampling rate $f_s$ to avoid aliasing

c) What happens if we sample at $f_s = 4$ kHz?

d) What happens if we sample at $f_s = 8$ kHz?


---


### Problem 1.3 (Advanced)

A signal is sampled at $f_s = 8$ kHz. The signal has components at:

- $f_1 = 2$ kHz

- $f_2 = 3$ kHz

- $f_3 = 5$ kHz


Find:

a) Which frequencies appear in the sampled signal spectrum?

b) What is the aliased frequency if $f_3 = 7$ kHz instead?

c) What is the aliased frequency if $f_3 = 9$ kHz instead?


---


## Exercise Set 2: Pulse Amplitude Modulation (PAM)


### Problem 2.1 (Basic)

A PAM signal is generated from:

- Analog signal: $m(t) = 3\cos(2\pi \cdot 2000t)$

- Sampling rate: $f_s = 8000$ Hz

- Pulse width: $\tau = 50$ $\mu$s


Find:

a) The sampling period $T_s$

b) The number of samples per period of $m(t)$

c) The duty cycle $\tau/T_s$

d) Write the mathematical expression for the PAM signal


---


### Problem 2.2 (Intermediate)

A PAM system samples a signal $m(t)$ with bandwidth $B = 5$ kHz.


Given:

- Sampling rate: $f_s = 15$ kHz

- Pulse width: $\tau = 0.05$ ms

- Pulse amplitude range: $-5$ V to $+5$ V


Find:

a) Is the sampling rate adequate? (Check Nyquist)

b) The sampling period $T_s$

c) The duty cycle

d) The approximate bandwidth of the PAM signal

e) The cutoff frequency needed for the reconstruction filter


---


### Problem 2.3 (Advanced)

A PAM signal is given by:

$$s_{PAM}(t) = \sum_{n=-\infty}^{+\infty} m(nT_s) p(t - nT_s)$$


where $p(t)$ is a rectangular pulse of width $\tau$ and amplitude 1.


Show that:

a) The spectrum contains the original signal spectrum (scaled) at baseband

b) The spectrum also contains replicas at multiples of $f_s$

c) A lowpass filter with cutoff $B$ can recover the original signal if $f_s \geq 2B$


---


## Exercise Set 3: Pulse Width Modulation (PWM)


### Problem 3.1 (Basic)

A PWM signal has:

- Constant pulse amplitude: $A = 10$ V

- Pulse repetition period: $T_s = 0.1$ ms

- Pulse width varies from $\tau_{min} = 0.01$ ms to $\tau_{max} = 0.09$ ms


Find:

a) The sampling rate $f_s$

b) The minimum duty cycle

c) The maximum duty cycle

d) The relationship between pulse width and modulating signal amplitude


---


### Problem 3.2 (Intermediate)

A PWM system modulates a signal $m(t)$ where:

- $m(t)$ ranges from $-2$ V to $+2$ V

- Pulse period: $T_s = 0.2$ ms

- Pulse width: $\tau(t) = 0.05 + 0.05 \cdot \frac{m(t)}{2}$ ms


Find:

a) The sampling rate $f_s$

b) The minimum pulse width $\tau_{min}$

c) The maximum pulse width $\tau_{max}$

d) The pulse width when $m(t) = 0$ V

e) The pulse width when $m(t) = +2$ V


---


### Problem 3.3 (Advanced)

Show that a PWM signal can be converted to PAM by:

a) Using a lowpass filter to extract the average value

b) The average value over one period equals the sample value

c) Derive the relationship between PWM pulse width and the recovered PAM sample


---


## Exercise Set 4: Pulse Position Modulation (PPM)


### Problem 4.1 (Basic)

A PPM signal has:

- Fixed pulse amplitude: $A = 5$ V

- Fixed pulse width: $\tau = 0.02$ ms

- Pulse period: $T_s = 0.1$ ms

- Pulse position varies from $t_0 = 0.01$ ms to $t_0 = 0.08$ ms


Find:

a) The sampling rate $f_s$

b) The range of pulse positions

c) The relationship between pulse position and modulating signal


---


### Problem 4.2 (Intermediate)

A PPM system has:

- Clock period: $T_s = 0.05$ ms

- Pulse width: $\tau = 0.005$ ms

- Position range: $0.01$ ms to $0.04$ ms (relative to clock edge)


Find:

a) The sampling rate $f_s$

b) The minimum time delay from clock edge

c) The maximum time delay from clock edge

d) The total range of position variation

e) The relationship: $t_{position} = t_0 + k \cdot m(t)$ where $k$ is a constant


---


### Problem 4.3 (Advanced)

Compare PPM with PWM:

a) Which is more resistant to amplitude noise? Why?

b) Which requires more bandwidth? Why?

c) Which is easier to generate? Why?

d) Which is easier to demodulate? Why?


---


## Exercise Set 5: Delta Modulation (DM)


### Problem 5.1 (Basic)

A delta modulator has:

- Step size: $\Delta = 0.1$ V

- Sampling rate: $f_s = 10$ kHz

- Input signal: $x(t) = 2\sin(2\pi \cdot 1000t)$


Find:

a) The sampling period $T_s$

b) The maximum tracking rate: $\Delta/T_s$

c) The maximum slope of the input signal

d) Will slope overload occur?


---


### Problem 5.2 (Intermediate)

A DM system encodes signal $x(t) = 5\cos(2\pi \cdot 2000t)$.


Given:

- Step size: $\Delta = 0.2$ V

- Sampling rate: $f_s = 20$ kHz


Find:

a) The maximum signal slope

b) The maximum tracking rate

c) Check for slope overload

d) If slope overload occurs, what should be changed?

e) The bit rate of the DM signal


---


### Problem 5.3 (Advanced)

For a delta modulator:

a) Derive the condition for slope overload: $\left|\frac{dx(t)}{dt}\right| > \frac{\Delta}{T_s}$

b) Show that for sinusoidal signal $x(t) = A\sin(\omega t)$, slope overload occurs if: $A\omega > \frac{\Delta}{T_s}$

c) Find the minimum step size to avoid slope overload for $x(t) = 3\sin(2\pi \cdot 5000t)$ with $f_s = 50$ kHz


---


## Exercise Set 6: Quantization


### Problem 6.1 (Basic)

A signal is quantized using 8 bits over a range of $-10$ V to $+10$ V.


Find:

a) The number of quantization levels $L$

b) The quantization step size $\Delta$

c) The quantization noise power $N_q$

d) The maximum quantization error


---


### Problem 6.2 (Intermediate)

A quantizer uses $b = 12$ bits to quantize a signal with peak-to-peak voltage $V_{pp} = 8$ V.


Find:

a) The number of levels $L = 2^b$

b) The step size $\Delta = V_{pp}/L$

c) The quantization noise power $N_q = \Delta^2/12$

d) The signal-to-quantization-noise ratio (SQNR) in dB for a sinusoidal signal

e) How much does SQNR improve if we increase to 16 bits?


---


### Problem 6.3 (Advanced)

Show that:

a) The quantization noise power is $N_q = \frac{\Delta^2}{12}$ assuming uniform distribution

b) For a sinusoidal signal with amplitude $A$, the signal power is $S = \frac{A^2}{2}$

c) The SQNR in dB is approximately: $\text{SQNR} \approx 6.02b + 1.76$ dB

d) Each additional bit improves SQNR by approximately 6 dB


---


## Exercise Set 7: Signal-to-Quantization-Noise Ratio (SQNR)


### Problem 7.1 (Basic)

A sinusoidal signal $x(t) = 4\sin(2\pi \cdot 1000t)$ is quantized using 10 bits over the range $-5$ V to $+5$ V.


Find:

a) The step size $\Delta$

b) The signal power $S$

c) The quantization noise power $N_q$

d) The SQNR in linear scale

e) The SQNR in dB


---


### Problem 7.2 (Intermediate)

A quantizer is designed for a signal with:

- Peak amplitude: $A = 6$ V

- Number of bits: $b = 14$

- Quantization range: $\pm A$ (i.e., $-6$ V to $+6$ V)


Find:

a) The step size $\Delta$

b) The signal power (assuming sinusoidal)

c) The noise power $N_q$

d) The SQNR in dB

e) What SQNR would we get with 8 bits? 16 bits?


---


### Problem 7.3 (Advanced)

For a quantized signal:

a) Derive the SQNR formula: $\text{SQNR} = \frac{S}{N_q} = \frac{3A^2}{2\Delta^2}$ for sinusoidal signal

b) Show that $\text{SQNR (dB)} = 6.02b + 1.76$ when $V_{pp} = 2A$

c) If we want SQNR = 60 dB, how many bits are needed?

d) If we want SQNR = 80 dB, how many bits are needed?


---


## Exercise Set 8: Comparison of Pulse Modulation Schemes


### Problem 8.1 (Basic)

Compare PAM, PWM, and PPM:


a) Which scheme varies the pulse amplitude?

b) Which scheme varies the pulse width?

c) Which scheme varies the pulse position?

d) Which is most sensitive to amplitude noise?

e) Which is least sensitive to amplitude noise?


---


### Problem 8.2 (Intermediate)

For a given analog signal $m(t)$ with bandwidth $B = 4$ kHz:


Compare PAM, PWM, and PPM in terms of:

a) Bandwidth requirements

b) Noise resistance

c) Implementation complexity

d) Power efficiency

e) Demodulation method


---


### Problem 8.3 (Advanced)

Analyze the trade-offs:


a) Why is PAM simpler but more noise-sensitive?

b) Why does PWM require constant amplitude amplifiers?

c) Why is PPM more complex but more noise-resistant?

d) When would you choose each modulation scheme?


---


## Exercise Set 9: Numerical Problems


### Problem 9.1

A voice signal with bandwidth $B = 3.4$ kHz is to be transmitted using PAM.


Given:

- Sampling rate: $f_s = 8$ kHz

- Pulse width: $\tau = 10$ $\mu$s

- Signal amplitude range: $-2$ V to $+2$ V


Find:

a) Is the sampling rate adequate?

b) The sampling period $T_s$

c) The duty cycle

d) The bandwidth of the PAM signal

e) The reconstruction filter cutoff frequency


---


### Problem 9.2

A delta modulator processes signal $x(t) = 3\cos(2\pi \cdot 3000t)$.


Given:

- Step size: $\Delta = 0.15$ V

- Sampling rate: $f_s = 30$ kHz


Find:

a) The maximum signal slope

b) The maximum tracking rate

c) Will slope overload occur?

d) If yes, what step size is needed to avoid it?

e) The bit rate


---


### Problem 9.3

A signal is quantized for digital transmission:


Given:

- Signal: $x(t) = 5\sin(2\pi \cdot 2000t)$

- Quantization: 12 bits

- Range: $-6$ V to $+6$ V


Find:

a) The step size $\Delta$

b) The signal power $S$

c) The quantization noise power $N_q$

d) The SQNR in dB

e) The data rate if sampled at $f_s = 8$ kHz


---


## Exercise Set 10: Conceptual Questions


### Problem 10.1

Explain the following concepts:


a) What is aliasing and how does it occur?

b) Why is the Nyquist rate $f_s = 2B$ the minimum sampling rate?

c) What is the purpose of an anti-aliasing filter?

d) What happens if we sample below the Nyquist rate?


---


### Problem 10.2

Answer the following:


a) Why does PAM require linear amplification?

b) Why is PWM more power-efficient than PAM?

c) Why is PPM more resistant to noise than PAM?

d) What is the main disadvantage of delta modulation?


---


### Problem 10.3

Discuss:


a) What is slope overload in delta modulation?

b) What is granular noise in delta modulation?

c) What is the trade-off between slope overload and granular noise?

d) How does adaptive delta modulation solve this trade-off?


---


## Exercise Set 11: Derivation Problems


### Problem 11.1

Derive the Nyquist-Shannon sampling theorem:


a) Start with a bandlimited signal $x(t)$ with spectrum $X(f) = 0$ for $|f| > B$

b) Show that sampling at $f_s$ creates replicas of the spectrum at multiples of $f_s$

c) Show that if $f_s < 2B$, the replicas overlap (aliasing)

d) Show that if $f_s \geq 2B$, the original signal can be recovered by lowpass filtering


---


### Problem 11.2

Derive the quantization noise power:


a) Assume uniform quantization with step size $\Delta$

b) Show that the quantization error $e$ is uniformly distributed in $[-\Delta/2, +\Delta/2]$

c) Find the mean of the error: $E[e] = 0$

d) Find the variance (power): $E[e^2] = \Delta^2/12$


---


### Problem 11.3

Derive the SQNR formula for a sinusoidal signal:


a) For signal $x(t) = A\sin(\omega t)$, show that signal power is $S = A^2/2$

b) For quantization with $b$ bits and range $[-A, +A]$, show that $\Delta = 2A/2^b$

c) Show that noise power is $N_q = \Delta^2/12 = A^2/(3 \cdot 2^{2b})$

d) Show that $\text{SQNR} = \frac{S}{N_q} = \frac{3 \cdot 2^{2b}}{2}$

e) Convert to dB: $\text{SQNR (dB)} = 10\log_{10}(3 \cdot 2^{2b}/2) \approx 6.02b + 1.76$


---


## Exercise Set 12: Combined Problems


### Problem 12.1

A complete PAM system:


Given:

- Analog signal: $m(t) = 4\cos(2\pi \cdot 3000t)$

- Sampling rate: $f_s = 10$ kHz

- Quantization: 8 bits, range $[-5, +5]$ V

- Pulse width: $\tau = 0.02$ ms


Find:

a) Check if sampling rate is adequate

b) The PAM signal parameters

c) The quantized PAM signal (step size, levels)

d) The SQNR in dB

e) The bandwidth required

f) The bit rate


---


### Problem 12.2

A delta modulation system:


Given:

- Input: $x(t) = 2\sin(2\pi \cdot 4000t)$

- Sampling rate: $f_s = 40$ kHz

- Step size: $\Delta = 0.1$ V


Find:

a) Check for slope overload

b) The bit rate

c) Compare with a quantized PAM system using 4 bits

d) Which system has higher bit rate?

e) Which system is simpler to implement?


---


### Problem 12.3

Design a quantization system:


Requirements:

- Signal: $x(t) = 6\cos(2\pi \cdot 2000t)$

- Required SQNR: $\geq 50$ dB

- Sampling rate: $f_s = 8$ kHz


Find:

a) Minimum number of bits needed

b) The step size $\Delta$

c) The quantization noise power

d) The actual SQNR achieved

e) The data rate


---


*Good luck with your exam preparation!*



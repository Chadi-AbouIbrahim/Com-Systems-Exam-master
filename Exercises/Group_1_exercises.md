# Group 1 Exercises - Foundations of Modulation


This document contains exercises and problems covering the fundamental concepts of modulation, complex envelope representation, and bandpass signals from Lecture 13.


---


## Exercise Set 1: Complex Envelope Representation


### Problem 1.1 (Basic)

Given a bandpass signal:

$$v(t) = 5\cos(2\pi \cdot 10^6 t + \pi/4)$$


Find:

a) The carrier frequency $f_c$

b) The real envelope $R(t)$

c) The phase $\theta(t)$

d) Express $v(t)$ in the form $v(t) = \text{Re}\{g(t)e^{j\omega_c t}\}$


**Solution Guide:**

- Compare with the general form: $v(t) = R(t)\cos[\omega_c t + \theta(t)]$

- Identify $R(t)$, $\omega_c$, and $\theta(t)$

- Construct the complex envelope $g(t) = R(t)e^{j\theta(t)}$


---


### Problem 1.2 (Intermediate)

A bandpass signal is given by:

$$v(t) = 3\cos(2\pi \cdot 1000t) - 4\sin(2\pi \cdot 1000t)$$


where the carrier frequency is $f_c = 1000$ Hz.


Find:

a) The in-phase component $x(t)$

b) The quadrature component $y(t)$

c) The complex envelope $g(t)$

d) The real envelope $R(t)$

e) The phase $\theta(t)$


**Solution Guide:**

- Use the quadrature form: $v(t) = x(t)\cos(\omega_c t) - y(t)\sin(\omega_c t)$

- Compare coefficients with the given expression

- Calculate $g(t) = x(t) + jy(t)$

- Find $R(t) = |g(t)|$ and $\theta(t) = \arg[g(t)]$


---


### Problem 1.3 (Advanced)

Given a complex envelope:

$$g(t) = 2e^{j\pi t/4} + 3e^{-j\pi t/2}$$


and carrier frequency $f_c = 500$ Hz, determine:

a) The bandpass signal $v(t)$

b) Express $v(t)$ in the form $R(t)\cos[\omega_c t + \theta(t)]$

c) Find the in-phase and quadrature components


---


## Exercise Set 2: Power Calculations


### Problem 2.1 (Basic)

A bandpass signal has a complex envelope:

$$g(t) = 4[1 + 0.5\cos(2\pi \cdot 100t)]$$


where $A_c = 4$ and the modulating signal is $m(t) = 0.5\cos(2\pi \cdot 100t)$.


Calculate:

a) The average power of the modulating signal $P_m = \langle m^2(t) \rangle$

b) The average power of the bandpass signal $P_s$

c) Verify that $P_s = \frac{1}{2}\langle |g(t)|^2 \rangle$


**Solution Guide:**

- For a cosine: $\langle \cos^2(\omega t) \rangle = \frac{1}{2}$

- Use: $P_s = \frac{1}{2}A_c^2[1 + P_m]$

- Calculate $\langle |g(t)|^2 \rangle$ directly


---


### Problem 2.2 (Intermediate)

Given a bandpass signal with complex envelope:

$$g(t) = 5e^{j\theta(t)}$$


where $\theta(t) = 0.1\sin(2\pi \cdot 200t)$.


Find:

a) The real envelope $R(t)$

b) The average power $P_v = \langle v^2(t) \rangle$

c) Express the power in terms of $A_c$ only


---


### Problem 2.3 (Advanced)

Prove that for any bandpass signal $v(t)$ with complex envelope $g(t)$:

$$P_v = \langle v^2(t) \rangle = \int_{-\infty}^{+\infty} P_v(f) df = R_v(0) = \frac{1}{2}\langle |g(t)|^2 \rangle$$


**Hint:** Start from $v(t) = \text{Re}\{g(t)e^{j\omega_c t}\}$ and use the relationship between autocorrelation functions.


---


## Exercise Set 3: Frequency Domain Analysis


### Problem 3.1 (Basic)

A baseband signal has a complex envelope with Fourier transform:


$$G(f) = \begin{cases}

2A_c, & |f| \leq B \\

0, & |f| > B

\end{cases}$$


where $B = 5$ kHz and $A_c = 3$ V.


Find:

a) The Fourier transform of the bandpass signal $V(f)$

b) The bandwidth of the bandpass signal

c) Sketch $|V(f)|$ vs $f$


**Solution Guide:**

- Use: $V(f) = \frac{1}{2}[G(f - f_c) + G^*(-f - f_c)]$

- For real $g(t)$, $G^*(-f) = G(f)$

- The bandwidth is $2B$


---


### Problem 3.2 (Intermediate)

Given a modulating signal with spectrum:


$$M(f) = \begin{cases}

1, & |f| \leq 10 \text{ kHz} \\

0, & |f| > 10 \text{ kHz}

\end{cases}$$


and complex envelope $g(t) = A_c[1 + m(t)]$ where $A_c = 5$ V.


Determine:

a) The spectrum of the complex envelope $G(f)$

b) The spectrum of the bandpass signal $S(f)$

c) Identify the carrier and sideband components

d) The total bandwidth


---


### Problem 3.3 (Advanced)

Show that the power spectral density of a bandpass signal is related to the power spectral density of its complex envelope by:

$$P_v(f) = \frac{1}{4}[P_g(f - f_c) + P_g^*(-f - f_c)]$$


**Hint:** Use the autocorrelation relationship: $R_v(\tau) = \frac{1}{2}\text{Re}\{R_g(\tau)e^{j\omega_c \tau}\}$


---


## Exercise Set 4: Quadrature Components


### Problem 4.1 (Basic)

Express the following bandpass signal in quadrature form:

$$v(t) = 6\cos(2\pi \cdot 2000t + \pi/6)$$


Find $x(t)$ and $y(t)$ such that:

$$v(t) = x(t)\cos(\omega_c t) - y(t)\sin(\omega_c t)$$


---


### Problem 4.2 (Intermediate)

Given:

$$x(t) = 3\cos(2\pi \cdot 50t)$$

$$y(t) = 4\sin(2\pi \cdot 50t)$$

$$f_c = 1 \text{ MHz}$$


Find:

a) The complex envelope $g(t)$

b) The bandpass signal $v(t)$

c) The real envelope $R(t)$

d) The phase $\theta(t)$


---


### Problem 4.3 (Advanced)

A bandpass signal is given by:

$$v(t) = [2 + \cos(2\pi \cdot 100t)]\cos(2\pi \cdot 10^6 t) - [1 + 0.5\sin(2\pi \cdot 100t)]\sin(2\pi \cdot 10^6 t)$$


Determine:

a) The complex envelope $g(t)$

b) The modulating signal $m(t)$ if this represents an AM signal

c) The average power of the signal


---


## Exercise Set 5: General Applications


### Problem 5.1 (Intermediate)

A communication system transmits a bandpass signal with:

- Carrier frequency: $f_c = 1$ MHz

- Complex envelope: $g(t) = 4[1 + 0.8m(t)]$

- Modulating signal: $m(t) = \cos(2\pi \cdot 5 \times 10^3 t)$


Find:

a) The time-domain expression for $s(t)$

b) The frequency-domain expression $S(f)$

c) The bandwidth required for transmission

d) The average transmitted power


---


### Problem 5.2 (Advanced)

For a bandpass signal with complex envelope:

$$g(t) = A_c[1 + m_1(t) + jm_2(t)]$$


where $m_1(t)$ and $m_2(t)$ are real modulating signals, show that:

a) The in-phase component is $x(t) = A_c[1 + m_1(t)]$

b) The quadrature component is $y(t) = A_c m_2(t)$

c) The real envelope is $R(t) = A_c\sqrt{[1 + m_1(t)]^2 + m_2^2(t)}$

d) The phase is $\theta(t) = \tan^{-1}\left[\frac{m_2(t)}{1 + m_1(t)}\right]$


---


### Problem 5.3 (Challenge)

Prove that any real bandpass signal $v(t)$ centered at frequency $f_c$ can be uniquely represented as:

$$v(t) = \text{Re}\{g(t)e^{j\omega_c t}\}$$


where $g(t)$ is a complex baseband signal (the complex envelope), and show that this representation is unique up to the choice of $f_c$.


**Hint:** Consider the analytic signal and its relationship to the complex envelope.


---


## Exercise Set 6: Numerical Problems


### Problem 6.1 (Basic Calculation)

Given:

- $v(t) = 10\cos(2\pi \cdot 500 \times 10^3 t + 0.5)$

- Find $R(t)$, $\theta(t)$, and express as $v(t) = \text{Re}\{g(t)e^{j\omega_c t}\}$


---


### Problem 6.2 (Power Calculation)

A bandpass signal has:

- Complex envelope: $g(t) = 6[1 + 0.6\cos(2\pi \cdot 1 \times 10^3 t)]$

- Calculate the average power $P_s$ in watts if the signal is measured across a 1Ω resistor


---


### Problem 6.3 (Bandwidth Calculation)

A modulating signal has bandwidth $B = 8$ kHz. If this signal is used to create a bandpass signal:

a) What is the minimum bandwidth required for the bandpass signal?

b) If the carrier frequency is $f_c = 100$ MHz, what frequency range does the bandpass signal occupy?


---


## Exercise Set 7: Conceptual Questions


### Question 7.1

Explain the difference between:

- A bandpass signal and its complex envelope

- The real envelope $R(t)$ and the complex envelope $g(t)$

- In-phase and quadrature components


---


### Question 7.2

Why is the complex envelope representation useful in communication systems? Discuss advantages in terms of:

- Signal processing

- Bandwidth efficiency

- Mathematical analysis


---


### Question 7.3

Given that $v(t) = \text{Re}\{g(t)e^{j\omega_c t}\}$, explain:

a) Why $g(t)$ is called the "complex envelope"

b) Why it is a baseband signal

c) How the carrier frequency $f_c$ is chosen


---


## Exercise Set 8: Derivation Problems


### Problem 8.1

Starting from $v(t) = R(t)\cos[\omega_c t + \theta(t)]$, derive the quadrature form:

$$v(t) = x(t)\cos(\omega_c t) - y(t)\sin(\omega_c t)$$


Show the relationship between $R(t)$, $\theta(t)$ and $x(t)$, $y(t)$.


---


### Problem 8.2

Derive the relationship:

$$V(f) = \frac{1}{2}[G(f - f_c) + G^*(-f - f_c)]$$


starting from $v(t) = \text{Re}\{g(t)e^{j\omega_c t}\}$.


**Hint:** Use the Fourier transform properties and the fact that $v(t)$ is real.


---


### Problem 8.3

Show that for a real bandpass signal $v(t)$:

$$R_v(\tau) = \frac{1}{2}\text{Re}\{R_g(\tau)e^{j\omega_c \tau}\}$$


where $R_v(\tau)$ and $R_g(\tau)$ are the autocorrelation functions of $v(t)$ and $g(t)$ respectively.


---


## Answer Key (Selected Problems)


### Solution 1.1

a) $f_c = 10^6$ Hz  

b) $R(t) = 5$ (constant)  

c) $\theta(t) = \pi/4$ (constant)  

d) $g(t) = 5e^{j\pi/4}$, so $v(t) = \text{Re}\{5e^{j\pi/4}e^{j2\pi \cdot 10^6 t}\}$


### Solution 1.2

a) $x(t) = 3$  

b) $y(t) = 4$  

c) $g(t) = 3 + j4$  

d) $R(t) = 5$  

e) $\theta(t) = \tan^{-1}(4/3) \approx 0.927$ rad


### Solution 2.1

a) $P_m = \langle [0.5\cos(2\pi \cdot 100t)]^2 \rangle = 0.25 \times \frac{1}{2} = 0.125$  

b) $P_s = \frac{1}{2} \times 4^2 \times [1 + 0.125] = 8 \times 1.125 = 9$ W  

c) $\langle |g(t)|^2 \rangle = 16\langle [1 + 0.5\cos(2\pi \cdot 100t)]^2 \rangle = 16[1 + 0.125] = 18$, so $P_s = \frac{1}{2} \times 18 = 9$ W ✓


---


## Study Tips


1. **Master the relationships:**

   - $v(t) = \text{Re}\{g(t)e^{j\omega_c t}\}$

   - $g(t) = x(t) + jy(t) = R(t)e^{j\theta(t)}$

   - $v(t) = x(t)\cos(\omega_c t) - y(t)\sin(\omega_c t) = R(t)\cos[\omega_c t + \theta(t)]$


2. **Power calculations:**

   - Always remember: $P_v = \frac{1}{2}\langle |g(t)|^2 \rangle$

   - For AM: $P_s = \frac{1}{2}A_c^2[1 + P_m]$


3. **Frequency domain:**

   - Bandpass signal bandwidth = $2 \times$ baseband bandwidth

   - $V(f)$ is symmetric about $f = 0$ (real signal property)


4. **Practice converting between representations:**

   - Time domain ↔ Complex envelope

   - Quadrature form ↔ Polar form

   - Time domain ↔ Frequency domain


---


*Good luck with your exam preparation!*



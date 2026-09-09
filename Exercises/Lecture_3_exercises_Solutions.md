# Lecture 3 Exercises - Complete Solutions


This document provides detailed solutions to all problems in `Lecture_3_exercises.md`.


---


## Exercise Set 1: Orthogonal Functions and Fourier Series


### Solution 1.1 (Basic)


**Given:** $\phi_1(t) = \cos(2\pi t)$ and $\phi_2(t) = \sin(2\pi t)$ over $[0, 1]$.


**Solution:**

Two functions are orthogonal over $[a, b]$ if $\int_a^b \phi_1(t)\phi_2^*(t) dt = 0$.

Here, the functions are real, so $\phi_2^*(t) = \phi_2(t)$.

$$\int_0^1 \cos(2\pi t)\sin(2\pi t) dt = \frac{1}{2} \int_0^1 \sin(4\pi t) dt$$

$$= \frac{1}{2} \left[ \frac{-\cos(4\pi t)}{4\pi} \right]_0^1 = \frac{-1}{8\pi} (\cos(4\pi) - \cos(0)) = \frac{-1}{8\pi} (1 - 1) = 0$$

**Conclusion:** The functions are orthogonal.


The constant $K_1$ is defined by $\int_0^1 \phi_1(t)\phi_1^*(t) dt = K_1$.

$$K_1 = \int_0^1 \cos^2(2\pi t) dt = \int_0^1 \frac{1 + \cos(4\pi t)}{2} dt = \left[ \frac{t}{2} + \frac{\sin(4\pi t)}{8\pi} \right]_0^1 = \frac{1}{2} + 0 - 0 = \frac{1}{2}$$

**Result:** $K_1 = 0.5$.


---


### Solution 1.2 (Intermediate)


**Given:** $w(t)$ is real and even, $T_0 = 4$, $c_1 = 3 + j0 = 3$, $c_2 = 2$.


**Solution:**

For a real signal, $c_{-n} = c_n^*$.

Therefore, $c_{-1} = c_1^* = (3)^* = 3$.


For a real and even signal, the Fourier coefficients must be real ($\text{Im}[c_n] = 0$).

Since $c_2 = 2$ is real and positive, its phase is:

$\arg[c_2] = \tan^{-1}\left(\frac{0}{2}\right) = 0$ radians.


**Result:** $c_{-1} = 3$, phase of $c_2$ is $0$.


---


### Solution 1.3 (Advanced)


**Given:** $w(t) = A$ for $|t| \leq \tau/2$ and $w(t) = 0$ elsewhere, periodic with $T_0 = T$.


**Solution:**

The Fourier coefficients are given by:

$$c_n = \frac{1}{T_0} \int_{-T_0/2}^{T_0/2} w(t)e^{-jn\omega_0 t} dt$$

Here, $\omega_0 = 2\pi/T$. The integral limits can be restricted to $[-\tau/2, \tau/2]$ where the signal is non-zero.

$$c_n = \frac{1}{T} \int_{-\tau/2}^{\tau/2} A e^{-jn\omega_0 t} dt$$

$$c_n = \frac{A}{T} \left[ \frac{e^{-jn\omega_0 t}}{-jn\omega_0} \right]_{-\tau/2}^{\tau/2}$$

$$c_n = \frac{A}{-jn\omega_0 T} (e^{-jn\omega_0 \tau/2} - e^{jn\omega_0 \tau/2})$$

Using Euler's formula: $\sin(\theta) = \frac{e^{j\theta} - e^{-j\theta}}{2j}$

$$c_n = \frac{A}{n\omega_0 T} \cdot 2\sin(n\omega_0 \tau/2)$$

Substitute $\omega_0 = 2\pi/T$:

$$c_n = \frac{2A}{n(2\pi/T)T} \sin\left(\frac{n(2\pi/T)\tau}{2}\right) = \frac{A}{n\pi} \sin(n\pi\tau/T)$$

Using the definition of the sinc function, $\text{sinc}(x) = \frac{\sin(\pi x)}{\pi x}$:

$$c_n = \frac{A\tau}{T} \frac{\sin(n\pi\tau/T)}{n\pi\tau/T} = \frac{A\tau}{T} \text{sinc}(n\tau/T)$$


**Result:** $c_n = \frac{A\tau}{T} \text{sinc}(n\tau/T)$.


---


## Exercise Set 2: PSD of Periodic Waveforms


### Solution 2.1 (Basic)


**Given:** $c_0 = 5$, $c_1 = 3 - 4j$, $c_{-1} = 3 + 4j$, $c_2 = 2j$, $c_{-2} = -2j$.


**Solution:**

The average power of a periodic signal from its Fourier coefficients is:

$$P = \sum_{n \in \mathbb{Z}} |c_n|^2$$

Calculate the squared magnitude of each coefficient:

- $|c_0|^2 = 5^2 = 25$

- $|c_1|^2 = 3^2 + (-4)^2 = 9 + 16 = 25$

- $|c_{-1}|^2 = 3^2 + 4^2 = 25$

- $|c_2|^2 = 0^2 + 2^2 = 4$

- $|c_{-2}|^2 = 0^2 + (-2)^2 = 4$


Total average power:

$$P = 25 + 25 + 25 + 4 + 4 = 83 \text{ W}$$


---


### Solution 2.2 (Intermediate)


**Given:** $\mathcal{P}_w(f) = 9\delta(f) + 4\delta(f - 10) + 4\delta(f + 10) + \delta(f - 20) + \delta(f + 20)$, $T_0 = 0.1$.


**Solution:**

a) **Average Power:**

The average power is the area under the PSD curve (or the sum of the weights of the delta functions for a periodic signal).

$$P = \int_{-\infty}^{\infty} \mathcal{P}_w(f) df = 9 + 4 + 4 + 1 + 1 = 19 \text{ W}$$


b) **Fourier Coefficients Magnitudes:**

The PSD of a periodic signal is given by:

$$\mathcal{P}_w(f) = \sum_{n \in \mathbb{Z}} |c_n|^2 \delta(f - nf_0)$$

The fundamental frequency is $f_0 = 1/T_0 = 1/0.1 = 10$ Hz.

The PSD has impulses at $0$ Hz, $\pm 10$ Hz, and $\pm 20$ Hz.

Comparing terms:

- For $n=0$ ($f=0$): $|c_0|^2 = 9 \implies |c_0| = 3$

- For $n=1$ ($f=10$): $|c_1|^2 = 4 \implies |c_1| = 2$

- For $n=2$ ($f=20$): $|c_2|^2 = 1 \implies |c_2| = 1$


**Result:** $P = 19 \text{ W}$, $|c_0| = 3$, $|c_1| = 2$, $|c_2| = 1$.


---


### Solution 2.3 (Advanced)


**Prove:** $P = |c_0|^2 + 2\sum_{n=1}^{\infty} |c_n|^2$ for a real periodic signal.


**Proof:**

The average power is given by Parseval's theorem for Fourier series:

$$P = \sum_{n=-\infty}^{\infty} |c_n|^2$$

We can split the sum into three parts: negative $n$, $n=0$, and positive $n$:

$$P = \sum_{n=-\infty}^{-1} |c_n|^2 + |c_0|^2 + \sum_{n=1}^{\infty} |c_n|^2$$

Let $m = -n$ in the first sum:

$$P = \sum_{m=1}^{\infty} |c_{-m}|^2 + |c_0|^2 + \sum_{n=1}^{\infty} |c_n|^2$$

For a real signal, $c_{-n} = c_n^*$, which means their magnitudes are equal: $|c_{-n}| = |c_n^*| = |c_n|$.

Therefore, $|c_{-m}|^2 = |c_m|^2$.

Substituting this into our equation:

$$P = \sum_{m=1}^{\infty} |c_m|^2 + |c_0|^2 + \sum_{n=1}^{\infty} |c_n|^2$$

The two sums are identical:

$$P = |c_0|^2 + 2\sum_{n=1}^{\infty} |c_n|^2 \quad \square$$


---


## Exercise Set 3: LTI Systems and Distortion-less Transmission


### Solution 3.1 (Intermediate)


**Given:** $\mathcal{P}_x(f) = 2$ for $|f| \leq 100$, $H(f) = \frac{1}{1 + j(f/50)}$.


**Solution:**

The power transfer function is $G_h(f) = |H(f)|^2$.

$$H(f) = \frac{1}{1 + j(f/50)}$$

$$|H(f)| = \frac{1}{\sqrt{1^2 + (f/50)^2}} = \frac{1}{\sqrt{1 + (f/50)^2}}$$

$$|H(f)|^2 = \frac{1}{1 + (f/50)^2}$$


The output PSD is:

$$\mathcal{P}_y(f) = |H(f)|^2 \mathcal{P}_x(f)$$

For $|f| \leq 100$:

$$\mathcal{P}_y(f) = \frac{1}{1 + (f/50)^2} \cdot 2 = \frac{2}{1 + (f/50)^2} \text{ W/Hz}$$

For $|f| > 100$:

$$\mathcal{P}_y(f) = |H(f)|^2 \cdot 0 = 0 \text{ W/Hz}$$


**Result:**

$$\mathcal{P}_y(f) = \begin{cases} \frac{2}{1 + (f/50)^2}, & |f| \leq 100 \\ 0, & |f| > 100 \end{cases}$$


---


### Solution 3.2 (Advanced)


**Given:** $H(f) = \frac{10}{1 + j\pi f}$.


**Solution:**

For a channel to be distortion-less, it must satisfy two conditions:

1. Flat amplitude response: $|H(f)| = \text{constant}$

2. Linear phase response: $\arg[H(f)] = -2\pi T_d f$ (where $T_d$ is a constant delay)


Let's check the given transfer function:

1. **Amplitude Response:**

$$|H(f)| = \frac{10}{\sqrt{1 + (\pi f)^2}}$$

The amplitude response is not constant; it depends on the frequency $f$ (it acts as a low-pass filter).


2. **Phase Response:**

$$\arg[H(f)] = \arg[10] - \arg[1 + j\pi f] = 0 - \tan^{-1}(\pi f) = -\tan^{-1}(\pi f)$$

The phase response is not linear; the inverse tangent function is non-linear.


**Result:** The channel is not distortion-less. Both the amplitude requirement and the phase requirement are violated.


---


### Solution 3.3 (Challenge)


**Given:** Delay line $T_d = 2$ ms, Amplifier $A = 5$.


**Solution:**

a) **Time Domain Expression:**

An amplifier scales the signal by $A$, and a delay line shifts it by $T_d$.

$$y(t) = A x(t - T_d) = 5 x(t - 0.002)$$


b) **Transfer Function $H(f)$:**

Take the Fourier transform of the time-domain expression:

$$\mathcal{F}[y(t)] = \mathcal{F}[5 x(t - 0.002)]$$

$$Y(f) = 5 e^{-j2\pi (0.002) f} X(f)$$

Since $Y(f) = H(f)X(f)$, the transfer function is:

$$H(f) = 5 e^{-j0.004\pi f}$$


c) **Verification of Distortion-less Criteria:**

- Amplitude response: $|H(f)| = |5 e^{-j0.004\pi f}| = 5 \times 1 = 5$. This is a constant $A = 5$, satisfying the flat amplitude requirement.

- Phase response: $\arg[H(f)] = -0.004\pi f$. This is a linear function of $f$ in the form $-2\pi T_d f$, where $T_d = 0.004\pi / 2\pi = 0.002$ seconds = 2 ms. This satisfies the linear phase requirement.


**Result:** The system satisfies both frequency domain criteria for distortion-less transmission.


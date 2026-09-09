# Group 1 Exercises - Complete Solutions


This document provides detailed solutions to all problems in Group_1_exercises.md.


---


## Exercise Set 1: Complex Envelope Representation


### Solution 1.1 (Basic)


**Given:** $v(t) = 5\cos(2\pi \cdot 10^6 t + \pi/4)$


**Solution:**


a) **Carrier frequency $f_c$:**

   - Comparing with $v(t) = R(t)\cos[\omega_c t + \theta(t)]$

   - We have $\omega_c = 2\pi \cdot 10^6$ rad/s

   - Therefore: $f_c = \frac{\omega_c}{2\pi} = 10^6$ Hz = **1 MHz**


b) **Real envelope $R(t)$:**

   - From the form: $v(t) = R(t)\cos[\omega_c t + \theta(t)]$

   - Comparing: $R(t) = 5$ (constant)


c) **Phase $\theta(t)$:**

   - From the form: $\theta(t) = \pi/4$ (constant)


d) **Complex envelope representation:**

   - Complex envelope: $g(t) = R(t)e^{j\theta(t)} = 5e^{j\pi/4}$

   - Therefore: $v(t) = \text{Re}\{g(t)e^{j\omega_c t}\} = \text{Re}\{5e^{j\pi/4}e^{j2\pi \cdot 10^6 t}\}$


---


### Solution 1.2 (Intermediate)


**Given:** $v(t) = 3\cos(2\pi \cdot 1000t) - 4\sin(2\pi \cdot 1000t)$, $f_c = 1000$ Hz


**Solution:**


The quadrature form is: $v(t) = x(t)\cos(\omega_c t) - y(t)\sin(\omega_c t)$


Comparing with the given expression:

- $\omega_c = 2\pi \cdot 1000$ rad/s

- $v(t) = 3\cos(2\pi \cdot 1000t) - 4\sin(2\pi \cdot 1000t)$


a) **In-phase component:** $x(t) = 3$ (constant)


b) **Quadrature component:** $y(t) = 4$ (constant)


c) **Complex envelope:**

   $$g(t) = x(t) + jy(t) = 3 + j4$$


d) **Real envelope:**

   $$R(t) = |g(t)| = \sqrt{x^2(t) + y^2(t)} = \sqrt{3^2 + 4^2} = \sqrt{9 + 16} = \sqrt{25} = 5$$


e) **Phase:**

   $$\theta(t) = \arg[g(t)] = \tan^{-1}\left(\frac{y(t)}{x(t)}\right) = \tan^{-1}\left(\frac{4}{3}\right) \approx 0.927 \text{ rad} \approx 53.13°$$


---


### Solution 1.3 (Advanced)


**Given:** $g(t) = 2e^{j\pi t/4} + 3e^{-j\pi t/2}$, $f_c = 500$ Hz


**Solution:**


a) **Bandpass signal $v(t)$:**

   $$v(t) = \text{Re}\{g(t)e^{j\omega_c t}\}$$

   
   where $\omega_c = 2\pi f_c = 2\pi \cdot 500 = 1000\pi$ rad/s

   
   $$v(t) = \text{Re}\{[2e^{j\pi t/4} + 3e^{-j\pi t/2}]e^{j1000\pi t}\}$$

   
   $$v(t) = \text{Re}\{2e^{j(\pi t/4 + 1000\pi t)} + 3e^{j(-j\pi t/2 + 1000\pi t)}\}$$

   
   $$v(t) = 2\cos\left(\frac{\pi t}{4} + 1000\pi t\right) + 3\cos\left(-\frac{\pi t}{2} + 1000\pi t\right)$$

   
   $$v(t) = 2\cos\left(1000\pi t + \frac{\pi t}{4}\right) + 3\cos\left(1000\pi t - \frac{\pi t}{2}\right)$$


b) **Express in form $R(t)\cos[\omega_c t + \theta(t)]$:**

   
   First, let's find the magnitude and phase of $g(t)$:

   $$g(t) = 2e^{j\pi t/4} + 3e^{-j\pi t/2}$$

   
   Using Euler's formula:

   $$g(t) = 2[\cos(\pi t/4) + j\sin(\pi t/4)] + 3[\cos(-\pi t/2) + j\sin(-\pi t/2)]$$

   
   $$g(t) = 2\cos(\pi t/4) + 2j\sin(\pi t/4) + 3\cos(\pi t/2) - 3j\sin(\pi t/2)$$

   
   $$g(t) = [2\cos(\pi t/4) + 3\cos(\pi t/2)] + j[2\sin(\pi t/4) - 3\sin(\pi t/2)]$$

   
   Therefore:

   - $x(t) = 2\cos(\pi t/4) + 3\cos(\pi t/2)$

   - $y(t) = 2\sin(\pi t/4) - 3\sin(\pi t/2)$

   
   Real envelope:

   $$R(t) = |g(t)| = \sqrt{x^2(t) + y^2(t)}$$

   
   $$R(t) = \sqrt{[2\cos(\pi t/4) + 3\cos(\pi t/2)]^2 + [2\sin(\pi t/4) - 3\sin(\pi t/2)]^2}$$

   
   Phase:

   $$\theta(t) = \tan^{-1}\left(\frac{y(t)}{x(t)}\right) = \tan^{-1}\left(\frac{2\sin(\pi t/4) - 3\sin(\pi t/2)}{2\cos(\pi t/4) + 3\cos(\pi t/2)}\right)$$


c) **In-phase and quadrature components:**

   - $x(t) = 2\cos(\pi t/4) + 3\cos(\pi t/2)$

   - $y(t) = 2\sin(\pi t/4) - 3\sin(\pi t/2)$


---


## Exercise Set 2: Power Calculations


### Solution 2.1 (Basic)


**Given:** $g(t) = 4[1 + 0.5\cos(2\pi \cdot 100t)]$, $A_c = 4$, $m(t) = 0.5\cos(2\pi \cdot 100t)$


**Solution:**


a) **Average power of modulating signal:**

   $$P_m = \langle m^2(t) \rangle = \langle [0.5\cos(2\pi \cdot 100t)]^2 \rangle$$

   
   $$P_m = 0.25 \langle \cos^2(2\pi \cdot 100t) \rangle$$

   
   Since $\langle \cos^2(\omega t) \rangle = \frac{1}{2}$:

   $$P_m = 0.25 \times \frac{1}{2} = 0.125$$


b) **Average power of bandpass signal:**

   $$P_s = \frac{1}{2}A_c^2[1 + P_m] = \frac{1}{2}(4)^2[1 + 0.125] = \frac{1}{2} \times 16 \times 1.125 = 8 \times 1.125 = 9 \text{ W}$$


c) **Verification:**

   $$|g(t)|^2 = [4(1 + 0.5\cos(2\pi \cdot 100t))]^2 = 16[1 + 0.5\cos(2\pi \cdot 100t)]^2$$

   
   $$|g(t)|^2 = 16[1 + \cos(2\pi \cdot 100t) + 0.25\cos^2(2\pi \cdot 100t)]$$

   
   $$|g(t)|^2 = 16[1 + \cos(2\pi \cdot 100t) + 0.25 \times \frac{1 + \cos(4\pi \cdot 100t)}{2}]$$

   
   $$|g(t)|^2 = 16[1 + \cos(2\pi \cdot 100t) + 0.125 + 0.125\cos(4\pi \cdot 100t)]$$

   
   $$|g(t)|^2 = 16[1.125 + \cos(2\pi \cdot 100t) + 0.125\cos(4\pi \cdot 100t)]$$

   
   Taking time average:

   $$\langle |g(t)|^2 \rangle = 16[1.125 + 0 + 0] = 16 \times 1.125 = 18$$

   
   Therefore:

   $$P_s = \frac{1}{2}\langle |g(t)|^2 \rangle = \frac{1}{2} \times 18 = 9 \text{ W} \quad \checkmark$$


---


### Solution 2.2 (Intermediate)


**Given:** $g(t) = 5e^{j\theta(t)}$, where $\theta(t) = 0.1\sin(2\pi \cdot 200t)$


**Solution:**


a) **Real envelope $R(t)$:**

   $$R(t) = |g(t)| = |5e^{j\theta(t)}| = 5|e^{j\theta(t)}| = 5 \times 1 = 5$$

   
   The envelope is constant: $R(t) = 5$


b) **Average power $P_v$:**

   $$P_v = \frac{1}{2}\langle |g(t)|^2 \rangle = \frac{1}{2}\langle |5e^{j\theta(t)}|^2 \rangle = \frac{1}{2}\langle 25 \rangle = \frac{25}{2} = 12.5 \text{ W}$$


c) **Power in terms of $A_c$:**

   Since $A_c = 5$:

   $$P_v = \frac{1}{2}A_c^2 = \frac{1}{2}(5)^2 = \frac{25}{2} = 12.5 \text{ W}$$


---


### Solution 2.3 (Advanced)


**Prove:** $P_v = \langle v^2(t) \rangle = \int_{-\infty}^{+\infty} P_v(f) df = R_v(0) = \frac{1}{2}\langle |g(t)|^2 \rangle$


**Proof:**


**Step 1:** Show $P_v = \langle v^2(t) \rangle$

- This is the definition of average power.


**Step 2:** Show $\langle v^2(t) \rangle = \int_{-\infty}^{+\infty} P_v(f) df$

- By Parseval's theorem: $\int_{-\infty}^{+\infty} |v(t)|^2 dt = \int_{-\infty}^{+\infty} |V(f)|^2 df$

- For power signals: $P_v = \lim_{T \to \infty} \frac{1}{2T}\int_{-T}^{T} |v(t)|^2 dt = \int_{-\infty}^{+\infty} P_v(f) df$

- Where $P_v(f)$ is the power spectral density.


**Step 3:** Show $\int_{-\infty}^{+\infty} P_v(f) df = R_v(0)$

- The autocorrelation function is: $R_v(\tau) = \langle v(t)v(t+\tau) \rangle$

- The power spectral density is: $P_v(f) = \mathcal{F}[R_v(\tau)]$

- By the inverse Fourier transform: $R_v(\tau) = \int_{-\infty}^{+\infty} P_v(f)e^{j2\pi f\tau} df$

- Setting $\tau = 0$: $R_v(0) = \int_{-\infty}^{+\infty} P_v(f) df$


**Step 4:** Show $R_v(0) = \frac{1}{2}\langle |g(t)|^2 \rangle$

- From Group 1, we know: $R_v(\tau) = \frac{1}{2}\text{Re}\{R_g(\tau)e^{j\omega_c \tau}\}$

- Where $R_g(\tau) = \langle g^*(t)g(t+\tau) \rangle$ is the autocorrelation of $g(t)$

- Setting $\tau = 0$: $R_v(0) = \frac{1}{2}\text{Re}\{R_g(0)\}$

- Since $R_g(0) = \langle |g(t)|^2 \rangle$ (real and positive):

  $$R_v(0) = \frac{1}{2}\langle |g(t)|^2 \rangle$$


**Therefore, all four expressions are equal!** $\square$


---


## Exercise Set 3: Frequency Domain Analysis


### Solution 3.1 (Basic)


**Given:** 


$$G(f) = \begin{cases}

2A_c, & |f| \leq B \\

0, & |f| > B

\end{cases}$$

where $B = 5$ kHz and $A_c = 3$ V


**Solution:**


a) **Fourier transform of bandpass signal:**

   $$V(f) = \frac{1}{2}[G(f - f_c) + G^*(-f - f_c)]$$

   
   Since $g(t)$ is real, $G^*(-f) = G(f)$, so:

   $$V(f) = \frac{1}{2}[G(f - f_c) + G(f + f_c)]$$

   
   This means:

   - $G(f - f_c)$ is $G(f)$ shifted right by $f_c$

   - $G(f + f_c)$ is $G(f)$ shifted left by $f_c$

   
   The spectrum appears around $\pm f_c$ (we need $f_c$ to be specified, but typically $f_c \gg B$)


b) **Bandwidth:**

   - Baseband bandwidth: $B = 5$ kHz

   - Bandpass bandwidth: $2B = 2 \times 5 = 10$ kHz


c) **Sketch of $|V(f)|$:**

   ```

   |V(f)|

     A_c

      |

      |     ___     ___

      |    /   \   /   \

      |   /     \ /     \

      |__/       |       \___

      |          |          |

    -fc-B  -fc   0   fc   fc+B

   ```

   The spectrum is symmetric about $f = 0$ (real signal property).


---


### Solution 3.2 (Intermediate)


**Given:**


$$M(f) = \begin{cases}

1, & |f| \leq 10 \text{ kHz} \\

0, & |f| > 10 \text{ kHz}

\end{cases}$$


$g(t) = A_c[1 + m(t)]$, $A_c = 5$ V


**Solution:**


a) **Spectrum of complex envelope:**

   $$G(f) = \mathcal{F}[A_c[1 + m(t)]] = A_c[\delta(f) + M(f)]$$

   
   $$G(f) = 5[\delta(f) + M(f)]$$

   
   Where $M(f)$ is the given rectangular spectrum.


b) **Spectrum of bandpass signal:**

   $$S(f) = \frac{1}{2}[G(f - f_c) + G^*(-f - f_c)]$$

   
   Since $g(t)$ is real: $G^*(-f) = G(-f)$

   
   $$S(f) = \frac{1}{2}[G(f - f_c) + G(-f - f_c)]$$

   
   Substituting $G(f)$:

   $$S(f) = \frac{1}{2}[5\delta(f - f_c) + 5M(f - f_c) + 5\delta(-f - f_c) + 5M(-f - f_c)]$$

   
   Using $\delta(-f) = \delta(f)$:

   $$S(f) = \frac{5}{2}[\delta(f - f_c) + M(f - f_c) + \delta(f + f_c) + M(f + f_c)]$$


c) **Carrier and sideband components:**

   - **Carrier:** $\frac{5}{2}\delta(f - f_c)$ and $\frac{5}{2}\delta(f + f_c)$ at $\pm f_c$

   - **Upper sideband:** $\frac{5}{2}M(f - f_c)$ around $+f_c$ (from $f_c - 10$ kHz to $f_c + 10$ kHz)

   - **Lower sideband:** $\frac{5}{2}M(f + f_c)$ around $-f_c$ (from $-f_c - 10$ kHz to $-f_c + 10$ kHz)


d) **Total bandwidth:**

   - Baseband bandwidth: $B = 10$ kHz

   - Bandpass bandwidth: $2B = 20$ kHz


---


### Solution 3.3 (Advanced)


**Prove:** $P_v(f) = \frac{1}{4}[P_g(f - f_c) + P_g^*(-f - f_c)]$


**Proof:**


From Group 1, we know:

$$R_v(\tau) = \frac{1}{2}\text{Re}\{R_g(\tau)e^{j\omega_c \tau}\}$$


Expressing the real part:

$$R_v(\tau) = \frac{1}{2} \cdot \frac{1}{2}[R_g(\tau)e^{j\omega_c \tau} + R_g^*(\tau)e^{-j\omega_c \tau}]$$


$$R_v(\tau) = \frac{1}{4}[R_g(\tau)e^{j\omega_c \tau} + R_g^*(\tau)e^{-j\omega_c \tau}]$$


Taking the Fourier transform:

$$P_v(f) = \mathcal{F}[R_v(\tau)] = \frac{1}{4}[\mathcal{F}[R_g(\tau)e^{j\omega_c \tau}] + \mathcal{F}[R_g^*(\tau)e^{-j\omega_c \tau}]]$$


Using frequency shifting property:

- $\mathcal{F}[R_g(\tau)e^{j\omega_c \tau}] = P_g(f - f_c)$

- $\mathcal{F}[R_g^*(\tau)e^{-j\omega_c \tau}] = P_g^*(-f - f_c)$


Therefore:

$$P_v(f) = \frac{1}{4}[P_g(f - f_c) + P_g^*(-f - f_c)] \quad \square$$


---


## Exercise Set 4: Quadrature Components


### Solution 4.1 (Basic)


**Given:** $v(t) = 6\cos(2\pi \cdot 2000t + \pi/6)$, $f_c = 2000$ Hz


**Solution:**


We need to express: $v(t) = x(t)\cos(\omega_c t) - y(t)\sin(\omega_c t)$


Expanding the given expression:

$$v(t) = 6\cos(2\pi \cdot 2000t + \pi/6)$$


Using the identity: $\cos(A + B) = \cos A \cos B - \sin A \sin B$


$$v(t) = 6[\cos(2\pi \cdot 2000t)\cos(\pi/6) - \sin(2\pi \cdot 2000t)\sin(\pi/6)]$$


$$v(t) = 6\cos(\pi/6)\cos(2\pi \cdot 2000t) - 6\sin(\pi/6)\sin(2\pi \cdot 2000t)$$


$$v(t) = 6 \times \frac{\sqrt{3}}{2}\cos(2\pi \cdot 2000t) - 6 \times \frac{1}{2}\sin(2\pi \cdot 2000t)$$


$$v(t) = 3\sqrt{3}\cos(2\pi \cdot 2000t) - 3\sin(2\pi \cdot 2000t)$$


Therefore:

- $x(t) = 3\sqrt{3} \approx 5.196$ (constant)

- $y(t) = 3$ (constant)


---


### Solution 4.2 (Intermediate)


**Given:** $x(t) = 3\cos(2\pi \cdot 50t)$, $y(t) = 4\sin(2\pi \cdot 50t)$, $f_c = 1$ MHz


**Solution:**


a) **Complex envelope:**

   $$g(t) = x(t) + jy(t) = 3\cos(2\pi \cdot 50t) + j4\sin(2\pi \cdot 50t)$$


b) **Bandpass signal:**

   $$v(t) = x(t)\cos(\omega_c t) - y(t)\sin(\omega_c t)$$

   
   $$v(t) = 3\cos(2\pi \cdot 50t)\cos(2\pi \cdot 10^6 t) - 4\sin(2\pi \cdot 50t)\sin(2\pi \cdot 10^6 t)$$

   
   Using identities:

   - $\cos A \cos B = \frac{1}{2}[\cos(A+B) + \cos(A-B)]$

   - $\sin A \sin B = \frac{1}{2}[\cos(A-B) - \cos(A+B)]$

   
   $$v(t) = \frac{3}{2}[\cos(2\pi(10^6 + 50)t) + \cos(2\pi(10^6 - 50)t)] - 2[\cos(2\pi(10^6 - 50)t) - \cos(2\pi(10^6 + 50)t)]$$

   
   $$v(t) = \frac{3}{2}\cos(2\pi \cdot 1,000,050t) + \frac{3}{2}\cos(2\pi \cdot 999,950t) - 2\cos(2\pi \cdot 999,950t) + 2\cos(2\pi \cdot 1,000,050t)$$

   
   $$v(t) = \frac{7}{2}\cos(2\pi \cdot 1,000,050t) - \frac{1}{2}\cos(2\pi \cdot 999,950t)$$


c) **Real envelope:**

   $$R(t) = |g(t)| = \sqrt{x^2(t) + y^2(t)}$$

   
   $$R(t) = \sqrt{[3\cos(2\pi \cdot 50t)]^2 + [4\sin(2\pi \cdot 50t)]^2}$$

   
   $$R(t) = \sqrt{9\cos^2(2\pi \cdot 50t) + 16\sin^2(2\pi \cdot 50t)}$$


d) **Phase:**

   $$\theta(t) = \tan^{-1}\left(\frac{y(t)}{x(t)}\right) = \tan^{-1}\left(\frac{4\sin(2\pi \cdot 50t)}{3\cos(2\pi \cdot 50t)}\right)$$

   
   $$\theta(t) = \tan^{-1}\left(\frac{4}{3}\tan(2\pi \cdot 50t)\right)$$


---


### Solution 4.3 (Advanced)


**Given:** 

$$v(t) = [2 + \cos(2\pi \cdot 100t)]\cos(2\pi \cdot 10^6 t) - [1 + 0.5\sin(2\pi \cdot 100t)]\sin(2\pi \cdot 10^6 t)$$


**Solution:**


a) **Complex envelope:**

   From the quadrature form: $v(t) = x(t)\cos(\omega_c t) - y(t)\sin(\omega_c t)$

   
   Comparing:

   - $x(t) = 2 + \cos(2\pi \cdot 100t)$

   - $y(t) = 1 + 0.5\sin(2\pi \cdot 100t)$

   
   Therefore:

   $$g(t) = x(t) + jy(t) = [2 + \cos(2\pi \cdot 100t)] + j[1 + 0.5\sin(2\pi \cdot 100t)]$$


b) **Modulating signal for AM:**

   For standard AM: $g(t) = A_c[1 + m(t)]$ where $g(t)$ is real.

   
   This signal has both real and imaginary parts, so it's **not** a standard AM signal.

   
   However, if we consider only the in-phase component as the AM part:

   $$x(t) = 2 + \cos(2\pi \cdot 100t) = 2[1 + 0.5\cos(2\pi \cdot 100t)]$$

   
   Then: $A_c = 2$ and $m(t) = 0.5\cos(2\pi \cdot 100t)$


c) **Average power:**

   $$P_s = \frac{1}{2}\langle |g(t)|^2 \rangle = \frac{1}{2}\langle x^2(t) + y^2(t) \rangle$$

   
   $$P_s = \frac{1}{2}\langle [2 + \cos(2\pi \cdot 100t)]^2 + [1 + 0.5\sin(2\pi \cdot 100t)]^2 \rangle$$

   
   Expanding:

   $$x^2(t) = 4 + 4\cos(2\pi \cdot 100t) + \cos^2(2\pi \cdot 100t)$$

   $$y^2(t) = 1 + \sin(2\pi \cdot 100t) + 0.25\sin^2(2\pi \cdot 100t)$$

   
   Taking time average:

   - $\langle 4 \rangle = 4$

   - $\langle 4\cos(2\pi \cdot 100t) \rangle = 0$

   - $\langle \cos^2(2\pi \cdot 100t) \rangle = \frac{1}{2}$

   - $\langle 1 \rangle = 1$

   - $\langle \sin(2\pi \cdot 100t) \rangle = 0$

   - $\langle 0.25\sin^2(2\pi \cdot 100t) \rangle = 0.25 \times \frac{1}{2} = 0.125$

   
   $$\langle |g(t)|^2 \rangle = 4 + 0.5 + 1 + 0.125 = 5.625$$

   
   $$P_s = \frac{1}{2} \times 5.625 = 2.8125 \text{ W}$$


---


## Exercise Set 5: General Applications


### Solution 5.1 (Intermediate)


**Given:** $f_c = 1$ MHz, $g(t) = 4[1 + 0.8m(t)]$, $m(t) = \cos(2\pi \cdot 5 \times 10^3 t)$


**Solution:**


a) **Time-domain expression:**

   $$s(t) = \text{Re}\{g(t)e^{j\omega_c t}\} = g(t)\cos(\omega_c t)$$

   
   Since $g(t)$ is real:

   $$s(t) = 4[1 + 0.8\cos(2\pi \cdot 5 \times 10^3 t)]\cos(2\pi \cdot 10^6 t)$$

   
   $$s(t) = 4\cos(2\pi \cdot 10^6 t) + 3.2\cos(2\pi \cdot 5 \times 10^3 t)\cos(2\pi \cdot 10^6 t)$$

   
   Using: $\cos A \cos B = \frac{1}{2}[\cos(A+B) + \cos(A-B)]$

   
   $$s(t) = 4\cos(2\pi \cdot 10^6 t) + 1.6\cos[2\pi(10^6 + 5000)t] + 1.6\cos[2\pi(10^6 - 5000)t]$$


b) **Frequency-domain expression:**

   $$G(f) = \mathcal{F}[4[1 + 0.8\cos(2\pi \cdot 5 \times 10^3 t)]]$$

   
   $$G(f) = 4[\delta(f) + 0.8 \times \frac{1}{2}[\delta(f - 5000) + \delta(f + 5000)]]$$

   
   $$G(f) = 4\delta(f) + 1.6\delta(f - 5000) + 1.6\delta(f + 5000)$$

   
   $$S(f) = \frac{1}{2}[G(f - f_c) + G(f + f_c)]$$

   
   $$S(f) = \frac{1}{2}[4\delta(f - 10^6) + 1.6\delta(f - 10^6 - 5000) + 1.6\delta(f - 10^6 + 5000) + 4\delta(f + 10^6) + 1.6\delta(f + 10^6 - 5000) + 1.6\delta(f + 10^6 + 5000)]$$

   
   Simplifying:

   $$S(f) = 2\delta(f - 10^6) + 0.8\delta(f - 1,005,000) + 0.8\delta(f - 995,000) + 2\delta(f + 10^6) + 0.8\delta(f + 1,005,000) + 0.8\delta(f + 995,000)$$


c) **Bandwidth:**

   - Baseband bandwidth: $B = 5$ kHz

   - Bandpass bandwidth: $2B = 10$ kHz


d) **Average transmitted power:**

   $$P_m = \langle m^2(t) \rangle = \langle \cos^2(2\pi \cdot 5 \times 10^3 t) \rangle = \frac{1}{2}$$

   
   $$P_s = \frac{1}{2}A_c^2[1 + P_m] = \frac{1}{2}(4)^2[1 + 0.5] = 8 \times 1.5 = 12 \text{ W}$$


---


### Solution 5.2 (Advanced)


**Given:** $g(t) = A_c[1 + m_1(t) + jm_2(t)]$


**Solution:**


a) **In-phase component:**

   $$g(t) = A_c[1 + m_1(t)] + jA_c m_2(t) = x(t) + jy(t)$$

   
   Therefore: $x(t) = A_c[1 + m_1(t)]$ $\square$


b) **Quadrature component:**

   From above: $y(t) = A_c m_2(t)$ $\square$


c) **Real envelope:**

   $$R(t) = |g(t)| = \sqrt{x^2(t) + y^2(t)}$$

   
   $$R(t) = \sqrt{[A_c(1 + m_1(t))]^2 + [A_c m_2(t)]^2}$$

   
   $$R(t) = A_c\sqrt{[1 + m_1(t)]^2 + m_2^2(t)}$$ $\square$


d) **Phase:**

   $$\theta(t) = \tan^{-1}\left(\frac{y(t)}{x(t)}\right) = \tan^{-1}\left(\frac{A_c m_2(t)}{A_c[1 + m_1(t)]}\right)$$

   
   $$\theta(t) = \tan^{-1}\left(\frac{m_2(t)}{1 + m_1(t)}\right)$$ $\square$


---


### Solution 5.3 (Challenge)


**Prove:** Any real bandpass signal $v(t)$ centered at $f_c$ can be uniquely represented as $v(t) = \text{Re}\{g(t)e^{j\omega_c t}\}$


**Proof:**


**Step 1: Existence**

- Any real bandpass signal $v(t)$ can be written in quadrature form:

  $$v(t) = x(t)\cos(\omega_c t) - y(t)\sin(\omega_c t)$$

- Define $g(t) = x(t) + jy(t)$

- Then: $v(t) = \text{Re}\{[x(t) + jy(t)]e^{j\omega_c t}\} = \text{Re}\{g(t)e^{j\omega_c t}\}$


**Step 2: Uniqueness**

- Suppose $v(t) = \text{Re}\{g_1(t)e^{j\omega_c t}\} = \text{Re}\{g_2(t)e^{j\omega_c t}\}$

- Then: $\text{Re}\{[g_1(t) - g_2(t)]e^{j\omega_c t}\} = 0$ for all $t$

- This implies $g_1(t) = g_2(t)$ (the complex envelope is unique)


**Step 3: Uniqueness up to $f_c$**

- The representation depends on the choice of $f_c$

- If we choose a different carrier frequency $f_c'$, we get a different complex envelope $g'(t)$

- However, for a given $f_c$, the complex envelope $g(t)$ is unique


**Therefore, the representation is unique up to the choice of $f_c$.** $\square$


---


## Exercise Set 6: Numerical Problems


### Solution 6.1 (Basic Calculation)


**Given:** $v(t) = 10\cos(2\pi \cdot 500 \times 10^3 t + 0.5)$


**Solution:**


Comparing with $v(t) = R(t)\cos[\omega_c t + \theta(t)]$:

- $R(t) = 10$ (constant)

- $\omega_c = 2\pi \cdot 500 \times 10^3 = 2\pi \cdot 5 \times 10^5$ rad/s

- $\theta(t) = 0.5$ rad (constant)


Complex envelope: $g(t) = R(t)e^{j\theta(t)} = 10e^{j0.5}$


Therefore: $v(t) = \text{Re}\{10e^{j0.5}e^{j2\pi \cdot 5 \times 10^5 t}\}$


---


### Solution 6.2 (Power Calculation)


**Given:** $g(t) = 6[1 + 0.6\cos(2\pi \cdot 1 \times 10^3 t)]$


**Solution:**


$$P_m = \langle [0.6\cos(2\pi \cdot 10^3 t)]^2 \rangle = 0.36 \times \frac{1}{2} = 0.18$$


$$P_s = \frac{1}{2}A_c^2[1 + P_m] = \frac{1}{2}(6)^2[1 + 0.18] = 18 \times 1.18 = 21.24 \text{ W}$$


---


### Solution 6.3 (Bandwidth Calculation)


**Given:** $B = 8$ kHz


**Solution:**


a) **Minimum bandwidth:**

   - For standard AM/DSB-SC: $2B = 2 \times 8 = 16$ kHz

   - For SSB-AM: $B = 8$ kHz (minimum)


b) **Frequency range:**

   - If $f_c = 100$ MHz and using standard AM/DSB-SC:

   - Lower limit: $f_c - B = 100 \times 10^6 - 8 \times 10^3 = 99.992$ MHz

   - Upper limit: $f_c + B = 100 \times 10^6 + 8 \times 10^3 = 100.008$ MHz

   - Range: **99.992 MHz to 100.008 MHz**


---


## Exercise Set 7: Conceptual Questions


### Solution 7.1


**Differences:**


1. **Bandpass signal vs Complex envelope:**

   - **Bandpass signal $v(t)$:** Real-valued, high-frequency signal centered around $\pm f_c$

   - **Complex envelope $g(t)$:** Complex-valued, baseband signal (0 to B Hz)

   - Relationship: $v(t) = \text{Re}\{g(t)e^{j\omega_c t}\}$


2. **Real envelope $R(t)$ vs Complex envelope $g(t)$:**

   - **Real envelope $R(t)$:** Magnitude of $g(t)$, $R(t) = |g(t)|$, always real and positive

   - **Complex envelope $g(t)$:** Contains both magnitude and phase information, $g(t) = R(t)e^{j\theta(t)}$

   - $R(t)$ is the amplitude modulation, while $g(t)$ contains all information


3. **In-phase vs Quadrature components:**

   - **In-phase $x(t)$:** Real part of $g(t)$, modulates the cosine carrier

   - **Quadrature $y(t)$:** Imaginary part of $g(t)$, modulates the sine carrier (90° out of phase)

   - Together: $g(t) = x(t) + jy(t)$


---


### Solution 7.2


**Why complex envelope representation is useful:**


1. **Signal Processing:**

   - Allows processing at baseband (low frequency) instead of high frequency

   - Reduces computational complexity

   - Easier to implement filters and signal processing algorithms


2. **Bandwidth Efficiency:**

   - All information is in the baseband signal (0 to B Hz)

   - The carrier just shifts it to transmission frequency

   - Makes bandwidth analysis simpler


3. **Mathematical Analysis:**

   - Separates amplitude and phase information clearly

   - Simplifies power calculations: $P_v = \frac{1}{2}\langle |g(t)|^2 \rangle$

   - Makes spectrum analysis easier: $V(f) = \frac{1}{2}[G(f - f_c) + G^*(-f - f_c)]$


---


### Solution 7.3


**Given:** $v(t) = \text{Re}\{g(t)e^{j\omega_c t}\}$


a) **Why "complex envelope":**

   - $g(t)$ "envelopes" the carrier signal - it determines the amplitude and phase variations

   - It's "complex" because it has both real and imaginary parts (amplitude and phase information)

   - The envelope "wraps around" the high-frequency carrier


b) **Why baseband:**

   - $g(t)$ contains only low-frequency components (0 to B Hz)

   - The carrier $e^{j\omega_c t}$ shifts it to high frequency

   - All information is in the baseband, carrier is just for transmission


c) **How $f_c$ is chosen:**

   - Must be much larger than the bandwidth: $f_c \gg B$

   - Determined by transmission requirements (antenna size, propagation, regulations)

   - Different $f_c$ values allow multiple signals to share the spectrum (frequency division)

   - Must satisfy: $f_c > B$ to avoid overlap of positive and negative frequency components


---


## Exercise Set 8: Derivation Problems


### Solution 8.1


**Derive:** $v(t) = x(t)\cos(\omega_c t) - y(t)\sin(\omega_c t)$ from $v(t) = R(t)\cos[\omega_c t + \theta(t)]$


**Derivation:**


Starting from:

$$v(t) = R(t)\cos[\omega_c t + \theta(t)]$$


Using the identity: $\cos(A + B) = \cos A \cos B - \sin A \sin B$


$$v(t) = R(t)[\cos(\omega_c t)\cos(\theta(t)) - \sin(\omega_c t)\sin(\theta(t))]$$


$$v(t) = R(t)\cos(\theta(t))\cos(\omega_c t) - R(t)\sin(\theta(t))\sin(\omega_c t)$$


Defining:

- $x(t) = R(t)\cos(\theta(t))$ (in-phase component)

- $y(t) = R(t)\sin(\theta(t))$ (quadrature component)


Therefore:

$$v(t) = x(t)\cos(\omega_c t) - y(t)\sin(\omega_c t) \quad \square$$


**Relationships:**

- $x(t) = R(t)\cos(\theta(t))$

- $y(t) = R(t)\sin(\theta(t))$

- $R(t) = \sqrt{x^2(t) + y^2(t)}$

- $\theta(t) = \tan^{-1}\left(\frac{y(t)}{x(t)}\right)$


---


### Solution 8.2


**Derive:** $V(f) = \frac{1}{2}[G(f - f_c) + G^*(-f - f_c)]$ from $v(t) = \text{Re}\{g(t)e^{j\omega_c t}\}$


**Derivation:**


Starting from:

$$v(t) = \text{Re}\{g(t)e^{j\omega_c t}\}$$


Expressing the real part:

$$v(t) = \frac{1}{2}[g(t)e^{j\omega_c t} + g^*(t)e^{-j\omega_c t}]$$


Taking the Fourier transform:

$$V(f) = \mathcal{F}[v(t)] = \frac{1}{2}[\mathcal{F}[g(t)e^{j\omega_c t}] + \mathcal{F}[g^*(t)e^{-j\omega_c t}]]$$


Using frequency shifting property:

- $\mathcal{F}[g(t)e^{j\omega_c t}] = G(f - f_c)$

- $\mathcal{F}[g^*(t)e^{-j\omega_c t}] = G^*(-f - f_c)$


Therefore:

$$V(f) = \frac{1}{2}[G(f - f_c) + G^*(-f - f_c)] \quad \square$$


**Note:** For real $g(t)$, $G^*(-f) = G(-f)$, so:

$$V(f) = \frac{1}{2}[G(f - f_c) + G(f + f_c)]$$


---


### Solution 8.3


**Prove:** $R_v(\tau) = \frac{1}{2}\text{Re}\{R_g(\tau)e^{j\omega_c \tau}\}$


**Proof:**


Starting from:

$$v(t) = \text{Re}\{g(t)e^{j\omega_c t}\} = \frac{1}{2}[g(t)e^{j\omega_c t} + g^*(t)e^{-j\omega_c t}]$$


The autocorrelation function:

$$R_v(\tau) = \langle v(t)v(t+\tau) \rangle$$


Substituting:

$$R_v(\tau) = \left\langle \frac{1}{2}[g(t)e^{j\omega_c t} + g^*(t)e^{-j\omega_c t}] \cdot \frac{1}{2}[g(t+\tau)e^{j\omega_c (t+\tau)} + g^*(t+\tau)e^{-j\omega_c (t+\tau)}] \right\rangle$$


Expanding:

$$R_v(\tau) = \frac{1}{4}\langle g(t)g(t+\tau)e^{j\omega_c (2t+\tau)} + g(t)g^*(t+\tau)e^{j\omega_c \tau} + g^*(t)g(t+\tau)e^{-j\omega_c \tau} + g^*(t)g^*(t+\tau)e^{-j\omega_c (2t+\tau)} \rangle$$


For wide-sense stationary processes, the terms with $e^{\pm j\omega_c (2t+\tau)}$ average to zero (they oscillate at $2f_c$).


Therefore:

$$R_v(\tau) = \frac{1}{4}[\langle g(t)g^*(t+\tau) \rangle e^{j\omega_c \tau} + \langle g^*(t)g(t+\tau) \rangle e^{-j\omega_c \tau}]$$


Since $\langle g^*(t)g(t+\tau) \rangle = R_g^*(\tau)$ and $\langle g(t)g^*(t+\tau) \rangle = R_g(\tau)$:


$$R_v(\tau) = \frac{1}{4}[R_g(\tau)e^{j\omega_c \tau} + R_g^*(\tau)e^{-j\omega_c \tau}]$$


$$R_v(\tau) = \frac{1}{2} \cdot \frac{1}{2}[R_g(\tau)e^{j\omega_c \tau} + R_g^*(\tau)e^{-j\omega_c \tau}]$$


$$R_v(\tau) = \frac{1}{2}\text{Re}\{R_g(\tau)e^{j\omega_c \tau}\} \quad \square$$


---


## Summary


All solutions have been provided with detailed step-by-step derivations. Key formulas to remember:


1. **Complex envelope:** $g(t) = x(t) + jy(t) = R(t)e^{j\theta(t)}$

2. **Bandpass signal:** $v(t) = \text{Re}\{g(t)e^{j\omega_c t}\}$

3. **Power:** $P_v = \frac{1}{2}\langle |g(t)|^2 \rangle$

4. **Spectrum:** $V(f) = \frac{1}{2}[G(f - f_c) + G^*(-f - f_c)]$


*Good luck with your exam!*



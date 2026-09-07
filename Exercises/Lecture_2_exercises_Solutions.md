# Lecture 2 Exercises - Complete Solutions

This document provides detailed solutions to all problems in `Lecture_2_exercises.md`.

---

## Exercise Set 1: Energy and Power Signals

### Solution 1.1 (Basic)

**Given:** Determine whether the signals are energy, power, or neither.

**Solution:**
a) $w(t) = 5\cos(10\pi t)$
- This is a periodic sinusoidal signal extending from $t = -\infty$ to $\infty$.
- Energy: $E = \lim_{T \to \infty} \int_{-T/2}^{T/2} [5\cos(10\pi t)]^2 dt \to \infty$.
- Power: $P = \frac{(5)^2}{2} = 12.5$ W (finite).
- **Result:** Power Signal.

b) $w(t) = A\text{rect}(t/T)$
- This is a pulse of finite duration $T$ and constant amplitude $A$.
- Energy: $E = \int_{-T/2}^{T/2} A^2 dt = A^2 T$ (finite).
- Power: $P = \lim_{\mathcal{T} \to \infty} \frac{1}{\mathcal{T}} \int_{-\mathcal{T}/2}^{\mathcal{T}/2} w^2(t) dt = \lim_{\mathcal{T} \to \infty} \frac{A^2 T}{\mathcal{T}} = 0$.
- **Result:** Energy Signal.

c) $w(t) = e^{2t}u(t)$
- This signal grows exponentially to infinity as $t \to \infty$.
- Energy: $E = \int_0^\infty e^{4t} dt \to \infty$.
- Power: $P = \lim_{T \to \infty} \frac{1}{T} \int_0^{T/2} e^{4t} dt \to \infty$.
- **Result:** Neither energy nor power signal.

---

### Solution 1.2 (Intermediate)

**Given:** $w(t) = 3\cos(2\pi \cdot 100t) + 4\sin(2\pi \cdot 100t)$

**Solution:**
The average power $P$ is given by $P = \langle w^2(t) \rangle$.
$$w^2(t) = [3\cos(2\pi \cdot 100t) + 4\sin(2\pi \cdot 100t)]^2$$
$$w^2(t) = 9\cos^2(2\pi \cdot 100t) + 16\sin^2(2\pi \cdot 100t) + 24\cos(2\pi \cdot 100t)\sin(2\pi \cdot 100t)$$

Taking the time average of each term:
- $\langle \cos^2(2\pi \cdot 100t) \rangle = 1/2$
- $\langle \sin^2(2\pi \cdot 100t) \rangle = 1/2$
- $\langle \cos(2\pi \cdot 100t)\sin(2\pi \cdot 100t) \rangle = \langle \frac{1}{2}\sin(4\pi \cdot 100t) \rangle = 0$

Therefore:
$$P = 9(1/2) + 16(1/2) + 0 = 4.5 + 8 = 12.5 \text{ W}$$

*(Alternatively, convert to $w(t) = R\cos(2\pi \cdot 100t - \phi)$, where $R = \sqrt{3^2 + 4^2} = 5$. Then $P = R^2 / 2 = 25/2 = 12.5$ W).*

---

### Solution 1.3 (Advanced)

**Given:** $w(t)$ is periodic with $T_0 = 2$. For $0 \le t < 2$, $w(t) = 2$ for $0 \le t < 1$, and $w(t) = -1$ for $1 \le t < 2$.

**Solution:**
a) **DC component $W_{dc}$:**
$$W_{dc} = \langle w(t) \rangle = \frac{1}{T_0} \int_0^{T_0} w(t) dt$$
$$W_{dc} = \frac{1}{2} \left[ \int_0^1 (2) dt + \int_1^2 (-1) dt \right]$$
$$W_{dc} = \frac{1}{2} [ 2(1 - 0) + (-1)(2 - 1) ] = \frac{1}{2} [2 - 1] = 0.5$$

b) **Average Power $P$:**
$$P = \langle w^2(t) \rangle = \frac{1}{T_0} \int_0^{T_0} w^2(t) dt$$
$$P = \frac{1}{2} \left[ \int_0^1 (2)^2 dt + \int_1^2 (-1)^2 dt \right]$$
$$P = \frac{1}{2} \left[ \int_0^1 4 dt + \int_1^2 1 dt \right]$$
$$P = \frac{1}{2} [ 4(1) + 1(1) ] = \frac{5}{2} = 2.5 \text{ W}$$

---

## Exercise Set 2: Autocorrelation and PSD

### Solution 2.1 (Basic)

**Given:** $R_w(\tau) = 10 \text{sinc}(1000\tau)$

**Solution:**
a) **Average power:**
Using the property $P = R_w(0)$:
$$P = 10 \text{sinc}(0) = 10 \times 1 = 10 \text{ W}$$
*(Note: $\text{sinc}(x) = \frac{\sin(\pi x)}{\pi x}$, so $\text{sinc}(0) = 1$)*

b) **Power Spectral Density $\mathcal{P}_w(f)$:**
Using the Wiener-Khintchine theorem: $\mathcal{P}_w(f) = \mathcal{F}[R_w(\tau)]$
From the Fourier transform properties (duality of rect and sinc):
$\mathcal{F}[W\text{sinc}(Wt)] = \text{rect}(f/W)$

Here, $W = 1000$, so $\mathcal{F}[\text{sinc}(1000\tau)] = \frac{1}{1000}\text{rect}\left(\frac{f}{1000}\right)$
$$\mathcal{P}_w(f) = 10 \times \frac{1}{1000} \text{rect}\left(\frac{f}{1000}\right) = 0.01 \text{rect}\left(\frac{f}{1000}\right) \text{ W/Hz}$$

---

### Solution 2.2 (Intermediate)

**Given:** $w(t) = A\cos(\omega_0 t + \theta)$

**Solution:**
a) **Autocorrelation $R_w(\tau)$:**
$$R_w(\tau) = \lim_{T \to \infty} \frac{1}{T} \int_{-T/2}^{T/2} A\cos(\omega_0 t + \theta)A\cos(\omega_0(t + \tau) + \theta) dt$$
Using $\cos(a)\cos(b) = \frac{1}{2}[\cos(a-b) + \cos(a+b)]$:
$$R_w(\tau) = \frac{A^2}{2} \lim_{T \to \infty} \frac{1}{T} \int_{-T/2}^{T/2} [\cos(-\omega_0\tau) + \cos(2\omega_0 t + \omega_0\tau + 2\theta)] dt$$
Since $\cos(-\omega_0\tau) = \cos(\omega_0\tau)$ is a constant with respect to $t$, its time average is simply $\cos(\omega_0\tau)$.
The time average of the second term (a sinusoid at frequency $2\omega_0$) over an infinite interval is zero.
$$R_w(\tau) = \frac{A^2}{2}\cos(\omega_0\tau)$$

b) **PSD $\mathcal{P}_w(f)$:**
By Wiener-Khintchine theorem, $\mathcal{P}_w(f) = \mathcal{F}[R_w(\tau)]$
Using $\mathcal{F}[\cos(2\pi f_0 t)] = \frac{1}{2}[\delta(f - f_0) + \delta(f + f_0)]$:
$$\mathcal{P}_w(f) = \mathcal{F}\left[ \frac{A^2}{2}\cos(2\pi f_0 \tau) \right] = \frac{A^2}{4}[\delta(f - f_0) + \delta(f + f_0)]$$

---

### Solution 2.3 (Advanced)

**Given:** $\mathcal{P}_w(f) = N_0/2$ for $|f| \le B$, and $0$ otherwise.

**Solution:**
a) **Average power $P$:**
$$P = \int_{-\infty}^{\infty} \mathcal{P}_w(f) df = \int_{-B}^{B} \frac{N_0}{2} df$$
$$P = \frac{N_0}{2} [f]_{-B}^{B} = \frac{N_0}{2} (B - (-B)) = \frac{N_0}{2} (2B) = N_0 B$$

b) **Autocorrelation $R_w(\tau)$:**
By inverse Fourier Transform: $R_w(\tau) = \int_{-\infty}^{\infty} \mathcal{P}_w(f) e^{j2\pi f\tau} df$
$$R_w(\tau) = \int_{-B}^{B} \frac{N_0}{2} e^{j2\pi f\tau} df = \frac{N_0}{2} \left[ \frac{e^{j2\pi f\tau}}{j2\pi\tau} \right]_{-B}^{B}$$
$$R_w(\tau) = \frac{N_0}{2} \frac{e^{j2\pi B\tau} - e^{-j2\pi B\tau}}{j2\pi\tau} = \frac{N_0}{2} \frac{2j\sin(2\pi B\tau)}{j2\pi\tau}$$
$$R_w(\tau) = N_0 B \frac{\sin(2\pi B\tau)}{2\pi B\tau} = N_0 B \text{sinc}(2B\tau)$$
*(Verify: $R_w(0) = N_0 B \text{sinc}(0) = N_0 B = P$, which matches our result above).*

---

## Exercise Set 3: Conceptual and Derivations

### Solution 3.1 (Challenge)

**Prove:** $R_w(0) \ge |R_w(\tau)|$ for all $\tau$.

**Proof:**
Since the time average of any real nonnegative waveform is nonnegative:
$$\langle [w(t) \pm w(t+\tau)]^2 \rangle \ge 0$$

Expanding the squared term:
$$\langle w^2(t) \pm 2w(t)w(t+\tau) + w^2(t+\tau) \rangle \ge 0$$

By linearity of the time average operator:
$$\langle w^2(t) \rangle \pm 2\langle w(t)w(t+\tau) \rangle + \langle w^2(t+\tau) \rangle \ge 0$$

By definition of autocorrelation:
$$R_w(0) \pm 2R_w(\tau) + R_w(0) \ge 0$$
*(Note: $\langle w^2(t+\tau) \rangle = \langle w^2(t) \rangle = R_w(0)$ because shifting the time axis by $\tau$ does not change the average over an infinite interval).*

Simplifying:
$$2R_w(0) \pm 2R_w(\tau) \ge 0$$
$$R_w(0) \pm R_w(\tau) \ge 0$$

This gives two inequalities:
1. $R_w(0) + R_w(\tau) \ge 0 \implies R_w(\tau) \ge -R_w(0)$
2. $R_w(0) - R_w(\tau) \ge 0 \implies R_w(\tau) \le R_w(0)$

Combining these:
$$-R_w(0) \le R_w(\tau) \le R_w(0)$$
$$|R_w(\tau)| \le R_w(0)$$
$$R_w(0) \ge |R_w(\tau)| \quad \square$$

---
*Generated for Lecture 2 - Power Spectral Density*

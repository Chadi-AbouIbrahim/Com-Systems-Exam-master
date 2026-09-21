# Lecture 4 Exercises - Complete Solutions

This document provides detailed solutions to all problems in `Lecture_4_exercises.md`.

---

## Exercise Set 1: Sampling Theorem and Aliasing

### Solution 1.1 (Basic)

**Given:** $w(t)$ is bandlimited to $B = 5 \text{ kHz}$.

**Solution:**

a) **Nyquist sampling frequency:**
According to the sampling theorem, the minimum sampling frequency to perfectly reconstruct a bandlimited signal is $2B$.
$f_s = 2B = 2 \times 5 \text{ kHz} = 10 \text{ kHz}$.

b) **Nyquist sampling interval:**
The sampling interval $T_s$ is the inverse of the sampling frequency.
$T_s = \frac{1}{f_s} = \frac{1}{10,000 \text{ Hz}} = 10^{-4} \text{ s} = 100 \text{ \mu s}$.

---

### Solution 1.2 (Intermediate)

**Given:** $w(t) = 10 \cos(2\pi \cdot 3000 t) + 5 \cos(2\pi \cdot 8000 t)$.

**Solution:**

a) **Absolute bandwidth $B$:**
The signal is composed of two sinusoids with frequencies $f_1 = 3000 \text{ Hz} = 3 \text{ kHz}$ and $f_2 = 8000 \text{ Hz} = 8 \text{ kHz}$.
For a baseband signal, the absolute bandwidth $B$ is the maximum positive frequency present in the spectrum.
$B = \max(3 \text{ kHz}, 8 \text{ kHz}) = 8 \text{ kHz}$.

b) **Minimum sampling frequency $f_s$:**
To avoid aliasing, we must sample at or above the Nyquist rate.
$f_s \ge 2B = 2 \times 8 \text{ kHz} = 16 \text{ kHz}$.

c) **Aliasing at $f_s = 12 \text{ kHz}$:**
Yes, aliasing will occur. The sampling frequency $f_s = 12 \text{ kHz}$ is strictly less than the Nyquist rate of $16 \text{ kHz}$.
Specifically, the $8 \text{ kHz}$ component will alias to a lower frequency: $|f - f_s| = |8 \text{ kHz} - 12 \text{ kHz}| = 4 \text{ kHz}$, which will distort the reconstructed signal.

---

### Solution 1.3 (Advanced)

**Given:** $w(t)$ is sampled at $f_s = 10 \text{ kHz}$. $W(f) \neq 0$ only for $|f| \le 4 \text{ kHz}$.

**Solution:**

a) **Spectrum of the sampled signal $W_s(f)$:**
By impulse sampling, the spectrum of the sampled signal is given by:
$W_s(f) = \frac{1}{T_s} \sum_{n=-\infty}^{+\infty} W(f - nf_s)$
This consists of replicas of the original baseband spectrum $W(f)$ shifted by integer multiples of $f_s = 10 \text{ kHz}$.
- Original baseband ($n=0$): extends from $-4 \text{ kHz}$ to $4 \text{ kHz}$.
- First replicas ($n=\pm 1$): centered at $\pm 10 \text{ kHz}$, extending from $6 \text{ kHz}$ to $14 \text{ kHz}$ and $-14 \text{ kHz}$ to $-6 \text{ kHz}$.
- Second replicas ($n=\pm 2$): centered at $\pm 20 \text{ kHz}$, extending from $16 \text{ kHz}$ to $24 \text{ kHz}$ (and negative).
For $|f| \le 15 \text{ kHz}$, the spectrum consists of the baseband signal (up to $4 \text{ kHz}$) and the first replicas (from $6$ to $14 \text{ kHz}$). Because the baseband signal ends at $4 \text{ kHz}$ and the first replica starts at $6 \text{ kHz}$, there is a $2 \text{ kHz}$ guard band and no overlap (no aliasing).

b) **Cutoff frequency $f_c$:**
To perfectly reconstruct $w(t)$, an ideal low-pass filter must pass the entire baseband spectrum and reject all high-frequency replicas.
- It must pass frequencies up to $B = 4 \text{ kHz}$, so $f_c \ge 4 \text{ kHz}$.
- It must reject frequencies from the first replica starting at $f_s - B = 10 - 4 = 6 \text{ kHz}$, so $f_c \le 6 \text{ kHz}$.
Any cutoff frequency in the range $4 \text{ kHz} \le f_c \le 6 \text{ kHz}$ will work. A common choice is the midpoint, $f_c = f_s / 2 = 5 \text{ kHz}$.

---

## Exercise Set 2: Dimensionality Theorem

### Solution 2.1 (Basic)

**Given:** $B = 20 \text{ kHz}$, $T_0 = 5 \text{ s}$.

**Solution:**
According to the Dimensionality Theorem, for a large $BT_0$ product, the number of independent dimensions (samples) required to specify the waveform is:
$N = 2BT_0$
$N = 2 \times (20 \times 10^3 \text{ Hz}) \times (5 \text{ s}) = 200,000$ dimensions.

---

### Solution 2.2 (Intermediate)

**Given:** $T_0 = 10 \text{ ms} = 0.01 \text{ s}$, $N = 200$.

**Solution:**
Using the Dimensionality Theorem $N = 2BT_0$, we can solve for the maximum absolute bandwidth $B$:
$B = \frac{N}{2T_0}$
$B = \frac{200}{2 \times 0.01 \text{ s}} = \frac{200}{0.02} = 10,000 \text{ Hz} = 10 \text{ kHz}$.

---

## Exercise Set 3: Bandwidth of Signals

### Solution 3.1 (Basic)

**Given:** Magnitude spectrum is maximum at $f=0$ and the first null is at $f = 2.5 \text{ MHz}$.

**Solution:**
For a baseband signal, the null-to-null bandwidth is defined as the frequency difference between the maximum magnitude and the first null along the positive frequency axis.
$B = f_{null} - f_0 = 2.5 \text{ MHz} - 0 = 2.5 \text{ MHz}$.

---

### Solution 3.2 (Intermediate)

**Given:** $|H(f)|^2 = \frac{1}{1 + (f/f_3)^2}$, where $f_3 = 10 \text{ kHz}$.

**Solution:**

a) **3-dB bandwidth:**
The maximum of the power transfer function occurs at $f=0$: $|H(0)|^2 = 1$.
The 3-dB bandwidth is the frequency $f_{3dB}$ where $|H(f)|^2$ drops to half its maximum value:
$\frac{1}{1 + (f_{3dB}/f_3)^2} = \frac{1}{2}$
$1 + (f_{3dB}/f_3)^2 = 2$
$(f_{3dB}/f_3)^2 = 1 \implies f_{3dB} = f_3$
Therefore, the 3-dB bandwidth is $f_3 = 10 \text{ kHz}$.

b) **Equivalent noise bandwidth $B_{eq}$:**
$B_{eq} = \frac{1}{|H(0)|^2} \int_0^{\infty} |H(f)|^2 df$
$B_{eq} = \int_0^{\infty} \frac{1}{1 + (f/f_3)^2} df$
Using the substitution $x = f/f_3 \implies df = f_3 dx$:
$B_{eq} = \int_0^{\infty} \frac{f_3}{1 + x^2} dx = f_3 [\arctan(x)]_0^{\infty}$
$B_{eq} = f_3 \left( \frac{\pi}{2} - 0 \right) = \frac{\pi}{2} f_3$
$B_{eq} = \frac{\pi}{2} \times 10 \text{ kHz} \approx 15.7 \text{ kHz}$.

---

### Solution 3.3 (Advanced)

**Given:** Passband signal centered at $f_c = 100 \text{ MHz}$, non-zero only between $98 \text{ MHz}$ and $102 \text{ MHz}$.

**Solution:**

a) **Absolute bandwidth:**
For a passband signal, the absolute bandwidth is $B = f_2 - f_1$ where the spectrum is zero outside the interval $[f_1, f_2]$ along the positive frequency axis.
$f_1 = 98 \text{ MHz}$, $f_2 = 102 \text{ MHz}$.
$B = 102 \text{ MHz} - 98 \text{ MHz} = 4 \text{ MHz}$.

b) **Energy vs. Power Signal:**
According to the theorem from the lecture, an absolutely bandlimited waveform cannot be absolutely time-limited, and vice versa. 
Since this signal is strictly bandlimited (its spectrum is non-zero only within $[98, 102] \text{ MHz}$), it must extend infinitely in time. A continuous signal of infinite duration typically has infinite energy. Because it is not time-limited and its spectrum implies a persistent oscillation over time, it is a **power signal**, not an energy signal.

---
*Generated for Lecture 4 - Sampling Theorem*

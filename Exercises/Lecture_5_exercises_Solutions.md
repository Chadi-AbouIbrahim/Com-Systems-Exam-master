# Lecture 5 Exercises - Complete Solutions

This document provides detailed solutions to all problems in `Lecture_5_exercises.md`.

---

## Exercise Set 1: Natural Sampling

### Solution 1.1 (Basic)

**Given:** $B = 4 \text{ kHz}$, $f_s = 10 \text{ kHz}$, $d = 0.2$.

**Solution:**

a) **Pulse duration $\tau$:**
The sampling interval is $T_s = \frac{1}{f_s} = \frac{1}{10 \text{ kHz}} = 100 \mu\text{s}$.
The duty cycle is $d = \frac{\tau}{T_s}$, so the pulse duration is:
$\tau = d \times T_s = 0.2 \times 100 \mu\text{s} = 20 \mu\text{s}$.

b) **Null-to-null bandwidth:**
The null-to-null bandwidth of a PAM signal is determined by the first zero-crossing of the sinc envelope, which occurs at $f = \frac{f_s}{d}$ (or equivalently, $\frac{1}{\tau}$).
$BW_{null} = \frac{f_s}{d} = \frac{10 \text{ kHz}}{0.2} = 50 \text{ kHz}$.

---

### Solution 1.2 (Intermediate)

**Given:** $f_s = 8 \text{ kHz}$, $\tau = 25 \mu\text{s}$, $B = 3 \text{ kHz}$.

**Solution:**

a) **Duty cycle $d$:**
First, calculate the sampling interval: $T_s = \frac{1}{f_s} = \frac{1}{8000} = 125 \mu\text{s}$.
The duty cycle is $d = \frac{\tau}{T_s} = \frac{25 \mu\text{s}}{125 \mu\text{s}} = 0.2$ (or $1/5$).

b) **First zero-crossing:**
The envelope of the PAM signal spectrum is determined by the $\text{sinc}(nd)$ function, which goes to zero when $nd$ is an integer.
The first zero-crossing occurs at frequency $f = \frac{f_s}{d} = \frac{8 \text{ kHz}}{0.2} = 40 \text{ kHz}$.

c) **Cutoff frequency $f_c$:**
To recover the original signal using an ideal low-pass filter without aliasing from the first replica (centered at $f_s$), the cutoff frequency must satisfy:
$B < f_c < f_s - B$
$3 \text{ kHz} < f_c < 8 \text{ kHz} - 3 \text{ kHz}$
$3 \text{ kHz} < f_c < 5 \text{ kHz}$.
Any frequency in this open interval can be used.

---

### Solution 1.3 (Advanced)

**Given:** $B = 5 \text{ kHz}$, $f_s = 12 \text{ kHz}$, $d = 1/3$. 

**Solution:**

a) **Oscillator frequency $f_o$:**
To shift the first harmonic ($n=1$), which is centered at $f_s = 12 \text{ kHz}$, down to baseband ($f=0$), the local oscillator frequency $f_o$ must be equal to the sampling frequency.
$f_o = f_s = 12 \text{ kHz}$.

b) **Amplitude factor of recovered signal:**
The spectrum at the output of the analog multiplier is $\frac{1}{2} W_s(f - f_s) + \frac{1}{2} W_s(f + f_s)$.
At baseband, the relevant terms come from the $n=1$ replica in $W_s(f - f_s)$ and the $n=-1$ replica in $W_s(f + f_s)$.
The $n=1$ replica in $W_s(f)$ has an amplitude factor of $d \cdot \text{sinc}(d)$. 
The $n=-1$ replica has an amplitude factor of $d \cdot \text{sinc}(-d) = d \cdot \text{sinc}(d)$.
When they are shifted to baseband and scaled by $1/2$ by the multiplier, they add together:
$\frac{1}{2} d \cdot \text{sinc}(d) W(f) + \frac{1}{2} d \cdot \text{sinc}(-d) W(f) = d \cdot \text{sinc}(d) W(f)$.
For $d = 1/3$, the factor is:
$\frac{1}{3} \text{sinc}(1/3) = \frac{1}{3} \frac{\sin(\pi/3)}{\pi/3} = \frac{\sqrt{3}}{2\pi} \approx 0.275$.
The amplitude factor compared to the original $W(f)$ is $\frac{\sqrt{3}}{2\pi}$.

---

## Exercise Set 2: Instantaneous Sampling (Flat-top)

### Solution 2.1 (Basic)

**Given:** $f_s = 20 \text{ kHz}$, $\tau = 10 \mu\text{s}$.

**Solution:**

a) **Mathematical expression for $h(t)$:**
For flat-top sampling, the pulse shape is a rectangular function of width $\tau$:
$h(t) = \text{rect}\left(\frac{t}{\tau}\right) = \text{rect}\left(\frac{t}{10 \mu\text{s}}\right) = \text{rect}(10^5 t)$.

b) **Zero frequency crossings of $H(f)$:**
The Fourier transform of the rectangular pulse is $H(f) = \tau \text{sinc}(\tau f)$.
The sinc function crosses zero when $\tau f = n$ for any non-zero integer $n$.
$f = \frac{n}{\tau} = \frac{n}{10 \mu\text{s}} = n \times 100 \text{ kHz}$ for $n \in \mathbb{Z} \setminus \{0\}$.

---

### Solution 2.2 (Intermediate)

**Given:** $|W(f)| = 1$ for $|f| \le B = 5 \text{ kHz}$.

**Solution:**

a) **High-frequency loss ratio:**
This effect is known as the **aperture effect**. The recovered signal is scaled by $|H(f)| = \tau |\text{sinc}(\tau f)|$.
At $f=0$, $|H(0)| = \tau \text{sinc}(0) = \tau$.
At $f=B=5 \text{ kHz}$, $\tau B = (10 \mu\text{s})(5 \text{ kHz}) = 0.05$.
The ratio is $\frac{|H(B)|}{|H(0)|} = |\text{sinc}(\tau B)| = \text{sinc}(0.05) = \frac{\sin(0.05\pi)}{0.05\pi} \approx 0.9959$.
The amplitude at $f=B$ drops to roughly $99.6\%$ of its DC value.

b) **Reducing high-frequency loss at transmitter:**
The aperture effect can be reduced by **decreasing the pulse duration $\tau$**, which flattens the $H(f)$ envelope over the signal band.
The disadvantage of this approach is an **increase in the transmission bandwidth** required for the PAM signal.

---

### Solution 2.3 (Advanced)

**Given:** $B = 4 \text{ kHz}$, $f_s = 10 \text{ kHz}$, $\tau = 20 \mu\text{s}$.

**Solution:**

a) **Transfer function $H_{eq}(f)$:**
The equalization filter perfectly compensates for the distortion introduced by $H(f)$. Therefore, its transfer function must be the inverse of $H(f)$ over the signal band:
$H_{eq}(f) = \frac{1}{H(f)} = \frac{1}{\tau \text{sinc}(\tau f)}$ for $-B \le f \le B$.

b) **Gain $|H_{eq}(f)|$ at $f = B$:**
At maximum frequency $f = 4 \text{ kHz}$:
$\tau f = (20 \times 10^{-6})(4 \times 10^3) = 0.08$.
$H(B) = \tau \text{sinc}(0.08) = (20 \mu\text{s}) \frac{\sin(0.08\pi)}{0.08\pi} \approx (20 \times 10^{-6}) \times 0.9894 = 19.78 \times 10^{-6}$.
$|H_{eq}(B)| = \frac{1}{|H(B)|} \approx \frac{1}{19.78 \times 10^{-6}} \approx 50,535$.
*(Note: Commonly, the equalizer is normalized to have a gain of 1 at DC, meaning $H_{eq\_norm}(f) = \frac{1}{\text{sinc}(\tau f)}$. In that case, the normalized gain would be $\frac{1}{0.9894} \approx 1.01$. Providing either the absolute inverse or normalized inverse is conceptually correct as long as the $\text{sinc}$ term is inverted.)*

---

## Exercise Set 3: Disadvantages of PAM

### Solution 3.1 (Basic)

**Solution:**
1. The **bandwidth required is much larger** than that of the original analog signal.
2. The **noise performance is poor**, which renders PAM not suitable for long-distance transmissions.

---

### Solution 3.2 (Intermediate)

**Given:** $B = 10 \text{ kHz}$, $d = 0.1$, $f_s = 2.5 B = 25 \text{ kHz}$.

**Solution:**
The bandwidth of the original baseband signal is $B = 10 \text{ kHz}$.
The null-to-null bandwidth of the natural PAM signal is:
$BW_{PAM} = \frac{f_s}{d} = \frac{25 \text{ kHz}}{0.1} = 250 \text{ kHz}$.
The ratio of the PAM bandwidth to the baseband bandwidth is:
$\frac{BW_{PAM}}{B} = \frac{250 \text{ kHz}}{10 \text{ kHz}} = 25$.
The PAM signal requires **$25$ times larger** bandwidth.

---
*Generated for Lecture 5 - Pulse Amplitude Modulation*

# Lecture 5 Exercises - Pulse Amplitude Modulation

These exercises cover the concepts from Lecture 5: Pulse Amplitude Modulation (PAM), Natural Sampling, Instantaneous (Flat-top) Sampling, and Equalization.

---

## Exercise Set 1: Natural Sampling

### Exercise 1.1 (Basic)

An analog signal $w(t)$ is bandlimited to $B = 4 \text{ kHz}$. It is sampled using natural sampling with a sampling frequency $f_s = 10 \text{ kHz}$ and a duty cycle $d = 0.2$.

a) What is the pulse duration $\tau$?
b) What is the null-to-null bandwidth of the resulting PAM signal?

### Exercise 1.2 (Intermediate)

A naturally sampled PAM signal is generated with $f_s = 8 \text{ kHz}$ and a pulse duration $\tau = 25 \mu\text{s}$. The original baseband signal has a bandwidth of $B = 3 \text{ kHz}$.

a) Calculate the duty cycle $d$.
b) Determine the location of the first zero-crossing in the envelope of the PAM signal spectrum (due to the sinc function).
c) If an ideal low-pass filter is used to recover the original signal, what are the permissible values for its cutoff frequency $f_c$?

### Exercise 1.3 (Advanced)

A baseband signal $w(t)$ with bandwidth $B = 5 \text{ kHz}$ is transmitted using natural sampling with $f_s = 12 \text{ kHz}$ and $d = 1/3$. The received signal is contaminated with significant low-frequency noise near $f = 0$.

a) To avoid this noise, the receiver shifts the first harmonic ($n=1$) to baseband using an analog multiplier and a local oscillator. What should be the frequency of the oscillator $f_o$ in Hz?
b) Based on the spectrum of the signal at the output of the multiplier, what is the amplitude factor of the recovered baseband signal spectrum compared to the original $W(f)$?

---

## Exercise Set 2: Instantaneous Sampling (Flat-top)

### Exercise 2.1 (Basic)

An instantaneous (flat-top) sampled PAM signal uses a sampling rate of $f_s = 20 \text{ kHz}$ and a rectangular pulse of duration $\tau = 10 \mu\text{s}$.

a) Write the mathematical expression for the sampling pulse shape $h(t)$.
b) Evaluate the zero frequency crossings of the Fourier transform $H(f)$ of the sampling pulse.

### Exercise 2.2 (Intermediate)

For the system in Exercise 2.1, assume the original signal $w(t)$ has a flat magnitude spectrum $|W(f)| = 1$ for $|f| \le B = 5 \text{ kHz}$.

a) The recovered signal using a simple low-pass filter suffers from a high-frequency loss distortion. What is the ratio of the restored spectrum's magnitude at $f = B$ to its magnitude at $f = 0$?
b) How could you reduce this high-frequency loss at the transmitter without changing $f_s$? What is the disadvantage of this approach?

### Exercise 2.3 (Advanced)

To perfectly compensate for the high-frequency loss in flat-top sampling for a signal bandlimited to $B = 4 \text{ kHz}$ with $f_s = 10 \text{ kHz}$ and $\tau = 20 \mu\text{s}$, an equalization filter is used at the receiver.

a) Determine the exact transfer function $H_{eq}(f)$ of this equalization filter for the frequency range $-B \le f \le B$.
b) What is the value of the equalization filter's gain $|H_{eq}(f)|$ at the maximum signal frequency $f = B$?

---

## Exercise Set 3: Disadvantages of PAM

### Exercise 3.1 (Basic)

State two primary disadvantages of both naturally-sampled and instantaneously-sampled Pulse Amplitude Modulation (PAM) systems compared to transmitting the baseband signal directly.

### Exercise 3.2 (Intermediate)

A signal $w(t)$ bandlimited to $10 \text{ kHz}$ is to be transmitted. Compare the null-to-null bandwidth required for natural PAM with a duty cycle $d = 0.1$ and a sampling frequency $f_s = 2.5 B$ to the absolute bandwidth of the original baseband signal. How many times larger is the PAM bandwidth?

# Lecture 4 Exercises - Sampling Theorem

These exercises cover the concepts from Lecture 4: Sampling Theorem, Dimensionality Theorem, Impulse Sampling, and Bandwidth of Signals.

---

## Exercise Set 1: Sampling Theorem and Aliasing

### Exercise 1.1 (Basic)

A signal $w(t)$ is bandlimited to $B = 5 \text{ kHz}$. 
a) What is the Nyquist sampling frequency for this signal?
b) What is the corresponding Nyquist sampling interval $T_s$?

### Exercise 1.2 (Intermediate)

A signal is given by $w(t) = 10 \cos(2\pi \cdot 3000 t) + 5 \cos(2\pi \cdot 8000 t)$.
a) Determine the absolute bandwidth $B$ of the signal.
b) What is the minimum sampling frequency $f_s$ required to avoid aliasing?
c) If the signal is sampled at $f_s = 12 \text{ kHz}$, will aliasing occur? Justify your answer.

### Exercise 1.3 (Advanced)

A signal $w(t)$ is sampled using impulse sampling at a rate $f_s = 10 \text{ kHz}$. The spectrum of the original signal $W(f)$ is non-zero only for $|f| \le 4 \text{ kHz}$.
a) Sketch the spectrum of the sampled signal $W_s(f)$ for $|f| \le 15 \text{ kHz}$.
b) Specify the cutoff frequency $f_c$ of an ideal low-pass filter required to perfectly reconstruct $w(t)$ from its samples.

---

## Exercise Set 2: Dimensionality Theorem

### Exercise 2.1 (Basic)

An audio signal has a bandwidth of $B = 20 \text{ kHz}$. According to the Dimensionality Theorem, how many independent pieces of information (dimensions) are required to specify this signal over a time interval of $T_0 = 5 \text{ seconds}$?

### Exercise 2.2 (Intermediate)

A communication system needs to transmit a bandlimited signal over a duration of $T_0 = 10 \text{ ms}$. If the system can only transmit $N = 200$ independent samples in that duration, what is the maximum absolute bandwidth $B$ the signal can have to be perfectly reconstructed?

---

## Exercise Set 3: Bandwidth of Signals

### Exercise 3.1 (Basic)

A baseband signal has a magnitude spectrum that is maximum at DC ($f=0$) and first reaches zero (a null) at $f = 2.5 \text{ MHz}$. What is the null-to-null bandwidth of this signal?

### Exercise 3.2 (Intermediate)

The power transfer function of a low-pass filter is given by $|H(f)|^2 = \frac{1}{1 + (f/f_3)^2}$, where $f_3 = 10 \text{ kHz}$.
a) Calculate the 3-dB bandwidth of this filter.
b) Calculate the equivalent noise bandwidth $B_{eq}$ of this filter.
*(Hint: $\int_0^{\infty} \frac{1}{1+x^2}dx = \frac{\pi}{2}$)*

### Exercise 3.3 (Advanced)

Consider a bandpass signal centered at $f_c = 100 \text{ MHz}$. Its magnitude spectrum is non-zero and constant between $98 \text{ MHz}$ and $102 \text{ MHz}$, and zero elsewhere.
a) Determine the absolute bandwidth of the signal.
b) Is this an energy signal or a power signal if it is defined over all time? Explain using the concept of time and band limitedness.

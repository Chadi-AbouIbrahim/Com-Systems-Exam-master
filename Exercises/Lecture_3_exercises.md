# Lecture 3 Exercises - Orthogonal Representation of Signals

These exercises cover the concepts from Lecture 3: Orthogonal Functions, Fourier Series, Power Spectral Density of Periodic Waveforms, and LTI Systems.

---

## Exercise Set 1: Orthogonal Functions and Fourier Series

### Exercise 1.1 (Basic)
Determine if the functions $\phi_1(t) = \cos(2\pi t)$ and $\phi_2(t) = \sin(2\pi t)$ are orthogonal over the interval $[0, 1]$. What is the value of the constant $K_1$ for $\phi_1(t)$?

### Exercise 1.2 (Intermediate)
A periodic signal $w(t)$ has a fundamental period $T_0 = 4$ seconds. It can be represented by a Fourier series. If $w(t)$ is real and even, and it is known that:
$$ c_1 = 3 + j0 \quad \text{and} \quad c_2 = 2 $$
determine the values of $c_{-1}$ and the phase of $c_2$.

### Exercise 1.3 (Advanced)
A signal $w(t)$ is defined over $[-T/2, T/2]$ as $w(t) = A$ for $|t| \leq \tau/2$ and $w(t) = 0$ elsewhere ($\tau < T$). 
Find the Fourier series coefficients $c_n$ if we represent $w(t)$ periodically with period $T_0 = T$.

---

## Exercise Set 2: PSD of Periodic Waveforms

### Exercise 2.1 (Basic)
A periodic signal $w(t)$ has the following non-zero Fourier coefficients:
$$ c_0 = 5, \quad c_1 = 3 - 4j, \quad c_{-1} = 3 + 4j, \quad c_2 = 2j, \quad c_{-2} = -2j $$
Calculate the average power of the signal $w(t)$.

### Exercise 2.2 (Intermediate)
A periodic signal $w(t)$ with period $T_0 = 0.1$ seconds has the following Power Spectral Density:
$$\mathcal{P}_w(f) = 9\delta(f) + 4\delta(f - 10) + 4\delta(f + 10) + \delta(f - 20) + \delta(f + 20)$$
What is the average power of the signal? What are the magnitudes of the Fourier coefficients $|c_0|$, $|c_1|$, and $|c_2|$?

### Exercise 2.3 (Advanced)
Prove that the average power $P$ of a real periodic signal $w(t)$ can be written in terms of its Fourier coefficients $c_n$ as:
$$P = |c_0|^2 + 2\sum_{n=1}^{\infty} |c_n|^2$$
(Hint: Use the fact that $|c_{-n}|^2 = |c_n|^2$ for a real signal).

---

## Exercise Set 3: LTI Systems and Distortion-less Transmission

### Exercise 3.1 (Intermediate)
A signal $x(t)$ with PSD $\mathcal{P}_x(f) = 2 \text{ W/Hz}$ for $|f| \leq 100$ Hz and $0$ otherwise, is passed through an LTI system with frequency response:
$$H(f) = \frac{1}{1 + j(f/50)}$$
Calculate the Power Spectral Density of the output signal, $\mathcal{P}_y(f)$.

### Exercise 3.2 (Advanced)
A channel has the following transfer function:
$$H(f) = \frac{10}{1 + j\pi f}$$
Is this channel distortion-less? If not, explain which of the two distortion-less requirements (amplitude or phase) are violated.

### Exercise 3.3 (Challenge)
A system is composed of an ideal delay line with delay $T_d = 2$ ms and an ideal amplifier with gain $A = 5$. 
a) Write the mathematical expression for the output $y(t)$ in terms of the input $x(t)$.
b) Find the transfer function $H(f)$ of this system.
c) Verify that this system provides distortion-less transmission according to the frequency domain criteria.

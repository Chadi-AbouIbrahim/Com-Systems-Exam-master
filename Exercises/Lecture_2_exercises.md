# Lecture 2 Exercises - Power Spectral Density


These exercises cover the concepts from Lecture 2: Energy and Power Signals, PSD, and Autocorrelation.


---


## Exercise Set 1: Energy and Power Signals


### Exercise 1.1 (Basic)

Determine whether the following signals are energy signals, power signals, or neither:

a) $w(t) = 5\cos(10\pi t)$

b) A rectangular pulse $w(t) = A\text{rect}(t/T)$ of width $T$ and amplitude $A$. Calculate its total energy.

c) $w(t) = e^{2t}u(t)$, where $u(t)$ is the unit step function.


### Exercise 1.2 (Intermediate)

Calculate the average power of the signal $w(t) = 3\cos(2\pi \cdot 100t) + 4\sin(2\pi \cdot 100t)$.


### Exercise 1.3 (Advanced)

A periodic signal $w(t)$ has a period $T_0 = 2$ seconds. Over one period ($0 \le t < 2$), it is defined as:


$$w(t) = \begin{cases} 2, & 0 \le t < 1 \\ -1, & 1 \le t < 2 \end{cases}$$


Calculate the DC component and the average power of this signal.


---


## Exercise Set 2: Autocorrelation and PSD


### Exercise 2.1 (Basic)

The autocorrelation function of a power signal $w(t)$ is given by $R_w(\tau) = 10 \text{sinc}(1000\tau)$.

a) What is the average power of $w(t)$?

b) What is the Power Spectral Density $\mathcal{P}_w(f)$?


### Exercise 2.2 (Intermediate)

Determine the autocorrelation function $R_w(\tau)$ and the PSD $\mathcal{P}_w(f)$ for the signal:


$$ w(t) = A\cos(\omega_0 t + \theta) $$


where $\theta$ is a constant. 


### Exercise 2.3 (Advanced)

A signal $w(t)$ has a Power Spectral Density given by:


$$\mathcal{P}_w(f) = \begin{cases} N_0/2, & |f| \le B \\ 0, & |f| > B \end{cases}$$


Determine the average power $P$ and the autocorrelation function $R_w(\tau)$.


### Exercise 2.4 (Advanced)

Using the definition of PSD via the limit of a truncated waveform:


$$ \mathcal{P}_w(f) = \lim_{T\rightarrow+\infty} \frac{1}{T}\vert W_T(f)\vert^2 $$


where $w_T(t)$ is the waveform truncated to $[-T/2, T/2]$, calculate the Power Spectral Density of the signal $w(t) = A e^{j\omega_0 t}$.


---


## Exercise Set 3: Conceptual and Derivations


### Exercise 3.1 (Challenge)

Using the definition of time average, prove that for any real power waveform $w(t)$, the autocorrelation function verifies the relation $R_w(0) \ge |R_w(\tau)|$ for all $\tau$.


### Exercise 3.2 (Challenge)

Using the definition of autocorrelation, prove that for any real power waveform $w(t)$, the autocorrelation function is an even function: $R_w(\tau) = R_w(-\tau)$.


### Exercise 3.3 (Challenge)

Prove that if a real power waveform $w(t)$ is periodic with period $T_0$, then its autocorrelation function $R_w(\tau)$ is also periodic with the same period $T_0$.


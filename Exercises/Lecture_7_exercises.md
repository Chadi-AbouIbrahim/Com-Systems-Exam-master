# Lecture 7 Exercises - Digital Signaling

These exercises cover the concepts from Lecture 7: Orthogonal Series Representation of Digital Signals, Baud Rate and Bit Rate, Matched Filter Detection, Bandwidth Estimation (Dimensionality Theorem), Binary Signaling (Rectangular and Sinc Pulses), and Multilevel Signaling with Gray Mapping.

---

## Exercise Set 1: Baud Rate and Bit Rate

### Exercise 1.1 (Basic)

The ASCII codeword $1010011$ is transmitted as a binary signal $w(t) = \sum_{k=1}^{N} w_k \varphi_k(t)$ over an interval $T_0 = 3.5 \text{ ms}$.

a) Determine $N$ and the values of $w_1, w_2, \ldots, w_N$.
b) Calculate the symbol duration $T_s$ and the bit duration $T_b$.
c) Calculate the baud rate $D$ and the bit rate $R$.
d) Is $w(t)$ a binary or a multilevel signal? Justify.

### Exercise 1.2 (Intermediate)

A source transmits $n = 12$ bits in $T_0 = 6 \text{ ms}$. The bits are grouped into multilevel symbols, each taking one of $L = 8$ possible values.

a) How many bits $l$ are carried by each symbol?
b) How many dimensions $N$ are needed to represent the signal over $[0, T_0]$?
c) Calculate $T_s$, $T_b$, $D$ and $R$.
d) Verify that the relation $R = \log_2(L)\, D$ holds.

### Exercise 1.3 (Advanced)

A digital transmitter sends $1200$ symbols per second, and each symbol takes one of $L = 16$ levels.

a) What is the bit rate $R$?
b) How long does it take to transmit a message of $9600$ bits?
c) How many dimensions $N$ are used in an interval of $T_0 = 0.5 \text{ s}$?
d) If the number of levels is reduced to $L = 4$ while keeping the same bit rate, what baud rate is required? By what factor did the baud rate change?

---

## Exercise Set 2: Detection Using the Orthogonal Series Coefficients

### Exercise 2.1 (Basic)

a) Write the expression used at the receiver to recover the data $w_k$ from the received waveform $w(t)$, and define the constant $K_k$.
b) What is this detection procedure called?
c) Under which type of noise is this procedure optimal?

### Exercise 2.2 (Intermediate)

A binary signal uses rectangular pulses with $T_s = 2 \text{ ms}$:
$$\varphi_k(t) = \text{rect}\left(\frac{t - (k - \frac{1}{2})T_s}{T_s}\right)$$

a) Calculate $K_k$.
b) During the third symbol interval ($2T_s \le t < 3T_s$), the transmitted value is $w_3 = 1$, but the received waveform is disturbed and equals:
$$w(t) = 1 + 0.2 \sin\left(\frac{2\pi t}{T_s}\right)$$
Compute $w_3$ using the orthogonal series coefficient (integration) formula.
c) For rectangular pulses, the lecture states that detection can be done by sampling the waveform anywhere within the symbol interval. Compute the detected value $\hat{w}_3$ if, instead of integrating, the receiver estimates $w_3$ by sampling the received waveform at $t = 2.25\, T_s$.
d) Which method is more robust to this disturbance? Explain why.

### Exercise 2.3 (Advanced)

Prove that the following sets of functions are orthogonal, i.e., that $\int_{-\infty}^{+\infty} \varphi_j(t)\varphi_k^*(t)\, dt = T_s\, \delta_{jk}$:

a) Rectangular pulses: $\varphi_k(t) = \text{rect}\left(\frac{t - (k - \frac{1}{2})T_s}{T_s}\right)$
b) Sinc pulses: $\varphi_k(t) = \text{sinc}\left(\frac{t - (k - \frac{1}{2})T_s}{T_s}\right)$

*(Hint for b: use Parseval's theorem and the fact that the Fourier transform of $\text{sinc}(t/T_s)$ is $T_s \text{rect}(T_s f)$.)*

---

## Exercise Set 3: Bandwidth Estimation

### Exercise 3.1 (Basic)

A digital signal is transmitted at a baud rate of $D = 9600 \text{ baud}$.

a) Using the dimensionality theorem, give the lower bound on the bandwidth of the signal.
b) Which pulse shape achieves this lower bound?
c) Will rectangular pulses require more or less bandwidth than this bound?

### Exercise 3.2 (Intermediate)

A binary signal is transmitted at a bit rate of $R = 64 \text{ kbits/s}$.

a) Calculate the null-to-null bandwidth when rectangular pulses are used.
b) Calculate the absolute bandwidth when sinc pulses are used.
c) Compare both results to the dimensionality theorem lower bound. By what factor does the rectangular pulse exceed it?

### Exercise 3.3 (Advanced)

A telephone channel has a usable bandwidth of $B = 3 \text{ kHz}$.

a) Using sinc pulses, what is the maximum baud rate $D$ that can be supported?
b) What is the maximum bit rate if binary signaling is used?
c) What is the minimum number of levels $L$ (a power of 2) needed to transmit $R = 24 \text{ kbits/s}$ with sinc pulses?
d) Repeat part (c) if rectangular pulses are used and the channel bandwidth must contain the null-to-null bandwidth of the signal.

---

## Exercise Set 4: Binary Signaling Waveforms

### Exercise 4.1 (Basic)

The bit sequence $10110010$ is transmitted as a unipolar binary signal ($w_k \in \{0, 1\}$) using rectangular pulses with $T_s = 0.5 \text{ ms}$.

a) Find $N$, $T_0$, $D$ and $R$.
b) Write the expression of $w(t)$ in terms of the $\varphi_k(t)$.
c) Specify the time intervals (in ms) where $w(t) = 1$.
d) Sketch $w(t)$.

### Exercise 4.2 (Intermediate)

The same sequence $10110010$ ($T_s = 0.5 \text{ ms}$) is now transmitted using sinc pulses:
$$\varphi_k(t) = \text{sinc}\left(\frac{t - (k - \frac{1}{2})T_s}{T_s}\right)$$

a) Show that sampling $w(t)$ at the middle of the $m$-th symbol interval, $t_m = (m - \frac{1}{2})T_s$, gives exactly $w_m$.
b) Compute the value of $w(t)$ at $t = 0$ (the beginning of the first symbol interval, not its middle). Is it equal to $w_1$?
c) What is the absolute bandwidth of this signal? Compare it with the null-to-null bandwidth of the rectangular-pulse signal of Exercise 4.1.

### Exercise 4.3 (Advanced)

For the sinc-pulse signal of Exercise 4.2, the receiver clock has a timing error and samples the fourth symbol at $t = (4 - \frac{1}{2})T_s + 0.1\,T_s$ instead of the middle of the interval.

a) Compute the sampled value. *(Keep 3 significant digits.)*
b) What is the relative error with respect to the correct value $w_4 = 1$?
c) Would the same timing error cause any error with rectangular pulses? Explain.
d) Based on these results, state one practical advantage of rectangular pulses and one advantage of sinc pulses.

---

## Exercise Set 5: Multilevel Signaling and Gray Mapping

Use the Gray mapping from the lecture for $L = 4$:

| Binary Input ($l = 2$ bits) | Output Level (V) |
|:---:|:---:|
| 11 | +3 |
| 10 | +1 |
| 00 | -1 |
| 01 | -3 |

### Exercise 5.1 (Basic)

a) Map the bit sequence $11011000$ to the corresponding 4-level symbols $w_1, \ldots, w_N$.
b) How many symbols $N$ are needed? Compare with binary signaling.

### Exercise 5.2 (Intermediate)

a) What property makes the above mapping a *Gray* mapping?
b) Because of noise, a transmitted level $+1$ is detected as $+3$. How many bit errors result?
c) Consider instead the natural binary mapping: $00 \to -3$, $01 \to -1$, $10 \to +1$, $11 \to +3$. If a transmitted $+1$ is detected as the adjacent level $-1$, how many bit errors result?
d) Construct a Gray mapping for $L = 8$ with levels $-7, -5, -3, -1, +1, +3, +5, +7$.

### Exercise 5.3 (Advanced)

The 12-bit sequence $101100111000$ is transmitted in $T_0 = 6 \text{ ms}$ using the 4-level Gray mapping above.

a) Find the symbols $w_1, \ldots, w_N$.
b) Calculate $T_s$, $T_b$, $D$ and $R$.
c) Calculate the null-to-null bandwidth for rectangular pulses and the absolute bandwidth for sinc pulses.
d) What would these two bandwidths be if the same bits were sent with binary signaling in the same $T_0$?
e) With rectangular pulses, the receiver samples the waveform at $t = 2.7 \text{ ms}$. Which symbol is detected, and which bits does it correspond to?

---

## Exercise Set 6: Binary vs. Multilevel Bandwidth Comparison

### Exercise 6.1 (Basic)

A binary signal requires a bandwidth of $B_{Binary} = 1.2 \text{ MHz}$. What bandwidth is required by the corresponding multilevel signal (same bit rate, same pulse shape) when:

a) $L = 4$
b) $L = 8$
c) $L = 16$

### Exercise 6.2 (Intermediate)

A data source transmits one of $M = 256$ possible messages every $1 \text{ ms}$, using sinc pulses.

a) How many bits are needed to represent each message? What is the bit rate $R$?
b) Complete the following table:

| $L$ | $l = \log_2 L$ | $N$ (symbols/message) | $D$ (baud) | Absolute bandwidth (Hz) |
|:---:|:---:|:---:|:---:|:---:|
| 2 | | | | |
| 4 | | | | |
| 16 | | | | |
| 256 | | | | |

### Exercise 6.3 (Advanced)

The levels of a multilevel signal are equally spaced in the range $[-A, +A]$ with $A = 3 \text{ V}$ (e.g., $-3, -1, +1, +3$ for $L = 4$).

a) Give the general expression of the spacing $\Delta$ between adjacent levels as a function of $A$ and $L$.
b) Compute $\Delta$ for $L = 4$ and $L = 16$.
c) Using your results, explain why the number of levels $L$ cannot be increased indefinitely to reduce the bandwidth, even though $B_{Multilevel} = B_{Binary} / \log_2(L)$.

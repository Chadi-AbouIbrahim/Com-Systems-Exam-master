# Lecture 7 Exercises - Complete Solutions

This document provides detailed solutions to all problems in `Lecture_7_exercises.md`.

---

## Exercise Set 1: Baud Rate and Bit Rate

### Solution 1.1 (Basic)

**Given:** Codeword $1010011$, $T_0 = 3.5 \text{ ms}$, binary signaling.

**Solution:**

a) **$N$ and the $w_k$'s:**
The codeword has 7 bits and each bit is one symbol, so $N = n = 7$:
$w_1 = 1, \; w_2 = 0, \; w_3 = 1, \; w_4 = 0, \; w_5 = 0, \; w_6 = 1, \; w_7 = 1$.

b) **Symbol and bit durations:**
$T_s = \frac{T_0}{N} = \frac{3.5 \text{ ms}}{7} = 0.5 \text{ ms}$.
For binary signaling $T_b = T_s = 0.5 \text{ ms}$.

c) **Baud rate and bit rate:**
$D = \frac{N}{T_0} = \frac{7}{3.5 \text{ ms}} = 2 \text{ kbaud}$.
$R = \frac{n}{T_0} = \frac{7}{3.5 \text{ ms}} = 2 \text{ kbits/s}$.

d) **Binary or multilevel:**
The $w_k$'s take only $L = 2$ values $\{0, 1\}$, so $w(t)$ is a **binary signal** (and $N = n$, $D = R$).

---

### Solution 1.2 (Intermediate)

**Given:** $n = 12$ bits, $T_0 = 6 \text{ ms}$, $L = 8$.

**Solution:**

a) **Bits per symbol:**
$l = \log_2(L) = \log_2(8) = 3$ bits/symbol.

b) **Number of dimensions:**
$N = \frac{n}{l} = \frac{12}{3} = 4$ symbols.

c) **Durations and rates:**
$T_s = \frac{T_0}{N} = \frac{6 \text{ ms}}{4} = 1.5 \text{ ms}$
$T_b = \frac{T_0}{n} = \frac{6 \text{ ms}}{12} = 0.5 \text{ ms}$
$D = \frac{1}{T_s} = \frac{1}{1.5 \text{ ms}} \approx 666.7 \text{ baud}$
$R = \frac{1}{T_b} = \frac{1}{0.5 \text{ ms}} = 2 \text{ kbits/s}$

d) **Verification:**
$\log_2(L)\, D = 3 \times 666.7 = 2000 \text{ bits/s} = R$ ✓
Equivalently, $T_s = \log_2(L)\, T_b = 3 \times 0.5 \text{ ms} = 1.5 \text{ ms}$ ✓

---

### Solution 1.3 (Advanced)

**Given:** $D = 1200 \text{ baud}$, $L = 16$.

**Solution:**

a) **Bit rate:**
$R = \log_2(L)\, D = 4 \times 1200 = 4800 \text{ bits/s}$.

b) **Time to transmit 9600 bits:**
$T = \frac{n}{R} = \frac{9600}{4800} = 2 \text{ s}$.

c) **Number of dimensions in $T_0 = 0.5 \text{ s}$:**
$N = D \times T_0 = 1200 \times 0.5 = 600$ dimensions (symbols).

d) **Baud rate with $L = 4$:**
$D' = \frac{R}{\log_2(4)} = \frac{4800}{2} = 2400 \text{ baud}$.
The baud rate **doubles** (factor $\frac{\log_2 16}{\log_2 4} = 2$), since each symbol now carries 2 bits instead of 4.

---

## Exercise Set 2: Detection Using the Orthogonal Series Coefficients

### Solution 2.1 (Basic)

**Solution:**

a) **Detection formula:**
$$w_k = \frac{1}{K_k} \int_0^{T_0} w(t)\varphi_k^*(t)\, dt \; ; \quad k = 1, \ldots, N$$
where $K_k = \int_{-\infty}^{+\infty} |\varphi_k(t)|^2 dt$ is the energy of the $k$-th orthogonal function, $w(t)$ is the received waveform, and the $\varphi_k(t)$ are the known orthogonal functions used at the transmitter.

b) This procedure is called **matched filter detection**.

c) It is the optimal way to detect the data when the received signal is corrupted by **white additive noise**.

---

### Solution 2.2 (Intermediate)

**Given:** Rectangular pulses, $T_s = 2 \text{ ms}$, $w(t) = 1 + 0.2\sin(2\pi t/T_s)$ for $2T_s \le t < 3T_s$.

**Solution:**

a) **Constant $K_k$:**
$K_k = \int_{-\infty}^{+\infty} |\varphi_k(t)|^2 dt = \int_{(k-1)T_s}^{kT_s} (1)^2 dt = T_s = 2 \text{ ms}$.

b) **Integration (matched filter) result:**
$\varphi_3(t) = 1$ only for $2T_s \le t < 3T_s$, and it is real ($\varphi_3^* = \varphi_3$):
$$w_3 = \frac{1}{T_s} \int_{2T_s}^{3T_s} \left[1 + 0.2 \sin\left(\frac{2\pi t}{T_s}\right)\right] dt = \frac{1}{T_s}\left[T_s - \frac{0.2\, T_s}{2\pi}\left(\cos 6\pi - \cos 4\pi\right)\right] = 1 - 0 = 1$$
The sinusoidal disturbance completes exactly one period over the symbol interval, so it integrates to zero and the correct value $w_3 = 1$ is obtained.

c) **Sampling at $t = 2.25\,T_s$:**
$$w(2.25\,T_s) = 1 + 0.2 \sin(2\pi \times 2.25) = 1 + 0.2 \sin(4.5\pi) = 1 + 0.2 \times 1 = 1.2$$

d) **Comparison:**
The **integration** (orthogonal series coefficient) method is more robust. It averages the received waveform over the whole symbol interval, so zero-mean disturbances are averaged out. Simple sampling only looks at one instant and picks up the full value of the disturbance at that instant (here a $20\%$ error).

---

### Solution 2.3 (Advanced)

**Solution:**

a) **Rectangular pulses:**
$\varphi_k(t) = 1$ for $(k-1)T_s \le t < kT_s$ and $0$ elsewhere.

- If $j \ne k$, the two pulses occupy **disjoint** time intervals, so $\varphi_j(t)\varphi_k(t) = 0$ for all $t$ and the integral is $0$.
- If $j = k$: $\int_{(k-1)T_s}^{kT_s} (1)^2 dt = T_s$.

Therefore $\int \varphi_j(t)\varphi_k^*(t)\, dt = T_s\,\delta_{jk}$ ✓

b) **Sinc pulses:**
Using the time-shift property, the Fourier transform of $\varphi_k(t)$ is:
$$\Phi_k(f) = T_s \text{rect}(T_s f)\, e^{-j2\pi (k - \frac{1}{2}) T_s f}$$
By Parseval's theorem:
$$\int_{-\infty}^{+\infty} \varphi_j(t)\varphi_k^*(t)\, dt = \int_{-\infty}^{+\infty} \Phi_j(f)\Phi_k^*(f)\, df = T_s^2 \int_{-\frac{1}{2T_s}}^{+\frac{1}{2T_s}} e^{-j2\pi (j-k) T_s f}\, df$$
Let $m = j - k$:
- If $m = 0$: $T_s^2 \times \frac{1}{T_s} = T_s$.
- If $m \ne 0$:
$$T_s^2 \cdot \frac{\sin(\pi m)}{\pi m T_s} = T_s\, \text{sinc}(m) = 0 \quad \text{(since } m \text{ is a non-zero integer)}$$

Therefore $\int \varphi_j(t)\varphi_k^*(t)\, dt = T_s\, \text{sinc}(j-k) = T_s\,\delta_{jk}$ ✓
*(For $j = k$, this matches the value $K_k = T_s$ derived in the lecture.)*

---

## Exercise Set 3: Bandwidth Estimation

### Solution 3.1 (Basic)

**Given:** $D = 9600 \text{ baud}$.

**Solution:**

a) **Lower bound:**
From the dimensionality theorem:
$B \ge \frac{N}{2T_0} = \frac{1}{2}D = \frac{9600}{2} = 4800 \text{ Hz}$.

b) The lower bound is achieved by **sinc-type pulses**.

c) Rectangular pulses require **more** bandwidth than the lower bound. Their null-to-null bandwidth is $\frac{1}{T_s} = D = 9600 \text{ Hz}$, which is twice the bound.

---

### Solution 3.2 (Intermediate)

**Given:** Binary, $R = 64 \text{ kbits/s}$.

**Solution:**
For binary signaling $D = R = 64 \text{ kbaud}$, so $T_s = T_b = \frac{1}{64000} \approx 15.6 \mu\text{s}$.

a) **Rectangular pulses (null-to-null):**
$B = \frac{1}{T_s} = 64 \text{ kHz}$.

b) **Sinc pulses (absolute):**
$B = \frac{1}{2T_s} = 32 \text{ kHz}$.

c) **Comparison with the lower bound:**
$B_{L.B.} = \frac{1}{2}D = 32 \text{ kHz}$.
The sinc pulses achieve the bound exactly. The rectangular pulses require $\frac{64}{32} = $ **2 times** the lower bound.

---

### Solution 3.3 (Advanced)

**Given:** $B = 3 \text{ kHz}$.

**Solution:**

a) **Maximum baud rate (sinc pulses):**
The absolute bandwidth is $\frac{1}{2}D \le B$, so:
$D_{max} = 2B = 6000 \text{ baud}$.

b) **Maximum binary bit rate:**
$R = D = 6 \text{ kbits/s}$.

c) **Minimum $L$ for $R = 24 \text{ kbits/s}$ (sinc):**
$\log_2(L) \ge \frac{R}{D_{max}} = \frac{24000}{6000} = 4 \Rightarrow L \ge 2^4 = 16$.
Minimum $L = 16$.

d) **Rectangular pulses:**
The null-to-null bandwidth is $D \le B$, so $D_{max} = 3000 \text{ baud}$.
$\log_2(L) \ge \frac{24000}{3000} = 8 \Rightarrow L \ge 2^8 = 256$.
Minimum $L = 256$, which shows how much more bandwidth-efficient sinc pulses are.

---

## Exercise Set 4: Binary Signaling Waveforms

### Solution 4.1 (Basic)

**Given:** Sequence $10110010$, unipolar, rectangular pulses, $T_s = 0.5 \text{ ms}$.

**Solution:**

a) **Parameters:**
$N = n = 8$
$T_0 = N T_s = 8 \times 0.5 \text{ ms} = 4 \text{ ms}$
$D = R = \frac{1}{T_s} = 2 \text{ kbaud} = 2 \text{ kbits/s}$

b) **Expression of $w(t)$:**
$$w(t) = \sum_{k=1}^{8} w_k\, \text{rect}\left(\frac{t - (k - \frac{1}{2})T_s}{T_s}\right)$$
with $w_1 = 1, w_2 = 0, w_3 = 1, w_4 = 1, w_5 = 0, w_6 = 0, w_7 = 1, w_8 = 0$. That is:
$$w(t) = \varphi_1(t) + \varphi_3(t) + \varphi_4(t) + \varphi_7(t)$$

c) **Intervals where $w(t) = 1$:**
Symbol $k$ occupies $[(k-1)T_s, kT_s)$:
- $k = 1$: $[0, 0.5) \text{ ms}$
- $k = 3, 4$: $[1, 2) \text{ ms}$
- $k = 7$: $[3, 3.5) \text{ ms}$

$w(t) = 0$ everywhere else in $[0, 4) \text{ ms}$.

d) **Sketch:**
```
w(t)
 1 |‾‾‾|   |‾‾‾‾‾‾‾|       |‾‾‾|
   |   |   |       |       |   |
 0 |   |___|       |_______|   |___
   0  0.5  1      2       3  3.5   4   t (ms)
```

---

### Solution 4.2 (Intermediate)

**Given:** Sinc pulses, $T_s = 0.5 \text{ ms}$, sequence $10110010$.

**Solution:**

a) **Mid-symbol sampling:**
At $t_m = (m - \frac{1}{2})T_s$:
$$w(t_m) = \sum_{k=1}^{8} w_k\, \text{sinc}\left(\frac{(m - \frac{1}{2})T_s - (k - \frac{1}{2})T_s}{T_s}\right) = \sum_{k=1}^{8} w_k\, \text{sinc}(m - k)$$
Since $\text{sinc}(0) = 1$ and $\text{sinc}(i) = 0$ for any non-zero integer $i$, only the term $k = m$ remains:
$w(t_m) = w_m$ ✓

b) **Value at $t = 0$:**
$$w(0) = \sum_{k} w_k\, \text{sinc}\left(-(k - \tfrac{1}{2})\right) = \text{sinc}(0.5) + \text{sinc}(2.5) + \text{sinc}(3.5) + \text{sinc}(6.5)$$
(only $k = 1, 3, 4, 7$ have $w_k = 1$). Using $\text{sinc}(x) = \frac{\sin(\pi x)}{\pi x}$:
- $\text{sinc}(0.5) = \frac{2}{\pi} \approx 0.6366$
- $\text{sinc}(2.5) = \frac{2}{5\pi} \approx 0.1273$
- $\text{sinc}(3.5) = -\frac{2}{7\pi} \approx -0.0909$
- $\text{sinc}(6.5) = \frac{2}{13\pi} \approx 0.0490$

$w(0) \approx 0.722$.
This is **not** equal to $w_1 = 1$. Away from the mid-symbol instants, the tails of the other sinc pulses do not vanish and interfere with the current symbol. This is why sinc pulses must be sampled exactly at the middle of each symbol interval.

c) **Bandwidth:**
Sinc pulses: $B = \frac{1}{2T_s} = \frac{1}{1 \text{ ms}} = 1 \text{ kHz}$ (absolute bandwidth).
Rectangular pulses (Exercise 4.1): $B = \frac{1}{T_s} = 2 \text{ kHz}$ (null-to-null).
The sinc pulses need **half** the bandwidth.

---

### Solution 4.3 (Advanced)

**Given:** Sampling instant $t = 3.5\,T_s + 0.1\,T_s = 3.6\,T_s$.

**Solution:**

a) **Sampled value:**
$$w(3.6\,T_s) = \sum_{k} w_k\, \text{sinc}(3.6 - (k - 0.5)) = \sum_{k} w_k\, \text{sinc}(4.1 - k)$$
For $k = 1, 3, 4, 7$:
- $k = 1$: $\text{sinc}(3.1) = \frac{\sin(3.1\pi)}{3.1\pi} = \frac{-0.3090}{9.7389} \approx -0.0317$
- $k = 3$: $\text{sinc}(1.1) = \frac{\sin(1.1\pi)}{1.1\pi} = \frac{-0.3090}{3.4558} \approx -0.0894$
- $k = 4$: $\text{sinc}(0.1) = \frac{\sin(0.1\pi)}{0.1\pi} = \frac{0.3090}{0.3142} \approx 0.9836$
- $k = 7$: $\text{sinc}(-2.9) = \frac{\sin(2.9\pi)}{2.9\pi} = \frac{0.3090}{9.1106} \approx 0.0339$

$w(3.6\,T_s) \approx -0.0317 - 0.0894 + 0.9836 + 0.0339 \approx 0.896$.

b) **Relative error:**
$\frac{|0.896 - 1|}{1} \approx 10.4\%$.

c) **Rectangular pulses:**
**No error.** With rectangular pulses, $w(t)$ is constant over the entire symbol interval $[3T_s, 4T_s)$. Since $3.6\,T_s$ is still inside that interval, the sample is exactly $w_4 = 1$. Rectangular pulses can be sampled **anywhere** within the symbol interval.

d) **Advantages:**
- **Rectangular pulses:** robust to timing errors (sample anywhere in the interval), and simple to generate since they are time-limited.
- **Sinc pulses:** require the **minimum bandwidth** $\frac{1}{2}D$ (they achieve the dimensionality-theorem lower bound), i.e., half the bandwidth of rectangular pulses.

---

## Exercise Set 5: Multilevel Signaling and Gray Mapping

### Solution 5.1 (Basic)

**Given:** Sequence $11011000$, $L = 4$ Gray mapping.

**Solution:**

a) **Mapping:**
Group the bits in pairs ($l = \log_2 4 = 2$): $11 \,|\, 01 \,|\, 10 \,|\, 00$
$w_1 = +3, \quad w_2 = -3, \quad w_3 = +1, \quad w_4 = -1$

b) **Number of symbols:**
$N = \frac{n}{l} = \frac{8}{2} = 4$ symbols, compared with $N = 8$ for binary signaling: **half** as many symbols.

---

### Solution 5.2 (Intermediate)

**Solution:**

a) **Gray property:**
The bit sequences assigned to any two **adjacent** levels differ in **exactly one bit**:
$-3 \,(01) \leftrightarrow -1 \,(00) \leftrightarrow +1 \,(10) \leftrightarrow +3 \,(11)$

b) **Error $+1 \to +3$ (Gray):**
$10 \to 11$: only **1 bit error**.

c) **Error $+1 \to -1$ (natural binary):**
$10 \to 01$: both bits differ, so **2 bit errors**.
Since noise most often causes a level to be mistaken for an *adjacent* one, Gray mapping keeps the number of bit errors to a minimum.

d) **Gray mapping for $L = 8$ ($l = 3$ bits):**

| Output Level (V) | Binary Input ($l = 3$ bits) |
|:---:|:---:|
| +7 | 100 |
| +5 | 101 |
| +3 | 111 |
| +1 | 110 |
| -1 | 010 |
| -3 | 011 |
| -5 | 001 |
| -7 | 000 |

Each pair of adjacent levels differs in exactly one bit. *(Other valid Gray mappings exist.)*

---

### Solution 5.3 (Advanced)

**Given:** $101100111000$, $n = 12$, $T_0 = 6 \text{ ms}$, $L = 4$.

**Solution:**

a) **Symbols:**
Pairs: $10 \,|\, 11 \,|\, 00 \,|\, 11 \,|\, 10 \,|\, 00$
$w_1 = +1, \; w_2 = +3, \; w_3 = -1, \; w_4 = +3, \; w_5 = +1, \; w_6 = -1$

b) **Durations and rates:**
$N = \frac{12}{2} = 6$
$T_s = \frac{T_0}{N} = \frac{6 \text{ ms}}{6} = 1 \text{ ms}$
$T_b = \frac{T_0}{n} = \frac{6 \text{ ms}}{12} = 0.5 \text{ ms}$
$D = \frac{1}{T_s} = 1 \text{ kbaud}$
$R = \frac{1}{T_b} = 2 \text{ kbits/s}$ (check: $R = \log_2(4) \times D = 2 \times 1 = 2$ kbits/s ✓)

c) **Bandwidths:**
Rectangular (null-to-null): $B = \frac{1}{T_s} = 1 \text{ kHz}$
Sinc (absolute): $B = \frac{1}{2T_s} = 500 \text{ Hz}$

d) **Binary signaling (same $T_0$):**
$T_s = T_b = 0.5 \text{ ms}$:
Rectangular: $B = \frac{1}{0.5 \text{ ms}} = 2 \text{ kHz}$
Sinc: $B = \frac{1}{1 \text{ ms}} = 1 \text{ kHz}$
The binary signal needs $\log_2(L) = 2$ times more bandwidth.

e) **Sampling at $t = 2.7 \text{ ms}$:**
With $T_s = 1 \text{ ms}$, the instant $2.7 \text{ ms}$ lies in the third interval $[2, 3) \text{ ms}$, so the detected symbol is $w_3 = -1$. From the Gray mapping, $-1 \to$ bits **$00$**.

---

## Exercise Set 6: Binary vs. Multilevel Bandwidth Comparison

### Solution 6.1 (Basic)

**Given:** $B_{Binary} = 1.2 \text{ MHz}$.

**Solution:**
Using $B_{Multilevel} = \frac{B_{Binary}}{\log_2(L)}$:

a) $L = 4$: $B = \frac{1.2 \text{ MHz}}{2} = 600 \text{ kHz}$
b) $L = 8$: $B = \frac{1.2 \text{ MHz}}{3} = 400 \text{ kHz}$
c) $L = 16$: $B = \frac{1.2 \text{ MHz}}{4} = 300 \text{ kHz}$

---

### Solution 6.2 (Intermediate)

**Given:** $M = 256$ messages, one message per $T_0 = 1 \text{ ms}$, sinc pulses.

**Solution:**

a) **Bits per message and bit rate:**
$n = \log_2(256) = 8$ bits/message
$R = \frac{8 \text{ bits}}{1 \text{ ms}} = 8 \text{ kbits/s}$

b) **Table** (with $N = n/l$, $D = N/T_0$, absolute bandwidth $= D/2$):

| $L$ | $l = \log_2 L$ | $N$ (symbols/message) | $D$ (baud) | Absolute bandwidth (Hz) |
|:---:|:---:|:---:|:---:|:---:|
| 2 | 1 | 8 | 8000 | 4000 |
| 4 | 2 | 4 | 4000 | 2000 |
| 16 | 4 | 2 | 2000 | 1000 |
| 256 | 8 | 1 | 1000 | 500 |

With $L = 256$, each message is sent as a **single** symbol, so the bandwidth is reduced by a factor of 8 compared with binary signaling.

---

### Solution 6.3 (Advanced)

**Given:** Levels equally spaced in $[-A, +A]$, $A = 3 \text{ V}$.

**Solution:**

a) **Level spacing:**
$L$ levels spanning a total range of $2A$ have $L - 1$ gaps:
$$\Delta = \frac{2A}{L - 1}$$

b) **Numerical values:**
$L = 4$: $\Delta = \frac{6}{3} = 2 \text{ V}$ (levels $-3, -1, +1, +3$ ✓)
$L = 16$: $\Delta = \frac{6}{15} = 0.4 \text{ V}$

c) **Why $L$ cannot grow indefinitely:**
Increasing $L$ reduces the bandwidth only logarithmically ($\propto 1/\log_2 L$), but for a fixed peak amplitude the levels get closer together ($\Delta \propto 1/(L-1)$): going from $L = 4$ to $L = 16$ halves the bandwidth but shrinks the spacing by a factor of 5. Closely spaced levels are much easier for noise to confuse, so more detection errors occur. Keeping the same spacing (same noise immunity) would require increasing the amplitude roughly in proportion to $L - 1$, i.e., much more transmitted power. Multilevel signaling therefore **trades bandwidth for power / noise immunity**.

---
*Generated for Lecture 7 - Digital Signaling*

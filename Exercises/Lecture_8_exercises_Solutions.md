# Lecture 8 Exercises - Complete Solutions

This document provides detailed solutions to all problems in `Lecture_8_exercises.md`.

---

## Exercise Set 1: Differential Encoding

### Solution 1.1 (Basic)

**Given:** $d_n = 1011001$, reference bit $e_0 = 0$, $e_n = d_n \oplus e_{n-1}$.

**Solution:**

a) **Encoding:**
Each encoded bit is the modulo-2 sum of the present information bit and the previous encoded bit:

$e_1 = 1 \oplus 0 = 1$

$e_2 = 0 \oplus 1 = 1$

$e_3 = 1 \oplus 1 = 0$

$e_4 = 1 \oplus 0 = 1$

$e_5 = 0 \oplus 1 = 1$

$e_6 = 0 \oplus 1 = 1$

$e_7 = 1 \oplus 1 = 0$

| Input sequence $d_n$ | | 1 | 0 | 1 | 1 | 0 | 0 | 1 |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| Encoded sequence $e_n$ | **0** | 1 | 1 | 0 | 1 | 1 | 1 | 0 |

The transmitted sequence (reference bit first) is $01101110$.

b) **Block diagram:**

```
 d_n  -->( + )-----------+-----> e_n --> [ Line encoder circuit ]
           ^   modulo-2  |
           |   adder     |
           |             |
           +--[ Delay Tb ]<--+
             e_(n-1)
```

- **Modulo-2 adder (XOR gate):** computes $e_n = d_n \oplus e_{n-1}$.
- **Delay $T_b$:** stores the previous encoded bit $e_{n-1}$ for one bit interval and feeds it back to the adder.
- **Line encoder circuit:** converts the encoded bits into the waveform sent on the channel.

c) **Purpose:**
When serial data passes through many circuits along a channel, the waveform is often **unintentionally inverted**. Differential encoding makes the data independent of the polarity of the received signal, since the information is carried by the *changes* between adjacent bits rather than by the bit values themselves.

---

### Solution 1.2 (Intermediate)

**Given:** $d_n = 0110100$.

**Solution:**

a) **Reference bit $e_0 = 1$:**

| $d_n$ | | 0 | 1 | 1 | 0 | 1 | 0 | 0 |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| $e_n$ | **1** | 1 | 0 | 1 | 1 | 0 | 0 | 0 |

Transmitted sequence: $11011000$.

b) **Reference bit $e_0 = 0$:**

| $d_n$ | | 0 | 1 | 1 | 0 | 1 | 0 | 0 |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| $e_n$ | **0** | 0 | 1 | 0 | 0 | 1 | 1 | 1 |

Transmitted sequence: $00100111$.

c) **Relation:**
The two sequences are the **complements** of each other: every bit of $11011000$ is inverted in $00100111$. Changing the reference bit is equivalent to inverting the whole encoded stream.

d) **Same decoded bits:**
The decoder only compares adjacent bits ($\tilde{d}_n = \tilde{e}_n \oplus \tilde{e}_{n-1}$). Inverting both bits of a pair does not change whether they are equal or different, so both sequences decode to $0110100$. This is exactly the same property that makes differential coding robust to polarity inversion.

---

### Solution 1.3 (Advanced)

**Solution:**

a) **Closed form:**
Apply the encoding rule repeatedly:

$e_1 = e_0 \oplus d_1$

$e_2 = e_1 \oplus d_2 = e_0 \oplus d_1 \oplus d_2$

$e_3 = e_2 \oplus d_3 = e_0 \oplus d_1 \oplus d_2 \oplus d_3$

Continuing in the same way (modulo-2 addition is associative), we get:

$$e_n = e_0 \oplus d_1 \oplus d_2 \oplus \cdots \oplus d_n$$

b) **Direct computation of $e_7$:**

$$e_7 = 0 \oplus 1 \oplus 0 \oplus 1 \oplus 1 \oplus 0 \oplus 0 \oplus 1$$

There are four ones, and an even number of ones adds up to $0$ in modulo-2 arithmetic, so $e_7 = 0$. This matches the table of Exercise 1.1. ✓

c) **Rule:**
$e_n = e_0$ if the number of ones among $d_1, \ldots, d_n$ is **even**, and $e_n = \overline{e_0}$ if it is **odd**. In other words, each information bit equal to $1$ toggles the encoded level, and each $0$ keeps it unchanged.

---

## Exercise Set 2: Differential Decoding

### Solution 2.1 (Basic)

**Given:** $\tilde{e}_n = 01101110$ (reference bit first), $\tilde{d}_n = \tilde{e}_n \oplus \tilde{e}_{n-1}$.

**Solution:**

a) **No inversion:**

| Received sequence $\tilde{e}_n$ | 0 | 1 | 1 | 0 | 1 | 1 | 1 | 0 |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| Decoded sequence $\tilde{d}_n$ | | 1 | 0 | 1 | 1 | 0 | 0 | 1 |

b) **With polarity inversion:**

| Received sequence $\tilde{e}_n$ | 1 | 0 | 0 | 1 | 0 | 0 | 0 | 1 |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| Decoded sequence $\tilde{d}_n$ | | 1 | 0 | 1 | 1 | 0 | 0 | 1 |

c) **Comparison:**
In both cases, the decoded sequence is $1011001$, which is exactly the information sequence of Exercise 1.1. The polarity inversion has no effect on the decoded data.

---

### Solution 2.2 (Intermediate)

**Given:** Transmitted $e_n = 01101110$ ($e_0$ to $e_7$), information bits $d_n = 1011001$.

**Solution:**

a) **Error on $e_4$:**
The fifth bit changes from $1$ to $0$:

| Received $\tilde{e}_n$ | 0 | 1 | 1 | 0 | **0** | 1 | 1 | 0 |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| Decoded $\tilde{d}_n$ | | 1 | 0 | 1 | **0** | **1** | 0 | 1 |
| Correct $d_n$ | | 1 | 0 | 1 | 1 | 0 | 0 | 1 |

The decoded sequence is $1010101$. The bits $\tilde{d}_4$ and $\tilde{d}_5$ are wrong: **2 decoded errors**.

b) **Error on $e_7$:**
The received sequence is $01101111$, which decodes to $1011000$. Only $\tilde{d}_7$ is wrong: **1 decoded error**.

c) **Error on $e_0$ (reference bit):**
The received sequence is $11101110$, which decodes to $0011001$. Only $\tilde{d}_1$ is wrong: **1 decoded error**.

d) **General rule:**
The received bit $\tilde{e}_k$ appears in **two** decoding equations:

$\tilde{d}_k = \tilde{e}_k \oplus \tilde{e}_{k-1}$

$\tilde{d}_{k+1} = \tilde{e}_{k+1} \oplus \tilde{e}_k$

So a single error on $\tilde{e}_k$ corrupts **two** decoded bits, $\tilde{d}_k$ and $\tilde{d}_{k+1}$. The only exceptions are the reference bit (used only in $\tilde{d}_1$) and the last bit (used only in $\tilde{d}_N$), which cause one decoded error each.

---

### Solution 2.3 (Advanced)

**Solution:**

a) **Truth table:**

| $a$ | $b$ | $\overline{a}$ | $\overline{b}$ | $\overline{a} \oplus \overline{b}$ | $a \oplus b$ |
|:---:|:---:|:---:|:---:|:---:|:---:|
| 0 | 0 | 1 | 1 | 0 | 0 |
| 0 | 1 | 1 | 0 | 1 | 1 |
| 1 | 0 | 0 | 1 | 1 | 1 |
| 1 | 1 | 0 | 0 | 0 | 0 |

The last two columns are identical, so $\overline{a} \oplus \overline{b} = a \oplus b$. ✓

b) **Full inversion:**
If all received bits are inverted, then $\tilde{e}_n = \overline{e_n}$ and $\tilde{e}_{n-1} = \overline{e_{n-1}}$. Using the identity of part (a):

$$\tilde{d}_n = \overline{e_n} \oplus \overline{e_{n-1}} = e_n \oplus e_{n-1} = (d_n \oplus e_{n-1}) \oplus e_{n-1} = d_n$$

The decoded bits are unchanged. ✓

c) **Inversion starting at $e_4$:**
The bits $e_4$ to $e_7$ ($1110$) are inverted to $0001$:

| Received $\tilde{e}_n$ | 0 | 1 | 1 | 0 | 0 | 0 | 0 | 1 |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| Decoded $\tilde{d}_n$ | | 1 | 0 | 1 | **0** | 0 | 0 | 1 |
| Correct $d_n$ | | 1 | 0 | 1 | 1 | 0 | 0 | 1 |

The decoded sequence is $1010001$. Only **one** bit, $\tilde{d}_4$, is wrong.

d) **Explanation:**
- For $n \le 3$, both bits are received correctly, so $\tilde{d}_n = d_n$.
- For $n \ge 5$, **both** bits of the pair are inverted, so by the identity of part (a), $\tilde{d}_n = d_n$.
- For $n = 4$, only $\tilde{e}_4$ is inverted, while $\tilde{e}_3$ is not:

$$\tilde{d}_4 = \overline{e_4} \oplus e_3 = \overline{e_4 \oplus e_3} = \overline{d_4}$$

So a polarity inversion that starts in the middle of the transmission costs only **one** decoded bit, at the instant where the inversion begins.

---

## Exercise Set 3: Regenerative Repeaters

### Solution 3.1 (Basic)

**Solution:**

a) **Need for repeaters:**
When a digital signal is transmitted over a channel, it is **attenuated, distorted and corrupted by noise**. Over long lines, these effects become so strong that the data cannot be recovered at the receiver. Repeaters must therefore be placed in cascade along the line.

b) **Drawback of amplifiers:**
An amplifier increases the level of the signal, but it also **amplifies the noise** added to the signal, so the noise accumulates along the line. Analog signals can only be amplified because their amplitude can take any value: there is no finite set of known levels to regenerate them from.

c) **Blocks of a regenerative repeater:**
- **Amplifier:** increases the amplitude of the low-level input signal.
- **Filter:** reduces the level of noise in the signal.
- **Bit synchronizer (timing circuit):** generates a clock signal at the desired frequency, which sets the sampling instants.
- **Sample-and-hold:** produces a sample value that is held constant for a bit interval $T_b$.
- **Comparator:** compares the sample with the threshold $V_T$. If the sample exceeds $V_T$, a binary 1 is produced. Otherwise, a binary 0 is produced.

---

### Solution 3.2 (Intermediate)

**Given:** Transmitted bits $101010$, polar levels $\pm 1 \text{ V}$, $V_T = 0 \text{ V}$.

**Solution:**

a) **Regenerated bits:**
Each sample is compared with $V_T = 0$: a sample above $0$ gives a 1, otherwise a 0.

| Bit index | 1 | 2 | 3 | 4 | 5 | 6 |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| Sample value (V) | 0.8 | -0.3 | -0.1 | -1.2 | 0.05 | 0.2 |
| Regenerated bit | 1 | 0 | 0 | 0 | 1 | 1 |
| Transmitted bit | 1 | 0 | 1 | 0 | 1 | 0 |

The regenerated sequence is $100011$.

b) **Errors:**
Bits **3** and **6** are regenerated in error (2 errors out of 6). In both cases, the noise pushed the sample to the wrong side of the threshold.

c) **Hold time and sampling instants:**
Each sample is held constant for one bit interval $T_b$. The sampling instants are set by the clock produced by the **bit synchronizer**.

d) **Bit 5:**
The sample $0.05 \text{ V}$ is only slightly above the threshold, compared with the nominal level of $+1 \text{ V}$. A small additional amount of noise would have pushed it below $V_T$ and caused an error. The decision was correct, but with almost no **noise margin**.

---

### Solution 3.3 (Advanced)

**Given:** $m = 3$, independent errors with probability $P_e$ at each repeater.

**Solution:**

a) **Error patterns** (C = correct, W = wrong):

| Repeater 1 | Repeater 2 | Repeater 3 | Number of errors | Output bit |
|:---:|:---:|:---:|:---:|:---:|
| C | C | C | 0 | Correct |
| W | C | C | 1 | **Wrong** |
| C | W | C | 1 | **Wrong** |
| C | C | W | 1 | **Wrong** |
| W | W | C | 2 | Correct |
| W | C | W | 2 | Correct |
| C | W | W | 2 | Correct |
| W | W | W | 3 | **Wrong** |

Each wrong decision flips the bit. Two flips cancel each other, so the output bit is wrong only when an **odd** number of repeaters make errors (1 or 3 here).

b) **Exact expression:**

$$P = \binom{3}{1} P_e (1 - P_e)^2 + \binom{3}{3} P_e^3 = 3 P_e (1 - P_e)^2 + P_e^3$$

c) **Numerical value for $P_e = 0.1$:**

$$P = 3 (0.1)(0.9)^2 + (0.1)^3 = 0.243 + 0.001 = 0.244$$

The approximation gives $m P_e = 3 \times 0.1 = 0.3$, which overestimates $P$ by about $23\%$. The approximation is poor here because $P_e = 0.1$ is not small: the factor $(1 - P_e)^{m-1} = 0.81$ is far from $1$.

---

## Exercise Set 4: Probability of Error of Cascaded Repeaters

### Solution 4.1 (Basic)

**Given:** $m = 20$, $P_e = 10^{-6}$.

**Solution:**

a) **Approximate probability of error:**
$P \approx m P_e = 20 \times 10^{-6} = 2 \times 10^{-5}$.

b) **All repeaters correct:**
$(1 - P_e)^m = (1 - 10^{-6})^{20} \approx 0.99998$.

c) **Justification:**
Since $P_e \ll 1$, we have $(1 - P_e)^{m-1} \approx 1$, and the terms with $P_e^3, P_e^5, \ldots$ are negligible (the second term is of the order of $\binom{20}{3} \times 10^{-18} \approx 10^{-15}$). Only the first term $m P_e$ is significant.

---

### Solution 4.2 (Intermediate)

**Given:** Line length $500 \text{ km}$, one repeater every $5 \text{ km}$, $P \le 10^{-6}$.

**Solution:**

a) **Number of repeaters:**
Repeaters are located at $5, 10, 15, \ldots, 500 \text{ km}$, the last one being the receiver:
$m = \frac{500}{5} = 100$.

b) **Maximum $P_e$:**
Using $P \approx m P_e$:

$$P_e \le \frac{P}{m} = \frac{10^{-6}}{100} = 10^{-8}$$

c) **Exactly 2 errors:**

$$P_2 = \binom{100}{2} P_e^2 (1 - P_e)^{98} \approx 4950 \times (10^{-8})^2 = 4.95 \times 10^{-13}$$

When exactly 2 repeaters make errors, the bit is flipped twice and arrives **correct** at the output, since an even number of errors cancel each other.

---

### Solution 4.3 (Advanced)

**Solution:**

a) **$m = 10$, $P_e = 0.01$:**

First term ($i = 1$):

$$10 \times 0.01 \times (0.99)^9 = 0.1 \times 0.91352 = 0.091352$$

Second term ($i = 3$):

$$\binom{10}{3} (0.01)^3 (0.99)^7 = 120 \times 10^{-6} \times 0.93207 = 1.118 \times 10^{-4}$$

Third term ($i = 5$):

$$\binom{10}{5} (0.01)^5 (0.99)^5 = 252 \times 10^{-10} \times 0.95099 = 2.40 \times 10^{-8}$$

Exact value: $P \approx 0.091352 + 0.000112 + 0.00000002 \approx 0.0915$.

Approximation: $m P_e = 0.1$.

Relative error: $\frac{0.1 - 0.0915}{0.0915} \approx 9.3\%$.

b) **$m = 50$, $P_e = 0.01$:**
The approximation gives $m P_e = 0.5$, while the exact value is $0.318$. The relative error is $\frac{0.5 - 0.318}{0.318} \approx 57\%$.

**Conclusion:** the approximation $P \approx m P_e$ is valid only when $m P_e \ll 1$. As $m P_e$ grows, the factor $(1 - P_e)^{m-1}$ is no longer close to $1$ and the approximation overestimates $P$. Note that $m P_e$ can even exceed $1$, which is impossible for a probability.

c) **Closed form:**
Let $p = P_e$ and $q = 1 - P_e$. By the binomial theorem:

$$(q + p)^m = \sum_{i=0}^{m} \binom{m}{i} p^i q^{m-i}$$

$$(q - p)^m = \sum_{i=0}^{m} (-1)^i \binom{m}{i} p^i q^{m-i}$$

Subtracting the second expansion from the first, the terms with even $i$ cancel and the terms with odd $i$ are doubled:

$$(q + p)^m - (q - p)^m = 2 \sum_{i \text{ odd}} \binom{m}{i} p^i q^{m-i} = 2P$$

Since $q + p = 1$ and $q - p = 1 - 2P_e$:

$$P = \frac{1 - (1 - 2P_e)^m}{2}$$

d) **Verification:**

For $m = 10$: $(0.98)^{10} = 0.81707$, so $P = \frac{1 - 0.81707}{2} = 0.09146$ ✓

For $m = 50$: $(0.98)^{50} = 0.36417$, so $P = \frac{1 - 0.36417}{2} = 0.31792$ ✓

---

## Exercise Set 5: Combined Problems

### Solution 5.1 (Intermediate)

**Given:** $m = 25$, $P_e = 2 \times 10^{-7}$, differential coding, one inverting amplifier on the line.

**Solution:**

a) **Error probability on the encoded bits:**
$P \approx m P_e = 25 \times 2 \times 10^{-7} = 5 \times 10^{-6}$.

b) **Effect of the inversion:**
**No decoding errors.** The inversion affects all the bits that follow the inverting amplifier, so every received pair $(\tilde{e}_n, \tilde{e}_{n-1})$ is either fully inverted or not inverted at all. Since $\overline{a} \oplus \overline{b} = a \oplus b$, the differential decoder output is unchanged.

c) **Error probability on the decoded bits:**
From Exercise 2.2, each isolated error on an encoded bit causes **two** errors on the decoded bits. When errors are rare, they are isolated, so the decoded bit error probability is approximately doubled:

$$P_{decoded} \approx 2P = 2 \times 5 \times 10^{-6} = 10^{-5}$$

d) **Why differential coding is still used:**
Without differential coding, a polarity inversion would invert **every** bit, giving a bit error rate close to $100\%$ until the inversion is detected. Doubling a small error probability (here from $5 \times 10^{-6}$ to $10^{-5}$) is a small price to pay for complete immunity to polarity inversion.

---
*Generated for Lecture 8 - Differential Coding and Regenerative Repeaters*

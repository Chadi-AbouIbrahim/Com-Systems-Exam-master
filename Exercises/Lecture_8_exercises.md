# Lecture 8 Exercises - Differential Coding and Regenerative Repeaters

These exercises cover the concepts from Lecture 8: Differential Encoding, Differential Decoding, Robustness to Polarity Inversion, Regenerative Repeaters, and the Probability of Error of Cascaded Repeaters.

---

## Exercise Set 1: Differential Encoding

### Exercise 1.1 (Basic)

The information bits $d_n = 1011001$ are differentially encoded using the rule $e_n = d_n \oplus e_{n-1}$, with a reference bit $e_0 = 0$.

a) Complete the following table:

| Input sequence $d_n$ | | 1 | 0 | 1 | 1 | 0 | 0 | 1 |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| Encoded sequence $e_n$ | **0** | | | | | | | |

b) Draw the block diagram of the differential encoder and name each block.

c) Why is differential encoding used in communication systems?

### Exercise 1.2 (Intermediate)

The information bits $d_n = 0110100$ are differentially encoded.

a) Find the encoded sequence when the reference bit is $e_0 = 1$.

b) Find the encoded sequence when the reference bit is $e_0 = 0$.

c) What is the relation between the two encoded sequences?

d) Explain why the receiver decodes the same information bits in both cases.

### Exercise 1.3 (Advanced)

a) Starting from $e_n = d_n \oplus e_{n-1}$, show that the encoded bit can be written directly as:

$$e_n = e_0 \oplus d_1 \oplus d_2 \oplus \cdots \oplus d_n$$

b) Use this result to find $e_7$ for the sequence of Exercise 1.1 without computing the intermediate encoded bits. Check your answer against Exercise 1.1.

c) State a simple rule, based on the number of ones in $d_1, \ldots, d_n$, that tells whether $e_n$ is equal to the reference bit $e_0$.

---

## Exercise Set 2: Differential Decoding

### Exercise 2.1 (Basic)

The decoding rule is $\tilde d_n = \tilde e_n \oplus \tilde e_{n-1}$.

a) Decode the received sequence $\tilde e_n = 01101110$, where the first bit is the reference bit.

b) The same sequence is received with a polarity inversion, i.e., $\tilde e_n = 10010001$. Decode it.

c) Compare both results with the information bits of Exercise 1.1.

### Exercise 2.2 (Intermediate)

The encoded sequence $e_n = 01101110$ (reference bit first) is transmitted. Because of noise, a **single** bit is received in error.

a) The bit $e_4$ (the fifth bit, counting the reference bit as $e_0$) is received in error. Write the received sequence, decode it, and identify the decoded bits that are wrong.

b) Repeat part (a) if the error is on the last bit $e_7$ instead.

c) Repeat part (a) if the error is on the reference bit $e_0$ instead.

d) In general, how many decoded bits are affected by a single error on $\tilde e_k$? Explain using the decoding rule.

### Exercise 2.3 (Advanced)

a) Using a truth table, show that for any two bits $a$ and $b$:

$$\overline{a} \oplus \overline{b} = a \oplus b$$

b) Use this identity to prove that the decoder output is unchanged when **all** the received bits are inverted.

c) Now suppose that the channel starts inverting the signal in the middle of the transmission: the encoded sequence $e_n = 01101110$ is received correctly up to $e_3$, but $e_4, e_5, e_6, e_7$ are all inverted. Write the received sequence and decode it. How many decoded bits are wrong, and which ones?

d) Explain your result of part (c) using the identity of part (a).

---

## Exercise Set 3: Regenerative Repeaters

### Exercise 3.1 (Basic)

a) Why is it not possible to recover data over long lines without placing repeaters along the line?

b) What is the main drawback of using amplifiers as repeaters? Why can only amplifiers be used for analog signals?

c) List the blocks of a regenerative repeater and give the function of each block.

### Exercise 3.2 (Intermediate)

A polar binary signal uses the levels $+1 \text{ V}$ (binary 1) and $-1 \text{ V}$ (binary 0). The transmitted bits are $101010$. At a regenerative repeater, the sample-and-hold block produces the following noisy sample values:

| Bit index | 1 | 2 | 3 | 4 | 5 | 6 |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| Sample value (V) | 0.8 | -0.3 | -0.1 | -1.2 | 0.05 | 0.2 |

The comparator threshold is $V_T = 0 \text{ V}$.

a) Find the regenerated bit sequence at the output of the repeater.

b) How many bits are regenerated in error, and which ones?

c) For how long is each sample held constant by the sample-and-hold block, and which block decides the sampling instants?

d) Bit 5 was regenerated correctly. Why is it still considered a risky decision?

### Exercise 3.3 (Advanced)

Consider $m = 3$ regenerative repeaters (including the receiver end) in cascade. Each repeater makes an error with probability $P_e$, independently of the others.

a) List the $8$ possible error patterns (correct / wrong at each repeater) and identify the patterns that lead to a bit error at the output. Explain why.

b) Write the exact expression of the output probability of error $P$ in terms of $P_e$.

c) Compute $P$ exactly for $P_e = 0.1$ and compare it with the approximation $P \approx m P_e$.

---

## Exercise Set 4: Probability of Error of Cascaded Repeaters

### Exercise 4.1 (Basic)

A transmission line uses $m = 20$ regenerative repeaters (including the receiver end), each with an error probability $P_e = 10^{-6}$.

a) Compute the approximate probability of error at the output.

b) Compute the probability that all $20$ repeaters make correct decisions.

c) Why is the approximation of part (a) justified here?

### Exercise 4.2 (Intermediate)

A digital link of length $500 \text{ km}$ uses a regenerative repeater every $5 \text{ km}$. The receiver at the end of the line counts as the last repeater.

a) How many repeaters $m$ are there in cascade?

b) The overall probability of error must not exceed $10^{-6}$. What is the maximum allowed error probability $P_e$ for each repeater?

c) With this value of $P_e$, compute the probability that exactly $2$ repeaters make errors. What is the effect of such an event on the output bit?

### Exercise 4.3 (Advanced)

a) For $m = 10$ and $P_e = 0.01$, compute the first three non-zero terms of the exact series for $P$. Give the exact value of $P$ and compare it with $m P_e$. What is the relative error of the approximation?

b) Repeat the comparison for $m = 50$ and $P_e = 0.01$, given that the exact value is $P \approx 0.318$. What do you conclude about the validity of $P \approx m P_e$?

c) Using the binomial expansions of $(q + p)^m$ and $(q - p)^m$ with $p = P_e$ and $q = 1 - P_e$, show that the exact probability of error has the closed form:

$$P = \frac{1 - (1 - 2P_e)^m}{2}$$

d) Use this closed form to verify the exact values of parts (a) and (b).

---

## Exercise Set 5: Combined Problems

### Exercise 5.1 (Intermediate)

A differentially encoded binary stream is transmitted over a line with $m = 25$ regenerative repeaters, each with $P_e = 2 \times 10^{-7}$. One of the repeaters contains an inverting amplifier, so the signal arrives at the receiver with inverted polarity.

a) Compute the approximate probability of error $P$ on the received encoded bits $\tilde e_n$.

b) Does the polarity inversion cause any decoding errors? Justify.

c) Using your result from Exercise 2.2, estimate the probability of error on the decoded information bits $\tilde d_n$, assuming errors are rare and isolated.

d) Differential coding roughly doubles the bit error probability. Why is it still used?

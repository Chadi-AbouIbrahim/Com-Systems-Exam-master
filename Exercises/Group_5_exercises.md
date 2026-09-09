# Group 5 Exercises - Multiplexing


This document contains exercises and problems covering Time Division Multiplexing (TDM) from Lecture 11.


---


## Exercise Set 1: Multiplexing Basics


### Problem 1.1 (Basic)

Explain the concept of multiplexing:


a) What is multiplexing?

b) Why is multiplexing used in communication systems?

c) What are the two main types of multiplexing?

d) What is the key requirement for TDM to work?


---


### Problem 1.2 (Intermediate)

Compare Time Division Multiplexing (TDM) and Frequency Division Multiplexing (FDM):


a) How does TDM separate signals?

b) How does FDM separate signals?

c) Which requires synchronization? Why?

d) Which is more bandwidth efficient? Why?


---


### Problem 1.3 (Advanced)

A communication system needs to transmit 5 voice signals, each with bandwidth $B = 4$ kHz.


Compare TDM and FDM:

a) What bandwidth is required for TDM?

b) What bandwidth is required for FDM (assuming guard bands of 1 kHz between signals)?

c) Which is more efficient?

d) What are the trade-offs between the two?


---


## Exercise Set 2: TDM System Architecture


### Problem 2.1 (Basic)

Draw and label the block diagram of a TDM system showing:


a) The multiplexer (transmitter) components

b) The demultiplexer (receiver) components

c) The channel

d) The synchronization system


---


### Problem 2.2 (Intermediate)

A TDM system multiplexes 4 signals:


a) What is the function of the commutator?

b) What is the function of the decommutator?

c) Why must they be synchronized?

d) What happens if synchronization is lost?


---


### Problem 2.3 (Advanced)

Explain the operation of a TDM system step-by-step:


a) How are signals sampled at the transmitter?

b) How are samples interleaved?

c) How are samples separated at the receiver?

d) How is each signal reconstructed?


---


## Exercise Set 3: Commutator Operation


### Problem 3.1 (Basic)

A TDM system has:

- Number of signals: $K = 6$

- Sampling rate per signal: $f_s = 8$ kHz


Find:

a) The commutator rotation frequency

b) The frame period $T_f$

c) The time per slot $T_s$ (assuming no sync word)

d) The total sampling rate of the TDM signal


---


### Problem 3.2 (Intermediate)

A commutator rotates at frequency $f_s = 10$ kHz and samples $K = 8$ signals.


Find:

a) The frame period $T_f$

b) The slot duration $T_s$ (without sync word)

c) The time allocated to each signal per frame

d) If each signal has bandwidth $B = 3$ kHz, is the sampling rate adequate?


---


### Problem 3.3 (Advanced)

For a TDM system with $K$ signals, each sampled at rate $f_s$:


a) Show that the commutator frequency equals $f_s$

b) Derive the relationship: $T_f = 1/f_s$

c) Derive the relationship: $T_s = T_f/K$ (without sync word)

d) Show that the total TDM rate is $K f_s$ samples/second


---


## Exercise Set 4: Frame Structure and Synchronization


### Problem 4.1 (Basic)

A TDM frame contains:

- Sync word: 4 bits

- Data slots: 8 signals


Find:

a) The total number of "slots" per frame

b) If frame period is $T_f = 0.125$ ms, what is the sampling rate $f_s$?

c) What is the purpose of the sync word?

d) What happens if the sync word is not unique?


---


### Problem 4.2 (Intermediate)

A TDM system has:

- Number of signals: $K = 12$

- Sampling rate: $f_s = 8$ kHz

- Sync word: 6 bits, duration $T_{sync} = 0.075$ ms


Find:

a) The frame period $T_f$

b) The time available for data slots: $T_{data} = T_f - T_{sync}$

c) The slot duration $T_s$ for each signal

d) The frame structure (sketch)


---


### Problem 4.3 (Advanced)

Explain frame synchronization in detail:


a) Why is frame synchronization critical?

b) What happens without synchronization?

c) How does the receiver detect frame boundaries?

d) What properties should a sync word have?

e) How can false sync detection be minimized?


---


## Exercise Set 5: Sampling Rate and Bandwidth


### Problem 5.1 (Basic)

A TDM system multiplexes 4 voice signals, each with bandwidth $B = 3.4$ kHz.


Find:

a) The minimum sampling rate per signal (Nyquist rate)

b) If $f_s = 8$ kHz is used, what is the total TDM bandwidth?

c) The frame period $T_f$

d) The total number of samples per second in the TDM signal


---


### Problem 5.2 (Intermediate)

A TDM system has:

- Number of signals: $K = 10$

- Each signal bandwidth: $B = 5$ kHz

- Sampling rate per signal: $f_s = 12$ kHz


Find:

a) Is the sampling rate adequate? (Check Nyquist)

b) The TDM signal bandwidth $B_{TDM}$

c) The frame rate (frames per second)

d) Compare with FDM bandwidth (assuming 1 kHz guard bands)


---


### Problem 5.3 (Advanced)

Derive the TDM bandwidth formula:


a) For $K$ signals, each with bandwidth $B$, show that $B_{TDM} = K \times 2B$ if $f_s = 2B$

b) Show that $B_{TDM} = K f_s$ in general

c) Why doesn't TDM need guard bands?

d) Compare with FDM bandwidth including guard bands


---


## Exercise Set 6: Synchronization Methods


### Problem 6.1 (Basic)

A TDM system uses a sync word for frame synchronization.


a) What is frame synchronization?

b) What is slot synchronization?

c) What is clock synchronization?

d) Why are all three needed?


---


### Problem 6.2 (Intermediate)

Explain the synchronization process:


a) How does the receiver find the frame start?

b) How does it identify which slot is which?

c) How does it maintain timing alignment?

d) What happens if synchronization is lost?


---


### Problem 6.3 (Advanced)

A TDM receiver uses correlation to detect the sync word:


a) How does correlation work?

b) What is the threshold for detection?

c) What is a false alarm?

d) What is a missed detection?

e) How can these be minimized?


---


## Exercise Set 7: Coincident Detector


### Problem 7.1 (Basic)

A coincident detector uses a 5-input AND gate to detect sync word $s = (1, 0, 1, 0, 1)$.


Given received signal $r = (1, 0, 1, 0, 1)$:

a) What is the output of the AND gate?

b) Is the sync word detected?

c) If $r = (1, 0, 1, 1, 1)$, what is the output?

d) Explain why the AND gate works


---


### Problem 7.2 (Intermediate)

A sync word has $K = 8$ bits: $s = (s_1, s_2, \ldots, s_8)$.


The coincident detector compares received bits $r_i$ with expected bits $s_i$:

a) Write the logic expression for the detector output

b) If all bits match, what is the output?

c) If any bit mismatches, what is the output?

d) Why is this called a "coincident" detector?


---


### Problem 7.3 (Advanced)

Derive the coincident detector operation:


a) Show that output = 1 only when $r_i = s_i$ for all $i$

b) Show that output = 0 if any $r_i \neq s_i$

c) Write the mathematical expression: $Output = \prod_{i=1}^{K} [1 - (r_i \oplus s_i)]$

d) Explain why this provides reliable frame synchronization


---


## Exercise Set 8: TDM vs FDM Comparison


### Problem 8.1 (Basic)

Compare TDM and FDM:


a) Which uses time slots?

b) Which uses frequency bands?

c) Which requires synchronization?

d) Which needs guard bands?


---


### Problem 8.2 (Intermediate)

For 6 signals, each with bandwidth $B = 4$ kHz:


a) Calculate TDM bandwidth (assume $f_s = 2B$)

b) Calculate FDM bandwidth (assume 1 kHz guard bands)

c) Which is more bandwidth efficient?

d) What are the advantages of each?


---


### Problem 8.3 (Advanced)

Analyze the trade-offs:


a) When would you choose TDM?

b) When would you choose FDM?

c) What are the implementation differences?

d) What are the performance differences?

e) Give examples of systems using each


---


## Exercise Set 9: Numerical Problems


### Problem 9.1

A TDM system multiplexes 8 voice signals:

- Each signal: $B = 3.4$ kHz

- Sampling rate: $f_s = 8$ kHz per signal

- Sync word: 4 bits


Find:

a) Frame period $T_f$

b) Number of samples per frame

c) Total TDM bandwidth

d) Frame rate (frames per second)

e) If sync word takes 0.05 ms, what is the slot duration?


---


### Problem 9.2

A TDM system has:

- Number of signals: $K = 16$

- Each signal bandwidth: $B = 5$ kHz

- Sampling rate: $f_s = 12$ kHz

- Sync word: 8 bits, duration $T_{sync} = 0.1$ ms


Find:

a) Is sampling rate adequate?

b) Frame period $T_f$

c) Time available for data: $T_{data} = T_f - T_{sync}$

d) Slot duration $T_s$

e) Total TDM bandwidth


---


### Problem 9.3

Design a TDM system for 12 signals:

- Each signal: $B = 4$ kHz

- Required: No aliasing, efficient bandwidth usage


Find:

a) Minimum sampling rate per signal

b) Recommended sampling rate (with margin)

c) Frame period

d) Total TDM bandwidth

e) Compare with FDM (1.5 kHz guard bands)


---


## Exercise Set 10: Conceptual Questions


### Problem 10.1

Answer the following:


a) Why is synchronization critical in TDM?

b) What happens if the receiver is not synchronized?

c) How does crosstalk occur in TDM?

d) Why doesn't FDM need synchronization?


---


### Problem 10.2

Explain:


a) Why does TDM not need guard bands?

b) Why does FDM need guard bands?

c) What is the advantage of no guard bands?

d) What is the trade-off?


---


### Problem 10.3

Discuss:


a) What is the commutator and how does it work?

b) What is the relationship between commutator frequency and sampling rate?

c) Why must commutator and decommutator be synchronized?

d) What happens if they are not synchronized?


---


## Exercise Set 11: Derivation Problems


### Problem 11.1

Derive the TDM bandwidth formula:


a) Start with $K$ signals, each with bandwidth $B$

b) Each signal sampled at $f_s \geq 2B$ (Nyquist)

c) Show that TDM signal contains $K f_s$ samples/second

d) Show that bandwidth $B_{TDM} = K f_s$

e) If $f_s = 2B$, show that $B_{TDM} = K \times 2B$


---


### Problem 11.2

Derive the frame and slot timing relationships:


a) Show that frame period $T_f = 1/f_s$

b) For $K$ signals, show that slot duration $T_s = T_f/K$ (without sync word)

c) With sync word of duration $T_{sync}$, show that $T_s = (T_f - T_{sync})/K$

d) Show that the commutator rotates at frequency $f_s$


---


### Problem 11.3

Derive the coincident detector operation:


a) For sync word $s = (s_1, s_2, \ldots, s_K)$ and received $r = (r_1, r_2, \ldots, r_K)$

b) Show that bit match occurs when $r_i = s_i$ (XOR = 0)

c) Show that all bits match when $\prod_{i=1}^{K} [1 - (r_i \oplus s_i)] = 1$

d) Show that any mismatch gives output = 0

e) Explain why this detects the sync word reliably


---


## Exercise Set 12: Combined Problems


### Problem 12.1

A complete TDM system:


Given:

- 6 voice signals, each $B = 3.4$ kHz

- Sampling rate: $f_s = 8$ kHz per signal

- Sync word: 5 bits, pattern $(1, 0, 1, 0, 1)$


Find:

a) Frame period $T_f$

b) Total TDM bandwidth

c) Frame structure (sketch)

d) Slot duration (if sync word takes 0.0625 ms)

e) Coincident detector operation for sync detection

f) Compare with FDM (1 kHz guard bands)


---


### Problem 12.2

A TDM system design problem:


Requirements:

- 10 signals, each with $B = 4$ kHz

- No aliasing

- Sync word: 6 bits

- Frame period: $T_f = 0.1$ ms


Find:

a) Minimum sampling rate per signal

b) Recommended sampling rate

c) Verify frame period is achievable

d) Slot duration (if sync word = 0.06 ms)

e) Total TDM bandwidth

f) Frame rate


---


### Problem 12.3

Analyze a TDM system:


Given:

- $K = 8$ signals

- Each signal: $B = 5$ kHz

- Sampling rate: $f_s = 12$ kHz

- Sync word: 4 bits, $T_{sync} = 0.033$ ms


Find:

a) Check if sampling rate is adequate

b) Frame period $T_f$

c) Time per data slot

d) Total TDM bandwidth

e) If receiver loses sync, what happens?

f) How does coincident detector work for sync word $(1, 1, 0, 0)$?


---


*Good luck with your exam preparation!*



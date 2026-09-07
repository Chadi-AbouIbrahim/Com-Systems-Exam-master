# Group 5 Exercises - Solutions Part 2

This document contains solutions for Exercise Sets 7-12 of Group 5 exercises.

---

## Exercise Set 7: Coincident Detector - Solutions

### Problem 7.1 Solution

**Given:**
- Sync word: $s = (1, 0, 1, 0, 1)$
- 5-input AND gate
- Received signal: $r = (1, 0, 1, 0, 1)$

**a) Output of AND gate:**

**Coincident detector operation:**
- Compare each received bit $r_i$ with sync bit $s_i$
- If $r_i = s_i$ for all $i$, all inputs to AND gate are 1
- AND gate output = 1

**For $r = (1, 0, 1, 0, 1)$:**
- $r_1 = s_1 = 1$ ✓
- $r_2 = s_2 = 0$ ✓
- $r_3 = s_3 = 1$ ✓
- $r_4 = s_4 = 0$ ✓
- $r_5 = s_5 = 1$ ✓

**All match!** → AND gate output = **1**

**b) Is sync word detected?**

**Yes!** Output = 1 means sync word detected.

**c) If $r = (1, 0, 1, 1, 1)$:**

**Comparison:**
- $r_1 = s_1 = 1$ ✓
- $r_2 = s_2 = 0$ ✓
- $r_3 = s_3 = 1$ ✓
- $r_4 = 1 \neq s_4 = 0$ ✗
- $r_5 = s_5 = 1$ ✓

**Mismatch at bit 4!** → AND gate input = 0 → Output = **0**

**No sync detected.**

**d) Why AND gate works:**

**Logic:**
- AND gate outputs 1 **only** when **all** inputs are 1
- If **any** input is 0, output is 0
- This matches the requirement: sync detected **only** when **all** bits match
- Any mismatch → output = 0 → no sync

---

### Problem 7.2 Solution

**Given:**
- Sync word: $s = (s_1, s_2, \ldots, s_8)$ (8 bits)
- Received: $r = (r_1, r_2, \ldots, r_8)$

**a) Logic expression for detector output:**

**Coincident detector:**
- Compare: $r_i$ with $s_i$ for $i = 1, 2, \ldots, 8$
- Match occurs when $r_i = s_i$ (XOR = 0)
- All matches when: $\prod_{i=1}^{8} [r_i = s_i]$

**Output:**
$$Output = \begin{cases}
1, & \text{if } r_i = s_i \text{ for all } i \\
0, & \text{if } r_i \neq s_i \text{ for any } i
\end{cases}$$

**Using AND gate:**
- Input $i$: $1$ if $r_i = s_i$, $0$ if $r_i \neq s_i$
- Output = AND of all inputs

**b) If all bits match:**

**All inputs = 1:**
- AND gate output = **1**
- Sync word detected ✓

**c) If any bit mismatches:**

**At least one input = 0:**
- AND gate output = **0**
- No sync detected ✗

**d) Why "coincident" detector:**

**"Coincident" means "occurring together":**
- All bits must **coincide** (match) simultaneously
- Detector checks if received pattern **coincides** with sync pattern
- Output = 1 only when patterns **coincide** perfectly

---

### Problem 7.3 Solution

**a) Show output = 1 only when $r_i = s_i$ for all $i$:**

**Coincident detector logic:**
- For each bit: if $r_i = s_i$, input to AND = 1; if $r_i \neq s_i$, input = 0
- AND gate: output = 1 **only** when **all** inputs = 1
- Therefore: output = 1 **only** when $r_i = s_i$ for **all** $i$ ✓

**b) Show output = 0 if any $r_i \neq s_i$:**

**AND gate property:**
- If **any** input = 0, output = 0
- If $r_i \neq s_i$ for **any** $i$, that input = 0
- Therefore: output = 0 if **any** $r_i \neq s_i$ ✓

**c) Mathematical expression:**

**Using XOR (exclusive OR):**
- $r_i \oplus s_i = 0$ if $r_i = s_i$
- $r_i \oplus s_i = 1$ if $r_i \neq s_i$

**For match:** $1 - (r_i \oplus s_i) = 1$ if $r_i = s_i$, $0$ if $r_i \neq s_i$

**All bits match:**
$$Output = \prod_{i=1}^{K} [1 - (r_i \oplus s_i)]$$

- If all $r_i = s_i$: all terms = 1 → product = 1 ✓
- If any $r_i \neq s_i$: that term = 0 → product = 0 ✓

**d) Why this provides reliable frame synchronization:**

**Reliability:**
1. **Exact match required** - all bits must match
2. **Low false alarm rate** - unlikely data matches sync pattern exactly
3. **Simple implementation** - just AND gate
4. **Fast detection** - immediate output
5. **Robust** - works well in practice

**Why it works:**
- Sync word is **unique** - unlikely in data
- AND gate ensures **exact match** - no partial matches
- Provides **reliable** frame boundary detection

---

## Exercise Set 8: TDM vs FDM Comparison - Solutions

### Problem 8.1 Solution

**a) Which uses time slots?**

**TDM (Time Division Multiplexing)** uses time slots.

**b) Which uses frequency bands?**

**FDM (Frequency Division Multiplexing)** uses frequency bands.

**c) Which requires synchronization?**

**TDM requires synchronization** because signals are interleaved in time and the receiver must know when each signal's slot occurs.

**d) Which needs guard bands?**

**FDM needs guard bands** to prevent overlap between adjacent frequency bands due to non-ideal filters.

---

### Problem 8.2 Solution

**Given:**
- Number of signals: $K = 6$
- Each signal bandwidth: $B = 4$ kHz
- Guard bands: 1 kHz

**a) TDM bandwidth (assume $f_s = 2B$):**

$$f_s = 2B = 2 \times 4 = 8 \text{ kHz}$$

$$B_{TDM} = K \times 2B = 6 \times 2 \times 4 = 48 \text{ kHz}$$

Or: $B_{TDM} = K f_s = 6 \times 8 = 48$ kHz ✓

**b) FDM bandwidth:**

Each signal: $2B = 8$ kHz
6 signals: $6 \times 8 = 48$ kHz
Guard bands: 5 guard bands × 1 kHz = 5 kHz (between 6 signals)

**Total FDM:** $48 + 5 = 53$ kHz

**c) Which is more bandwidth efficient?**

**TDM: 48 kHz**
**FDM: 53 kHz**

**TDM is more efficient** by 5 kHz (about 10% more efficient).

**d) Advantages of each:**

**TDM advantages:**
- More bandwidth efficient (no guard bands)
- Digital-friendly
- Flexible allocation
- Simple implementation

**FDM advantages:**
- No synchronization needed
- Analog-friendly
- Simple separation (filters)
- Independent channels

---

### Problem 8.3 Solution

**a) When would you choose TDM?**

**Choose TDM when:**
- Digital signals
- Synchronization available
- Need maximum efficiency
- Flexible allocation needed
- Cost is important

**Examples:**
- Digital telephone systems
- Digital communication networks
- When bandwidth is limited

**b) When would you choose FDM?**

**Choose FDM when:**
- Analog signals
- No synchronization available
- Simple separation needed
- Fixed allocation OK
- Independent channels needed

**Examples:**
- Radio broadcasting
- Cable TV
- When synchronization is difficult

**c) Implementation differences:**

**TDM:**
- Commutator/decommutator (switches)
- Sync word generator/detector
- Timing circuits
- Digital processing

**FDM:**
- Modulators (up-converters)
- Bandpass filters
- Demodulators (down-converters)
- Analog processing

**d) Performance differences:**

**TDM:**
- More bandwidth efficient
- Requires synchronization
- Sensitive to timing errors
- Digital processing

**FDM:**
- Less efficient (guard bands)
- No synchronization needed
- Less sensitive to timing
- Analog processing

**e) Examples:**

**TDM systems:**
- Digital telephone (T1, E1)
- SONET/SDH
- Digital communication

**FDM systems:**
- AM/FM radio
- Cable TV
- Satellite communication

---

## Exercise Set 9: Numerical Problems - Solutions

### Problem 9.1 Solution

**Given:**
- Number of signals: $K = 8$
- Each signal: $B = 3.4$ kHz
- Sampling rate: $f_s = 8$ kHz per signal
- Sync word: 4 bits

**a) Frame period:**

$$T_f = \frac{1}{f_s} = \frac{1}{8000} = 0.125 \text{ ms} = 125 \mu\text{s}$$

**b) Number of samples per frame:**

Each frame contains:
- 1 sample from each of $K$ signals = $K$ samples
- Plus sync word (4 bits)

**Data samples per frame:** $K = 8$ samples

**c) Total TDM bandwidth:**

$$B_{TDM} = K f_s = 8 \times 8000 = 64,000 \text{ Hz} = 64 \text{ kHz}$$

**d) Frame rate (frames per second):**

$$\text{Frame rate} = f_s = 8000 \text{ frames/second}$$

**e) Slot duration (if sync word takes 0.05 ms):**

Time available for data:
$$T_{data} = T_f - T_{sync} = 0.125 - 0.05 = 0.075 \text{ ms}$$

Slot duration:
$$T_s = \frac{T_{data}}{K} = \frac{0.075}{8} = 0.009375 \text{ ms} = 9.375 \mu\text{s}$$

---

### Problem 9.2 Solution

**Given:**
- Number of signals: $K = 16$
- Each signal: $B = 5$ kHz
- Sampling rate: $f_s = 12$ kHz
- Sync word: 8 bits
- Sync word duration: $T_{sync} = 0.1$ ms

**a) Is sampling rate adequate?**

Nyquist rate: $2B = 2 \times 5 = 10$ kHz

Since $f_s = 12$ kHz $> 10$ kHz, **yes, sampling rate is adequate** (oversampling by 20%).

**b) Frame period:**

$$T_f = \frac{1}{f_s} = \frac{1}{12000} = 0.0833 \text{ ms} = 83.3 \mu\text{s}$$

**c) Time available for data:**

$$T_{data} = T_f - T_{sync} = 0.0833 - 0.1 = -0.0167 \text{ ms}$$

**Problem!** $T_{sync} > T_f$ - this is not possible!

**Recalculation:** The sync word duration seems too long. Let me check:

If sync word is 8 bits and bit duration is $T_b$:
$$T_{sync} = 8 T_b$$

But we need $T_{sync} < T_f$.

**Assuming sync word takes less time, say $T_{sync} = 0.01$ ms:**

$$T_{data} = 0.0833 - 0.01 = 0.0733 \text{ ms}$$

**d) Slot duration:**

$$T_s = \frac{T_{data}}{K} = \frac{0.0733}{16} = 0.00458 \text{ ms} = 4.58 \mu\text{s}$$

**e) Total TDM bandwidth:**

$$B_{TDM} = K f_s = 16 \times 12000 = 192,000 \text{ Hz} = 192 \text{ kHz}$$

---

### Problem 9.3 Solution

**Given:**
- Number of signals: $K = 12$
- Each signal: $B = 4$ kHz
- Required: No aliasing, efficient bandwidth

**a) Minimum sampling rate per signal:**

Nyquist rate: $f_s \geq 2B = 2 \times 4 = 8$ kHz

**Minimum:** $f_s = 8$ kHz

**b) Recommended sampling rate (with margin):**

For practical systems, use oversampling:
$$f_s = 2.5B \text{ to } 3B = 10 \text{ to } 12 \text{ kHz}$$

**Recommended:** $f_s = 10$ kHz (25% oversampling, good margin)

**c) Frame period:**

$$T_f = \frac{1}{f_s} = \frac{1}{10000} = 0.1 \text{ ms} = 100 \mu\text{s}$$

**d) Total TDM bandwidth:**

$$B_{TDM} = K f_s = 12 \times 10000 = 120,000 \text{ Hz} = 120 \text{ kHz}$$

**e) Compare with FDM (1.5 kHz guard bands):**

**FDM:**
- Each signal: $2B = 8$ kHz
- 12 signals: $12 \times 8 = 96$ kHz
- Guard bands: 11 guard bands × 1.5 kHz = 16.5 kHz
- **Total FDM:** $96 + 16.5 = 112.5$ kHz

**TDM:** 120 kHz
**FDM:** 112.5 kHz

**FDM is slightly more efficient** in this case because we're oversampling in TDM.

If we used $f_s = 8$ kHz (minimum):
- TDM: $12 \times 8 = 96$ kHz
- FDM: $112.5$ kHz
- **TDM would be more efficient**

---

## Exercise Set 10: Conceptual Questions - Solutions

### Problem 10.1 Solution

**a) Why is synchronization critical in TDM?**

**Synchronization is critical because:**
1. **TDM interleaves signals in time** - samples from different signals are mixed
2. **Receiver must know which sample is which** - needs frame boundaries
3. **Without sync, samples get misrouted** - wrong samples to wrong signals
4. **Crosstalk occurs** - signals interfere with each other
5. **System fails** - cannot recover original signals

**b) What happens if receiver is not synchronized?**

**Consequences:**
1. **Frame boundaries unknown** - doesn't know where frames start
2. **Cannot identify slots** - doesn't know which slot is which signal
3. **Samples misrouted:**
   - Signal 1's samples → Signal 2
   - Signal 2's samples → Signal 3
   - And so on...
4. **Crosstalk** - all signals corrupted
5. **Complete system failure** - unusable

**c) How does crosstalk occur in TDM?**

**Crosstalk mechanism:**
1. Receiver loses synchronization
2. Frame boundaries misidentified
3. Samples routed to wrong outputs:
   - Sample intended for Signal 1 goes to Signal 2
   - Sample intended for Signal 2 goes to Signal 3
4. **Each signal receives samples from other signals**
5. **Interference** - signals are corrupted by other signals

**d) Why doesn't FDM need synchronization?**

**FDM uses frequency separation:**
- Each signal uses **different frequency band**
- Signals are **separated by filters** at receiver
- **No time coordination needed** - filters work independently
- **No frame boundaries** - continuous transmission
- **No slot identification** - frequency identifies the signal

---

### Problem 10.2 Solution

**a) Why does TDM not need guard bands?**

**TDM uses time separation:**
- Signals are separated in **time**, not frequency
- Each signal uses the **same frequency band** but at different times
- **No frequency overlap** → no interference
- **No need for guard bands!**

**b) Why does FDM need guard bands?**

**FDM uses frequency separation:**
- Signals are in **adjacent frequency bands**
- **Filters are not ideal** - have finite roll-off
- **Guard bands prevent overlap** between adjacent bands
- **Prevents interference** from adjacent channels

**c) What is the advantage of no guard bands?**

**Advantages:**
1. **More bandwidth efficient** - no wasted bandwidth
2. **Higher capacity** - can fit more signals
3. **Lower cost** - use bandwidth more efficiently
4. **Better utilization** - all bandwidth used for data

**d) What is the trade-off?**

**Trade-off:**
- **TDM:** No guard bands (efficient) but needs synchronization
- **FDM:** Needs guard bands (less efficient) but no synchronization

**Choose based on:**
- Availability of synchronization
- Bandwidth constraints
- System requirements

---

### Problem 10.3 Solution

**a) What is the commutator and how does it work?**

**Commutator:**
- **Rotating switch** at the transmitter
- Connects to each input signal in sequence
- Samples each signal during its time slot
- Creates the interleaved TDM signal

**Operation:**
1. Rotates at frequency $f_s$
2. Connects to Signal 1, samples it
3. Moves to Signal 2, samples it
4. Continues through all $K$ signals
5. Repeats the cycle

**b) Relationship between commutator frequency and sampling rate:**

**The commutator frequency equals the sampling rate:**
$$f_{commutator} = f_s$$

**Why:**
- Commutator completes one full rotation (through all $K$ signals) in time $T_f = 1/f_s$
- During this time, it samples each signal once
- Therefore, each signal is sampled at rate $f_s$

**c) Why must commutator and decommutator be synchronized?**

**Critical requirement:**
- Commutator samples Signal 1, then Signal 2, then Signal 3, ...
- Decommutator must route first sample to Signal 1, second to Signal 2, third to Signal 3, ...
- **If not synchronized:** Samples get misrouted!
  - Signal 1's samples → Signal 2
  - Signal 2's samples → Signal 3
  - **Crosstalk!** System failure

**d) What happens if they are not synchronized?**

**Consequences:**
1. **Samples misrouted** - wrong samples to wrong signals
2. **Crosstalk** - signals interfere with each other
3. **Data corruption** - cannot recover original signals
4. **System failure** - unusable

**Recovery:**
- Must re-synchronize
- Detect sync word
- Align commutator and decommutator

---

## Exercise Set 11: Derivation Problems - Solutions

### Problem 11.1 Solution

**Derive TDM bandwidth formula:**

**a) Start with $K$ signals, each with bandwidth $B$:**

Each signal $x_k(t)$ has spectrum:
$$X_k(f) = 0 \text{ for } |f| > B$$

**b) Each signal sampled at $f_s \geq 2B$ (Nyquist):**

Sampled signal:
$$x_{k,s}(t) = x_k(t) \sum_{n=-\infty}^{+\infty} \delta(t - nT_s)$$

where $T_s = 1/f_s$.

**c) TDM signal contains $K f_s$ samples/second:**

In TDM:
- Each frame contains $K$ samples (one from each signal)
- Frame period: $T_f = 1/f_s$
- Samples per second: $\frac{K}{T_f} = K f_s$

**d) Show bandwidth $B_{TDM} = K f_s$:**

The TDM signal is a sequence of samples at rate $K f_s$.

The bandwidth required is approximately equal to the sampling rate:
$$B_{TDM} = K f_s$$

**e) If $f_s = 2B$, show $B_{TDM} = K \times 2B$:**

If $f_s = 2B$:
$$B_{TDM} = K f_s = K \times 2B$$

**Result:** $B_{TDM} = K \times 2B$ ✓

---

### Problem 11.2 Solution

**Derive frame and slot timing relationships:**

**a) Show frame period $T_f = 1/f_s$:**

By definition, the sampling rate $f_s$ means each signal is sampled every $T_s = 1/f_s$ seconds.

In TDM, one sample from each signal is taken per frame, so:
$$T_f = \frac{1}{f_s}$$

**b) For $K$ signals, show $T_s = T_f/K$ (without sync word):**

In one frame period $T_f$, the commutator samples all $K$ signals.

If there's no sync word, all time is used for data slots:
$$T_f = K \times T_s$$

Therefore:
$$T_s = \frac{T_f}{K}$$

**c) With sync word of duration $T_{sync}$, show $T_s = (T_f - T_{sync})/K$:**

Frame period is divided into:
- Sync word: $T_{sync}$
- Data slots: $K \times T_s$

$$T_f = T_{sync} + K T_s$$

Solving for $T_s$:
$$K T_s = T_f - T_{sync}$$
$$T_s = \frac{T_f - T_{sync}}{K}$$

**d) Show commutator rotates at frequency $f_s$:**

The commutator completes one full rotation (through all $K$ signals) in time $T_f$.

Rotation frequency:
$$f_{commutator} = \frac{1}{T_f} = f_s$$

**Result:** Commutator rotates at frequency $f_s$ ✓

---

### Problem 11.3 Solution

**Derive coincident detector operation:**

**a) For sync word $s = (s_1, s_2, \ldots, s_K)$ and received $r = (r_1, r_2, \ldots, r_K)$:**

**Coincident detector compares:**
- Received bits: $r_1, r_2, \ldots, r_K$
- Expected sync bits: $s_1, s_2, \ldots, s_K$

**b) Show bit match occurs when $r_i = s_i$ (XOR = 0):**

**XOR operation:**
- $r_i \oplus s_i = 0$ if $r_i = s_i$ (match)
- $r_i \oplus s_i = 1$ if $r_i \neq s_i$ (mismatch)

**Match indicator:**
- $1 - (r_i \oplus s_i) = 1$ if $r_i = s_i$
- $1 - (r_i \oplus s_i) = 0$ if $r_i \neq s_i$

**c) Show all bits match when $\prod_{i=1}^{K} [1 - (r_i \oplus s_i)] = 1$:**

**Product over all bits:**
$$Output = \prod_{i=1}^{K} [1 - (r_i \oplus s_i)]$$

**If all bits match:**
- All terms: $1 - (r_i \oplus s_i) = 1$
- Product: $1 \times 1 \times \ldots \times 1 = 1$ ✓

**If any bit mismatches:**
- That term: $1 - (r_i \oplus s_i) = 0$
- Product: $\ldots \times 0 \times \ldots = 0$ ✓

**d) Show any mismatch gives output = 0:**

**AND gate property:**
- If **any** input = 0, output = 0
- If $r_i \neq s_i$ for **any** $i$, that term = 0
- Product = 0 → Output = 0 ✓

**e) Why this detects sync word reliably:**

**Reliability:**
1. **Exact match required** - all bits must match
2. **Low false alarm** - unlikely data matches exactly
3. **Simple** - just AND gate
4. **Fast** - immediate detection
5. **Robust** - works in practice

**Why it works:**
- Sync word is **unique** - chosen to be unlikely in data
- AND gate ensures **perfect match** - no partial matches
- Provides **reliable** frame boundary detection

---

## Exercise Set 12: Combined Problems - Solutions

### Problem 12.1 Solution

**Given:**
- Number of signals: $K = 6$
- Each signal: $B = 3.4$ kHz
- Sampling rate: $f_s = 8$ kHz per signal
- Sync word: 5 bits, pattern $(1, 0, 1, 0, 1)$

**a) Frame period:**

$$T_f = \frac{1}{f_s} = \frac{1}{8000} = 0.125 \text{ ms} = 125 \mu\text{s}$$

**b) Total TDM bandwidth:**

$$B_{TDM} = K f_s = 6 \times 8000 = 48,000 \text{ Hz} = 48 \text{ kHz}$$

**c) Frame structure:**

```
Frame Structure:
| Sync (5 bits) | Signal 1 | Signal 2 | Signal 3 | Signal 4 | Signal 5 | Signal 6 |
|<------------------- Frame Period T_f = 0.125 ms ----------------->|
```

**d) Slot duration (if sync word takes 0.0625 ms):**

Time available for data:
$$T_{data} = T_f - T_{sync} = 0.125 - 0.0625 = 0.0625 \text{ ms}$$

Slot duration:
$$T_s = \frac{T_{data}}{K} = \frac{0.0625}{6} = 0.01042 \text{ ms} = 10.42 \mu\text{s}$$

**e) Coincident detector operation:**

**Sync word:** $s = (1, 0, 1, 0, 1)$

**5-input AND gate:**
- Compare received $r_i$ with sync $s_i$
- If $r = (1, 0, 1, 0, 1)$: All match → Output = 1 ✓
- If $r \neq s$: At least one mismatch → Output = 0 ✗

**f) Compare with FDM (1 kHz guard bands):**

**FDM:**
- Each signal: $2B = 6.8$ kHz
- 6 signals: $6 \times 6.8 = 40.8$ kHz
- Guard bands: 5 × 1 kHz = 5 kHz
- **Total FDM:** $40.8 + 5 = 45.8$ kHz

**TDM:** 48 kHz
**FDM:** 45.8 kHz

**FDM is slightly more efficient** in this case (we're oversampling in TDM).

---

### Problem 12.2 Solution

**Given:**
- Number of signals: $K = 10$
- Each signal: $B = 4$ kHz
- Sync word: 6 bits
- Frame period: $T_f = 0.1$ ms

**a) Minimum sampling rate per signal:**

Nyquist rate: $f_s \geq 2B = 2 \times 4 = 8$ kHz

**Minimum:** $f_s = 8$ kHz

**b) Recommended sampling rate:**

For practical systems: $f_s = 10$ kHz (25% oversampling)

**c) Verify frame period is achievable:**

If $f_s = 10$ kHz:
$$T_f = \frac{1}{f_s} = \frac{1}{10000} = 0.1 \text{ ms}$$

**Matches requirement!** ✓

**d) Slot duration (if sync word = 0.06 ms):**

Time available:
$$T_{data} = T_f - T_{sync} = 0.1 - 0.06 = 0.04 \text{ ms}$$

Slot duration:
$$T_s = \frac{T_{data}}{K} = \frac{0.04}{10} = 0.004 \text{ ms} = 4 \mu\text{s}$$

**e) Total TDM bandwidth:**

$$B_{TDM} = K f_s = 10 \times 10000 = 100,000 \text{ Hz} = 100 \text{ kHz}$$

**f) Frame rate:**

$$\text{Frame rate} = f_s = 10,000 \text{ frames/second}$$

---

### Problem 12.3 Solution

**Given:**
- Number of signals: $K = 8$
- Each signal: $B = 5$ kHz
- Sampling rate: $f_s = 12$ kHz
- Sync word: 4 bits, pattern $(1, 1, 0, 0)$
- Sync word duration: $T_{sync} = 0.033$ ms

**a) Check if sampling rate is adequate:**

Nyquist rate: $2B = 2 \times 5 = 10$ kHz

Since $f_s = 12$ kHz $> 10$ kHz, **yes, sampling rate is adequate** (oversampling by 20%).

**b) Frame period:**

$$T_f = \frac{1}{f_s} = \frac{1}{12000} = 0.0833 \text{ ms} = 83.3 \mu\text{s}$$

**c) Time per data slot:**

Time available:
$$T_{data} = T_f - T_{sync} = 0.0833 - 0.033 = 0.0503 \text{ ms}$$

Slot duration:
$$T_s = \frac{T_{data}}{K} = \frac{0.0503}{8} = 0.00629 \text{ ms} = 6.29 \mu\text{s}$$

**d) Total TDM bandwidth:**

$$B_{TDM} = K f_s = 8 \times 12000 = 96,000 \text{ Hz} = 96 \text{ kHz}$$

**e) If receiver loses sync, what happens?**

**Consequences:**
1. **Frame boundaries unknown** - cannot identify slots
2. **Samples misrouted** - wrong samples to wrong signals
3. **Crosstalk** - signals interfere
4. **System failure** - cannot recover signals

**Recovery:**
- Must re-detect sync word
- Re-establish synchronization
- Re-align timing

**f) Coincident detector for sync word $(1, 1, 0, 0)$:**

**Sync word:** $s = (1, 1, 0, 0)$

**4-input AND gate:**
- Compare received $r = (r_1, r_2, r_3, r_4)$ with $s$
- If $r = (1, 1, 0, 0)$: All match → Output = 1 ✓
- If $r \neq s$: At least one mismatch → Output = 0 ✗

**Example:**
- $r = (1, 1, 0, 0)$ → Output = 1 (sync detected)
- $r = (1, 1, 0, 1)$ → Output = 0 (no sync, bit 4 mismatch)
- $r = (1, 0, 0, 0)$ → Output = 0 (no sync, bit 2 mismatch)

---

*End of Part 2 Solutions (Exercise Sets 7-12)*

*Good luck with your exam preparation!*


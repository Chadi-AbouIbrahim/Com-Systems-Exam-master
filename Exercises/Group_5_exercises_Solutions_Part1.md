# Group 5 Exercises - Solutions Part 1

This document contains solutions for Exercise Sets 1-6 of Group 5 exercises.

---

## Exercise Set 1: Multiplexing Basics - Solutions

### Problem 1.1 Solution

**a) What is multiplexing?**

**Multiplexing** is the process of combining multiple signals into a single signal for transmission over a shared channel, then separating them at the receiver.

**Key idea:** Multiple signals share one channel by using different resources (time or frequency).

**b) Why is multiplexing used in communication systems?**

**Reasons:**
1. **Efficient use of bandwidth** - share one channel among many signals
2. **Cost effective** - one transmission system for multiple signals
3. **Widely used** - telephone systems, digital communication, broadcasting
4. **Scalability** - can add more signals to the same channel

**c) What are the two main types of multiplexing?**

1. **Time Division Multiplexing (TDM):** Signals share the channel by taking turns in time
2. **Frequency Division Multiplexing (FDM):** Signals share the channel by using different frequency bands

**d) What is the key requirement for TDM to work?**

**Synchronization** - the receiver must know which sample belongs to which signal!

Without synchronization:
- Receiver doesn't know where frame starts
- Samples get misrouted to wrong signals
- **Crosstalk** occurs
- Complete system failure

---

### Problem 1.2 Solution

**a) How does TDM separate signals?**

**TDM uses time slots:**
- Each signal is assigned specific time slots
- Signals take turns in time
- All signals use the same frequency band
- Separation is by **time**, not frequency

**b) How does FDM separate signals?**

**FDM uses frequency bands:**
- Each signal gets its own frequency band
- All signals transmitted simultaneously
- Separation is by **frequency**, not time
- Uses filters at receiver to separate

**c) Which requires synchronization? Why?**

**TDM requires synchronization** because:
- Signals are interleaved in time
- Receiver must know when each signal's slot occurs
- Must identify frame boundaries
- Must route samples to correct outputs

**FDM does not require synchronization** because:
- Signals are separated by frequency
- Filters can separate them independently
- No timing coordination needed

**d) Which is more bandwidth efficient? Why?**

**TDM is more bandwidth efficient** because:
- TDM: $B_{TDM} = K \times 2B$ (no guard bands)
- FDM: $B_{FDM} = K \times 2B + \text{guard bands}$
- Guard bands add overhead in FDM
- TDM uses time, so no frequency separation needed

---

### Problem 1.3 Solution

**Given:**
- Number of signals: $K = 5$
- Each signal bandwidth: $B = 4$ kHz

**a) Bandwidth required for TDM:**

Each signal must be sampled at $f_s \geq 2B = 8$ kHz (Nyquist).

If $f_s = 8$ kHz:
$$B_{TDM} = K \times 2B = 5 \times 2 \times 4 = 40 \text{ kHz}$$

Or: $B_{TDM} = K f_s = 5 \times 8 = 40$ kHz ✓

**b) Bandwidth required for FDM:**

Each signal needs $2B = 8$ kHz bandwidth.

With guard bands of 1 kHz between signals:
- 5 signals need 4 guard bands (between them)
- Total: $5 \times 8 + 4 \times 1 = 40 + 4 = 44$ kHz

**c) Which is more efficient?**

**TDM is more efficient:**
- TDM: 40 kHz
- FDM: 44 kHz
- **Difference:** 4 kHz (10% more for FDM)

**d) Trade-offs:**

**TDM advantages:**
- More bandwidth efficient (no guard bands)
- Digital-friendly
- Flexible allocation
- Simple implementation

**TDM disadvantages:**
- Requires synchronization
- Sensitive to timing errors
- Needs buffering

**FDM advantages:**
- No synchronization needed
- Analog-friendly
- Simple separation (filters)

**FDM disadvantages:**
- Less efficient (guard bands)
- Less flexible
- More complex filters

---

## Exercise Set 2: TDM System Architecture - Solutions

### Problem 2.1 Solution

**Block Diagram:**

```
TRANSMITTER (Multiplexer):
Signal 1 ──┐
Signal 2 ──┤
Signal 3 ──┼──> [Commutator] ──> [TDM Signal]
  ...      │
Signal K ──┘
           ↑
      [Clock/Sync]

CHANNEL:
[TDM Signal] ──> [Channel] ──> [TDM Signal]

RECEIVER (Demultiplexer):
[TDM Signal] ──> [Decommutator] ──┐
           ↑                       │
      [Sync Detector]              │
                                  ▼
                           [Separated Signals]
                           Signal 1
                           Signal 2
                           Signal 3
                           ...
                           Signal K
```

**Components:**

**Transmitter:**
1. **Input signals** - $K$ signals to be multiplexed
2. **Commutator** - rotating switch that samples each signal in sequence
3. **Clock/Sync generator** - provides timing and sync word

**Channel:**
- Transmits the TDM signal

**Receiver:**
1. **Sync detector** - detects frame boundaries using sync word
2. **Decommutator** - synchronized switch that routes samples to correct outputs
3. **Output signals** - reconstructed $K$ signals

---

### Problem 2.2 Solution

**a) Function of the commutator:**

The **commutator** (at transmitter):
- Rotates through input signals at frequency $f_s$
- Samples each signal in sequence
- Creates the interleaved TDM signal
- Acts as a rotating switch

**Operation:**
- Connects to Signal 1, samples it
- Moves to Signal 2, samples it
- Continues through all $K$ signals
- Repeats the cycle

**b) Function of the decommutator:**

The **decommutator** (at receiver):
- Synchronized with the commutator
- Receives the TDM signal
- Routes each sample to the correct output
- Separates the interleaved samples back to original signals

**Operation:**
- Receives sample, routes to Signal 1 output
- Receives next sample, routes to Signal 2 output
- Continues through all $K$ signals
- Repeats the cycle

**c) Why must they be synchronized?**

**Critical requirement:**
- Commutator samples Signal 1, then Signal 2, then Signal 3, ...
- Decommutator must route first sample to Signal 1, second to Signal 2, third to Signal 3, ...
- **If not synchronized:** Samples get misrouted!
  - Signal 1's samples go to Signal 2
  - Signal 2's samples go to Signal 3
  - **Crosstalk!** Complete system failure

**d) What happens if synchronization is lost?**

**Consequences:**
1. **Crosstalk** - signals interfere with each other
2. **Data corruption** - wrong samples in wrong signals
3. **System failure** - cannot recover original signals
4. **Must re-synchronize** - detect sync word again

---

### Problem 2.3 Solution

**a) How are signals sampled at the transmitter?**

**Sampling process:**
1. Each signal is sampled at regular intervals
2. Sampling rate: $f_s$ (same for all signals)
3. Sampling instants: $t = nT_s$ where $T_s = 1/f_s$
4. Commutator rotates and samples each signal in sequence
5. Samples: $x_1(nT_s), x_2(nT_s), \ldots, x_K(nT_s)$

**b) How are samples interleaved?**

**Interleaving:**
- Frame 1: $x_1(0), x_2(0), x_3(0), \ldots, x_K(0)$
- Frame 2: $x_1(T_s), x_2(T_s), x_3(T_s), \ldots, x_K(T_s)$
- Frame 3: $x_1(2T_s), x_2(2T_s), x_3(2T_s), \ldots, x_K(2T_s)$
- And so on...

**TDM signal:** Samples from different signals are interleaved sequentially.

**c) How are samples separated at the receiver?**

**Separation process:**
1. Receiver detects frame boundaries (using sync word)
2. Decommutator knows which slot corresponds to which signal
3. Routes each sample to correct output:
   - First slot → Signal 1
   - Second slot → Signal 2
   - Third slot → Signal 3
   - And so on...
4. Repeats for each frame

**d) How is each signal reconstructed?**

**Reconstruction:**
1. Samples for each signal are collected at the output
2. Samples are at rate $f_s$ (one per frame)
3. Use **lowpass filter** with cutoff $B$ (signal bandwidth)
4. Filter interpolates between samples
5. Reconstructs the continuous-time signal

**Mathematically:**
- Samples: $x_k(nT_s)$ for $n = 0, 1, 2, \ldots$
- Reconstruction filter: Lowpass with cutoff $B$
- Recovered signal: $\hat{x}_k(t)$

---

## Exercise Set 3: Commutator Operation - Solutions

### Problem 3.1 Solution

**Given:**
- Number of signals: $K = 6$
- Sampling rate per signal: $f_s = 8$ kHz

**a) Commutator rotation frequency:**

The commutator rotates at the same frequency as the sampling rate:
$$f_{commutator} = f_s = 8 \text{ kHz}$$

**b) Frame period:**

$$T_f = \frac{1}{f_s} = \frac{1}{8000} = 0.125 \text{ ms} = 125 \mu\text{s}$$

**c) Time per slot (assuming no sync word):**

$$T_s = \frac{T_f}{K} = \frac{0.125}{6} = 0.02083 \text{ ms} = 20.83 \mu\text{s}$$

**d) Total sampling rate of TDM signal:**

The TDM signal contains samples from all $K$ signals:
$$\text{Total rate} = K \times f_s = 6 \times 8000 = 48,000 \text{ samples/second}$$

---

### Problem 3.2 Solution

**Given:**
- Commutator frequency: $f_s = 10$ kHz
- Number of signals: $K = 8$
- Each signal bandwidth: $B = 3$ kHz

**a) Frame period:**

$$T_f = \frac{1}{f_s} = \frac{1}{10000} = 0.1 \text{ ms} = 100 \mu\text{s}$$

**b) Slot duration (without sync word):**

$$T_s = \frac{T_f}{K} = \frac{0.1}{8} = 0.0125 \text{ ms} = 12.5 \mu\text{s}$$

**c) Time allocated to each signal per frame:**

Each signal gets one slot per frame:
$$\text{Time per signal} = T_s = 12.5 \mu\text{s}$$

**d) Is sampling rate adequate?**

Nyquist rate: $2B = 2 \times 3 = 6$ kHz

Since $f_s = 10$ kHz $> 6$ kHz, **yes, the sampling rate is adequate** (oversampling by ~67%).

---

### Problem 3.3 Solution

**a) Show commutator frequency equals $f_s$:**

The commutator must complete one full rotation (through all $K$ signals) in time $T_f$.

During $T_f$, it samples each signal once, so:
- Time per signal = $T_f/K$
- Sampling rate per signal = $1/(T_f/K) = K/T_f$

But we also have: $f_s = 1/T_f$ (sampling rate per signal)

Therefore: $K/T_f = K f_s$

Wait, let me reconsider. The sampling rate per signal is $f_s$, meaning each signal is sampled every $T_f = 1/f_s$ seconds.

The commutator rotates through all $K$ signals in time $T_f$, so:
$$f_{commutator} = \frac{1}{T_f} = f_s$$

**b) Derive $T_f = 1/f_s$:**

By definition, the sampling rate $f_s$ means samples are taken every $T_s = 1/f_s$ seconds.

But in TDM, one sample from each signal is taken per frame, so:
$$T_f = \frac{1}{f_s}$$

**c) Derive $T_s = T_f/K$ (without sync word):**

In one frame period $T_f$, the commutator must sample all $K$ signals.

If there's no sync word, all time is used for data:
$$T_f = K \times T_s$$

Therefore:
$$T_s = \frac{T_f}{K}$$

**d) Show total TDM rate is $K f_s$:**

In one frame:
- $K$ samples (one from each signal)
- Frame period: $T_f = 1/f_s$

Total samples per second:
$$\text{Total rate} = \frac{K}{T_f} = \frac{K}{1/f_s} = K f_s$$

---

## Exercise Set 4: Frame Structure and Synchronization - Solutions

### Problem 4.1 Solution

**Given:**
- Sync word: 4 bits
- Data slots: 8 signals
- Frame period: $T_f = 0.125$ ms

**a) Total number of "slots" per frame:**

Total slots = Sync word slots + Data slots = $4 + 8 = 12$ slots

**b) Sampling rate:**

$$f_s = \frac{1}{T_f} = \frac{1}{0.125 \times 10^{-3}} = 8000 \text{ Hz} = 8 \text{ kHz}$$

**c) Purpose of sync word:**

The sync word:
1. **Identifies frame boundaries** - receiver knows when a new frame starts
2. **Enables synchronization** - allows receiver to align with transmitter
3. **Prevents crosstalk** - ensures samples are routed to correct signals
4. **Critical for operation** - TDM cannot work without it

**d) What happens if sync word is not unique?**

**Problems:**
1. **False detection** - data that matches sync pattern triggers false sync
2. **Loss of synchronization** - receiver thinks it found frame start when it didn't
3. **Crosstalk** - samples get misrouted
4. **System failure** - cannot recover original signals

**Solution:** Sync word must be **unique** - should not appear in data.

---

### Problem 4.2 Solution

**Given:**
- Number of signals: $K = 12$
- Sampling rate: $f_s = 8$ kHz
- Sync word: 6 bits
- Sync word duration: $T_{sync} = 0.075$ ms

**a) Frame period:**

$$T_f = \frac{1}{f_s} = \frac{1}{8000} = 0.125 \text{ ms} = 125 \mu\text{s}$$

**b) Time available for data slots:**

$$T_{data} = T_f - T_{sync} = 0.125 - 0.075 = 0.05 \text{ ms} = 50 \mu\text{s}$$

**c) Slot duration for each signal:**

$$T_s = \frac{T_{data}}{K} = \frac{0.05}{12} = 0.00417 \text{ ms} = 4.17 \mu\text{s}$$

**d) Frame structure:**

```
Frame Structure:
| Sync (6 bits, 0.075 ms) | Signal 1 | Signal 2 | ... | Signal 12 |
|<----------- Frame Period T_f = 0.125 ms ------------>|
|                         |<-- Data Slots: 0.05 ms -->|
```

---

### Problem 4.3 Solution

**a) Why is frame synchronization critical?**

**Frame synchronization is critical because:**
1. **Without it, TDM cannot work** - receiver doesn't know where frames start
2. **Samples get misrouted** - wrong samples go to wrong signals
3. **Crosstalk occurs** - signals interfere with each other
4. **Complete system failure** - cannot recover original signals

**b) What happens without synchronization?**

**Consequences:**
1. Receiver doesn't know frame boundaries
2. Cannot identify which slot is which
3. Samples routed incorrectly:
   - Signal 1's samples → Signal 2
   - Signal 2's samples → Signal 3
   - And so on...
4. **Crosstalk** - all signals corrupted
5. System unusable

**c) How does receiver detect frame boundaries?**

**Sync word detection:**
1. Receiver searches for the unique sync word pattern
2. Uses **correlator** or **coincident detector**
3. Compares received signal with expected sync word
4. When match found → frame boundary detected
5. Receiver aligns with frame structure

**d) Properties sync word should have:**

1. **Unique** - should not appear in data
2. **Good autocorrelation** - easy to detect
3. **Distinctive pattern** - stands out from data
4. **Fixed length** - known number of bits
5. **Reliable detection** - low false alarm rate

**e) How to minimize false sync detection:**

**Methods:**
1. **Choose unique pattern** - unlikely to appear in data
2. **Use longer sync word** - more bits = less likely to match data
3. **Use specific patterns** - alternating, specific sequences
4. **Threshold setting** - require high correlation
5. **Verification** - check multiple frames

---

## Exercise Set 5: Sampling Rate and Bandwidth - Solutions

### Problem 5.1 Solution

**Given:**
- Number of signals: $K = 4$
- Each signal bandwidth: $B = 3.4$ kHz

**a) Minimum sampling rate per signal (Nyquist rate):**

$$f_s \geq 2B = 2 \times 3.4 = 6.8 \text{ kHz}$$

**Minimum:** $f_s = 6.8$ kHz

**b) Total TDM bandwidth if $f_s = 8$ kHz:**

$$B_{TDM} = K \times 2B = 4 \times 2 \times 3.4 = 27.2 \text{ kHz}$$

Or: $B_{TDM} = K f_s = 4 \times 8 = 32$ kHz

(Note: The first formula assumes $f_s = 2B$, but we're using $f_s = 8$ kHz $> 6.8$ kHz, so the second formula is more accurate: $B_{TDM} = 32$ kHz)

**c) Frame period:**

$$T_f = \frac{1}{f_s} = \frac{1}{8000} = 0.125 \text{ ms} = 125 \mu\text{s}$$

**d) Total number of samples per second:**

$$\text{Total rate} = K \times f_s = 4 \times 8000 = 32,000 \text{ samples/second}$$

---

### Problem 5.2 Solution

**Given:**
- Number of signals: $K = 10$
- Each signal bandwidth: $B = 5$ kHz
- Sampling rate: $f_s = 12$ kHz

**a) Is sampling rate adequate?**

Nyquist rate: $2B = 2 \times 5 = 10$ kHz

Since $f_s = 12$ kHz $> 10$ kHz, **yes, the sampling rate is adequate** (oversampling by 20%).

**b) TDM signal bandwidth:**

$$B_{TDM} = K f_s = 10 \times 12 = 120 \text{ kHz}$$

**c) Frame rate (frames per second):**

$$\text{Frame rate} = f_s = 12,000 \text{ frames/second}$$

**d) Compare with FDM bandwidth:**

**FDM:**
- Each signal: $2B = 10$ kHz
- 10 signals: $10 \times 10 = 100$ kHz
- Guard bands: 9 guard bands × 1 kHz = 9 kHz
- **Total FDM:** $100 + 9 = 109$ kHz

**TDM:** 120 kHz
**FDM:** 109 kHz

**FDM is slightly more efficient in this case** because we're oversampling in TDM ($f_s = 12$ kHz $> 10$ kHz).

If we used $f_s = 10$ kHz (minimum):
- TDM: $10 \times 10 = 100$ kHz
- FDM: $109$ kHz
- **TDM would be more efficient**

---

### Problem 5.3 Solution

**a) Show $B_{TDM} = K \times 2B$ if $f_s = 2B$:**

For $K$ signals, each with bandwidth $B$:
- Each sampled at $f_s = 2B$ (Nyquist rate)
- TDM signal contains $K$ samples per frame
- Frame period: $T_f = 1/f_s = 1/(2B)$
- Total samples per second: $K f_s = K \times 2B$

The bandwidth of the TDM signal is approximately equal to the total sampling rate:
$$B_{TDM} = K f_s = K \times 2B$$

**b) Show $B_{TDM} = K f_s$ in general:**

The TDM signal is a sequence of samples from $K$ signals.

If each signal is sampled at rate $f_s$:
- Total samples per second: $K f_s$
- The bandwidth required is approximately equal to this rate:
$$B_{TDM} = K f_s$$

**c) Why doesn't TDM need guard bands?**

**TDM uses time separation:**
- Signals are separated in **time**, not frequency
- Each signal uses the **same frequency band** but at different times
- No frequency overlap → no interference
- **No guard bands needed!**

**FDM needs guard bands because:**
- Signals are separated in **frequency**
- Filters are not ideal (finite roll-off)
- Guard bands prevent overlap between adjacent frequency bands

**d) Compare with FDM bandwidth:**

**TDM:**
$$B_{TDM} = K f_s = K \times 2B \text{ (if } f_s = 2B)$$

**FDM:**
$$B_{FDM} = K \times 2B + \text{guard bands}$$

**TDM is more efficient** because:
- No guard bands
- Uses time, not frequency separation
- More bandwidth efficient

---

## Exercise Set 6: Synchronization Methods - Solutions

### Problem 6.1 Solution

**a) What is frame synchronization?**

**Frame synchronization:**
- Process of identifying **frame boundaries**
- Receiver must know **when a frame starts**
- Detected using the **sync word**
- Critical for proper operation

**b) What is slot synchronization?**

**Slot synchronization:**
- Once frame is synchronized, receiver knows frame boundaries
- Can **count slots** to identify which signal each slot belongs to
- First slot = Signal 1, second = Signal 2, etc.
- Routes each sample to correct output

**c) What is clock synchronization?**

**Clock synchronization:**
- Receiver clock must be **aligned** with transmitter clock
- Prevents **drift** and **timing errors**
- Can extract clock from signal or use separate clock channel
- Maintains timing alignment

**d) Why are all three needed?**

**All three work together:**
1. **Frame sync** - finds frame start
2. **Slot sync** - identifies which slot is which
3. **Clock sync** - maintains timing alignment

**Without any one:**
- System fails or degrades
- Crosstalk occurs
- Signals cannot be recovered

---

### Problem 6.2 Solution

**a) How does receiver find frame start?**

**Sync word detection:**
1. Receiver continuously searches for the sync word pattern
2. Uses **correlator** or **coincident detector**
3. Compares received signal with expected sync word
4. When high correlation → sync word detected
5. Frame start identified

**b) How does it identify which slot is which?**

**Slot identification:**
1. After frame sync, receiver knows frame boundaries
2. Counts slots from frame start:
   - Slot 1 → Signal 1
   - Slot 2 → Signal 2
   - Slot 3 → Signal 3
   - And so on...
3. Routes each slot to corresponding output

**c) How does it maintain timing alignment?**

**Clock synchronization methods:**
1. **Extract clock from signal** - use transitions in TDM signal
2. **Separate clock channel** - transmit clock separately
3. **PLL (Phase-Locked Loop)** - lock receiver clock to transmitter
4. **Periodic sync word** - helps maintain alignment

**d) What happens if synchronization is lost?**

**Consequences:**
1. **Frame boundaries unknown** - cannot identify slots
2. **Samples misrouted** - wrong samples to wrong signals
3. **Crosstalk** - signals interfere
4. **System failure** - cannot recover signals

**Recovery:**
- Must re-detect sync word
- Re-establish frame synchronization
- Re-align timing

---

### Problem 6.3 Solution

**a) How does correlation work?**

**Correlation process:**
1. Compare received signal $r(t)$ with expected sync word $s(t)$
2. Compute correlation: $R(\tau) = \int r(t) s(t-\tau) dt$
3. High correlation → sync word present
4. Low correlation → not sync word

**For discrete signals:**
- Compare received bits $r_i$ with sync bits $s_i$
- Count matches
- High match count → sync detected

**b) What is the threshold for detection?**

**Threshold setting:**
- Set a threshold value
- If correlation $>$ threshold → sync detected
- If correlation $<$ threshold → continue searching

**Trade-off:**
- High threshold → fewer false alarms, but may miss sync
- Low threshold → catch sync easily, but more false alarms

**c) What is a false alarm?**

**False alarm:**
- Receiver thinks it detected sync word when it didn't
- Data accidentally matches sync pattern
- Causes loss of synchronization
- Samples get misrouted

**Minimization:**
- Use unique sync word
- Use longer sync word
- Set higher threshold

**d) What is a missed detection?**

**Missed detection:**
- Sync word is present but receiver doesn't detect it
- Correlation below threshold
- Receiver continues searching
- May lose synchronization

**Minimization:**
- Use distinctive sync pattern
- Set appropriate threshold
- Use good detection algorithm

**e) How can these be minimized?**

**Minimize false alarms:**
1. **Unique sync word** - unlikely in data
2. **Longer sync word** - more bits = less likely match
3. **Higher threshold** - require strong match
4. **Verification** - check multiple frames

**Minimize missed detections:**
1. **Good sync pattern** - high autocorrelation
2. **Appropriate threshold** - not too high
3. **Robust detection** - handle noise
4. **Periodic sync** - multiple opportunities

---

*End of Part 1 Solutions (Exercise Sets 1-6)*


# GROUP 5 - Multiplexing: Detailed Explanation

## Lecture 11: Time Division Multiplexing (TDM)

---

## Table of Contents

1. [Introduction: What is Multiplexing?](#introduction)
2. [Time Division Multiplexing (TDM) - The Basics](#tdm-basics)
3. [TDM System Architecture](#tdm-architecture)
4. [Commutator Operation](#commutator)
5. [Frame Structure and Synchronization](#frame-sync)
6. [Sampling Rate and Bandwidth](#sampling-bandwidth)
7. [Synchronization Methods](#synchronization)
8. [Coincident Detector](#coincident-detector)
9. [Comparison: TDM vs FDM](#tdm-vs-fdm)
10. [Detailed Example: TDM System](#detailed-example)
11. [Key Takeaways](#key-takeaways)

---

## 1. Introduction: What is Multiplexing? {#introduction}

### The Basic Idea

**Multiplexing** is the process of combining multiple signals into a single signal for transmission over a shared channel, then separating them at the receiver.

**Why Multiplexing?**
- **Efficient use of bandwidth** - share one channel among many signals
- **Cost effective** - one transmission system for multiple signals
- **Widely used** - telephone systems, digital communication, broadcasting

### Two Main Types

1. **Time Division Multiplexing (TDM):** Signals share the channel by taking turns in time
2. **Frequency Division Multiplexing (FDM):** Signals share the channel by using different frequency bands

**This lecture focuses on TDM.**

### The Multiplexing Process

**Transmitter (Multiplexer):**
1. Sample multiple signals at different times
2. Interleave the samples
3. Transmit the combined signal

**Receiver (Demultiplexer):**
1. Receive the combined signal
2. Separate samples back to original signals
3. Reconstruct each signal

**Key Requirement:** Synchronization - receiver must know which sample belongs to which signal!

---

## 2. Time Division Multiplexing (TDM) - The Basics {#tdm-basics}

### The Concept

**Time Division Multiplexing (TDM)** divides time into slots, with each signal assigned specific time slots.

**How It Works:**
- Each signal is **sampled** at regular intervals
- Samples from different signals are **interleaved** (one after another)
- The combined signal is transmitted
- At the receiver, samples are **separated** and each signal is **reconstructed**

### Visual Example

```
Signal 1:  A1  A2  A3  A4  ...
Signal 2:  B1  B2  B3  B4  ...
Signal 3:  C1  C2  C3  C4  ...

TDM Output: A1 B1 C1 A2 B2 C2 A3 B3 C3 A4 B4 C4 ...
            |<-- Frame 1 -->|<-- Frame 2 -->|
```

**Key Points:**
- Each signal gets a **time slot** in each frame
- Samples are transmitted **sequentially**
- All signals share the **same channel**

### Advantages of TDM

1. **Digital friendly** - works naturally with digital signals
2. **Flexible** - can allocate different numbers of slots to different signals
3. **Efficient** - no guard bands needed (unlike FDM)
4. **Simple** - just switching in time

### Disadvantages of TDM

1. **Requires synchronization** - receiver must know slot boundaries
2. **Sensitive to timing errors** - misalignment causes crosstalk
3. **Requires buffering** - samples must be stored temporarily

---

## 3. TDM System Architecture {#tdm-architecture}

### Basic Block Diagram

```
Signal 1 ──┐
Signal 2 ──┤
Signal 3 ──┼──> [Commutator] ──> [Channel] ──> [Decommutator] ──┐
  ...      │                                                      │
Signal K ──┘                                                      │
                                                                   │
                                                                   ▼
                                                              [Separated Signals]
```

### Components

1. **Commutator (Multiplexer):**
   - Rotates through input signals
   - Samples each signal in sequence
   - Creates the interleaved TDM signal

2. **Channel:**
   - Transmits the TDM signal
   - Can be wire, fiber, radio, etc.

3. **Decommutator (Demultiplexer):**
   - Synchronized with commutator
   - Separates samples back to original signals
   - Routes each sample to correct output

4. **Synchronization System:**
   - Ensures commutator and decommutator are aligned
   - Critical for proper operation

---

## 4. Commutator Operation {#commutator}

### How the Commutator Works

The **commutator** is a rotating switch that connects to each input signal in sequence.

**Operation:**
1. **Rotates** at frequency $f_s$ (sampling frequency)
2. **Connects** to each input for a time slot
3. **Samples** the signal during that slot
4. **Moves** to next input
5. **Repeats** the cycle

### Mathematical Description

If we have $K$ signals, each sampled at rate $f_s$:

**Time per frame:**
$$T_f = \frac{1}{f_s}$$

**Time per slot:**
$$T_s = \frac{T_f}{K} = \frac{1}{K f_s}$$

**Slot for signal $k$:**
- Starts at: $t = (k-1)T_s + nT_f$ for frame $n$
- Duration: $T_s$

### Sampling Process

For signal $k$ with samples $x_k(nT_f)$:

The TDM signal contains:
- Frame 1: $x_1(0), x_2(0), x_3(0), \ldots, x_K(0)$
- Frame 2: $x_1(T_f), x_2(T_f), x_3(T_f), \ldots, x_K(T_f)$
- Frame 3: $x_1(2T_f), x_2(2T_f), x_3(2T_f), \ldots, x_K(2T_f)$
- And so on...

### Commutator Frequency

The **commutator rotation frequency** $f_s$ determines:
- How fast samples are taken
- The frame rate
- The bandwidth required

**Key Relationship:**
- If each signal has bandwidth $B$
- Sampling rate per signal: $f_s \geq 2B$ (Nyquist)
- Total TDM rate: $K f_s$ samples/second

---

## 5. Frame Structure and Synchronization {#frame-sync}

### Frame Structure

A **frame** is one complete cycle through all signals.

**Frame Contents:**
```
Frame = [Sync Word] + [Slot 1] + [Slot 2] + ... + [Slot K]
```

**Components:**
1. **Sync Word (Synchronization Word):**
   - Unique pattern: $s = (s_1, s_2, \ldots, s_N)$
   - Identifies frame boundaries
   - Allows receiver to synchronize

2. **Data Slots:**
   - One slot per signal
   - Contains sample value
   - Sequential order: 1, 2, 3, ..., K

### Frame Timing

**Frame Period:**
$$T_f = \frac{1}{f_s}$$

**Frame Structure:**
```
| Sync | Slot 1 | Slot 2 | ... | Slot K |
|<----------- Frame Period T_f ---------->|
```

**Slot Duration:**
$$T_{slot} = \frac{T_f - T_{sync}}{K}$$

where $T_{sync}$ is the duration of the sync word.

### Why Synchronization is Critical

**Without synchronization:**
- Receiver doesn't know where frame starts
- Samples get misrouted to wrong signals
- **Crosstalk** occurs - signal 1's samples go to signal 2, etc.
- Complete system failure!

**With synchronization:**
- Receiver knows frame boundaries
- Samples routed correctly
- Each signal reconstructed properly

---

## 6. Sampling Rate and Bandwidth {#sampling-bandwidth}

### Sampling Requirements

For TDM to work properly:

**Per Signal:**
- Each signal must be sampled at $f_s \geq 2B$ (Nyquist theorem)
- Where $B$ is the bandwidth of each signal

**Total System:**
- TDM signal contains $K$ signals
- Each sampled at rate $f_s$
- Total sampling rate: $K f_s$ samples/second

### Bandwidth Requirements

**TDM Signal Bandwidth:**
- If each signal has bandwidth $B$
- And is sampled at $f_s = 2B$ (minimum)
- TDM signal bandwidth: $B_{TDM} = K \times 2B = 2KB$

**Key Insight:**
- TDM uses **time** to separate signals
- All signals share the **same frequency band**
- Bandwidth = sum of individual signal bandwidths

### Comparison with FDM

**FDM:**
- Each signal gets its own frequency band
- Total bandwidth: $K \times 2B$ (same as TDM!)
- But needs **guard bands** between signals
- Actually uses more bandwidth

**TDM:**
- All signals use same frequency band
- Total bandwidth: $K \times 2B$
- **No guard bands needed!**
- More bandwidth efficient

---

## 7. Synchronization Methods {#synchronization}

### Why Synchronization is Needed

The receiver must know:
1. **When a frame starts** (frame synchronization)
2. **Which slot is which** (slot synchronization)
3. **Timing alignment** (clock synchronization)

### Frame Synchronization

**Method 1: Sync Word**
- Transmitter sends unique pattern at start of each frame
- Receiver searches for this pattern
- When found, knows frame boundary

**Sync Word Properties:**
- Must be **unique** - not appear in data
- Should have **good autocorrelation** - easy to detect
- Typically: Alternating pattern or specific sequence

**Example:**
- Sync word: $s = (1, -1, 1, -1, 1, -1, \ldots)$
- Or: $s = (1, 1, 1, -1, -1, -1)$ (specific pattern)

### Slot Synchronization

Once frame is synchronized:
- Receiver knows frame boundaries
- Can count slots: 1, 2, 3, ..., K
- Routes each slot to correct output

**Method:**
- After sync word, first slot = Signal 1
- Second slot = Signal 2
- And so on...

### Clock Synchronization

**Problem:** Receiver clock may drift from transmitter clock

**Solutions:**
1. **Extract clock from signal** - use transitions in TDM signal
2. **Separate clock channel** - transmit clock separately
3. **PLL (Phase-Locked Loop)** - lock receiver clock to transmitter

### Synchronization Word Detection

The receiver uses a **correlator** or **matched filter** to detect the sync word:

**Correlation:**
- Compare received signal with expected sync word
- High correlation → sync word detected
- Low correlation → not sync word

**Threshold:**
- Set threshold for detection
- Above threshold → frame start detected
- Below threshold → continue searching

---

## 8. Coincident Detector {#coincident-detector}

### What is a Coincident Detector?

A **coincident detector** is a circuit that detects when multiple conditions are met simultaneously.

**For TDM Synchronization:**
- Detects when received signal matches sync word
- Uses a **K-input AND gate** (where K is the number of bits in sync word)

### Operation

**Sync Word:** $s = (s_1, s_2, \ldots, s_K)$

**Received Signal:** $r = (r_1, r_2, \ldots, r_K)$

**Detection:**
1. Compare each bit: $r_i$ with $s_i$
2. If $r_i = s_i$ for all $i$ → match!
3. Output = 1 (sync detected)
4. If any $r_i \neq s_i$ → no match
5. Output = 0 (no sync)

### K-Input AND Gate

**Logic:**
- Input 1: $r_1 \oplus s_1$ (XOR - 0 if match, 1 if mismatch)
- Input 2: $r_2 \oplus s_2$
- ...
- Input K: $r_K \oplus s_K$

**Output:**
- If all inputs are 0 (all match) → output = 1
- If any input is 1 (any mismatch) → output = 0

**Mathematical:**
$$Output = \prod_{i=1}^{K} [1 - (r_i \oplus s_i)]$$

Where $\oplus$ is XOR (0 if equal, 1 if different).

### Why It Works

**When sync word is present:**
- All bits match: $r_i = s_i$ for all $i$
- All XOR outputs = 0
- AND gate output = 1 ✓

**When data is present:**
- Bits don't match sync pattern
- At least one XOR output = 1
- AND gate output = 0 ✓

**Result:**
- Output = 1 only when sync word is detected
- Output = 0 otherwise
- Provides reliable frame synchronization!

---

## 9. Comparison: TDM vs FDM {#tdm-vs-fdm}

### Time Division Multiplexing (TDM)

**How it works:**
- Signals take turns in time
- All use same frequency band
- Samples interleaved sequentially

**Advantages:**
- No guard bands needed
- Digital-friendly
- Flexible allocation
- Simple implementation

**Disadvantages:**
- Requires synchronization
- Sensitive to timing errors
- Needs buffering

**Bandwidth:**
- $B_{TDM} = K \times 2B$ (if $f_s = 2B$)
- No additional guard bands

### Frequency Division Multiplexing (FDM)

**How it works:**
- Signals use different frequency bands
- All transmitted simultaneously
- Separated by filters at receiver

**Advantages:**
- No synchronization needed
- Analog-friendly
- Simple separation (filters)

**Disadvantages:**
- Needs guard bands
- Less flexible
- More complex filters

**Bandwidth:**
- $B_{FDM} = K \times 2B + \text{guard bands}$
- Guard bands add overhead

### Comparison Table

| Feature | TDM | FDM |
|---------|-----|-----|
| **Separation Method** | Time slots | Frequency bands |
| **Synchronization** | Required | Not required |
| **Guard Bands** | Not needed | Needed |
| **Bandwidth Efficiency** | High | Lower (guard bands) |
| **Digital/Analog** | Digital | Analog |
| **Complexity** | Medium | Medium-High |
| **Flexibility** | High | Low |
| **Timing Sensitivity** | High | Low |

### When to Use Each

**Use TDM when:**
- Digital signals
- Synchronization available
- Need maximum efficiency
- Flexible allocation needed

**Use FDM when:**
- Analog signals
- No synchronization
- Simple separation needed
- Fixed allocation OK

---

## 10. Detailed Example: TDM System {#detailed-example}

Let's work through a **complete TDM example**.

### Problem Setup

**Given:**
- 4 voice signals, each with bandwidth $B = 4$ kHz
- Sampling rate: $f_s = 8$ kHz per signal (Nyquist rate)
- Sync word: 3 bits: $(1, 0, 1)$

**Find:**
1. Frame structure
2. Frame period $T_f$
3. Slot duration $T_s$
4. Total TDM bandwidth
5. How sync word detection works

---

### Step 1: Frame Structure

**Number of signals:** $K = 4$

**Frame Structure:**
```
| Sync (3 bits) | Signal 1 | Signal 2 | Signal 3 | Signal 4 |
|<------------------- Frame ------------------------->|
```

**Per frame:**
- 3 sync bits
- 4 data samples (one per signal)
- Total: 7 "slots" per frame

---

### Step 2: Frame Period

**Sampling rate per signal:** $f_s = 8$ kHz

**Frame period:**
$$T_f = \frac{1}{f_s} = \frac{1}{8 \times 10^3} = 0.125 \text{ ms} = 125 \mu\text{s}$$

**Frame rate:** 8,000 frames per second

---

### Step 3: Slot Duration

**If sync word takes time $T_{sync}$ and each data slot is $T_s$:**

$$T_f = T_{sync} + K T_s$$

If sync word is 3 bits and bit duration is $T_b$:
$$T_{sync} = 3 T_b$$

And if data is sampled at $f_s$:
$$T_s = \frac{1}{f_s} = 125 \mu\text{s}$$

**Actually, the slot duration depends on how we encode the samples.**

For simplicity, assume:
- Each sample is one "time unit"
- Sync word = 3 time units
- Each data slot = 1 time unit

**Slot duration:** $T_s = \frac{T_f}{K+3} = \frac{125}{7} \approx 17.86 \mu\text{s}$

---

### Step 4: Total TDM Bandwidth

**Per signal bandwidth:** $B = 4$ kHz

**Sampling rate:** $f_s = 8$ kHz = $2B$ (Nyquist)

**TDM signal contains:**
- 4 signals × 8,000 samples/sec = 32,000 samples/sec

**Bandwidth:**
$$B_{TDM} = K \times 2B = 4 \times 2 \times 4 \times 10^3 = 32 \text{ kHz}$$

**Or:** $B_{TDM} = K f_s = 4 \times 8 \times 10^3 = 32 \text{ kHz}$ ✓

---

### Step 5: Sync Word Detection

**Sync word:** $s = (1, 0, 1)$

**Coincident detector (3-input AND gate):**

**When sync word is received:**
- Received: $r = (1, 0, 1)$
- Compare: $r_1 = s_1 = 1$ ✓, $r_2 = s_2 = 0$ ✓, $r_3 = s_3 = 1$ ✓
- All match → AND gate output = 1
- **Sync detected!**

**When data is received:**
- Received: $r = (0, 1, 1)$ (example data)
- Compare: $r_1 \neq s_1$ (0 ≠ 1) ✗
- Mismatch → AND gate output = 0
- **No sync**

**Result:**
- Detector outputs 1 only at frame boundaries
- Provides reliable synchronization

---

## 11. Key Takeaways {#key-takeaways}

### Essential Concepts

1. **Multiplexing** combines multiple signals into one channel
2. **TDM** uses time slots to separate signals
3. **Synchronization** is critical for TDM operation
4. **Commutator** rotates through signals at rate $f_s$
5. **Frame** contains sync word + data slots
6. **Coincident detector** identifies sync word using AND gate
7. **Bandwidth** = $K \times 2B$ for $K$ signals of bandwidth $B$

### Key Formulas

**Frame Period:**
$$T_f = \frac{1}{f_s}$$

**Slot Duration:**
$$T_s = \frac{T_f}{K} \text{ (if no sync word)}$$

**TDM Bandwidth:**
$$B_{TDM} = K \times 2B = K f_s$$

**Sampling Rate:**
$$f_s \geq 2B \text{ (Nyquist for each signal)}$$

### Common Mistakes to Avoid

1. **Forgetting synchronization** - TDM won't work without it!
2. **Wrong bandwidth calculation** - remember it's $K \times 2B$, not just $2B$
3. **Confusing TDM and FDM** - time vs frequency separation
4. **Sync word in data** - must be unique to avoid false detection
5. **Timing errors** - can cause crosstalk between signals

### Study Tips

1. **Understand the commutator:**
   - Rotates at $f_s$
   - Samples each signal in sequence
   - Creates interleaved TDM signal

2. **Frame structure:**
   - Sync word + data slots
   - Must be unique and detectable

3. **Synchronization:**
   - Critical for operation
   - Coincident detector uses AND gate
   - Detects sync word pattern

4. **Bandwidth:**
   - TDM: $K \times 2B$ (no guard bands)
   - FDM: $K \times 2B + \text{guard bands}$
   - TDM is more efficient

5. **Applications:**
   - Digital telephone systems
   - Digital communication
   - When synchronization is available

---

## Summary of Key Formulas

### Frame and Timing
- **Frame period:** $T_f = \frac{1}{f_s}$
- **Slot duration:** $T_s = \frac{T_f}{K}$ (without sync word)
- **Commutator frequency:** $f_s$ (same as sampling rate per signal)

### Bandwidth
- **TDM bandwidth:** $B_{TDM} = K \times 2B = K f_s$
- **Per signal:** $f_s \geq 2B$ (Nyquist)

### Synchronization
- **Sync word:** Unique pattern $s = (s_1, s_2, \ldots, s_K)$
- **Coincident detector:** K-input AND gate
- **Detection:** Output = 1 when all bits match

---

*End of Group 5 Detailed Explanation*


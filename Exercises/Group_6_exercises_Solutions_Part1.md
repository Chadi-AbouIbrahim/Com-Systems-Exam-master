# Group 6 Exercises - Solutions Part 1

This document contains solutions for Exercise Sets 1-6 of Group 6 exercises.

---

## Exercise Set 1: Frequency Translation Basics - Solutions

### Problem 1.1 Solution

**a) What is frequency translation?**

**Frequency translation** (also called **frequency conversion** or **mixing**) is the process of shifting a signal from one frequency band to another.

**Key idea:** Change the carrier frequency while preserving the information (modulation).

**b) Why is frequency translation needed?**

**Reasons:**
1. **Different services use different frequency bands** - need to convert between bands
2. **Processing is easier at certain frequencies** - standardized IF frequencies
3. **Separate desired signals from interference** - channel selection
4. **Standardized design** - fixed IF simplifies receiver design

**c) What are the two types of frequency translation?**

1. **Up-conversion:** Shift signal to **higher** frequency
   - Example: Baseband → RF (Radio Frequency)
   - Used in transmitters

2. **Down-conversion:** Shift signal to **lower** frequency
   - Example: RF → IF (Intermediate Frequency)
   - Used in receivers

**d) Examples:**

**Up-conversion:**
- Transmitter: Baseband audio → RF for transmission
- Frequency hopping: Change frequency for security

**Down-conversion:**
- Receiver: RF signal → IF for processing
- Channel selection: Tune to different frequencies

---

### Problem 1.2 Solution

**Given:**
- Input signal: $f_c = 10$ MHz

**a) Up-conversion to $f_{out} = 100$ MHz:**

**Mixer produces:** $f_c + f_{LO}$ and $f_c - f_{LO}$

To get $f_{out} = 100$ MHz:
- Option 1: $f_c + f_{LO} = 100$ → $f_{LO} = 100 - 10 = 90$ MHz
- Option 2: $f_c - f_{LO} = 100$ → $f_{LO} = 10 - 100 = -90$ MHz (not possible)

**Answer:** $f_{LO} = 90$ MHz (use upper sideband)

**Frequencies produced:**
- Upper: $f_c + f_{LO} = 10 + 90 = 100$ MHz ✓ (desired)
- Lower: $f_c - f_{LO} = 10 - 90 = -80$ MHz → $80$ MHz (reject)

**b) Down-conversion to $f_{out} = 1$ MHz:**

To get $f_{out} = 1$ MHz:
- Option 1: $f_c - f_{LO} = 1$ → $f_{LO} = 10 - 1 = 9$ MHz
- Option 2: $f_c + f_{LO} = 1$ → $f_{LO} = 1 - 10 = -9$ MHz (not possible)

**Answer:** $f_{LO} = 9$ MHz (use lower sideband)

**Frequencies produced:**
- Upper: $f_c + f_{LO} = 10 + 9 = 19$ MHz (reject)
- Lower: $f_c - f_{LO} = 10 - 9 = 1$ MHz ✓ (desired)

**c) Frequencies produced by mixer:**

**Always two frequencies:**
- Sum: $f_c + f_{LO}$
- Difference: $|f_c - f_{LO}|$

**d) Which frequency to select:**

**Up-conversion:** Filter to select **upper sideband** ($f_c + f_{LO}$)

**Down-conversion:** Filter to select **lower sideband** ($f_c - f_{LO}$)

---

### Problem 1.3 Solution

**a) Purpose of up-conversion:**

**Up-conversion:**
- Shift signal to **higher frequency** for transmission
- Baseband → RF
- Allows efficient transmission through air
- Enables multiple signals on different carriers

**b) Purpose of down-conversion:**

**Down-conversion:**
- Shift signal to **lower frequency** for processing
- RF → IF
- Easier to process at lower frequency
- Standardized IF simplifies design

**c) Applications:**

**Up-conversion:**
- Transmitters
- Frequency hopping systems
- When high-frequency transmission needed

**Down-conversion:**
- Receivers (superheterodyne)
- Channel selection
- When processing at lower frequency is easier

**d) Advantages and disadvantages:**

**Up-conversion:**
- ✓ Enables high-frequency transmission
- ✓ Efficient for transmission
- ✗ Requires high-frequency components
- ✗ More complex

**Down-conversion:**
- ✓ Easier processing at lower frequency
- ✓ Standardized IF
- ✓ Better filtering possible
- ✗ Requires LO
- ✗ Image frequency problem

---

## Exercise Set 2: Mixers and Multipliers - Solutions

### Problem 2.1 Solution

**Given:**
- Input: $v_{in}(t) = 5\cos(2\pi \cdot 1 \times 10^6 t)$ → $f_c = 1$ MHz
- LO: $v_{LO}(t) = 2\cos(2\pi \cdot 5 \times 10^6 t)$ → $f_0 = 5$ MHz

**a) Mixer output:**

$$v_{out}(t) = v_{in}(t) \times v_{LO}(t)$$

$$v_{out}(t) = 5\cos(2\pi \cdot 10^6 t) \times 2\cos(2\pi \cdot 5 \times 10^6 t)$$

Using: $\cos A \cos B = \frac{1}{2}[\cos(A+B) + \cos(A-B)]$

$$v_{out}(t) = 5 \times 2 \times \frac{1}{2}[\cos(2\pi(10^6 + 5 \times 10^6)t) + \cos(2\pi(10^6 - 5 \times 10^6)t)]$$

$$v_{out}(t) = 5[\cos(2\pi \cdot 6 \times 10^6 t) + \cos(2\pi \cdot (-4 \times 10^6)t)]$$

Since $\cos(-x) = \cos(x)$:
$$v_{out}(t) = 5\cos(2\pi \cdot 6 \times 10^6 t) + 5\cos(2\pi \cdot 4 \times 10^6 t)$$

**b) Two frequencies produced:**

- Upper: $f_c + f_0 = 1 + 5 = 6$ MHz
- Lower: $|f_c - f_0| = |1 - 5| = 4$ MHz

**c) Up-conversion frequency:**

**Upper sideband:** $6$ MHz (up-conversion)

**d) Down-conversion frequency:**

**Lower sideband:** $4$ MHz (down-conversion)

---

### Problem 2.2 Solution

**Given:**
- Input: $v_{in}(t) = R(t)\cos[\omega_c t + \theta(t)]$ where $f_c = 50$ MHz
- LO: $v_{LO}(t) = A_0\cos(\omega_0 t)$ where $f_0 = 45$ MHz

**a) Mixer output expression:**

$$v_1(t) = v_{in}(t) \times v_{LO}(t)$$

$$v_1(t) = R(t)\cos[\omega_c t + \theta(t)] \times A_0\cos(\omega_0 t)$$

Using trigonometric identity:
$$v_1(t) = \frac{A_0 R(t)}{2}\cos[(\omega_c + \omega_0)t + \theta(t)] + \frac{A_0 R(t)}{2}\cos[(\omega_c - \omega_0)t + \theta(t)]$$

**b) Two output frequencies:**

- Upper: $f_c + f_0 = 50 + 45 = 95$ MHz
- Lower: $f_c - f_0 = 50 - 45 = 5$ MHz

**c) Complex envelope of up-converted signal (at 95 MHz):**

The up-converted term is:
$$\frac{A_0 R(t)}{2}\cos[(\omega_c + \omega_0)t + \theta(t)]$$

In complex form:
$$\frac{A_0 R(t)}{2}\text{Re}\{e^{j[(\omega_c + \omega_0)t + \theta(t)]}\} = \frac{A_0 R(t)}{2}\text{Re}\{e^{j\theta(t)}e^{j(\omega_c + \omega_0)t}\}$$

Complex envelope: $g_2(t) = \frac{A_0}{2}R(t)e^{j\theta(t)} = \frac{A_0}{2}g_{in}(t)$

**d) Complex envelope of down-converted signal (at 5 MHz):**

The down-converted term is:
$$\frac{A_0 R(t)}{2}\cos[(\omega_c - \omega_0)t + \theta(t)]$$

Complex envelope: $g_2(t) = \frac{A_0}{2}R(t)e^{j\theta(t)} = \frac{A_0}{2}g_{in}(t)$

**Same complex envelope!** Only carrier frequency changes.

---

### Problem 2.3 Solution

**a) Starting with $v_{out}(t) = v_{in}(t) \times v_{LO}(t)$:**

Let:
- $v_{in}(t) = A_{in}\cos(\omega_{in} t)$
- $v_{LO}(t) = A_{LO}\cos(\omega_0 t)$

**b) Using trigonometric identity:**

$$\cos A \cos B = \frac{1}{2}[\cos(A+B) + \cos(A-B)]$$

$$v_{out}(t) = A_{in}\cos(\omega_{in} t) \times A_{LO}\cos(\omega_0 t)$$

$$v_{out}(t) = \frac{A_{in} A_{LO}}{2}[\cos(\omega_{in} + \omega_0)t + \cos(\omega_{in} - \omega_0)t]$$

**c) Frequencies produced:**

- Sum frequency: $f_{in} + f_0$
- Difference frequency: $|f_{in} - f_0|$

**d) Why filtering is needed:**

**Both frequencies are always present!**
- Mixer produces both $f_{in} + f_0$ and $|f_{in} - f_0|$
- We usually want **only one** of them
- **Filtering selects** the desired frequency
- The other is rejected

**Example:**
- For up-conversion: Filter to select $f_{in} + f_0$
- For down-conversion: Filter to select $|f_{in} - f_0|$

---

## Exercise Set 3: Complex Envelope in Frequency Translation - Solutions

### Problem 3.1 Solution

**Given:**
- Input complex envelope: $g_{in}(t) = A_c e^{j\theta(t)}$

**a) Complex envelope of up-converted signal (at $f_c + f_0$):**

From mixer analysis:
$$g_2(t) = \frac{A_0}{2}g_{in}(t) = \frac{A_0}{2}A_c e^{j\theta(t)}$$

**b) Complex envelope of down-converted signal (at $f_c - f_0$):**

Same relationship:
$$g_2(t) = \frac{A_0}{2}g_{in}(t) = \frac{A_0}{2}A_c e^{j\theta(t)}$$

**c) How does complex envelope change?**

**Changes:**
- **Scaled** by constant factor $\frac{A_0}{2}$ (LO amplitude dependent)
- **Phase and amplitude modulation preserved** - $e^{j\theta(t)}$ unchanged
- **Information content unchanged**

**d) Is information content preserved?**

**Yes!** The complex envelope is preserved (scaled):
- Phase modulation: $\theta(t)$ is unchanged
- Amplitude modulation: $A_c$ is unchanged (scaled by constant)
- **All information is preserved!**

Only the **carrier frequency** changes, not the modulation.

---

### Problem 3.2 Solution

**a) Show output complex envelope: $g_2(t) = \frac{A_0}{2}g_{in}(t)$:**

**From mixer output:**
$$v_1(t) = \frac{A_0}{2}\text{Re}\{g_{in}(t)e^{j(\omega_c + \omega_0)t}\} + \frac{A_0}{2}\text{Re}\{g_{in}(t)e^{j(\omega_c - \omega_0)t}\}$$

**For up-conversion (at $f_c + f_0$):**
The term is: $\frac{A_0}{2}\text{Re}\{g_{in}(t)e^{j(\omega_c + \omega_0)t}\}$

Complex envelope: $g_2(t) = \frac{A_0}{2}g_{in}(t)$ ✓

**For down-conversion (at $f_c - f_0$):**
The term is: $\frac{A_0}{2}\text{Re}\{g_{in}(t)e^{j(\omega_c - \omega_0)t}\}$

Complex envelope: $g_2(t) = \frac{A_0}{2}g_{in}(t)$ ✓

**b) Complex envelope is preserved (scaled by constant):**

**Preservation:**
- $g_{in}(t)$ contains all modulation information
- Output: $g_2(t) = \frac{A_0}{2}g_{in}(t)$
- Only scaled by constant $\frac{A_0}{2}$
- **Modulation is preserved!**

**c) Only carrier frequency changes:**

**Input:** Carrier at $f_c$
**Output:** Carrier at $f_c + f_0$ (up) or $f_c - f_0$ (down)

**Modulation (complex envelope) unchanged!**

**d) Modulation (information) is unchanged:**

**Information is in the complex envelope:**
- Phase: $\theta(t)$ - unchanged
- Amplitude: $R(t)$ - unchanged (scaled by constant)
- **All information preserved!**

---

### Problem 3.3 Solution

**a) Start with input: $v_{in}(t) = \text{Re}\{g_{in}(t)e^{j\omega_c t}\}$:**

This represents a bandpass signal with complex envelope $g_{in}(t)$.

**b) Mixer output:**

$$v_1(t) = v_{in}(t) \times v_{LO}(t) = \text{Re}\{g_{in}(t)e^{j\omega_c t}\} \times A_0\cos(\omega_0 t)$$

Using: $\cos(\omega_0 t) = \frac{e^{j\omega_0 t} + e^{-j\omega_0 t}}{2}$

$$v_1(t) = \text{Re}\{g_{in}(t)e^{j\omega_c t}\} \times A_0 \frac{e^{j\omega_0 t} + e^{-j\omega_0 t}}{2}$$

$$v_1(t) = \frac{A_0}{2}\text{Re}\{g_{in}(t)e^{j(\omega_c + \omega_0)t}\} + \frac{A_0}{2}\text{Re}\{g_{in}(t)e^{j(\omega_c - \omega_0)t}\}$$

**c) Show output contains these terms:**

**Up-conversion term:**
$$\frac{A_0}{2}\text{Re}\{g_{in}(t)e^{j(\omega_c + \omega_0)t}\}$$

**Down-conversion term:**
$$\frac{A_0}{2}\text{Re}\{g_{in}(t)e^{j(\omega_c - \omega_0)t}\}$$

**d) Show output complex envelope is $g_2(t) = \frac{A_0}{2}g_{in}(t)$:**

**For up-conversion:**
The signal is: $\text{Re}\{g_2(t)e^{j(\omega_c + \omega_0)t}\}$

Comparing with: $\text{Re}\{g_{in}(t)e^{j(\omega_c + \omega_0)t}\}$

We have: $g_2(t) = \frac{A_0}{2}g_{in}(t)$ ✓

**Same for down-conversion!**

---

## Exercise Set 4: Nonlinear Devices and Harmonics - Solutions

### Problem 4.1 Solution

**Given:**
- Nonlinear device: $v_{out}(t) = K_2 v_{in}^2(t)$
- Input: $v_{in}(t) = R(t)\cos[\omega_c t + \theta(t)]$

**a) Output expression:**

$$v_{out}(t) = K_2 [R(t)\cos[\omega_c t + \theta(t)]]^2$$

$$v_{out}(t) = K_2 R^2(t) \cos^2[\omega_c t + \theta(t)]$$

Using: $\cos^2 x = \frac{1 + \cos(2x)}{2}$

$$v_{out}(t) = K_2 R^2(t) \frac{1 + \cos[2(\omega_c t + \theta(t))]}{2}$$

$$v_{out}(t) = \frac{K_2 R^2(t)}{2} + \frac{K_2 R^2(t)}{2}\cos[2\omega_c t + 2\theta(t)]$$

**b) Frequencies produced:**

- **DC component:** 0 Hz (from $\frac{K_2 R^2(t)}{2}$)
- **Second harmonic:** $2f_c$ (from $\cos[2\omega_c t + 2\theta(t)]$)

**c) Order of nonlinearity:**

**Second-order** ($n = 2$) because $v_{out} \propto v_{in}^2$.

**d) Harmonics present:**

- **DC:** 0 Hz
- **Second harmonic:** $2f_c$

**No fundamental frequency $f_c$!**

---

### Problem 4.2 Solution

**Given:**
- Nonlinear device: $v_{out}(t) = K_n v_{in}^n(t)$
- Input: $v_{in}(t) = R(t)\cos[\omega_c t + \theta(t)]$

**a) Show output appears at $n$-th harmonic: $nf_c$:**

**Using trigonometric identities:**
- $\cos^n(x)$ produces harmonics at $0, 2f_c, 4f_c, \ldots$ for even $n$
- Or at $f_c, 3f_c, 5f_c, \ldots$ for odd $n$

**In general:** The highest harmonic is at $nf_c$.

**For the dominant term:**
$$v_{out}(t) \approx C R^n(t)\cos[n\omega_c t + n\theta(t)]$$

This shows output at frequency $nf_c$.

**b) Show output envelope is $R^n(t)$:**

From the expression:
$$v_{out}(t) = C R^n(t)\cos[n\omega_c t + n\theta(t)]$$

The envelope is: $R^n(t)$ ✓

**c) Show output phase is $n\theta(t)$:**

From the expression:
$$v_{out}(t) = C R^n(t)\cos[n\omega_c t + n\theta(t)]$$

The phase is: $n\theta(t)$ ✓

**d) Why is filtering needed?**

**Filtering is needed because:**
1. **Multiple harmonics produced** - not just $nf_c$
2. **Unwanted frequencies** - DC, other harmonics
3. **Select desired frequency** - filter to $nf_c$
4. **Reject unwanted** - filter out other components

---

### Problem 4.3 Solution

**a) Show $v_{in}^2(t)$ produces DC, $2f_c$, and envelope terms:**

**Input:** $v_{in}(t) = R(t)\cos[\omega_c t + \theta(t)]$

**Output:**
$$v_{out}(t) = K_2 [R(t)\cos[\omega_c t + \theta(t)]]^2$$

$$= K_2 R^2(t) \cos^2[\omega_c t + \theta(t)]$$

Using: $\cos^2 x = \frac{1 + \cos(2x)}{2}$

$$v_{out}(t) = \frac{K_2 R^2(t)}{2} + \frac{K_2 R^2(t)}{2}\cos[2\omega_c t + 2\theta(t)]$$

**Components:**
- **DC term:** $\frac{K_2 R^2(t)}{2}$ (envelope-dependent DC)
- **Second harmonic:** $\frac{K_2 R^2(t)}{2}\cos[2\omega_c t + 2\theta(t)]$ at $2f_c$

**b) Frequencies present:**

- **DC:** 0 Hz (envelope-dependent)
- **Second harmonic:** $2f_c$

**c) How to select desired frequency:**

**To select $2f_c$:**
- Use **bandpass filter** centered at $2f_c$
- Rejects DC component
- Passes second harmonic

**d) Unwanted frequencies to filter:**

**Must filter:**
1. **DC component** - $\frac{K_2 R^2(t)}{2}$
2. **Other harmonics** (if present from higher-order terms)
3. **Fundamental** (if any leakage)

**Use bandpass filter** to select only $2f_c$.

---

## Exercise Set 5: Superheterodyne Receiver Architecture - Solutions

### Problem 5.1 Solution

**Block Diagram:**

```
ANTENNA
   |
   v
[RF Amplifier] ──> [RF BPF] ──> [Mixer] ──> [IF BPF] ──> [IF Amplifier] ──> [Detector] ──> OUTPUT
                        ^                              ^
                        |                              |
                   [Local Oscillator]            [Fixed IF Filter]
```

**a) Components:**

1. **RF Amplifier:** Amplifies weak received signal
2. **RF Bandpass Filter (BPF):** Selects desired frequency band, rejects image
3. **Mixer:** Multiplies RF signal with LO
4. **Local Oscillator (LO):** Generates sinusoidal signal
5. **IF Bandpass Filter:** Selects IF frequency
6. **IF Amplifier:** Provides gain at fixed IF
7. **Detector:** Extracts information (AM: envelope detector, FM: discriminator)

**b) Signal frequencies:**

- **Antenna:** RF signal at $f_c$
- **After RF filter:** RF signal at $f_c$ (filtered)
- **After mixer:** $f_c + f_{LO}$ and $f_c - f_{LO}$ (or $f_{LO} - f_c$)
- **After IF filter:** IF signal at $f_{IF}$
- **After detector:** Baseband signal (information)

**c) Function of each component:**

**RF Amplifier:** Initial gain, low noise
**RF BPF:** Channel selection, image rejection
**Mixer:** Frequency translation (RF → IF)
**LO:** Provides mixing frequency
**IF BPF:** Selects IF, rejects unwanted mixer products
**IF Amplifier:** Main gain stage
**Detector:** Information extraction

**d) Why this architecture:**

**Advantages:**
1. **Fixed IF** - all channels processed at same frequency
2. **Better filtering** - easier to build good filters at IF
3. **Gain** - amplification at fixed IF
4. **Selectivity** - better channel separation
5. **Standardization** - common IF frequencies

---

### Problem 5.2 Solution

**Given:**
- RF signal: $f_c = 100$ MHz
- IF frequency: $f_{IF} = 10.7$ MHz
- High-side LO injection

**a) LO frequency:**

For high-side injection:
$$f_{LO} = f_c + f_{IF} = 100 + 10.7 = 110.7 \text{ MHz}$$

**b) Frequency translation process:**

1. **RF signal** at $f_c = 100$ MHz enters mixer
2. **Mixed with LO** at $f_{LO} = 110.7$ MHz
3. **Mixer produces:**
   - Upper: $f_c + f_{LO} = 100 + 110.7 = 210.7$ MHz
   - Lower: $f_{LO} - f_c = 110.7 - 100 = 10.7$ MHz = **IF!** ✓
4. **IF filter** selects 10.7 MHz
5. **Signal at IF** for processing

**c) Why is IF fixed?**

**Fixed IF advantages:**
1. **All channels processed at same frequency** - simplifies design
2. **Can optimize filters, amplifiers, detectors** for one frequency
3. **Standardized components** - off-the-shelf IF filters
4. **Better performance** - easier to achieve good specs at fixed frequency

**d) Advantages of fixed IF:**

1. **Simplified design** - one set of IF components
2. **Better performance** - optimized for one frequency
3. **Cost effective** - standard components
4. **Flexibility** - tune LO to select different channels

---

### Problem 5.3 Solution

**a) Why is RF filtering needed?**

**RF filter purposes:**
1. **Select desired channel** - pass signal at $f_c$
2. **Reject image frequency** - critical for operation
3. **Reduce interference** - reject out-of-band signals
4. **Prevent overload** - reduce strong unwanted signals

**b) What does the mixer do?**

**Mixer function:**
1. **Multiplies** RF signal with LO signal
2. **Produces sum and difference frequencies**
3. **Frequency translation** - RF → IF
4. **Preserves information** - complex envelope unchanged

**c) Why is IF filtering important?**

**IF filter purposes:**
1. **Select IF frequency** - pass $f_{IF}$, reject other mixer products
2. **Reject unwanted frequencies** - $f_c + f_{LO}$ and other harmonics
3. **Channel selectivity** - separate adjacent channels
4. **Critical for performance** - determines receiver selectivity

**d) What does the detector do?**

**Detector function:**
1. **Extracts information** from IF signal
2. **AM:** Envelope detector - recovers $m(t)$
3. **FM:** Discriminator - recovers frequency deviation
4. **Output:** Baseband signal (information)

**e) Why is this architecture preferred?**

**Advantages:**
1. **Fixed IF** - simplifies design
2. **Better performance** - optimized components
3. **Flexibility** - tune LO for channel selection
4. **Standardization** - common IF frequencies
5. **Proven** - widely used in practice

---

## Exercise Set 6: Intermediate Frequency (IF) - Solutions

### Problem 6.1 Solution

**Given:**
- IF: $f_{IF} = 455$ kHz
- Desired channel: $f_c = 1000$ kHz

**a) LO frequency for high-side injection:**

$$f_{LO} = f_c + f_{IF} = 1000 + 455 = 1455 \text{ kHz}$$

**b) LO frequency for low-side injection:**

$$f_{LO} = f_c - f_{IF} = 1000 - 455 = 545 \text{ kHz}$$

**c) Which injection method for AM?**

**High-side injection** is typically used for AM broadcast receivers.

**Reason:** LO frequency is higher than signal frequency, which is often easier to implement.

**d) What happens if we tune to different channel?**

**To tune to different channel:**
- Change $f_c$ (desired channel frequency)
- **LO frequency changes:** $f_{LO} = f_c \pm f_{IF}$
- **IF stays constant!** ✓

**Example:**
- Channel 1: $f_c = 1000$ kHz → $f_{LO} = 1455$ kHz
- Channel 2: $f_c = 1200$ kHz → $f_{LO} = 1655$ kHz
- **IF:** Still 455 kHz (unchanged)

---

### Problem 6.2 Solution

**Given:**
- Channels: 540 kHz to 1600 kHz
- IF: $f_{IF} = 455$ kHz
- High-side LO injection

**a) LO frequency range:**

**For $f_c = 540$ kHz:**
$$f_{LO} = f_c + f_{IF} = 540 + 455 = 995 \text{ kHz}$$

**For $f_c = 1600$ kHz:**
$$f_{LO} = f_c + f_{IF} = 1600 + 455 = 2055 \text{ kHz}$$

**LO range:** 995 kHz to 2055 kHz

**b) Why does IF stay constant?**

**IF is fixed by design:**
- All channels processed at same IF
- Only LO frequency changes
- IF components (filters, amplifiers) stay the same
- **Simplifies design!**

**c) Advantage of fixed IF:**

1. **One set of IF components** - filters, amplifiers, detectors
2. **Optimized for one frequency** - better performance
3. **Standard components** - off-the-shelf availability
4. **Cost effective** - don't need to tune IF components

**d) How does channel selection work?**

**Channel selection:**
1. **User selects channel** (e.g., 1000 kHz)
2. **LO frequency set** to $f_{LO} = f_c + f_{IF} = 1455$ kHz
3. **Mixer translates** RF at $f_c$ to IF at $f_{IF}$
4. **IF components** process signal (same for all channels)
5. **Detector** extracts information

**Only LO is tuned!** IF stays fixed.

---

### Problem 6.3 Solution

**a) Why must IF be high enough?**

**IF must be high for:**
1. **Image rejection** - image is at $f_c + 2f_{IF}$ (high-side)
   - Higher $f_{IF}$ → image farther from desired
   - Easier to filter
2. **Separation:** $\Delta f = 2f_{IF}$
   - Larger separation → better filtering
3. **Avoid interference** - image signal far from desired

**b) Why must IF be low enough?**

**IF must be low for:**
1. **Practical filters** - easier to build good filters at lower frequencies
2. **Component availability** - standard IF frequencies (455 kHz, 10.7 MHz)
3. **Cost** - lower frequency components often cheaper
4. **Performance** - better filter characteristics at lower frequencies

**c) Common IF frequencies and why:**

1. **AM broadcast: 455 kHz**
   - Low enough for good filters
   - High enough for image rejection (AM band: 540-1600 kHz)
   - Standard, widely available

2. **FM broadcast: 10.7 MHz**
   - Higher because FM band is higher (88-108 MHz)
   - Need better image rejection
   - Standard for FM

3. **TV: 45.75 MHz**
   - Very high because TV band is very high
   - Need large separation for image rejection

**d) Trade-off in IF selection:**

**Trade-off:**
- **High IF:** Better image rejection, but harder to build good filters
- **Low IF:** Easier filters, but poor image rejection

**Solution:** Choose IF as compromise:
- High enough for adequate image rejection
- Low enough for practical filters
- **Standard values** are chosen as good compromise

---

*End of Part 1 Solutions (Exercise Sets 1-6)*


# Group 6 Exercises - Solutions Part 2

This document contains solutions for Exercise Sets 7-12 of Group 6 exercises.

---

## Exercise Set 7: Image Frequency Problem - Solutions

### Problem 7.1 Solution

**Given:**
- Desired signal: $f_c = 1000$ kHz
- IF: $f_{IF} = 455$ kHz
- High-side LO injection

**a) LO frequency:**

$$f_{LO} = f_c + f_{IF} = 1000 + 455 = 1455 \text{ kHz}$$

**b) Image frequency:**

For high-side injection:
$$f_{image} = f_c + 2f_{IF} = 1000 + 2(455) = 1910 \text{ kHz}$$

**c) Why is image frequency a problem?**

**The problem:**
- When image signal at $f_{image}$ is mixed with LO, it also produces IF!
- **Both desired and image produce IF frequency**
- **Interference!** Image signal appears in desired channel
- Cannot be separated at IF

**d) What happens if image signal is present?**

**Consequences:**
1. **Image signal also produces IF** when mixed with LO
2. **Both signals appear at IF** - cannot separate
3. **Interference** - image corrupts desired signal
4. **Degraded performance** - signal quality reduced

**Solution:** RF filter must reject image before mixing!

---

### Problem 7.2 Solution

**Given:**
- Desired: $f_c = 50$ MHz
- IF: $f_{IF} = 10.7$ MHz

**a) Image frequency (high-side injection):**

$$f_{LO} = f_c + f_{IF} = 50 + 10.7 = 60.7 \text{ MHz}$$

$$f_{image} = f_c + 2f_{IF} = 50 + 2(10.7) = 71.4 \text{ MHz}$$

**b) Image frequency (low-side injection):**

$$f_{LO} = f_c - f_{IF} = 50 - 10.7 = 39.3 \text{ MHz}$$

$$f_{image} = f_c - 2f_{IF} = 50 - 2(10.7) = 28.6 \text{ MHz}$$

**c) Separation between desired and image:**

**High-side:**
$$\Delta f = f_{image} - f_c = 71.4 - 50 = 21.4 \text{ MHz}$$

**Low-side:**
$$\Delta f = f_c - f_{image} = 50 - 28.6 = 21.4 \text{ MHz}$$

**Same separation:** $\Delta f = 2f_{IF} = 21.4$ MHz

**d) Which injection gives better image rejection?**

**Both give same separation** ($2f_{IF}$), but:

**High-side injection:**
- Image is **above** desired frequency
- Often easier to filter (if no signals above desired)

**Low-side injection:**
- Image is **below** desired frequency
- May be easier if no signals below desired

**Choice depends on:**
- Frequency band location
- Available filter characteristics
- System requirements

**For this case:** Both similar, but high-side often preferred.

---

### Problem 7.3 Solution

**a) For high-side injection: $f_{LO} = f_c + f_{IF}$:**

**Desired signal at $f_c$:**
When mixed with LO:
$$f_{LO} - f_c = (f_c + f_{IF}) - f_c = f_{IF}$$ ✓

**b) Show image at $f_{image} = f_c + 2f_{IF}$ also produces IF:**

**Image signal at $f_{image} = f_c + 2f_{IF}$:**
When mixed with LO at $f_{LO} = f_c + f_{IF}$:
$$f_{image} - f_{LO} = (f_c + 2f_{IF}) - (f_c + f_{IF}) = f_{IF}$$ ✓

**Both produce IF!** This is the problem.

**c) For low-side injection: $f_{LO} = f_c - f_{IF}$:**

**Desired signal at $f_c$:**
When mixed with LO:
$$f_c - f_{LO} = f_c - (f_c - f_{IF}) = f_{IF}$$ ✓

**d) Show image at $f_{image} = f_c - 2f_{IF}$ also produces IF:**

**Image signal at $f_{image} = f_c - 2f_{IF}$:**
When mixed with LO at $f_{LO} = f_c - f_{IF}$:
$$f_{LO} - f_{image} = (f_c - f_{IF}) - (f_c - 2f_{IF}) = f_{IF}$$ ✓

**Both produce IF!** Same problem.

**e) Why is image always $2f_{IF}$ away from desired?**

**Mathematical relationship:**

**For high-side injection:**
- Desired: $f_c$
- LO: $f_{LO} = f_c + f_{IF}$
- Image must satisfy: $f_{image} - f_{LO} = f_{IF}$
- Therefore: $f_{image} = f_{LO} + f_{IF} = (f_c + f_{IF}) + f_{IF} = f_c + 2f_{IF}$

**Separation:**
$$\Delta f = f_{image} - f_c = (f_c + 2f_{IF}) - f_c = 2f_{IF}$$

**Always $2f_{IF}$ away!**

**For low-side:** Same result, image is $2f_{IF}$ below desired.

---

## Exercise Set 8: RF Filtering and Image Rejection - Solutions

### Problem 8.1 Solution

**Given:**
- RF filter: 30 dB attenuation at image
- Desired signal power: 1 mW
- Image signal power: 1 mW (before filtering)

**a) Image power after filtering:**

**30 dB attenuation means:**
$$\text{Power ratio} = 10^{-30/10} = 10^{-3} = 0.001$$

**Image power after filtering:**
$$P_{image,out} = P_{image,in} \times 0.001 = 1 \times 0.001 = 0.001 \text{ mW} = 1 \mu\text{W}$$

**b) Image rejection ratio:**

$$\text{Image Rejection} = \frac{P_{desired}}{P_{image,out}} = \frac{1 \text{ mW}}{0.001 \text{ mW}} = 1000 = 30 \text{ dB}$$

**c) Is this adequate?**

**30 dB rejection:**
- Image is 1000× weaker than desired
- **May be adequate** for some applications
- **May not be enough** for high-quality systems
- Typically want **40-60 dB** for good performance

**d) What happens if attenuation is insufficient?**

**Insufficient attenuation:**
1. **Image interference** - image signal appears in desired channel
2. **Degraded signal quality** - noise, distortion
3. **Crosstalk** - interference from image channel
4. **Poor performance** - system unusable

**Solution:** Need better RF filter or higher IF.

---

### Problem 8.2 Solution

**Given:**
- Desired: $f_c = 1000$ kHz
- IF: $f_{IF} = 455$ kHz
- Image: $f_{image} = 1910$ kHz
- RF filter: 40 dB attenuation at image

**a) Separation between desired and image:**

$$\Delta f = f_{image} - f_c = 1910 - 1000 = 910 \text{ kHz}$$

**b) Why is this separation important?**

**Separation is critical:**
- **Larger separation** → easier to filter
- **Smaller separation** → harder to filter
- **910 kHz separation** is good - easy to filter
- Allows RF filter to pass desired and reject image

**c) Image rejection ratio:**

**40 dB attenuation:**
$$\text{Power ratio} = 10^{-40/10} = 10^{-4} = 0.0001$$

**Image rejection:**
$$\text{Rejection} = \frac{1}{0.0001} = 10,000 = 40 \text{ dB}$$

**d) What IF would give better rejection?**

**Better rejection with higher IF:**

**Current:** $f_{IF} = 455$ kHz → $\Delta f = 910$ kHz → 40 dB rejection

**If $f_{IF} = 500$ kHz:**
- $\Delta f = 2 \times 500 = 1000$ kHz (larger separation)
- **Easier to filter** → potentially better rejection
- But: Higher IF may be harder to build good filters

**Trade-off:** Higher IF → better separation but harder IF filters.

---

### Problem 8.3 Solution

**a) Why must RF filter pass desired signal?**

**RF filter must:**
1. **Pass desired signal** at $f_c$ with **low loss**
2. **Preserve signal quality** - minimal distortion
3. **Allow signal through** for processing
4. **Critical for sensitivity** - any loss reduces signal strength

**b) Why must it reject image frequency?**

**RF filter must:**
1. **Reject image** at $f_{image}$ with **high attenuation**
2. **Prevent interference** - image would corrupt desired signal
3. **Critical for operation** - without rejection, system fails
4. **High attenuation needed** - typically 40-60 dB

**c) How does IF frequency affect filter design?**

**Relationship:** $\Delta f = 2f_{IF}$

**Higher IF:**
- Larger $\Delta f$ → easier to separate desired and image
- **Easier filter design** - can use simpler filter
- **Better rejection possible** - larger separation

**Lower IF:**
- Smaller $\Delta f$ → harder to separate
- **Harder filter design** - need sharper filter
- **Worse rejection** - smaller separation

**d) Relationship: $\Delta f = 2f_{IF}$:**

**Derivation:**
- Image frequency: $f_{image} = f_c + 2f_{IF}$ (high-side)
- Desired frequency: $f_c$
- Separation: $\Delta f = f_{image} - f_c = 2f_{IF}$ ✓

**This is fundamental relationship!**

**e) Why does higher IF help?**

**Higher IF advantages:**
1. **Larger separation:** $\Delta f = 2f_{IF}$ increases
2. **Easier filtering** - larger gap between desired and image
3. **Better rejection** - filter can more easily separate them
4. **More margin** - less critical filter design

**Example:**
- $f_{IF} = 10$ kHz → $\Delta f = 20$ kHz (hard to filter)
- $f_{IF} = 455$ kHz → $\Delta f = 910$ kHz (easy to filter)

**Higher IF → better image rejection!**

---

## Exercise Set 9: Numerical Problems - Solutions

### Problem 9.1 Solution

**Given:**
- Input: $v_{in}(t) = 3\cos(2\pi \cdot 2 \times 10^6 t)$ → $f_c = 2$ MHz
- LO: $v_{LO}(t) = 2\cos(2\pi \cdot 8 \times 10^6 t)$ → $f_0 = 8$ MHz

**a) Mixer output frequencies:**

$$v_{out}(t) = v_{in}(t) \times v_{LO}(t)$$

Using: $\cos A \cos B = \frac{1}{2}[\cos(A+B) + \cos(A-B)]$

**Frequencies:**
- Upper: $f_c + f_0 = 2 + 8 = 10$ MHz
- Lower: $|f_c - f_0| = |2 - 8| = 6$ MHz

**b) Output expression:**

$$v_{out}(t) = 3 \times 2 \times \frac{1}{2}[\cos(2\pi \cdot 10 \times 10^6 t) + \cos(2\pi \cdot 6 \times 10^6 t)]$$

$$v_{out}(t) = 3\cos(2\pi \cdot 10 \times 10^6 t) + 3\cos(2\pi \cdot 6 \times 10^6 t)$$

**c) Up-conversion frequency:**

**Upper sideband:** $10$ MHz (up-conversion)

**d) Down-conversion frequency:**

**Lower sideband:** $6$ MHz (down-conversion)

**e) If we want output at 10 MHz:**

**Filter to select upper sideband:**
- Use **bandpass filter** centered at 10 MHz
- Reject 6 MHz component
- Output: $3\cos(2\pi \cdot 10 \times 10^6 t)$

---

### Problem 9.2 Solution

**Given:**
- Desired channel: $f_c = 1200$ kHz
- IF: $f_{IF} = 455$ kHz
- High-side injection
- RF filter: 35 dB rejection at image

**a) LO frequency:**

$$f_{LO} = f_c + f_{IF} = 1200 + 455 = 1655 \text{ kHz}$$

**b) Image frequency:**

$$f_{image} = f_c + 2f_{IF} = 1200 + 2(455) = 2110 \text{ kHz}$$

**c) Separation between desired and image:**

$$\Delta f = f_{image} - f_c = 2110 - 1200 = 910 \text{ kHz}$$

**d) Image rejection ratio:**

**35 dB attenuation:**
$$\text{Power ratio} = 10^{-35/10} = 10^{-3.5} = 3.162 \times 10^{-4}$$

**Image rejection:**
$$\text{Rejection} = \frac{1}{3.162 \times 10^{-4}} = 3162 = 35 \text{ dB}$$

**Image is 3162× weaker than desired.**

---

### Problem 9.3 Solution

**Given:**
- FM channels: 88 MHz to 108 MHz
- IF: $f_{IF} = 10.7$ MHz
- High-side injection

**a) LO frequency range:**

**For $f_c = 88$ MHz:**
$$f_{LO} = f_c + f_{IF} = 88 + 10.7 = 98.7 \text{ MHz}$$

**For $f_c = 108$ MHz:**
$$f_{LO} = f_c + f_{IF} = 108 + 10.7 = 118.7 \text{ MHz}$$

**LO range:** 98.7 MHz to 118.7 MHz

**b) Image frequency range:**

**For $f_c = 88$ MHz:**
$$f_{image} = f_c + 2f_{IF} = 88 + 2(10.7) = 109.4 \text{ MHz}$$

**For $f_c = 108$ MHz:**
$$f_{image} = f_c + 2f_{IF} = 108 + 2(10.7) = 129.4 \text{ MHz}$$

**Image range:** 109.4 MHz to 129.4 MHz

**c) Minimum separation between desired and image:**

**Separation:** $\Delta f = 2f_{IF} = 2(10.7) = 21.4$ MHz

**This is constant** for all channels.

**d) Why is this IF frequency used?**

**10.7 MHz IF for FM:**
1. **High enough** - provides 21.4 MHz separation (good image rejection)
2. **Low enough** - practical to build good filters
3. **Standard** - widely available components
4. **Good compromise** - balances image rejection and filter design
5. **Proven** - used in all FM receivers

---

## Exercise Set 10: Conceptual Questions - Solutions

### Problem 10.1 Solution

**a) Why does a mixer always produce two frequencies?**

**Mathematical reason:**
- Mixer multiplies: $v_{out} = v_{in} \times v_{LO}$
- Using: $\cos A \cos B = \frac{1}{2}[\cos(A+B) + \cos(A-B)]$
- **Always produces sum and difference frequencies**
- Cannot produce only one frequency

**Physical reason:**
- Multiplication in time domain = convolution in frequency domain
- Creates sum and difference components
- **Fundamental property** of mixing

**b) Why is filtering needed after mixing?**

**Filtering is needed because:**
1. **Two frequencies produced** - we usually want only one
2. **Select desired frequency** - up or down conversion
3. **Reject unwanted frequency** - prevent interference
4. **Remove harmonics** - if nonlinear device used
5. **Critical for operation** - without filtering, both frequencies present

**c) What happens to complex envelope in frequency translation?**

**Complex envelope is preserved:**
- Input: $g_{in}(t)$
- Output: $g_2(t) = \frac{A_0}{2}g_{in}(t)$
- **Only scaled by constant** - modulation unchanged
- **Information preserved!**

**d) Why is information preserved in mixing?**

**Information is in complex envelope:**
- Complex envelope contains all modulation
- Mixer preserves complex envelope (scaled)
- Only carrier frequency changes
- **Modulation (information) unchanged!**

---

### Problem 10.2 Solution

**a) Why is superheterodyne architecture used?**

**Advantages:**
1. **Fixed IF** - all channels processed at same frequency
2. **Better filtering** - easier to build good filters at IF
3. **Gain** - amplification at fixed IF
4. **Selectivity** - better channel separation
5. **Standardization** - common IF frequencies
6. **Proven** - widely used, reliable

**b) Why is IF frequency fixed?**

**Fixed IF advantages:**
1. **One set of components** - filters, amplifiers, detectors
2. **Optimized design** - can optimize for one frequency
3. **Standard components** - off-the-shelf availability
4. **Cost effective** - don't need tunable IF components
5. **Better performance** - optimized for one frequency

**c) What is the image frequency problem?**

**The problem:**
- Image frequency at $f_{image} = f_c + 2f_{IF}$ (high-side)
- When mixed with LO, **also produces IF**
- **Both desired and image appear at IF**
- Cannot be separated at IF
- **Interference!**

**Solution:** RF filter must reject image before mixing.

**d) How does RF filtering solve the image problem?**

**RF filter solution:**
1. **Passes desired signal** at $f_c$ (low loss)
2. **Rejects image signal** at $f_{image}$ (high attenuation, 40-60 dB)
3. **Image removed before mixing** - doesn't reach IF
4. **Only desired signal** produces IF
5. **Problem solved!**

**Key:** Filter must have good rejection at image frequency.

---

### Problem 10.3 Solution

**a) Relationship between IF and image rejection:**

**Relationship:** $\Delta f = 2f_{IF}$

**Higher IF:**
- Larger separation $\Delta f$
- **Easier to filter** - larger gap
- **Better rejection possible**

**Lower IF:**
- Smaller separation $\Delta f$
- **Harder to filter** - smaller gap
- **Worse rejection**

**b) Why must IF be high enough?**

**For image rejection:**
- Need separation: $\Delta f = 2f_{IF}$
- Larger $\Delta f$ → easier filtering
- **Higher IF → better image rejection**

**Example:**
- $f_{IF} = 10$ kHz → $\Delta f = 20$ kHz (hard to filter)
- $f_{IF} = 455$ kHz → $\Delta f = 910$ kHz (easy to filter)

**c) Why must IF be low enough?**

**For practical filters:**
- Lower frequencies → easier to build good filters
- Better filter characteristics at lower frequencies
- **Lower IF → better filter performance**

**Trade-off:**
- High IF: Better image rejection, but harder filters
- Low IF: Easier filters, but worse image rejection

**d) Trade-off in IF selection:**

**The trade-off:**
1. **High IF:**
   - ✓ Better image rejection
   - ✗ Harder to build good filters
   - ✗ More expensive components

2. **Low IF:**
   - ✓ Easier to build good filters
   - ✓ Cheaper components
   - ✗ Worse image rejection

**Solution:** Choose IF as compromise:
- **High enough** for adequate image rejection
- **Low enough** for practical filters
- **Standard values** (455 kHz, 10.7 MHz) are good compromises

---

## Exercise Set 11: Derivation Problems - Solutions

### Problem 11.1 Solution

**Derive mixer output expression:**

**a) Start with $v_{out}(t) = v_{in}(t) \times v_{LO}(t)$:**

Let:
- $v_{in}(t) = R(t)\cos[\omega_c t + \theta(t)]$
- $v_{LO}(t) = A_0\cos(\omega_0 t)$

**b) Use trigonometric identity:**

$$\cos A \cos B = \frac{1}{2}[\cos(A+B) + \cos(A-B)]$$

**c) Apply identity:**

$$v_{out}(t) = R(t)\cos[\omega_c t + \theta(t)] \times A_0\cos(\omega_0 t)$$

$$v_{out}(t) = A_0 R(t) \cos[\omega_c t + \theta(t)] \cos(\omega_0 t)$$

Using identity with $A = \omega_c t + \theta(t)$ and $B = \omega_0 t$:

$$v_{out}(t) = A_0 R(t) \times \frac{1}{2}[\cos(\omega_c t + \theta(t) + \omega_0 t) + \cos(\omega_c t + \theta(t) - \omega_0 t)]$$

$$v_{out}(t) = \frac{A_0 R(t)}{2}\cos[(\omega_c + \omega_0)t + \theta(t)] + \frac{A_0 R(t)}{2}\cos[(\omega_c - \omega_0)t + \theta(t)]$$

**d) Show output has frequencies $f_c + f_0$ and $f_c - f_0$:**

From the expression:
- First term: $\cos[(\omega_c + \omega_0)t + \theta(t)]$ → frequency $f_c + f_0$
- Second term: $\cos[(\omega_c - \omega_0)t + \theta(t)]$ → frequency $f_c - f_0$

**Result:** Mixer produces frequencies $f_c + f_0$ and $f_c - f_0$ ✓

---

### Problem 11.2 Solution

**Derive complex envelope relationship:**

**a) Input: $v_{in}(t) = \text{Re}\{g_{in}(t)e^{j\omega_c t}\}$:**

This represents a bandpass signal with complex envelope $g_{in}(t)$.

**b) Mixer output:**

$$v_1(t) = v_{in}(t) \times v_{LO}(t) = \text{Re}\{g_{in}(t)e^{j\omega_c t}\} \times A_0\cos(\omega_0 t)$$

Using: $\cos(\omega_0 t) = \frac{e^{j\omega_0 t} + e^{-j\omega_0 t}}{2}$

$$v_1(t) = \text{Re}\{g_{in}(t)e^{j\omega_c t}\} \times A_0 \frac{e^{j\omega_0 t} + e^{-j\omega_0 t}}{2}$$

$$v_1(t) = \frac{A_0}{2}\text{Re}\{g_{in}(t)e^{j(\omega_c + \omega_0)t}\} + \frac{A_0}{2}\text{Re}\{g_{in}(t)e^{j(\omega_c - \omega_0)t}\}$$

**c) Show output complex envelope is $g_2(t) = \frac{A_0}{2}g_{in}(t)$:**

**For up-conversion term:**
$$\frac{A_0}{2}\text{Re}\{g_{in}(t)e^{j(\omega_c + \omega_0)t}\}$$

This is: $\text{Re}\{g_2(t)e^{j(\omega_c + \omega_0)t}\}$ where $g_2(t) = \frac{A_0}{2}g_{in}(t)$ ✓

**For down-conversion term:**
$$\frac{A_0}{2}\text{Re}\{g_{in}(t)e^{j(\omega_c - \omega_0)t}\}$$

This is: $\text{Re}\{g_2(t)e^{j(\omega_c - \omega_0)t}\}$ where $g_2(t) = \frac{A_0}{2}g_{in}(t)$ ✓

**d) Explain why information is preserved:**

**Information is in complex envelope:**
- Input: $g_{in}(t)$ contains all modulation
- Output: $g_2(t) = \frac{A_0}{2}g_{in}(t)$
- **Only scaled by constant** - modulation unchanged
- Phase: $\theta(t)$ - unchanged
- Amplitude: $R(t)$ - unchanged (scaled)
- **All information preserved!**

---

### Problem 11.3 Solution

**Derive image frequency formula:**

**a) For high-side injection: $f_{LO} = f_c + f_{IF}$:**

**Desired signal at $f_c$:**
When mixed with LO:
$$f_{LO} - f_c = (f_c + f_{IF}) - f_c = f_{IF}$$ ✓

**b) Show desired signal produces: $f_{LO} - f_c = f_{IF}$:**

From above: $f_{LO} - f_c = f_{IF}$ ✓

**c) Show image at $f_{image} = f_c + 2f_{IF}$ produces: $f_{image} - f_{LO} = f_{IF}$:**

**Image signal at $f_{image} = f_c + 2f_{IF}$:**
When mixed with LO at $f_{LO} = f_c + f_{IF}$:
$$f_{image} - f_{LO} = (f_c + 2f_{IF}) - (f_c + f_{IF}) = f_{IF}$$ ✓

**Both produce IF!** This is why image is a problem.

**d) Show separation: $\Delta f = f_{image} - f_c = 2f_{IF}$:**

**Separation:**
$$\Delta f = f_{image} - f_c = (f_c + 2f_{IF}) - f_c = 2f_{IF}$$ ✓

**Result:** Image is always $2f_{IF}$ away from desired frequency.

---

## Exercise Set 12: Combined Problems - Solutions

### Problem 12.1 Solution

**Given:**
- Desired: $s(t) = m(t)\cos[\omega_c t]$ at $f_c = 1000$ kHz
- Adjacent channel: $s_1(t) = m_1(t)\cos[(\omega_c + 2\omega_{IF})t]$ at $f_c + 2f_{IF}$
- IF: $f_{IF} = 455$ kHz
- High-side injection
- RF filter: 40 dB attenuation at image

**a) LO frequency:**

$$f_{LO} = f_c + f_{IF} = 1000 + 455 = 1455 \text{ kHz}$$

**b) Image frequency:**

$$f_{image} = f_c + 2f_{IF} = 1000 + 2(455) = 1910 \text{ kHz}$$

**This is the adjacent channel frequency!**

**c) Mixer output for desired signal:**

$$v_2(t) = s(t) \times v_{LO}(t) = m(t)\cos[\omega_c t] \times A_0\cos[\omega_{LO} t]$$

$$v_2(t) = \frac{A_0 m(t)}{2}\cos[(\omega_c + \omega_{LO})t] + \frac{A_0 m(t)}{2}\cos[(\omega_{LO} - \omega_c)t]$$

**Frequencies:**
- Upper: $f_c + f_{LO} = 1000 + 1455 = 2455$ kHz
- Lower: $f_{LO} - f_c = 1455 - 1000 = 455$ kHz = **IF!** ✓

**IF output:**
$$v_{IF}(t) = \frac{A_0 m(t)}{2}\cos[\omega_{IF} t]$$

**d) Mixer output for image signal:**

$$v_2(t) = s_1(t) \times v_{LO}(t) = m_1(t)\cos[(\omega_c + 2\omega_{IF})t] \times A_0\cos[\omega_{LO} t]$$

**Frequencies:**
- Upper: $(f_c + 2f_{IF}) + f_{LO} = 1910 + 1455 = 3365$ kHz
- Lower: $f_{LO} - (f_c + 2f_{IF}) = 1455 - 1910 = -455$ kHz → $455$ kHz

**Image also produces IF!**

**IF output from image:**
$$v_{IF,image}(t) = \frac{A_0 m_1(t)}{2}\cos[\omega_{IF} t]$$

**e) Total IF output:**

**Without RF filtering:**
$$v_{IF,total}(t) = \frac{A_0 m(t)}{2}\cos[\omega_{IF} t] + \frac{A_0 m_1(t)}{2}\cos[\omega_{IF} t]$$

$$v_{IF,total}(t) = \frac{A_0}{2}[m(t) + m_1(t)]\cos[\omega_{IF} t]$$

**Both signals appear at IF!** (Interference)

**f) Image rejection ratio:**

**40 dB attenuation:**
$$\text{Power ratio} = 10^{-40/10} = 10^{-4} = 0.0001$$

**Image rejection:**
$$\text{Rejection} = \frac{1}{0.0001} = 10,000 = 40 \text{ dB}$$

**Image is 10,000× weaker than desired** (after RF filtering).

**With RF filter:**
- Desired signal: Full strength
- Image signal: Reduced by 40 dB
- **Image interference is small!**

---

### Problem 12.2 Solution

**Given:**
- Channels: 540-1600 kHz (AM broadcast)
- IF: $f_{IF} = 455$ kHz
- High-side injection
- Image rejection: $\geq 40$ dB

**a) LO frequency range:**

**For $f_c = 540$ kHz:**
$$f_{LO} = f_c + f_{IF} = 540 + 455 = 995 \text{ kHz}$$

**For $f_c = 1600$ kHz:**
$$f_{LO} = f_c + f_{IF} = 1600 + 455 = 2055 \text{ kHz}$$

**LO range:** 995 kHz to 2055 kHz

**b) Image frequency range:**

**For $f_c = 540$ kHz:**
$$f_{image} = f_c + 2f_{IF} = 540 + 2(455) = 1450 \text{ kHz}$$

**For $f_c = 1600$ kHz:**
$$f_{image} = f_c + 2f_{IF} = 1600 + 2(455) = 2510 \text{ kHz}$$

**Image range:** 1450 kHz to 2510 kHz

**c) Minimum separation between desired and image:**

**Separation:** $\Delta f = 2f_{IF} = 2(455) = 910$ kHz

**This is constant** for all channels.

**d) Is 40 dB rejection achievable?**

**Yes!** With 910 kHz separation:
- **Easy to filter** - large gap
- **RF filter can provide 40 dB** or more rejection
- **Standard design** - 40 dB is typical for AM receivers

**e) What IF would give better rejection?**

**Higher IF gives better separation:**

**Current:** $f_{IF} = 455$ kHz → $\Delta f = 910$ kHz

**If $f_{IF} = 500$ kHz:**
- $\Delta f = 2(500) = 1000$ kHz (larger)
- **Easier to filter** → potentially better rejection
- But: May be harder to build good IF filters

**Trade-off:** Higher IF → better image rejection but harder IF filters.

**455 kHz is a good compromise** for AM broadcast.

---

### Problem 12.3 Solution

**Given:**
- Input: $v_{in}(t) = 4\cos(2\pi \cdot 50 \times 10^6 t + \phi(t))$ → $f_c = 50$ MHz
- LO: $v_{LO}(t) = 3\cos(2\pi \cdot 45 \times 10^6 t)$ → $f_0 = 45$ MHz
- Complex envelope: $g_{in}(t) = 4e^{j\phi(t)}$

**a) Mixer output frequencies:**

**Frequencies:**
- Upper: $f_c + f_0 = 50 + 45 = 95$ MHz
- Lower: $f_c - f_0 = 50 - 45 = 5$ MHz

**b) Output complex envelope (up-conversion at 95 MHz):**

From mixer analysis:
$$g_2(t) = \frac{A_0}{2}g_{in}(t) = \frac{3}{2} \times 4e^{j\phi(t)} = 6e^{j\phi(t)}$$

**c) Output complex envelope (down-conversion at 5 MHz):**

Same relationship:
$$g_2(t) = \frac{A_0}{2}g_{in}(t) = 6e^{j\phi(t)}$$

**d) If we want output at 5 MHz:**

**Select lower sideband:**
- Use **bandpass filter** centered at 5 MHz
- Reject 95 MHz component
- Output: Down-converted signal at 5 MHz

**e) What filter is needed?**

**Bandpass filter:**
- **Center frequency:** 5 MHz
- **Bandwidth:** Appropriate for signal bandwidth
- **Reject:** 95 MHz and other unwanted frequencies
- **Purpose:** Select down-converted signal, reject up-converted

---

*End of Part 2 Solutions (Exercise Sets 7-12)*

*Good luck with your exam preparation!*


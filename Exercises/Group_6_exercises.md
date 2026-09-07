# Group 6 Exercises - Frequency Translation & Receiver Design

This document contains exercises and problems covering mixers, frequency translation, and superheterodyne receivers from Lectures 14 & 16.

---

## Exercise Set 1: Frequency Translation Basics

### Problem 1.1 (Basic)
Explain the concept of frequency translation:

a) What is frequency translation?
b) Why is frequency translation needed in communication systems?
c) What are the two types of frequency translation?
d) Give examples of each type

---

### Problem 1.2 (Intermediate)
A signal at $f_c = 10$ MHz needs to be translated.

Find:
a) Up-conversion to $f_{out} = 100$ MHz - what LO frequency is needed?
b) Down-conversion to $f_{out} = 1$ MHz - what LO frequency is needed?
c) In each case, what frequencies are produced by the mixer?
d) Which frequency should be selected by filtering?

---

### Problem 1.3 (Advanced)
Compare up-conversion and down-conversion:

a) What is the purpose of up-conversion?
b) What is the purpose of down-conversion?
c) What are the applications of each?
d) What are the advantages and disadvantages?

---

## Exercise Set 2: Mixers and Multipliers

### Problem 2.1 (Basic)
A mixer multiplies two signals:
- Input signal: $v_{in}(t) = 5\cos(2\pi \cdot 1 \times 10^6 t)$
- Local oscillator: $v_{LO}(t) = 2\cos(2\pi \cdot 5 \times 10^6 t)$

Find:
a) The mixer output $v_{out}(t)$
b) The two frequencies produced
c) Which frequency is for up-conversion?
d) Which frequency is for down-conversion?

---

### Problem 2.2 (Intermediate)
A bandpass signal is mixed with a local oscillator:
- Input: $v_{in}(t) = R(t)\cos[\omega_c t + \theta(t)]$ where $f_c = 50$ MHz
- LO: $v_{LO}(t) = A_0\cos(\omega_0 t)$ where $f_0 = 45$ MHz

Find:
a) The mixer output expression
b) The two output frequencies
c) The complex envelope of the up-converted signal
d) The complex envelope of the down-converted signal

---

### Problem 2.3 (Advanced)
Show that a mixer always produces two frequencies:

a) Starting with $v_{out}(t) = v_{in}(t) \times v_{LO}(t)$
b) Use trigonometric identity: $\cos A \cos B = \frac{1}{2}[\cos(A+B) + \cos(A-B)]$
c) Show that frequencies are $f_{in} + f_{LO}$ and $|f_{in} - f_{LO}|$
d) Explain why filtering is needed to select the desired frequency

---

## Exercise Set 3: Complex Envelope in Frequency Translation

### Problem 3.1 (Basic)
A signal has complex envelope $g_{in}(t) = A_c e^{j\theta(t)}$.

After mixing with LO at frequency $f_0$:

Find:
a) The complex envelope of the up-converted signal (at $f_c + f_0$)
b) The complex envelope of the down-converted signal (at $f_c - f_0$)
c) How does the complex envelope change?
d) Is the information content preserved?

---

### Problem 3.2 (Intermediate)
For a mixer with input complex envelope $g_{in}(t)$ and LO amplitude $A_0$:

Show that:
a) Output complex envelope: $g_2(t) = \frac{A_0}{2}g_{in}(t)$
b) The complex envelope is preserved (scaled by constant)
c) Only the carrier frequency changes
d) The modulation (information) is unchanged

---

### Problem 3.3 (Advanced)
Derive the complex envelope relationship:

a) Start with input: $v_{in}(t) = \text{Re}\{g_{in}(t)e^{j\omega_c t}\}$
b) Mix with LO: $v_{LO}(t) = A_0\cos(\omega_0 t)$
c) Show mixer output contains: $g_{in}(t)e^{j(\omega_c + \omega_0)t}$ and $g_{in}(t)e^{j(\omega_c - \omega_0)t}$
d) Show output complex envelope is $g_2(t) = \frac{A_0}{2}g_{in}(t)$

---

## Exercise Set 4: Nonlinear Devices and Harmonics

### Problem 4.1 (Basic)
A nonlinear device has output: $v_{out}(t) = K_2 v_{in}^2(t)$

Given input: $v_{in}(t) = R(t)\cos[\omega_c t + \theta(t)]$

Find:
a) The output expression
b) The frequencies produced
c) What is the order of nonlinearity?
d) What harmonics are present?

---

### Problem 4.2 (Intermediate)
A nonlinear device produces: $v_{out}(t) = K_n v_{in}^n(t)$

For input: $v_{in}(t) = R(t)\cos[\omega_c t + \theta(t)]$

Show that:
a) Output appears at $n$-th harmonic: $nf_c$
b) Output envelope is $R^n(t)$
c) Output phase is $n\theta(t)$
d) Why is filtering needed?

---

### Problem 4.3 (Advanced)
Analyze a second-order nonlinear device:

a) Show that $v_{in}^2(t)$ produces DC, $2f_c$, and envelope terms
b) What frequencies are present in the output?
c) How can the desired frequency be selected?
d) What unwanted frequencies must be filtered?

---

## Exercise Set 5: Superheterodyne Receiver Architecture

### Problem 5.1 (Basic)
Draw and label the block diagram of a superheterodyne receiver:

a) Show all components
b) Label the signal frequencies at each point
c) Explain the function of each component
d) Why is this architecture used?

---

### Problem 5.2 (Intermediate)
A superheterodyne receiver has:
- RF signal at $f_c = 100$ MHz
- IF frequency: $f_{IF} = 10.7$ MHz
- High-side LO injection

Find:
a) LO frequency $f_{LO}$
b) The frequency translation process
c) Why is IF fixed?
d) What are the advantages of fixed IF?

---

### Problem 5.3 (Advanced)
Explain the superheterodyne receiver operation:

a) Why is RF filtering needed?
b) What does the mixer do?
c) Why is IF filtering important?
d) What does the detector do?
e) Why is this architecture preferred?

---

## Exercise Set 6: Intermediate Frequency (IF)

### Problem 6.1 (Basic)
A superheterodyne receiver uses IF frequency $f_{IF} = 455$ kHz.

Given desired channel at $f_c = 1000$ kHz:

Find:
a) LO frequency for high-side injection
b) LO frequency for low-side injection
c) Which injection method is typically used for AM?
d) What happens if we want to tune to a different channel?

---

### Problem 6.2 (Intermediate)
A receiver needs to tune to channels from 540 kHz to 1600 kHz.

Given:
- IF frequency: $f_{IF} = 455$ kHz
- High-side LO injection

Find:
a) LO frequency range
b) Why does IF stay constant?
c) What is the advantage of fixed IF?
d) How does channel selection work?

---

### Problem 6.3 (Advanced)
Analyze IF selection criteria:

a) Why must IF be high enough?
b) Why must IF be low enough?
c) What are common IF frequencies and why?
d) What is the trade-off in IF selection?

---

## Exercise Set 7: Image Frequency Problem

### Problem 7.1 (Basic)
A superheterodyne receiver has:
- Desired signal: $f_c = 1000$ kHz
- IF frequency: $f_{IF} = 455$ kHz
- High-side LO injection

Find:
a) LO frequency $f_{LO}$
b) Image frequency $f_{image}$
c) Why is image frequency a problem?
d) What happens if image signal is present?

---

### Problem 7.2 (Intermediate)
For a receiver with $f_c = 50$ MHz and $f_{IF} = 10.7$ MHz:

Find:
a) Image frequency (high-side injection)
b) Image frequency (low-side injection)
c) Separation between desired and image
d) Which injection gives better image rejection?

---

### Problem 7.3 (Advanced)
Derive the image frequency formula:

a) For high-side injection: $f_{LO} = f_c + f_{IF}$
b) Show that image at $f_{image} = f_c + 2f_{IF}$ also produces IF
c) For low-side injection: $f_{LO} = f_c - f_{IF}$
d) Show that image at $f_{image} = f_c - 2f_{IF}$ also produces IF
e) Why is image always $2f_{IF}$ away from desired?

---

## Exercise Set 8: RF Filtering and Image Rejection

### Problem 8.1 (Basic)
An RF filter provides 30 dB attenuation at image frequency.

Given:
- Desired signal power: 1 mW
- Image signal power: 1 mW (before filtering)

Find:
a) Image power after filtering
b) Image rejection ratio
c) Is this adequate?
d) What happens if attenuation is insufficient?

---

### Problem 8.2 (Intermediate)
A receiver has:
- Desired: $f_c = 1000$ kHz
- IF: $f_{IF} = 455$ kHz
- Image: $f_{image} = 1910$ kHz
- RF filter: 40 dB attenuation at image

Find:
a) Separation between desired and image
b) Why is this separation important?
c) Image rejection ratio
d) What IF would give better rejection?

---

### Problem 8.3 (Advanced)
Analyze RF filter requirements:

a) Why must RF filter pass desired signal?
b) Why must it reject image frequency?
c) How does IF frequency affect filter design?
d) What is the relationship: $\Delta f = 2f_{IF}$?
e) Why does higher IF help?

---

## Exercise Set 9: Numerical Problems

### Problem 9.1
A mixer has:
- Input: $v_{in}(t) = 3\cos(2\pi \cdot 2 \times 10^6 t)$
- LO: $v_{LO}(t) = 2\cos(2\pi \cdot 8 \times 10^6 t)$

Find:
a) Mixer output frequencies
b) Output expression
c) Which frequency is up-conversion?
d) Which frequency is down-conversion?
e) If we want output at 10 MHz, which should we filter?

---

### Problem 9.2
A superheterodyne AM receiver:
- Desired channel: $f_c = 1200$ kHz
- IF: $f_{IF} = 455$ kHz
- High-side injection

Find:
a) LO frequency
b) Image frequency
c) Separation between desired and image
d) If RF filter provides 35 dB rejection at image, what is image rejection ratio?

---

### Problem 9.3
Design a receiver for FM broadcast:
- Channels: 88 MHz to 108 MHz
- IF: $f_{IF} = 10.7$ MHz
- High-side injection

Find:
a) LO frequency range
b) Image frequency range
c) Minimum separation between desired and image
d) Why is this IF frequency used?

---

## Exercise Set 10: Conceptual Questions

### Problem 10.1
Answer the following:

a) Why does a mixer always produce two frequencies?
b) Why is filtering needed after mixing?
c) What happens to the complex envelope in frequency translation?
d) Why is information preserved in mixing?

---

### Problem 10.2
Explain:

a) Why is the superheterodyne architecture used?
b) Why is IF frequency fixed?
c) What is the image frequency problem?
d) How does RF filtering solve the image problem?

---

### Problem 10.3
Discuss:

a) What is the relationship between IF and image rejection?
b) Why must IF be high enough?
c) Why must IF be low enough?
d) What is the trade-off in IF selection?

---

## Exercise Set 11: Derivation Problems

### Problem 11.1
Derive the mixer output expression:

a) Start with $v_{out}(t) = v_{in}(t) \times v_{LO}(t)$
b) Use $v_{in}(t) = R(t)\cos[\omega_c t + \theta(t)]$ and $v_{LO}(t) = A_0\cos(\omega_0 t)$
c) Apply trigonometric identity: $\cos A \cos B = \frac{1}{2}[\cos(A+B) + \cos(A-B)]$
d) Show output has frequencies $f_c + f_0$ and $f_c - f_0$

---

### Problem 11.2
Derive the complex envelope relationship:

a) Input: $v_{in}(t) = \text{Re}\{g_{in}(t)e^{j\omega_c t}\}$
b) Mixer output: $v_1(t) = \frac{A_0}{2}\text{Re}\{g_{in}(t)e^{j(\omega_c + \omega_0)t}\} + \frac{A_0}{2}\text{Re}\{g_{in}(t)e^{j(\omega_c - \omega_0)t}\}$
c) Show that output complex envelope is $g_2(t) = \frac{A_0}{2}g_{in}(t)$
d) Explain why information is preserved

---

### Problem 11.3
Derive the image frequency formula:

a) For high-side injection: $f_{LO} = f_c + f_{IF}$
b) Show desired signal produces: $f_{LO} - f_c = f_{IF}$
c) Show image at $f_{image} = f_c + 2f_{IF}$ produces: $f_{image} - f_{LO} = f_{IF}$
d) Show separation: $\Delta f = f_{image} - f_c = 2f_{IF}$

---

## Exercise Set 12: Combined Problems

### Problem 12.1
A complete superheterodyne AM receiver:

Given:
- Desired signal: $s(t) = m(t)\cos[\omega_c t]$ at $f_c = 1000$ kHz
- Adjacent channel: $s_1(t) = m_1(t)\cos[(\omega_c + 2\omega_{IF})t]$ at $f_c + 2f_{IF}$
- IF: $f_{IF} = 455$ kHz
- High-side injection
- RF filter: 40 dB attenuation at image

Find:
a) LO frequency
b) Image frequency
c) Mixer output for desired signal
d) Mixer output for image signal
e) Total IF output
f) Image rejection ratio

---

### Problem 12.2
Design a superheterodyne receiver:

Requirements:
- Tune to channels: 540-1600 kHz (AM broadcast)
- IF: $f_{IF} = 455$ kHz
- High-side injection
- Image rejection: $\geq 40$ dB

Find:
a) LO frequency range
b) Image frequency range
c) Minimum separation between desired and image
d) Is 40 dB rejection achievable?
e) What IF would give better rejection?

---

### Problem 12.3
Analyze a mixer system:

Given:
- Input: $v_{in}(t) = 4\cos(2\pi \cdot 50 \times 10^6 t + \phi(t))$
- LO: $v_{LO}(t) = 3\cos(2\pi \cdot 45 \times 10^6 t)$
- Complex envelope: $g_{in}(t) = 4e^{j\phi(t)}$

Find:
a) Mixer output frequencies
b) Output complex envelope (up-conversion)
c) Output complex envelope (down-conversion)
d) If we want output at 5 MHz, which frequency should be selected?
e) What filter is needed?

---

*Good luck with your exam preparation!*


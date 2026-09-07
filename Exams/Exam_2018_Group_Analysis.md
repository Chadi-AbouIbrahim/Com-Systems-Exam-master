# Fall 2018 Exam - Group Relevance Analysis

## Overview
This document maps each problem from the Fall 2018 Communication Systems exam to the relevant study groups (Group 1-6).

---

## Problem 1: (10 points: 5×2) - Multiple Topics

### Part (a): Delta Modulation (DM) Sampling Frequency
**Relevant Group:** **Group 4** (Digital & Pulse Modulation)
- **Topics:** Delta Modulation, sampling frequency effects
- **Concepts:** Advantages/disadvantages of increasing sampling frequency in DM systems
- **Key Points:**
  - Higher sampling frequency → better tracking, less slope overload
  - Higher sampling frequency → more bandwidth required, more granular noise

### Part (b): TDM Synchronization Word Length
**Relevant Group:** **Group 5** (Multiplexing)
- **Topics:** Time Division Multiplexing, synchronization
- **Concepts:** Synchronization word length K in TDM systems
- **Key Points:**
  - Longer K → better synchronization reliability
  - Longer K → more overhead, reduced efficiency

### Part (c): Adaptive Delta Modulation (ADM)
**Relevant Group:** **Group 4** (Digital & Pulse Modulation)
- **Topics:** Adaptive Delta Modulation
- **Concepts:** Advantages/disadvantages of ADM
- **Key Points:**
  - Adaptive step-size → better performance
  - More complex implementation

### Part (d): DSB-SC-AM vs Conventional AM
**Relevant Group:** **Group 2** (Analog Modulation - Amplitude-based)
- **Topics:** DSB-SC, Standard AM comparison
- **Concepts:** Power efficiency, carrier suppression
- **Key Points:**
  - DSB-SC: No carrier → better power efficiency
  - DSB-SC: Requires coherent detection (product detector)

### Part (e): Product Detector vs Envelope Detector
**Relevant Group:** **Group 2** (Analog Modulation - Amplitude-based)
- **Topics:** AM demodulation methods
- **Concepts:** Product detector vs envelope detector
- **Key Points:**
  - Product detector: Coherent, works for DSB-SC
  - Envelope detector: Non-coherent, simpler, only for AM with carrier

---

## Problem 2: (5 points: 2,3) - Channel Characteristics

### Part (a): Inter-Symbol Interference (ISI)
**Relevant Group:** **Group 6** (Frequency Translation & Receiver Design) - *Partial*
- **Topics:** Channel bandwidth, ISI
- **Concepts:** Channel bandwidth vs signal bandwidth
- **Key Points:**
  - Channel bandwidth (2 MHz) > Signal bandwidth (1 MHz) → No ISI
  - ISI occurs when channel bandwidth < signal bandwidth

### Part (b): Nyquist First Method for Eliminating ISI
**Relevant Group:** **Group 6** (Frequency Translation & Receiver Design) - *Partial*
- **Topics:** Nyquist criterion, impulse response
- **Concepts:** Maximum baud rate calculation
- **Key Points:**
  - $h_e(t) = \text{sinc}^2(200t)$
  - Find maximum baud rate satisfying Nyquist criterion

---

## Problem 3: (5 points) - Delta Modulation

**Relevant Group:** **Group 4** (Digital & Pulse Modulation)
- **Topics:** Delta Modulation, step-size calculation
- **Concepts:** Slope overload vs granular noise trade-off
- **Given:**
  - Signal: $w(t) = 10\cos(200\pi t)$
  - Transmission rate: 10 kbits/s
- **Key Points:**
  - Find step-size that eliminates slope overload
  - Minimize granular noise
  - Requires finding maximum slope of signal

---

## Problem 4: (10 points: 7,3) - TDM System Design

**Relevant Group:** **Group 5** (Multiplexing)
- **Topics:** TDM system design, commutator, frame structure
- **Concepts:** 
  - Multiple sources (analog and digital)
  - Pulse stuffing
  - PCM encoding
  - Raised cosine filter
- **Given:**
  - One analog source: 100 Hz bandwidth
  - One analog source: 300 Hz bandwidth
  - Three digital sources: 235 bits/s each
  - 3-bit PCM codewords
  - Two commutators allowed
- **Key Points:**
  - Design TDM system block diagram
  - Calculate data rates at various points
  - Find absolute bandwidth with raised cosine filter (r=0.5)

---

## Problem 5: (10 points: 2,2,3,3) - Modulation Power Calculations

### Part (a): DSB-SC AM Power
**Relevant Group:** **Group 2** (Analog Modulation - Amplitude-based)
- **Topics:** DSB-SC AM, normalized average power
- **Given:** $m(t) = \cos(200\pi t)$, $A_c = 10$
- **Key Points:**
  - DSB-SC: $P_s = \frac{A_c^2}{2}P_m$
  - No carrier power

### Part (b): FM Power
**Relevant Group:** **Group 3** (Analog Modulation - Angle-based)
- **Topics:** Frequency Modulation, power calculation
- **Given:** $m(t) = \cos(200\pi t)$, $A_c = 10$
- **Key Points:**
  - FM power: $P_s = \frac{A_c^2}{2}$ (constant, independent of modulation)
  - Power is constant regardless of modulation index

### Part (c): AM Power
**Relevant Group:** **Group 2** (Analog Modulation - Amplitude-based)
- **Topics:** Standard AM, normalized average power
- **Given:** $m(t) = \cos(200\pi t)$, $A_c = 10$
- **Key Points:**
  - AM: $P_s = \frac{A_c^2}{2}\left(1 + \frac{\mu^2}{2}\right)$
  - Includes carrier and sideband power

### Part (d): USSB AM Power
**Relevant Group:** **Group 2** (Analog Modulation - Amplitude-based)
- **Topics:** Upper Single-Sideband AM, power calculation
- **Given:** $m(t) = \cos(200\pi t)$, $A_c = 10$
- **Key Points:**
  - SSB power: $P_s = \frac{A_c^2}{4}P_m$
  - Only one sideband present

---

## Problem 6: (10 points: 3,3,4) - AM Detection

**Relevant Group:** **Group 2** (Analog Modulation - Amplitude-based)
- **Topics:** AM demodulation, product detector, envelope detector
- **Given:** 
  - $m(t) = 2\sin(2\pi f_1 t)$
  - $A_c = 1$
  - Carrier frequency: $f_c$
- **Key Points:**
  - Product detector output expression
  - Envelope detector output expression
  - Sketch AM signal and envelope detector output
  - Detection success analysis

---

## Problem 7: (5 points) - LSSB AM Spectrum

**Relevant Group:** **Group 2** (Analog Modulation - Amplitude-based)
- **Topics:** Lower Single-Sideband AM, spectrum analysis
- **Given:**
  - Baseband spectrum (shown in figure)
  - $f_c = 1$ MHz
  - $A_c = 100$
- **Key Points:**
  - Find complex envelope $G(f)$ first
  - Sketch LSSB spectrum
  - Only lower sideband present

---

## Problem 8: (5 points) - Nonlinear System Harmonic Distortion

**Relevant Group:** **Group 3** (Analog Modulation - Angle-based) - *Partial*
- **Topics:** Nonlinear systems, harmonic distortion
- **Given:** $y(t) = x^3(t)$
- **Key Points:**
  - Let $x(t) = \cos(\omega_c t)$
  - Find total harmonic distortion
  - Related to angle modulation analysis (nonlinear devices)

---

## Problem 9: (5 points) - Peak Envelope Power (PEP)

**Relevant Group:** **Group 1** (Foundations of Modulation)
- **Topics:** Peak envelope power, complex envelope
- **Given:** $s(t) = 5\cos((\omega_c - \omega_a)t) + 5\cos((\omega_c + \omega_a)t)$
- **Key Points:**
  - Find normalized peak envelope power
  - Relates to complex envelope representation
  - $PEP = \frac{1}{2}\max|g(t)|^2$

---

## Problem 10: (6 points: 2,2,2) - Superheterodyne Receiver

**Relevant Group:** **Group 6** (Frequency Translation & Receiver Design)
- **Topics:** Superheterodyne receiver, LO frequency, image frequency, IF filter
- **Given:**
  - FM radio tuned to 100 MHz
  - High-side LO injection
  - IF = 10 MHz
- **Key Points:**
  - Calculate LO frequency: $f_{LO} = f_c + f_{IF} = 110$ MHz
  - Calculate image frequency: $f_{image} = f_{LO} + f_{IF} = 120$ MHz
  - IF filter requirements for 200 kHz bandwidth

---

## Problem 11: (9 points: 3,3,3) - PM and FM Analysis

**Relevant Group:** **Group 3** (Analog Modulation - Angle-based)
- **Topics:** Phase Modulation, Frequency Modulation, power, modulation constants
- **Given:** 
  - $s(t) = 100\cos(2\pi \cdot 10^8 t + 4\cos(300\pi t))$
  - Part (b): PM with $D_p = 100$ rad/V
  - Part (c): FM with $D_f = 10^4$ rad/(V·s)
- **Key Points:**
  - Calculate average power in 50-Ω resistor
  - Find modulating signal for PM case
  - Find modulating signal for FM case
  - Relationship between PM and FM

---

## Problem 12: (5 points) - PM Spectrum

**Relevant Group:** **Group 3** (Analog Modulation - Angle-based)
- **Topics:** Phase Modulation, spectrum, Carson's bandwidth
- **Given:** $s(t) = 10\cos(2\pi \cdot 10^6 t + \sin(2000\pi t))$
- **Key Points:**
  - Sketch magnitude spectrum $|S(f)|$ for positive frequencies
  - Show only spectrum within Carson's bandwidth
  - Use Bessel functions for sideband amplitudes
  - Modulation index: $\beta = 1$

---

## Problem 13: (5 points) - Envelope Detector Design

**Relevant Group:** **Group 2** (Analog Modulation - Amplitude-based)
- **Topics:** Envelope detector, RC time constant
- **Given:**
  - Carrier frequency: 1 MHz
  - Modulating signal bandwidth: 5 kHz
- **Key Points:**
  - Find appropriate range for RC time constant
  - Must satisfy: $\frac{1}{f_c} \ll RC \ll \frac{1}{B}$
  - Prevents distortion and carrier ripple

---

## Problem 14: (10 points: 4,2,4) - FM/PM Instantaneous Frequency

**Relevant Group:** **Group 3** (Analog Modulation - Angle-based)
- **Topics:** Frequency Modulation, instantaneous frequency, peak frequency deviation
- **Given:** 
  - $s(t) = \cos\left(2\pi f_c t + 5\int_{-\infty}^{t} m(\sigma) d\sigma\right)$
  - $m(t)$ shown in figure
- **Key Points:**
  - Sketch instantaneous frequency
  - Find peak frequency deviation
  - Identify which figure best describes $s(t)$ variation
  - Relates to FM analysis

---

## Summary by Group

### Group 1 (Foundations of Modulation)
- **Problem 9:** Peak Envelope Power (PEP) - 5 points

### Group 2 (Analog Modulation - Amplitude-based)
- **Problem 1d:** DSB-SC vs AM - 2 points
- **Problem 1e:** Product vs Envelope Detector - 2 points
- **Problem 5a:** DSB-SC Power - 2 points
- **Problem 5c:** AM Power - 3 points
- **Problem 5d:** USSB AM Power - 3 points
- **Problem 6:** AM Detection - 10 points
- **Problem 7:** LSSB Spectrum - 5 points
- **Problem 13:** Envelope Detector Design - 5 points
- **Total: ~32 points**

### Group 3 (Analog Modulation - Angle-based)
- **Problem 5b:** FM Power - 2 points
- **Problem 8:** Harmonic Distortion - 5 points
- **Problem 11:** PM/FM Analysis - 9 points
- **Problem 12:** PM Spectrum - 5 points
- **Problem 14:** FM Instantaneous Frequency - 10 points
- **Total: ~31 points**

### Group 4 (Digital & Pulse Modulation)
- **Problem 1a:** DM Sampling Frequency - 2 points
- **Problem 1c:** ADM - 2 points
- **Problem 3:** DM Step-size - 5 points
- **Total: ~9 points**

### Group 5 (Multiplexing)
- **Problem 1b:** TDM Synchronization - 2 points
- **Problem 4:** TDM System Design - 10 points
- **Total: ~12 points**

### Group 6 (Frequency Translation & Receiver Design)
- **Problem 2:** ISI and Nyquist - 5 points
- **Problem 10:** Superheterodyne Receiver - 6 points
- **Total: ~11 points**

---

## Notes

1. **Problem 2** is partially related to Group 6 but also involves general channel theory
2. **Problem 8** (harmonic distortion) is tangentially related to Group 3 through nonlinear device analysis
3. Some problems span multiple groups (e.g., Problem 1 covers Groups 2, 4, and 5)
4. The exam heavily emphasizes **Group 2** (AM) and **Group 3** (PM/FM) with ~63 points combined
5. **Group 1** has minimal coverage (only 5 points)
6. **Group 4** and **Group 5** have moderate coverage (~21 points combined)

---

*Analysis completed based on Fall 2018 Communication Systems Final Exam*


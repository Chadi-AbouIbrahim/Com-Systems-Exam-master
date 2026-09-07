# Communication Systems - Comprehensive Study Guide

This study guide organizes formulas and concepts from the lecture materials into 6 logical groups for comprehensive exam preparation.

---

## Lecture 2 - Power Spectral Density

### Key Formulas

**Formula 1: Energy of a real-valued signal $w(t)$**
$$E = \lim_{T \to \infty} \int_{-T/2}^{T/2} w^2(t) dt$$

**Formula 2: Power of a real-valued signal $w(t)$**
$$P = \lim_{T \to \infty} \frac{1}{T} \int_{-T/2}^{T/2} w^2(t) dt = \langle w^2(t) \rangle$$

**Formula 3: Time Average Operator**
$$\langle w(t) \rangle = \lim_{T \to \infty} \frac{1}{T} \int_{-T/2}^{T/2} w(t) dt$$
For periodic signals with period $T_0$: $\langle w(t) \rangle = \frac{1}{T_0} \int_{T_0} w(t) dt$

**Formula 4: Fourier Transform**
$$W(f) = \mathcal{F}[w(t)] = \int_{-\infty}^{\infty} w(t) e^{-j2\pi ft} dt$$

**Formula 5: Average power related to PSD**
$$P = \int_{-\infty}^{\infty} \mathcal{P}_w(f) df$$

**Formula 6: Autocorrelation of a real power waveform**
$$R_w(\tau) = \langle w(t)w(t+\tau) \rangle = \lim_{T \to \infty} \frac{1}{T} \int_{-T/2}^{T/2} w(t)w(t+\tau) dt$$
For periodic signals: $R_w(\tau) = \frac{1}{T_0} \int_{T_0} w(t)w(t+\tau) dt$

**Formula 7: Average power from Autocorrelation**
$$P = R_w(0)$$

**Formula 8: Wiener-Khintchine theorem**
$$\mathcal{P}_w(f) = \mathcal{F}[R_w(\tau)]$$

### Key Concepts

- **Energy vs. Power Signals:** 
  - Energy Signals have finite $E$ ($P = 0$), e.g., Rectangular pulse.
  - Power Signals have finite $P$ ($E \to \infty$), e.g., Sinusoidal function.
- **DC Component:** The DC component (direct current) of $w(t)$ is its time average $W_{dc} = \langle w(t) \rangle$.
- **Fourier Transform of Real Signals:** If $w(t)$ is real, then $W(-f) = W^*(f)$, $|W(f)|$ is even, and $\theta(f)$ is odd.
- **Power Spectral Density (PSD):** $\mathcal{P}_w(f)$ is a real, even, and non-negative function. It describes how power is distributed in the frequency domain. It is expressed in W/Hz.
- **Autocorrelation Function:** $R_w(\tau)$ describes the resemblance of a waveform with a shifted version of itself.
- **Properties of Autocorrelation:**
  - It is an even function: $R_w(\tau) = R_w(-\tau)$.
  - If $w(t)$ is periodic with $T_0$, then $R_w(\tau)$ is also periodic with $T_0$.
  - It verifies: $R_w(0) \geq |R_w(\tau)|$ for all $\tau$.

---

## Lecture 3 - Orthogonal Representation of Signals

### Key Formulas

**Formula 1: Condition for Orthogonal Functions**
$$\int_a^b \phi_n(t)\phi_m^*(t) dt = \begin{cases} 0, & n \neq m \\ K_n, & n = m \end{cases} = K_n \delta_{nm}$$

**Formula 2: Orthogonal Series Representation**
$$w(t) = \sum_n a_n \phi_n(t)$$
where the coefficients are given by: $a_n = \frac{1}{K_n} \int_a^b w(t)\phi_n^*(t) dt$

**Formula 3: Fourier Series Coefficients**
$$c_n = \frac{1}{T_0} \int_{a}^{a+T_0} w(t)e^{-jn\omega_0 t} dt$$
where $\omega_0 = 2\pi f_0 = \frac{2\pi}{T_0}$

**Formula 4: Spectrum of Periodic Waveforms**
$$W(f) = \sum_{n \in \mathbb{Z}} c_n \delta(f - nf_0)$$

**Formula 5: Power Spectral Density of Periodic Waveforms**
$$\mathcal{P}_w(f) = \sum_{n \in \mathbb{Z}} |c_n|^2 \delta(f - nf_0)$$

**Formula 6: Average Power from Fourier Coefficients**
$$P = \sum_{n \in \mathbb{Z}} |c_n|^2$$

**Formula 7: Power Transfer Function of LTI Systems**
$$\mathcal{P}_y(f) = |H(f)|^2 \mathcal{P}_x(f)$$
where $G_h(f) = |H(f)|^2$ is the power transfer function.

**Formula 8: Distortion-less Channel Conditions**
Time domain: $y(t) = A x(t - T_d)$
Frequency domain: $Y(f) = A e^{-j2\pi T_d f} X(f)$
Implies: $|H(f)| = A$ (constant) and $\arg[H(f)] = -2\pi T_d f$ (linear phase)

### Key Concepts

- **Orthogonal vs. Orthonormal:** A set $\{\phi_n(t)\}$ is orthogonal if the integral of the product of different functions is zero over $[a,b]$. It is orthonormal if $K_n = 1$. The complex exponentials $\{e^{jn\omega_0t}\}$ form an orthogonal set (with $K_n = T_0$) over any interval of length $T_0$.
- **Fourier Series Properties:** If $w(t)$ is real, $c_n = c_{-n}^*$. If $w(t)$ is real and even, $\text{Im}[c_n] = 0$. If $w(t)$ is real and odd, $\text{Re}[c_n] = 0$.
- **PSD of Periodic Signals:** The PSD consists of impulses located at harmonics $nf_0$, scaled by the squared magnitude of the Fourier coefficients $|c_n|^2$.
- **LTI Systems:** The PSD of the output of an LTI system is simply the input PSD multiplied by the squared magnitude of the system's transfer function (the power transfer function).
- **Distortion-less Transmission:** For a signal to pass through a channel without distortion, the channel must scale all frequencies by the same amount (flat amplitude response) and delay all frequencies by the same amount of time (linear phase response).

---

## GROUP 1 - Foundations of Modulation

### Lecture 13

#### Key Formulas

**Formula 1:**

$$v(t) = R(t)\cos[\omega_c t + \theta(t)] = x(t)\cos(\omega_c t) - y(t)\sin(\omega_c t)$$

**Formula 2:**

$$v(t) = \text{Re}\{g(t)e^{j\omega_c t}\} = \text{Re}\{R(t)e^{j(\omega_c t + \theta(t))}\} = R(t)\cos[\omega_c t + \theta(t)]$$

**Formula 3:**

$$s(t) = \text{Re}\{g(t)e^{j\omega_c t}\}$$

**Formula 4:**

$$g(t) =g[m(t)]$$

**Formula 5:**

$$g(t) = A_c[1 + m(t)] = R(t)e^{j\theta(t)} \Rightarrow R(t) = A_c[1 + m(t)], \quad \theta(t) = 0$$

**Formula 6:**

$$V(f) = \frac{1}{2}[G(f - f_c) + G^*(-f - f_c)]$$

**Formula 7:**

$$R_v(\tau) = \frac{1}{2}\text{Re}\{R_g(\tau)e^{j\omega_c \tau}\}$$

**Formula 8:**

$$P_v(f) = \mathcal{F}[R_v(\tau)] = \frac{1}{4}[P_g(f - f_c) + P_g^*(-f - f_c)]$$

**Formula 9:**

$$g(f) =P_g(f)$$

**Formula 10:**

$$g(t) =A_c[1+m(t)]$$

**Formula 11:**

$$V(f) = \frac{1}{2}[G(f - f_c) + G^*(-f - f_c)] = \frac{1}{2}[G(f - f_c) + G(f + f_c)]$$

**Formula 12:**

$$S(f) = \frac{1}{2}A_c[\delta(f - f_c) + M(f - f_c) + \delta(f + f_c) + M(f + f_c)]$$

**Formula 13:**

$$s(t) = \text{Re}\{g(t)e^{j\omega_c t}\} = g(t)\cos(\omega_c t) = A_c[1 + m(t)]\cos(\omega_c t)$$


#### Key Concepts

- Any physical bandpass waveform (about ±fc) can be

- associated carrier frequency ( ωc= 2πfc)

- quadrature modulation associated with v(t)

- modulated signal): Bandpass and real

- complex envelope): Baseband and complex

- bandpass signal s(t) (modulated signal)

- modulated signal is given by: s(t) =Re/braceleftbig g(t)ejωct/bracerightbig whereωc= 2πfcandfcis the carrier frequency

- complex envelope g(t) is a function of m(t): g(t) =g[m(t)] whereg[

- complex envelope representation of signals

- bandpass signal v(t) can be calculated from: Pv=/an}bracketle{tv2(t)/an}bracketri}ht=/integraldisplay+∞ −∞Pv(f)df=Rv(0) =1 2/an}bracketle{t|g(t)|2/an}bracketri}ht Proof: We have previously proven the ﬁrst 3 equaliti

- average signal power becomes: Ps=1 2A2 c[1+Pm] where:Pm=/an}bracketle{tm2(t)/an}bracketri}htis the average power of the modulating signalm(t)


---

## GROUP 2 - Analog Modulation (Amplitude-based)

### Lecture 17

#### Key Formulas

**Formula 1:**

$$g(t) =A_c[1+m(t)]$$

**Formula 2:**

$$s(t) = A_c[1 + m(t)]\cos(\omega_c t)$$

**Formula 3:**

$$R(t) = |g(t)| = A_c[1 + m(t)]$$

**Formula 4:**

$$S(f) = \frac{A_c}{2}[\delta(f - f_c) + M(f - f_c) + \delta(f + f_c) + M(f + f_c)]$$

**Formula 5:**

$$s(t) = A_c m(t)\cos(\omega_c t)$$

**Formula 6:**

$$v_{in}(t) = \text{Re}\{g(t)e^{j\omega_c t}\} = g(t)\cos(\omega_c t)$$

**Formula 7:**

$$v_{out}(t) = \frac{1}{2}g(t)$$

**Formula 8:**

$$v_{out}(t) = \frac{A_c}{2}m(t)$$

**Formula 9:**

$$g(t) = A_c[m(t) + j\hat{m}(t)]$$

**Formula 10:**

$$G(f) = A_c[M(f) + j\mathcal{F}[\hat{m}(t)]] = A_c M(f)[1 + jH(f)] = \begin{cases} 2A_c M(f), & f > 0 \\ 0, & f < 0 \end{cases}$$

**Formula 11:**

$$S(f) =1 2[G(f−f_c)+G∗(−f−f_c)]$$


#### Key Concepts

- that the in-phase component of the complex envelope is

- that only the sideband component conveys information.

- that USSB-AM signals and LSSB-AM signals occupy the

- complex envelope of an AM signal is given by: g(t) =Ac[1+m(t)] whereAc>0 andm(t) is the modulating signal

- AM signal is given by: s(t) =Ac[1+m(t)]cos(ωct) wherefcis the carrier frequency

- complex envelope is x(t) =Ac[1+m(t)] while the quadrature component is y(t) = 0

- real envelope ( R(t) =|g(t)|) is equal to Ac[1+m(t)] whenm(t)≥ −1

- AM signal when m(t) is sinusoidal (with peak-to-peak value of one)

- AM signal is said to be 100% modulated

- modulating signal m(t) can be recovered by using either: Product detector (with θ0= 0)

- real envelope will be the same as the complex envelope: R(t) =|g(t)|=g(t)

- product detector must be used in order to recover an undistorted version of m(t)

- product detector is superior to the envelope detector

- AM signal is: /angbracketleftbig s2(t)/angbracketrightbig =1 2/angbracketleftbig g2(t)/angbracketrightbig =1 2A2 c/angbracketleftbig [1+m(t)]2/angbracketrightbig =1 2A2 c/angbracketleftbig 1+2m(t)+m2(t)/angbra

- peak envelope power of the AM signal is: PPEP=1 2{max|g(t)|}2 =1 2A2 c{1+max[ m(t)]}2 Communication Systems Lecture-17: Amplitude Modulation Amplitude Modulation (6) Given that s(t) =Ac[1+m(t)]cos(ωct), then the

- AM signal is given by: S(f)=Ac[δ(f)+M(f)]∗/bracketleftbigg1 2δ(f−fc)+1 2δ(f+fc)/bracketrightbigg =Ac 2[δ(f−fc)+M(f−fc)+δ(f+fc)+M(f+fc)] The bandwidth of the AM signal is 2 Bwhile the bandwidth of the modulatin

- AM signal that has a suppressed discrete carrier

- product detector can be used for the demodulation of both AM and DSB-SC signals

- modulated signal can be written as vin(t) =Re{g(t)ejωct}=g(t)cos(ωct) since g(t) =Ac[1+m(t)] for AM and g(t) =Acm(t) for DSB-SC where both expressions are real valued

- complex envelope: g(t) =Ac[m(t)+jˆm(t)] where ˆm(t) denotes the Hilbert transform ofm(t) given by: ˆm(t)/definesm(t)∗h(t)/definesm(t)∗1 πt whereH(f) =F[h(t)] corresponds to a −90◦phase-shift: H(f) =/braceleftbigg−j,f

- complex envelope: g(t) =Ac[m(t)−jˆm(t)] The LSSB-AM signal is given by: s(t) =Ac[m(t)cos(ωct)+ ˆm(t)sin(ωct)] Note that USSB-AM signals and LSSB-AM signals occupy the same bandwidth as the modulating signal m(t) (thi


### Lecture 15

#### Key Formulas

**Formula 1:**

$$v_{in}(t) = R(t)\cos[\omega_c t + \theta(t)]$$

**Formula 2:**

$$vin(t) =\text{Re}\{ g(t)e^{j\omega_ct}$$

**Formula 3:**

$$v_{out}(t) = K R(t) = K|g(t)| = K A_c|1 + m(t)|$$

**Formula 4:**

$$v_1(t) = R(t)\cos[\omega_c t + \theta(t)] A_0\cos(\omega_c t + \theta_0) = \frac{1}{2}A_0 R(t)\cos[\theta(t) - \theta_0] + \frac{1}{2}A_0 R(t)\cos[2\omega_c t + \theta(t) + \theta_0]$$

**Formula 5:**

$$v_{out}(t) = \frac{1}{2}A_0 R(t)\cos[\theta(t) - \theta_0] = \frac{1}{2}A_0\text{Re}\{g(t)e^{-j\theta_0}\}$$

**Formula 6:**

$$v_{out}(t) = \frac{1}{2}A_0\text{Re}\{g(t)\} = \frac{1}{2}A_0 x(t)$$

**Formula 7:**

$$\text{If } \theta_0 = \pi/2: \quad v_{out}(t) = \frac{1}{2}A_0 R(t)\cos[\theta(t) - \pi/2] = \frac{1}{2}A_0 R(t)\sin[\theta(t)] = \frac{1}{2}A_0 y(t)$$

**Formula 8:**

$$v_{out}(t) = \frac{1}{2}A_0 R(t)$$

**Formula 9:**

$$v_{out}(t) = \frac{1}{2}A_0 A_c\cos[\theta(t) - \pi/2] = \frac{1}{2}A_0 A_c\sin[\theta(t)]$$

**Formula 10:**

$$v_{out}(t) = K_d \frac{d[\omega_c t + \theta(t)]}{dt} = K\left[\omega_c + \frac{d\theta(t)}{dt}\right]$$

**Formula 11:**

$$v_{out}(t) = K_d \frac{d\theta(t)}{dt}$$

**Formula 12:**

$$v_{in}(t) = A(t)s(t) = A_c A(t)\cos[\omega_c t + \theta(t)]$$

**Formula 13:**

$$v_1(t) = V_L\cos[\omega_c t + \theta(t)]$$


#### Key Concepts

- that while the envelope detector is nonlinear, the

- ideal Envelope Detector is a circuit that produces at its output a waveform that is proportional to the real envelope R(t) of its input passband signal

- ideal envelope detector must b e: vout(t) =KR(t) whereKis a proportionality constant

- envelope detector is typically used to detect AM signals

- complex envelope of vin(t) is given by: g(t) =Ac[1+m(t)] whereAc>0 andm(t) is the modulating signal

- envelope detector is: vout(t) =KR(t) =K|g(t)|=KAc|1+m(t)| If|m(t)|<1, then: vout(t) =KAc[1+m(t)] =KAc+KAcm(t) KAcis the DC voltage

- input signal to produce the output signal illustrated in the previous ﬁgure

- output signal follows the real envelope R(t) and not the rapid variations in vin(t)

- real envelope): If1 2πRC<B(RCis very large), the detector is slower than the real envelope: Communication Systems Lecture-15: Detector Circuits Product Detector (1) TheProduct Detector is a mixer circuit that dow

- complex envelope of the input: g(t) =R(t)ejθ(t)=x(t)+jy(t) wherex(t) andy(t) are the quadrature components

- carrier frequency of the incoming signal, the oscillator has beenfrequency synchronized with the input signal

- product detector is sensitive to both AM and angle modulation

- reference phase is set to zero ( θ0= 0), then: vout(t) =1 2A0R(t) In this case, the real envelope is obtained at the output of the product detector

- envelope detector is nonlinear, the product detector is linear

- reference phase is θ0=π/2, then: vout(t) =1 2A0Accos[θ(t)−π/2] =1 2A0Acsin[θ(t)] Assuming that the phase diﬀerence is small, |θ(t)| ≪π/2, then sinθ(t)≈θ(t) and consequently: vout(t) =1 2A0Acθ(t) In this case, the pr

- product detector is proportional to the phase diﬀerence (when the phase diﬀerence is small)

- bandpass signal at the input of the detector is given by vin(t) =R(t)cos[ωct+θ(t)], then the output of the ideal FM detector is: vout(t) =Kd[ωct+θ(t)] dt=K/bracketleftbigg ωc+dθ(t) dt/bracketrightbigg whereKis a pro

- instantaneous frequency of the modulated signal is proportional to the information signal m(t) since: dθ(t) dt=Kfm(t) At the output of the communication channel (and the input of the receiver), the signal can be written as:

- undesired amplitude variations ( A(t)) on the input signal

- envelope detector is the magnitude of the complex envelope of v2(t): vout(t) =/vextendsingle/vextendsingle/vextendsingle/vextendsingle−VL/bracketleftbigg ωc+dθ(t) dt/bracketrightbigg/vextendsingle/vextendsingle/vexten

- reference signal such as a synchronized oscillator signal

- modulated signal that is to be demodulated


---

## GROUP 3 - Analog Modulation (Angle-based)

### Lecture 18

#### Key Formulas

**Formula 1:**

$$s(t) = \text{Re}\{g(t)e^{j\omega_c t}\} = \text{Re}\{A_c e^{j\theta(t)}e^{j\omega_c t}\} = A_c\cos[\omega_c t + \theta(t)]$$

**Formula 2:**

$$f_i(t) = \frac{1}{2\pi}\frac{d[\omega_c t + \theta(t)]}{dt} = f_c + \frac{1}{2\pi}\frac{d\theta(t)}{dt}$$

**Formula 3:**

$$S(f) =1 2[G(f−f_c)+G∗(−f−f_c)]$$

**Formula 4:**

$$\beta = \beta_p \text{ for PM}$$

**Formula 5:**

$$m_p(t) = A_m\sin[\omega_m t]$$

**Formula 6:**

$$m_f(t) = A_m\cos[\omega_m t]$$

**Formula 7:**

$$g(t) = \sum_{n=-\infty}^{+\infty} c_n e^{jn\omega_m t}$$

**Formula 8:**

$$G(f) = A_c \sum_{n=-\infty}^{+\infty} J_n(\beta)\delta(f - nf_m)$$


#### Key Concepts

- complex envelope is given by: g(t) =Acejθ(t) Acis a positive real number

- real envelope is given by R(t) =|g(t)|=Acis a constant

- modulating signal: θ(t) =Dpm(t) whereDpis the phase sensitivity of the PM

- carrier frequency is: fd(t) =fi(t)−fc=1 2π/bracketleftbiggdθ(t) dt/bracketrightbigg Communication Systems Lecture-18: Angle Modulation Angle Modulation (3) For FM: fi(t) =fc+1 2πDfm(t) fd(t) =1 2πDfm(t) This is the r

- instantaneous frequency varies about the carrier frequency fcin a manner that is directly proportional to the modulating signal m(t)

- FM signal when the modulating signalm(t) is sinusoidal

- modulating signalm(t), then a general formula relating G(f) (and consequently S(f)) toM(f) can not be obtained

- PM signal takes the following form: mp(t) =Amsin[ωmt] In this case: θ(t) =Dpmp(t) =DpAmsin[ωmt] implying that β=DpAm

- phase modulation index is given by: βp=Dpmax[mp(t)] =DpAm The last equations imply that: β=βp=DpAm Communication Systems Lecture-18: Angle Modulation Spectra of Angle-Modulated Signals (3) For FM,θ(t) =βsin[ωmt] whe

- FM signal takes the following form: mf(t) =Amcos[ωmt] In this case: dθ(t) dt=Dfmf(t) ⇒βωmcos[ωmt] =DfAmcos[ωmt] implying that β=DfAm/ωm

- frequency modulation index is: βf/defines∆F B=/bracketleftbigg1 fm/bracketrightbigg/bracketleftbigg1 2πDfmax[mf(t)]/bracketrightbigg =DfAm ωm The last equations imply that: β=βf=DfAm ωm Communication Systems Lecture-18:

- complex envelope is given by: g(t) =Acejθ(t)=Acejβsin(ωmt) g(t) is periodic with period Tm= 1/fm

- complex envelope is: G(f) =Ac+∞/summationdisplay n=−∞Jn(β)δ(f−nfm) The spectrum of the angle-modulated signal is: S(f) =1 2[G(f−fc)+G∗(−f−fc)] Communication Systems Lecture-18: Angle Modulation Spectra of Angle-Modu

- carrier frequency will decrease in magnitude since the total power of the signal remains constant

- phase modulation index or the frequency modulation index

- modulating signal ( B=fmwhen m(t) is a sinusoidal function)

- modulated signals must not overlap, otherwise, crosstalk will occur between the diﬀerent messages

- main carrier to produce a passband FDM signal that is transmitted over the wideband channel

- audio signal consists of a right-channel audio and a left-channel audio

- audio signal (left-channel audio plus right-channel audio) from both speakers

- reference signal for the coherent product detector at the receiver


### Lecture 14 - Limiters

#### Key Formulas

**Formula 1:**

$$vin(t) =R(t)\cos[\omega_ct+\theta(t)] The signal$$

**Formula 2:**

$$v1(t) =A_{0} 2\text{Re}braceleftBig gin(t)ej(\omega_c+\omega_{0})t/bracerightBig +A_{0} 2\text{Re}braceleftBig gin(t)ej(\omega_c−\omega_{0})t/bracerightBig$$

**Formula 3:**

$$g2(t) =A_{0} 2gin(t)$$

**Formula 4:**

$$vin(t) =R(t)\cos[\omega_ct+\theta(t)] The output of the nonlinear device is: v1(t) =Knvn$$

**Formula 5:**

$$vout(t) =CRn(t)\cos[n\omega_ct+n\theta(t)]$$


#### Key Concepts

- that when f0=fc, a lowpass ﬁlter can be used to select

- input signal are eliminated in the output signal

- real envelope of the receiver input signal tha t are caused by noise

- input signal with a sinusoidal waveform produced by a local oscillator

- input signal is a bandpass signal that has a nonzero spectrum around f=fc

- input signal with a spectrum nearf=fchas been converted to 2 output bandpass signals: Anup-conversion band around fu=fc+f0

- complex envelope of the signal at the output of the up-converter (located at fu=fc+f0) is: g2(t) =A0 2gin(t) In the same way, the complex envelope of the signal at the output of the down-converter (located at fd=fc−f

- bandpass signal aroundf=fc, the output will appear in a frequency band at then-th harmonic of the input carrier frequency (i

- real envelope of the output signal is Rn(t))


---

## GROUP 4 - Digital & Pulse Modulation

### Lecture 12

#### Key Concepts

- input signal is a sine wave: w(t) =Asin(ωat)

- analog signal band|f|<Bis: N=/angbracketleftn2/angbracketright=/integraldisplayB −BPn(f)df=δ2B 3fs=4π2A2f2 aB 3f3s On the other hand, the signal power is: S=/angbracketleftw2(t)/angbracketright=A2 2 The resulting

- binary signal, this will correspond to a data rate of R= 1×fs=fs= 10

- input signal does not vary rapidly

- input signal changes rapidly to reduce the slope overload noise

- analog signal into the time axis of a digital signal

- analog signal determine the width of the transmitted pulse

- analog signal determine the position of a narrow pulse relative to the clocking time

- PWM signal goes low, the amplitude of the truncated ramp signal will be equal to the corresponding PAM sample value

- analog signal is generated from the PAM samples using a low-pass ﬁlter


---

## GROUP 5 - Multiplexing

### Lecture 11

#### Key Concepts

- by fsthe frequency of rotation of the commutator. fs

- TDM signal with the expected unique sync word s= (s1,

- coincident detector is a K-input AND gate

- coincident detector is equal to 0 resulting in a zero-level output


---

## GROUP 6 - Frequency Translation & Receiver Design

### Lecture 14 - Mixers & Multipliers

#### Key Formulas

**Formula 1:**

$$v_{in}(t) = R(t)\cos[\omega_c t + \theta(t)]$$

**Formula 2:**

$$v_1(t) = \frac{A_0}{2}\text{Re}\{g_{in}(t)e^{j(\omega_c + \omega_0)t}\} + \frac{A_0}{2}\text{Re}\{g_{in}(t)e^{j(\omega_c - \omega_0)t}\}$$

**Formula 3:**

$$g_2(t) = \frac{A_0}{2}g_{in}(t)$$

**Formula 4:**

$$v_1(t) = K_n v_{in}^n(t) = K_n R^n(t)\cos^n[\omega_c t + \theta(t)]$$

**Formula 5:**

$$v_{out}(t) = C R^n(t)\cos[n\omega_c t + n\theta(t)]$$


#### Key Concepts

- that when f0=fc, a lowpass ﬁlter can be used to select

- input signal are eliminated in the output signal

- real envelope of the receiver input signal tha t are caused by noise

- input signal with a sinusoidal waveform produced by a local oscillator

- input signal is a bandpass signal that has a nonzero spectrum around f=fc

- input signal with a spectrum nearf=fchas been converted to 2 output bandpass signals: Anup-conversion band around fu=fc+f0

- complex envelope of the signal at the output of the up-converter (located at fu=fc+f0) is: g2(t) =A0 2gin(t) In the same way, the complex envelope of the signal at the output of the down-converter (located at fd=fc−f

- bandpass signal aroundf=fc, the output will appear in a frequency band at then-th harmonic of the input carrier frequency (i

- real envelope of the output signal is Rn(t))


### Lecture 16

#### Key Formulas

**Formula 1:**

$$s(t) = m(t)\cos[\omega_c t]$$

**Formula 2:**

$$s_1(t) = m_1(t)\cos[(\omega_c + 2\omega_{IF})t]$$

**Formula 3:**

$$v_2(t) = \frac{1}{2}m(t)\cos[\omega_{IF} t] + \frac{1}{2}m_1(t)\cos[\omega_{IF} t]$$


#### Key Concepts

- input signal to some convenient frequency band called the Intermediate-Frequency (IF) band

- appropriate detector is used to extract the information (for example, envelope detector for AM

- AM signal having a carrier frequency of fc: s(t) =m(t)cos[ωct] wherem(t) is the modulating signal

- carrier frequency of fc+2fIF: s1(t) =m1(t)cos[(ωc+2ωIF)t] wherem1(t) is the modulating signal of the adjacent channel

- unwanted signal located at the image frequency due to insuﬃcient attenuation of the image signal by the RF ampliﬁer ﬁlter

- image frequency is small compared to the signal of the desired channel because the former is attenuated by the RF-BPF (band-pass ﬁlter)

- IF frequency with AM broadcast radios is fIF= 455 kHz

- image frequency is at fc+2fIF= 1760 kHz

- input signal and the signal at the output of the local oscillator respectively

- intermediate frequency fIFmust be high enough so that the image response at the receiver is acceptably small


---


## Notes

- This summary includes formulas and concepts explicitly mentioned in the lecture PDFs.
- PLL (Phase Locked Loop) content from Lecture 16 has been excluded as specified.
- Formulas are formatted using LaTeX notation for proper mathematical display.

---
*Generated from Communication Systems lecture materials*

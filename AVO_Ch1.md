## Chapter 1 Introduction

As described in the Foreword, the intuitive notions of signals and systems arise in a rich variety of contexts. Moreover, as we will see in this book, there is an analytical framework--that is, a language for describing signals and systems and an extremely powerful set of tools for analyzing them--that applies equally well to problems in many fields. In this chapter, we begin our development of the analytical framework for signals and systems by introducing their mathematical description and representations. In the chapters that follow, we build on this foundation in order to develop and describe additional concepts and methods that add considerably both to our understanding of signals and systems and to our ability to analyze and solve problems involving signals and systems that arise in a broad array of applications.

### 1.1 Continuous-time and Discrete-time Signals

#### Examples and Mathematical Representation

Signals may describe a wide variety of physical phenomena. Although signals can be represented in many ways, in all cases the information in a signal is contained in a pattern of variations of some form. For example, consider the simple circuit in Figure 1.1. In this case, the patterns of variation over time in the source and capacitor voltages, \(v_{s}\) and \(v_{c}\), are examples of signals. Similarly, as depicted in Figure 1.2, the variations over time of the applied force \(f\) and the resulting automobile velocity \(v\) are signals. As another example, consider the human vocal mechanism, which produces speech by creating fluctuations in acoustic pressure. Figure 1.3 is an illustration of a recording of such a speech signal, obtained byusing a microphone to sense variations in acoustic pressure, which are then converted into an electrical signal. As can be seen in the figure, different sounds correspond to different patterns in the variations of acoustic pressure, and the human vocal system produces intelligible speech by generating particular sequences of these patterns. Alternatively, for the monochromatic picture, shown in Figure 4, it is the pattern of variations in brightness across the image that is important.

Figure 3: Example of a recording of speech. [Adapted from _Applications of Digital Signal Processing_, A.V. Oppenheim, ed. (Englewood Cliffs, N.J.: Prentice-Hall, Inc., 1978), p. 121.] The signal represents acoustic pressure variations as a function of time for the spoken words “should we chase.” The top line of the figure corresponds to the word “should,” the second line to the word “we,” and the last two lines to the word “chase.” (We have indicated the approximate beginnings and endings of each successive sound in each word.)

Figure 1.4: A monochromatic

Signals are represented mathematically as functions of one or more independent variables. For example, a speech signal can be represented mathematically by acoustic pressure as a function of time, and a picture can be represented by brightness as a function of two spatial variables. In this book, we focus our attention on signals involving a single independent variable. For convenience, we will generally refer to the independent variable as time, although it may not in fact represent time in specific applications. For example, in geophysics, signals representing variations with depth of physical quantities such as density, porosity, and electrical resistivity are used to study the structure of the earth. Also, knowledge of the variations of air pressure, temperature, and wind speed with altitude are extremely important in meteorological investigations. Figure 1.5 depicts a typical example of annual average vertical wind profile as a function of height. The measured variations of wind speed with height are used in examining weather patterns, as well as wind conditions that may affect an aircraft during final approach and landing.

Throughout this book we will be considering two basic types of signals: continuous-time signals and discrete-time signals. In the case of continuous-time signals the independent variable is continuous, and thus these signals are defined for a continuum of values

Figure 1.5: Typical annual vertical wind profile. (Adapted from Crawford and Hudson, National Severe Storms Laboratory Report, ESSA ERLTM-NSSL 48, August 1970.)

of the independent variable. On the other hand, discrete-time signals are defined only at discrete times, and consequently, for these signals, the independent variable takes on only a discrete set of values. A speech signal as a function of time and atmospheric pressure as a function of altitude are examples of continuous-time signals. The weekly Dow-Jones stock market index, as illustrated in Figure 6, is an example of a discrete-time signal. Other examples of discrete-time signals can be found in demographic studies in which various attributes, such as average budget, crime rate, or pounds of fish caught, are tabulated against such discrete variables as family size, total population, or type of fishing vessel, respectively.

To distinguish between continuous-time and discrete-time signals, we will use the symbol \(t\) to denote the continuous-time independent variable and \(n\) to denote the discrete-time independent variable. In addition, for continuous-time signals we will enclose the independent variable in parentheses \((\,\cdot\,)\), whereas for discrete-time signals we will use brackets \([\,\cdot\,]\) to enclose the independent variable. We will also have frequent occasions when it will be useful to represent signals graphically. Illustrations of a continuous-time signal \(x(t)\) and a discrete-time signal \(x[n]\) are shown in Figure 7. It is important to note that the discrete-time signal \(x[n]\) is defined _only_ for integer values of the independent variable. Our choice of graphical representation for \(x[n]\) emphasizes this fact, and for further emphasis we will on occasion refer to \(x[n]\) as a discrete-time _sequence_.

A discrete-time signal \(x[n]\) may represent a phenomenon for which the independent variable is inherently discrete. Signals such as demographic data are examples of this. On the other hand, a very important class of discrete-time signals arises from the _sampling_ of continuous-time signals. In this case, the discrete-time signal \(x[n]\) represents successive samples of an underlying phenomenon for which the independent variable is continuous. Because of their speed, computational power, and flexibility, modern digital processors are used to implement many practical systems, ranging from digital autopilots to digital audio systems. Such systems require the use of discrete-time sequences representing sampled versions of continuous-time signals--e.g., aircraft position, velocity, and heading for an

Figure 6: An example of a discrete-time signal: The weekly Dow-Jones stock market index from January 5, 1929, to January 4, 1930.

 

[MISSING_PAGE_EMPTY:5]

[MISSING_PAGE_FAIL:6]

[MISSING_PAGE_EMPTY:7]

#### Examples of Transformations of the Independent Variable

A simple and very important example of transforming the independent variable of a signal is a _time shift_. A time shift in discrete time is illustrated in Figure 1.8, in which we have two signals \(x[n]\) and \(x[n-n_{0}]\) that are identical in shape, but that are displaced or shifted relative to each other. We will also encounter time shifts in continuous time, as illustrated in Figure 1.9, in which \(x(t-t_{0})\) represents a delayed (if \(t_{0}\) is positive) or advanced (if \(t_{0}\) is negative) version of \(x(t)\). Signals that are related in this fashion arise in applications such as radar, sonar, and seismic signal processing, in which several receivers at different locations observe a signal being transmitted through a medium (water, rock, air, etc.). In this case, the difference in propagation time from the point of origin of the transmitted signal to any two receivers results in a time shift between the signals at the two receivers.

A second basic transformation of the time axis is that of _time reversal_. For example, as illustrated in Figure 1.10, the signal \(x[-n]\) is obtained from the signal \(x[n]\) by a reflection about \(n=0\) (i.e., by reversing the signal). Similarly, as depicted in Figure 1.11, the signal \(x(-t)\) is obtained from the signal \(x(t)\) by a reflection about \(t=0\). Thus, if \(x(t)\) represents an audio tape recording, then \(x(-t)\) is the same tape recording played backward. Another transformation is that of _time scaling_. In Figure 1.12 we have illustrated three signals, \(x(t)\), \(x(2t)\), and \(x(t/2)\), that are related by linear scale changes in the independent variable. If we again think of the example of \(x(t)\) as a tape recording, then \(x(2t)\) is that recording played at twice the speed, and \(x(t/2)\) is the recording played at half-speed.

It is often of interest to determine the effect of transforming the independent variable of a given signal \(x(t)\) to obtain a signal of the form \(x(\alpha t+\beta)\), where \(\alpha\) and \(\beta\) are given numbers. Such a transformation of the independent variable preserves the shape of \(x(t)\), except that the resulting signal may be linearly stretched if \(|\alpha|<1\), linearly compressed if \(|\alpha|>1\), reversed in time if \(\alpha<0\), and shifted in time if \(\beta\) is nonzero. This is illustrated in the following set of examples.

Figure 1.8: Discrete-time signals related by a time shift. In this figure \(n_{0}>0\), so that \(x[n-n_{0}]\) is a delayed version of \(x[n]\) (i.e., each point in \(x[n]\) occurs later in \(x[n-n_{0}]\)).

Figure 1.11: (a) A continuous-time signal \(x(t)\); (b) its reflection \(x(-t)\) about \(t=0\). Figure 1.12: Continuous-time signals related by time scaling.

[MISSING_PAGE_EMPTY:10]

[MISSING_PAGE_EMPTY:11]

An example of a periodic continuous-time signal is given in Figure 14. From the figure or from eq. (11), we can readily deduce that if \(x(t)\) is periodic with period \(T\), then \(x(t)=x(t+mT)\) for all \(t\) and for any integer \(m\). Thus, \(x(t)\) is also periodic with period \(2T\), \(3T\), \(4T\),... The _fundamental period_\(T_{0}\) of \(x(t)\) is the smallest positive value of \(T\) for which eq. (11) holds. This definition of the fundamental period works, except if \(x(t)\) is a constant. In this case the fundamental period is undefined, since \(x(t)\) is periodic for _any_ choice of \(T\) (so there is no smallest positive value). A signal \(x(t)\) that is not periodic will be referred to as an _aperiodic_ signal.

Periodic signals are defined analogously in discrete time. Specifically, a discrete-time signal \(x[n]\) is periodic with period \(N\), where \(N\) is a positive integer, if it is unchanged by a time shift of \(N\), i.e., if

\[x[n]\,=\,x[n+N] \tag{12}\]

for all values of \(n\). If eq. (12) holds, then \(x[n]\) is also periodic with period \(2N\), \(3N\),... The _fundamental period_\(N_{0}\) is the smallest positive value of \(N\) for which eq. (12) holds. An example of a discrete-time periodic signal with fundamental period \(N_{0}\,=\,3\) is shown in Figure 15.

## Example 4

Let us illustrate the type of problem solving that may be required in determining whether or not a given signal is periodic. The signal whose periodicity we wish to check is given by

\[x(t)\,=\,\left\{\begin{array}{ll}\cos(t)&\mbox{if $t<0$}\\ \sin(t)&\mbox{if $t\,\,\cong\,0$}\end{array}\right.. \tag{13}\]

From trigonometry, we know that \(\cos(t+2\pi)\,=\,\cos(t)\) and \(\sin(t+2\pi)\,=\,\sin(t)\). Thus, considering \(t>0\) and \(t<0\) separately, we see that \(x(t)\) does repeat itself over every interval of length \(2\pi\). However, as illustrated in Figure 16, \(x(t)\) also has a discontinuity at the time origin that does not recur at any other time. Since every feature in the shape of a periodic signal _must_ recur periodically, we conclude that the signal \(x(t)\) is not periodic.

Figure 14: A continuous-time periodic signal.

#### Even and Odd Signals

Another set of useful properties of signals relates to their symmetry under time reversal. A signal \(x(t)\) or \(x[n]\) is referred to as an _even_ signal if it is identical to its time-reversed counterpart, i.e., with its reflection about the origin. In continuous time a signal is even if

\[x(-t)\;=\;x(t), \tag{1.14}\]

while a discrete-time signal is even if

\[x[-n]\;=\;x[n]. \tag{1.15}\]

A signal is referred to as _odd_ if

\[x(-t)\;=\;-x(t), \tag{1.16}\] \[x[-n]\;=\;-x[n]. \tag{1.17}\]

An odd signal must necessarily be \(0\) at \(t\;=\;0\) or \(n\;=\;0\), since eqs. (1.16) and (1.17) require that \(x(0)\;=\;-x(0)\) and \(x[0]\;=\;-x[0]\). Examples of even and odd continuous-time signals are shown in Figure 1.17.

Figure 1.16: The signal \(x(t)\) considered in Example 1.4.

An important fact is that any signal can be broken into a sum of two signals, one of which is even and one of which is odd. To see this, consider the signal

\[\mathfrak{E}v\big{[}\ x(t)\big{]}\ =\ \frac{1}{2}\big{[}\ x(t)\,+\,x(-t)\big{]}, \tag{18}\]

which is referred to as the _even part_ of \(x(t)\). Similarly, the _odd part_ of \(x(t)\) is given by

\[\mathcal{O}d\{x(t)\}\ =\ \frac{1}{2}\big{[}x(t)\,-\,x(-t)\big{]}. \tag{19}\]

It is a simple exercise to check that the even part is in fact even, that the odd part is odd, and that \(x(t)\) is the sum of the two. Exactly analogous definitions hold in the discrete-time case. An example of the even-odd decomposition of a discrete-time signal is given in Figure 18.

### 3 Exponential and sinusoidal signals

In this section and the next, we introduce several basic continuous-time and discrete-time signals. Not only do these signals occur frequently, but they also serve as basic building blocks from which we can construct many other signals.

#### Continuous-Time Complex Exponential

and Sinusoidal Signals

The continuous-time _complex exponential signal_ is of the form

\[x(t)\,=\,Ce^{at}, \tag{20}\]

where \(C\) and \(a\) are, in general, complex numbers. Depending upon the values of these parameters, the complex exponential can exhibit several different characteristics.

##### Real Exponential Signals

As illustrated in Figure 19, if \(C\) and \(a\) are real [in which case \(x(t)\) is called a _real exponential_], there are basically two types of behavior. If \(a\) is positive, then as \(t\) increases \(x(t)\) is a growing exponential, a form that is used in describing many different physical processes, including chain reactions in atomic explosions and complex chemical reactions. If \(a\) is negative, then \(x(t)\) is a decaying exponential, a signal that is also used to describe a wide variety of phenomena, including the process of radioactive decay and the responses of \(RC\) circuits and damped mechanical systems. In particular, as shown in Problems 2.61 and 2.62, the natural responses of the circuit in Figure 1 and the automobile in Figure 2 are decaying exponentials. Also, we note that for \(a=0\), \(x(t)\) is constant.

Figure 19: Continuous-time real exponential \(x(t)\,=\,Ce^{at}\): (a) \(a>0\); (b) \(a<0\).

[MISSING_PAGE_EMPTY:16]

complex exponential signals are also used to describe the characteristics of many physical processes--in particular, physical systems in which energy is conserved. For example, as shown in Problem 2.61, the natural response of an \(LC\) circuit is sinusoidal, as is the simple harmonic motion of a mechanical system consisting of a mass connected by a spring to a stationary support. The acoustic pressure variations corresponding to a single musical tone are also sinusoidal.

By using Euler's relation,2 the complex exponential in eq. (21) can be written in terms of sinusoidal signals with the same fundamental period:

Footnote 2: Euler’s relation and other basic ideas related to the manipulation of complex numbers and exponentials are considered in the mathematical review section of the problems at the end of the chapter.

\[e^{ju_{0}t}\,=\,\cos\omega_{0}t\,+\,j\sin\omega_{0}t. \tag{26}\]

Similarly, the sinusoidal signal of eq. (25) can be written in terms of periodic complex exponentials, again with the same fundamental period:

\[A\cos(\omega_{0}t\,+\,\phi)\,=\,\frac{A}{2}e^{j\phi}e^{ju_{0}t}\,+\,\frac{A}{2 }e^{-j\phi}e^{-ju_{0}t}. \tag{27}\]

Note that the two exponentials in eq. (27) have complex amplitudes. Alternatively, we can express a sinusoid in terms of a complex exponential signal as

\[A\cos(\omega_{0}t\,+\,\phi)\,=\,A(\mathfrak{R}e\{e^{j(\omega_{0}t+\phi)}\}, \tag{28}\]

where, if \(c\) is a complex number, \(\mathfrak{R}e\{c\}\) denotes its real part. We will also use the notation \(\mathfrak{g}_{m}\{c\}\) for the imaginary part of \(c\), so that, for example,

\[A\sin(\omega_{0}t\,+\,\phi)\,=\,A\mathfrak{g}m\{e^{j(\omega_{0}t+\phi)}\}. \tag{29}\]

From eq. (24), we see that the fundamental period \(T_{0}\) of a continuous-time sinusoidal signal or a periodic complex exponential is inversely proportional to \(|\omega_{0}|\), which we will refer to as the _fundamental frequency_. From Figure 21, we see graphically what this means. If we decrease the magnitude of \(\omega_{0}\), we slow down the rate of oscillation and therefore increase the period. Exactly the opposite effects occur if we increase the magnitude of \(\omega_{0}\). Consider now the case \(\omega_{0}=0\). In this case, as we mentioned earlier, \(x(t)\) is constant and therefore is periodic with period \(T\) for any positive value of \(T\). Thus, the fundamental period of a constant signal is undefined. On the other hand, there is no ambiguity in defining the fundamental frequency of a constant signal to be zero. That is, a constant signal has a zero rate of oscillation.

Periodic signals--and in particular, the complex periodic exponential signal in eq. (21) and the sinusoidal signal in eq. (25)--provide important examples of signals with infinite total energy but finite average power. For example, consider the periodic exponential signal of eq. (21), and suppose that we calculate the total energy and average power in this signal over one period:

\[\begin{split} E_{\text{period}}&\,=\,\int_{0}^{T_{ 0}}|e^{ju_{0}t}|^{2}\,dt\\ &\,=\,\int_{0}^{T_{0}}1\cdot dt\,=\,T_{0},\end{split} \tag{30}\]

[MISSING_PAGE_EMPTY:18]

[MISSING_PAGE_FAIL:19]

plot the magnitude of the signal \[x(t)\,=\,e^{j2t}\,+\,e^{j3t}.\] (1.38) To do this, we first factor out a complex exponential from the right side of eq. (1.38), where the frequency of this exponential factor is taken as the average of the frequencies of the two exponentials in the sum. Doing this, we obtain \[x(t)\,=\,e^{j2.5t}(e^{-j0.5}\,+\,e^{j0.5t}),\] (1.39) which, because of Euler's relation, can be rewritten as \[x(t)\,=\,2e^{j2.5t}\cos(0.5t).\] (1.40) From this, we can directly obtain an expression for the magnitude of \(x(t)\): \[|x(t)|\,=\,2|\cos(0.5t)|.\] (1.41) Here, we have used the fact that the magnitude of the complex exponential \(e^{j2.5t}\) is always unity. Thus, \(|x(t)|\) is what is commonly referred to as a full-wave rectified sinusoid, as shown in Figure 1.22.

General Complex Exponential SignalsThe most general case of a complex exponential can be expressed and interpreted in terms of the two cases we have examined so far: the real exponential and the periodic complex exponential. Specifically, consider a complex exponential \(Ce^{at}\), where \(C\) is expressed in polar form and \(a\) in rectangular form. That is,

\[C\,=\,|C|e^{j\theta}\]

and

\[a\,=\,r\,+\,j\omega_{0}.\]

Then

\[Ce^{at}\,=\,|C|e^{j\theta}e^{(r+j\omega_{0})t}\,=\,|C|e^{rt}e^{j( \omega_{0}t+\theta)}. \tag{1.42}\]

Using Euler's relation, we can expand this further as

\[Ce^{at}\,=\,|C|e^{rt}\cos(\omega_{0}t+\theta)+\,j|C|e^{rt}\sin( \omega_{0}t+\theta). \tag{1.43}\]

Figure 1.22: The full-wave rectified sinusoid of Example 1.5.

Thus, for \(r\,=\,0\), the real and imaginary parts of a complex exponential are sinusoidal. For \(r>0\) they correspond to sinusoidal signals multiplied by a growing exponential, and for \(r<0\) they correspond to sinusoidal signals multiplied by a decaying exponential. These two cases are shown in Figure 23. The dashed lines in the figure correspond to the functions \(\pm|C|e^{rt}\). From eq. (42), we see that \(|C|e^{rt}\) is the magnitude of the complex exponential. Thus, the dashed curves act as an envelope for the oscillatory curve in the figure in that the peaks of the oscillations just reach these curves, and in this way the envelope provides us with a convenient way to visualize the general trend in the amplitude of the oscillations.

Sinusoidal signals multiplied by decaying exponentials are commonly referred to as _damped sinusoids_. Examples of damped sinusoids arise in the response of \(RLC\) circuits and in mechanical systems containing both damping and restoring forces, such as automotive suspension systems. These kinds of systems have mechanisms that dissipate energy (resistors, damping forces such as friction) with oscillations that decay in time. Examples illustrating such systems and their damped sinusoidal natural responses can be found in Problems 61 and 62.

#### Discrete-Time Complex Exponential and Sinusoidal Signals

As in continuous time, an important signal in discrete time is the _complex exponential signal_ or _sequence_, defined by

\[x[n]\,=\,C\alpha^{n}, \tag{44}\]where \(C\) and \(\alpha\) are, in general, complex numbers. This could alternatively be expressed in the form

\[x[n]\,=\,Ce^{\beta n}, \tag{45}\]

where

\[\alpha\,=\,e^{\beta}.\]

Although the form of the discrete-time complex exponential sequence given in eq. (45) is more analogous to the form of the continuous-time exponential, it is often more convenient to express the discrete-time complex exponential sequence in the form of eq. (44).

#### Real Exponential Signals

If \(C\) and \(\alpha\) are real, we can have one of several types of behavior, as illustrated in Figure 24. If \(|\alpha|\,>\,1\) the magnitude of the signal grows exponentially with \(n\), while if \(|\alpha|\,<\,1\) we have a decaying exponential. Furthermore, if \(\alpha\) is positive, all the values of \(C\alpha^{n}\) are of the same sign, but if \(\alpha\) is negative then the sign of \(x[n]\) alternates. Note also that if \(\alpha\,=\,1\) then \(x[n]\) is a constant, whereas if \(\alpha\,=\,-1\), \(x[n]\) alternates in value between \(+\,C\) and \(-\,C\). Real-valued discrete-time exponentials are often used to describe population growth as a function of generation and total return on investment as a function of day, month, or quarter.

#### Sinusoidal Signals

Another important complex exponential is obtained by using the form given in eq. (45) and by constraining \(\beta\) to be purely imaginary (so that \(|\alpha|\,=\,1\)). Specifically, consider

\[x[n]\,=\,e^{j\omega_{0}n}. \tag{46}\]

As in the continuous-time case, this signal is closely related to the sinusoidal signal

\[x[n]\,=\,A\cos(\omega_{0}n\,+\,\phi). \tag{47}\]

If we take \(n\) to be dimensionless, then both \(\omega_{0}\) and \(\phi\) have units of radians. Three examples of sinusoidal sequences are shown in Figure 25.

As before, Euler's relation allows us to relate complex exponentials and sinusoids:

\[e^{j\omega_{0}n}\,=\,\cos\omega_{0}n\,+\,j\sin\omega_{0}n \tag{48}\]

and

\[A\cos(\omega_{0}n\,+\,\phi)\,=\,\frac{A}{2}\,e^{j\phi}e^{j\omega_{0}n}\,+\, \frac{A}{2}\,e^{-j\phi}e^{-j\omega_{0}n}. \tag{49}\]

The signals in eqs. (46) and (47) are examples of discrete-time signals with infinite total energy but finite average power. For example, since \(|e^{j\omega_{0}n}|Figure 1.24: The real exponential signal \(x[n]=\mathcal{C}\alpha^{n}\):

(a) \(\alpha>1\); (b) \(0<\alpha<1\);

(c) \(-1<\alpha<0\); (d) \(\alpha<-1\).

#### General Complex Exponential Signals

The general discrete-time complex exponential can be written and interpreted in terms of real exponentials and sinusoidal signals. Specifically, if we write \(C\) and \(\alpha\) in polar form,

Figure 1.25: Discrete-time sinusoidal signals.

\[C\,=\,|C|e^{j\theta}\]

and

\[\alpha\,=\,|\alpha|e^{j\omega_{0}},\]

then

\[C\alpha^{n}\,=\,|C||\alpha|^{n}\cos(\omega_{0}n+\theta)\,+\,j|C|| \alpha|^{n}\sin(\omega_{0}n+\theta). \tag{1.50}\]

Thus, for \(|\alpha|=1\), the real and imaginary parts of a complex exponential sequence are sinusoidal. For \(|\alpha|<1\) they correspond to sinusoidal sequences multiplied by a decaying exponential, while for \(|\alpha|>1\) they correspond to sinusoidal sequences multiplied by a growing exponential. Examples of these signals are depicted in Figure 1.26.

#### Periodicity Properties of Discrete-Time Complex Exponentials

While there are many similarities between continuous-time and discrete-time signals, there are also a number of important differences. One of these concerns the discrete-time exponential signal \(e^{j\omega_{0}n}\). In Section 1.3.1, we identified the following two properties of its

Figure 1.26: (a) Growing discrete-time sinusoidal signals; (b) decaying discrete-time sinusoid.

[MISSING_PAGE_FAIL:26]

Figure 1.27: Discrete-time sinusoidal sequences for several different frequencies.

[MISSING_PAGE_EMPTY:28]

In contrast, consider the signal \(x[n]=\cos(8\pi n/31)\), depicted in Figure 1.25(b), which we can view as the set of samples of \(x(t)=\cos\left(8\pi t/31\right)\) at integer points in time. In this case, \(x(t)\) is periodic with fundamental period \(31/4\). On the other hand, \(x[n]\) is periodic with fundamental period \(31\). The reason for this difference is that the discrete-time signal is defined only for integer values of the independent variable. Thus, there is no sample at time \(t=31/4\), when \(x(t)\) completes one period (starting from \(t=0\)). Similarly, there is no sample at \(t=2\cdot 31/4\) or \(t=3\cdot 31/4\), when \(x(t)\) has completed two or three periods, but there is a sample at \(t=4\cdot 31/4=31\), when \(x(t)\) has completed _four_ periods. This can be seen in Figure 1.25(b), where the pattern of \(x[n]\) values does _not_ repeat with each single cycle of positive and negative values. Rather, the pattern repeats after four such cycles, namely, every \(31\) points.

Similarly, the signal \(x[n]=\cos(n/6)\) can be viewed as the set of samples of the signal \(x(t)=\cos(t/6)\) at integer time points. In this case, the values of \(x(t)\) at integer sample points never repeat, as these sample points never span an interval that is an exact multiple of the period, \(12\pi\), of \(x(t)\). Thus, \(x[n]\) is not periodic, although the eye visually interpolates between the sample points, suggesting the envelope \(x(t)\), which _is_ periodic. The use of the concept of sampling to gain insight into the periodicity of discrete-time sinusoidal sequences is explored further in Problem 1.36.

### Example 1.6

Suppose that we wish to determine the fundamental period of the discrete-time signal

\[x[n]=e^{i(2\pi/3)n}+e^{i(3\pi t/4)n}. \tag{1.59}\]

The first exponential on the right-hand side of eq. (1.59) has a fundamental period of \(3\). While this can be verified from eq. (1.58), there is a simpler way to obtain that answer. In particular, note that the angle \((2\pi/3)n\) of the first term must be incremented by a multiple of \(2\pi\) for the values of this exponential to begin repeating. We then immediately see that if \(n\) is incremented by \(3\), the angle will be incremented by a single multiple of \(2\pi\). With regard to the second term, we see that incrementing the angle \((3\pi/4)n\) by \(2\pi\) would require \(n\) to be incremented by \(8/3\), which is impossible, since \(n\) is restricted to being an integer. Similarly, incrementing the angle by \(4\pi\) would require a noninteger increment of \(16/3\) to \(n\). However, incrementing the angle by \(6\pi\) requires an increment of \(8\) to \(n\), and thus the fundamental period of the second term is \(8\).

Now, for the entire signal \(x[n]\) to repeat, each of the terms in eq. (1.59) must go through an integer number of its own fundamental period. The smallest increment of \(n\) that accomplishes this is \(24\). That is, over an interval of \(24\) points, the first term on the right-hand side of eq. (1.59) will have gone through eight of its fundamental periods, the second term through three of its fundamental periods, and the overall signal \(x[n]\) through exactly one of its fundamental periods.

As in continuous time, it is also of considerable value in discrete-time signal and system analysis to consider sets of harmonically related periodic exponentials--that is, periodic exponentials with a common period \(N\). From eq. (1.56), we know that these are precisely the signals which are at frequencies which are multiples of \(2\pi/N\). That is,

\[\phi_{k}[n]=e^{jk(2\pi/N)n},\qquad k=0,\,\pm 1,\ldots. \tag{1.60}\]

[MISSING_PAGE_FAIL:30]

[MISSING_PAGE_EMPTY:31]

Equation (67) is illustrated in Figure 31. In this case the nonzero value of \(\delta[n-k]\) is at the value of \(k\) equal to \(n\), so that again we see that the summation in eq. (67) is \(0\) for \(n<0\) and \(1\) for \(n\,\geq\,0\).

An interpretation of eq. (67) is as a superposition of delayed impulses; i.e., we can view the equation as the sum of a unit impulse \(\delta[n]\) at \(n\,=\,0\), a unit impulse \(\delta[n-1]\) at \(n\,=\,1\), another, \(\delta[n-2]\), at \(n\,=\,2\), etc. We will make explicit use of this interpretation in Chapter 2.

The unit impulse sequence can be used to sample the value of a signal at \(n\,=\,0\). In particular, since \(\delta[n]\) is nonzero (and equal to \(1\)) only for \(n\,=\,0\), it follows that

\[x[n]\delta[n]\,=\,x[0]\delta[n]. \tag{68}\]

More generally, if we consider a unit impulse \(\delta[n-n_{0}]\) at \(n\,=\,n_{0}\), then

\[x[n]\delta[n-n_{0}]\,=\,x[n_{0}]\delta[n-n_{0}]. \tag{69}\]

This sampling property of the unit impulse will play an important role in Chapters 2 and 7.

#### The Continuous-Time Unit Step

and Unit Impulse Functions

The continuous-time _unit step function_\(u(t)\) is defined in a manner similar to its discrete-time counterpart. Specifically,

\[u(t)\,=\,\left\{\begin{array}{ll}0,&t<0\\ 1,&t>0\end{array},\right. \tag{70}\]

as is shown in Figure 32. Note that the unit step is discontinuous at \(t=0\). The continuous-time _unit impulse function_\(\delta(t)\) is related to the unit step in a manner analogous

Figure 31: Relationship given in eq. (67): (a) \(n<0\); (b) \(n>0\).

[MISSING_PAGE_EMPTY:33]

Note that \(\delta_{\Delta}(t)\) is a short pulse, of duration \(\Delta\) and with unit area for any value of \(\Delta\). As \(\Delta\to 0\), \(\delta_{\Delta}(t)\) becomes narrower and higher, maintaining its unit area. Its limiting form,

\[\delta(t)\;=\;\lim_{\Delta\to 0}\delta_{\Delta}(t), \tag{74}\]

can then be thought of as an idealization of the short pulse \(\delta_{\Delta}(t)\) as the duration \(\Delta\) becomes insignificant. Since \(\delta(t)\) has, in effect, no duration but unit area, we adopt the graphical notation for it shown in Figure 35, where the arrow at \(t\,=\,0\) indicates that the area of the pulse is concentrated at \(t\,=\,0\) and the height of the arrow and the "1" next to the arrow are used to represent the _area_ of the impulse. More generally, a scaled impulse \(k\delta(t)\) will have an area \(k\), and thus,

\[\int_{-\infty}^{t}k\delta(\tau)\,d\tau\;=\;ku(t).\]

A scaled impulse with area \(k\) is shown in Figure 36, where the height of the arrow used to depict the scaled impulse is chosen to be proportional to the area of the impulse.

As with discrete time, we can provide a simple graphical interpretation of the running integral of eq. (71); this is shown in Figure 37. Since the area of the continuous-time unit impulse \(\delta(\tau)\) is concentrated at \(\tau\,=\,0\), we see that the running integral is \(0\) for \(t<0\) and \(1\) for \(t>0\). Also, we note that the relationship in eq. (71) between the continuous-time unit step and impulse can be rewritten in a different form, analogous to the discrete-time form in eq. (67), by changing the variable of integration from \(\tau\) to \(\sigma\,=\,t-\tau\):

\[u(t)\,=\,\int_{-\infty}^{t}\delta(\tau)\,d\tau\;=\,\int_{\infty}^{0}\delta(t- \sigma)(-d\sigma),\]

or equivalently,

\[u(t)\,=\,\int_{0}^{\,\,\times}\delta(t-\sigma)\,d\sigma. \tag{75}\]

The graphical interpretation of this form of the relationship between \(u(t)\) and \(\delta(t)\) is given in Figure 38. Since in this 

[MISSING_PAGE_FAIL:35]

Although our discussion of the unit impulse in this section has been somewhat informal, it does provide us with some important intuition about this signal that will be useful throughout the book. As we have stated, the unit impulse should be viewed as an idealization. As we illustrate and discuss in more detail in Section 2.5, any real physical system has some inertia associated with it and thus does not respond instantaneously to inputs. Consequently, if a pulse of sufficiently short duration is applied to such a system, the system response will not be noticeably influenced by the pulse's duration or by the details of the shape of the pulse, for that matter. Instead, the primary characteristic of the pulse that will matter is the net, integrated effect of the pulse--i.e., its area. For systems that respond much more quickly than others, the pulse will have to be of much shorter duration before the details of the pulse shape or its duration no longer matter. Nevertheless, for any physical system, we can always find a pulse that is "short enough." The unit impulse then is an idealization of this concept--the pulse that is short enough for _any_ system. As we will see in Chapter 2, the response of a system to this idealized pulse plays a crucial role in signal and system analysis, and in the process of developing and understanding this role, we will develop additional insight into the idealized signal.3

Figure 1.39: The product \(x(t)\delta_{\Delta}(t)\): (a) graphs of both functions; (b) enlarged view of the nonzero portion of their product.

[MISSING_PAGE_EMPTY:37]

As a check of our result, we can verify that we can recover \(x(t)\) from \(\dot{x}(t)\). Specifically, since \(x(t)\) and \(\dot{x}(t)\) are both zero for \(t\,\leq\,0\), we need only check that for \(t\,>\,0\),

\[x(t)\,=\,\int_{0}^{t}\dot{x}(\tau)\,d\tau. \tag{77}\]

As illustrated in Figure 40(c), for \(t\,<\,1\), the integral on the right-hand side of eq. (77) is zero, since none of the impulses that constitute \(\dot{x}(t)\) are within the interval of integration. For \(1\,<\,t\,<\,2\), the first impulse (located at \(t\,=\,1\)) is the only one within the integration interval, and thus the integral in eq. (77) equals \(2\), the area of this impulse. For \(2\,<\,t\,<\,4\), the first two impulses are within the interval of integration, and the integral accumulates the sum of both of their areas, namely, \(2\,-\,3\,=\,-\,1\). Finally, for \(t\,>\,4\), all three impulses are within the integration interval, so that the integral equals the sum of all three areas--that is, \(2\,-\,3\,+\,2\,=\,+\,1\). The result is exactly the signal \(x(t)\) depicted in Figure 40(a).

### 5 Continuous-time and discrete-time systems

Physical systems in the broadest sense are an interconnection of components, devices, or subsystems. In contexts ranging from signal processing and communications to electromechanical motors, automotive vehicles, and chemical-processing plants, a _system_ can be viewed as a process in which input signals are transformed by the system or cause the system to respond in some way, resulting in other signals as outputs. For example, a high-fidelity system takes a recorded audio signal and generates a reproduction of that signal. If the hi-fi system has tone controls, we can change the tonal quality of the reproduced signal. Similarly, the circuit in Figure 1 can be viewed as a system with input voltage \(v_{s}(t)\) and output voltage \(v_{c}(t)\), while the automobile in Figure 2 can be thought of as a system with input equal to the force \(f(t)\) and output equal to the velocity \(v(t)\) of the vehicle. An image-enhancement system transforms an input image into an output image that has some desired properties, such as improved contrast.

A _continuous-time system_ is a system in which continuous-time input signals are applied and result in continuous-time output signals. Such a system will be represented pictorially as in Figure 41(a), where \(x(t)\) is the input and \(y(t)\) is the output. Alternatively, we will often represent the input-output relation of a continuous-time system by the notation

\[x(t)\,\to\,y(t). \tag{78}\]

Figure 41: (a) Continuous-time system; (b) discrete-time system.

Similarly, a _discrete-time system_--that is, a system that transforms discrete-time inputs into discrete-time outputs--will be depicted as in Figure 1.41(b) and will sometimes be represented symbolically as

\[x[n]\,\to\,y[n]. \tag{1.79}\]

In most of this book, we will treat discrete-time systems and continuous-time systems separately but in parallel. In Chapter 7, we will bring continuous-time and discrete-time systems together through the concept of sampling, and we will develop some insights into the use of discrete-time systems to process continuous-time signals that have been sampled.

#### Simple Examples of Systems

One of the most important motivations for the development of general tools for analyzing and designing systems is that systems from many different applications have very similar mathematical descriptions. To illustrate this, we begin with a few simple examples.

**Example 1.8**: Consider the \(RC\) circuit depicted in Figure 1.1. If we regard \(v_{s}(t)\) as the input signal and \(v_{c}(t)\) as the output signal, then we can use simple circuit analysis to derive an equation describing the relationship between the input and output. Specifically, from Ohm's law, the current \(i(t)\) through the resistor is proportional (with proportionality constant \(1/R\)) to the voltage drop across the resistor; i.e.,

\[i(t)\,=\,\frac{v_{s}(t)-v_{c}(t)}{R}. \tag{1.80}\]

Similarly, using the defining constitutive relation for a capacitor, we can relate \(i(t)\) to the rate of change with time of the voltage across the capacitor:

\[i(t)\,=\,C\frac{dv_{c}(t)}{dt}. \tag{1.81}\]

Equating the right-hand sides of eqs. (1.80) and (1.81), we obtain a differential equation describing the relationship between the input \(v_{s}(t)\) and the output \(v_{c}(t)\):

\[\frac{dv_{c}(t)}{dt}+\frac{1}{RC}v_{c}(t)\,=\,\frac{1}{RC}v_{s}(t). \tag{1.82}\]

## Example 1.9

Consider Figure 1.2, in which we regard the force \(f(t)\) as the input and the velocity \(v(t)\) as the output. If we let \(m\) denote the mass of the automobile and \(mpv\) the resistance due to friction, then equating acceleration--i.e., the time derivative of velocity--with net force divided by mass, we obtain

\[\frac{dv(t)}{dt}\,=\,\frac{1}{m}\left[\,f(t)-\rho v(t)\right], \tag{1.83}\]i.e.,

\[\frac{dv(t)}{dt}+\frac{\rho}{m}v(t)=\frac{1}{m}f(t). \tag{1.84}\]

Examining and comparing eqs. (1.82) and (1.84) in the above examples, we see that the input-output relationships captured in these two equations for these two very different physical systems are basically the same. In particular, they are both examples of first-order linear differential equations of the form

\[\frac{dy(t)}{dt}+ay(t)=bx(t), \tag{1.85}\]

where \(x(t)\) is the input, \(y(t)\) is the output, and \(a\) and \(b\) are constants. This is one very simple example of the fact that, by developing methods for analyzing general classes of systems such as that represented by eq. (1.85), we will be able to use them in a wide variety of applications.

### Example 1.10

As a simple example of a discrete-time system, consider a simple model for the balance in a bank account from month to month. Specifically, let \(y[n]\) denote the balance at the end of the \(n\)th month, and suppose that \(y[n]\) evolves from month to month according to the equation

\[y[n]=1.01y[n-1]+x[n], \tag{1.86}\]

or equivalently,

\[y[n]-1.01y[n-1]=x[n], \tag{1.87}\]

where \(x[n]\) represents the net deposit (i.e., deposits minus withdrawals) during the \(n\)th month and the term \(1.01y[n-1]\) models the fact that we accrue 1% interest each month.

### Example 1.11

As a second example, consider a simple digital simulation of the differential equation in eq. (1.84) in which we resolve time into discrete intervals of length \(\Delta\) and approximate \(dv(t)/dt\) at \(t=n\Delta\) by the first backward difference, i.e.,

\[\frac{v(n\Delta)-v((n-1)\Delta)}{\Delta}.\]

In this case, if we let \(v[n]=v(n\Delta)\) and \(f[n]=f(n\Delta)\), we obtain the following discrete-time model relating the sampled signals \(f[n]\) and \(v[n]\):

\[v[n]-\frac{m}{(m+\rho\Delta)}v[n-1]=\frac{\Delta}{(m+\rho\Delta)}f[n]. \tag{1.88}\]

Comparing eqs. (1.87) and (1.88), we see that they are both examples of the same general first-orderAs the preceding examples suggest, the mathematical descriptions of systems from a wide variety of applications frequently have a great deal in common, and it is this fact that provides considerable motivation for the development of broadly applicable tools for signal and system analysis. The key to doing this successfully is identifying classes of systems that have two important characteristics: (1) The systems in this class have properties and structures that we can exploit to gain insight into their behavior and to develop effective tools for their analysis; and (2) many systems of practical importance can be accurately modeled using systems in this class. It is on the first of these characteristics that most of this book focuses, as we develop tools for a particular class of systems referred to as linear, time-invariant systems. In the next section, we will introduce the properties that characterize this class, as well as a number of other very important basic system properties.

The second characteristic mentioned in the preceding paragraph is of obvious importance for any system analysis technique to be of value in practice. It is a well-established fact that a wide range of physical systems (including those in Examples 1.8-1.10) can be well modeled within the class of systems on which we focus in this book. However, a critical point is that _any_ model used in describing or analyzing a physical system represents an idealization of that system, and thus, any resulting analysis is only as good as the model itself. For example, the simple linear model of a resistor in eq. (1.80) and that of a capacitor in eq. (1.81) are idealizations. However, these idealizations are quite accurate for real resistors and capacitors in many applications, and thus, analyses employing such idealizations provide useful results and conclusions, as long as the voltages and currents remain within the operating conditions under which these simple linear models are valid. Similarly, the use of a linear retarding force to represent frictional effects in eq. (1.83) is an approximation with a range of validity. Consequently, although we will not address this issue in the book, it is important to remember that an essential component of engineering practice in using the methods we develop here consists of identifying the range of validity of the assumptions that have gone into a model and ensuring that any analysis or design based on that model does not violate those assumptions.

#### Interconnections of Systems

An important idea that we will use throughout this book is the concept of the interconnection of systems. Many real systems are built as interconnections of several subsystems. One example is an audio system, which involves the interconnection of a radio receiver, compact disc player, or tape deck with an amplifier and one or more speakers. Another is a digitally controlled aircraft, which is an interconnection of the aircraft, described by its equations of motion and the aerodynamic forces affecting it; the sensors, which measure various aircraft variables such as accelerations, rotation rates, and heading; a digital autopilot, which responds to the measured variables and to command inputs from the pilot (e.g., the desired course, altitude, and speed); and the aircraft's actuators, which respond to inputs provided by the autopilot in order to use the aircraft control surfaces (rudder, tail, ailerons) to change the aerodynamic forces on the aircraft. By viewing such a system as an interconnection of its components, we can use our understanding of the component systems and of how they are interconnected in order to analyze the operation and behavior of the overall system. In addition, by describing a system in terms of an interconnection of simpler subsystems, we may in fact be able to define useful ways in which to synthesize complex systems out of simpler, basic building blocks.

While one can construct a variety of system interconnections, there are several basic ones that are frequently encountered. A _series_ or _cascade interconnection_ of two systems is illustrated in Figure 1.42(a). Diagrams such as this are referred to as _block diagrams._ Here, the output of System 1 is the input to System 2, and the overall system transforms an input by processing it first by System 1 and then by System 2. An example of a series interconnection is a radio receiver followed by an amplifier. Similarly, one can define a series interconnection of three or more systems.

A _parallel interconnection_ of two systems is illustrated in Figure 1.42(b). Here, the same input signal is applied to Systems 1 and 2. The symbol "\(\oplus\)" in the figure denotes addition, so that the output of the parallel interconnection is the sum of the outputs of Systems 1 and 2. An example of a parallel interconnection is a simple audio system with several microphones feeding into a single amplifier and speaker system. In addition to the simple parallel interconnection in Figure 1.42(b), we can define parallel interconnections of more than two systems, and we can combine both cascade and parallel interconnections

Figure 1.42: Interconnection of two systems: (a) series (cascade) interconnection; (b) parallel interconnection; (c) series-parallel interconnection.

to obtain more complicated interconnections. An example of such an interconnection is given in Figure 1.42(c).4

Footnote 4: On occasion, we will also use the symbol \(\otimes\) in our pictorial representation of systems to denote the operation of multiplying two signals (see, for example, Figure 4.26).

Another important type of system interconnection is a _feedback interconnection_, an example of which is illustrated in Figure 1.43. Here, the output of System 1 is the input to System 2, while the output of System 2 is fed back and added to the external input to produce the actual input to System 1. Feedback systems arise in a wide variety of applications. For example, a cruise control system on an automobile senses the vehicle's velocity and adjusts the fuel flow in order to keep the speed at the desired level. Similarly, a digitally controlled aircraft is most naturally thought of as a feedback system in which differences between actual and desired speed, heading, or altitude are fed back through the autopilot in order to correct these discrepancies. Also, electrical circuits are often usefully viewed as containing feedback interconnections. As an example, consider the circuit depicted in Figure 1.44(a). As indicated in Figure 1.44(b), this system can be viewed as the feedback interconnection of the two circuit elements.

Figure 1.44: (a) Simple electrical circuit; (b) block diagram in which the circuit is depicted as the feedback interconnection of two circuit elements.

### Basic System Properties

In this section we introduce and discuss a number of basic properties of continuous-time and discrete-time systems. These properties have important physical interpretations and relatively simple mathematical descriptions using the signals and systems language that we have begun to develop.

#### Systems with and without Memory

A system is said to be _memoryless_ if its output for each value of the independent variable at a given time is dependent only on the input at that same time. For example, the system specified by the relationship

\[y[n]\,=\,(2x[n]\,-\,x^{2}[n])^{2} \tag{90}\]

is memoryless, as the value of \(y[n]\) at any particular time \(n_{0}\) depends only on the value of \(x[n]\) at that time. Similarly, a resistor is a memoryless system; with the input \(x(t)\) taken as the current and with the voltage taken as the output \(y(t)\), the input-output relationship of a resistor is

\[y(t)\,=\,Rx(t), \tag{91}\]

where \(R\) is the resistance. One particularly simple memoryless system is the _identity system,_ whose output is identical to its input. That is, the input-output relationship for the continuous-time identity system is

\[y(t)\,=\,x(t),\]

and the corresponding relationship in discrete time is

\[y[n]\,=\,x[n].\]

An example of a discrete-time system with memory is an _accumulator_ or _summer_

\[y[n]\,=\,\sum_{k\,=\,-\,\infty}^{n}x[k], \tag{92}\]

and a second example is a _delay_

\[y[n]\,=\,x[n-1]. \tag{93}\]

A capacitor is an example of a continuous-time system with memory, since if the input is taken to be the current and the output is the voltage, then

\[y(t)\,=\,\frac{1}{C}\,\int_{-\,\infty}^{t}x(\tau)\,d\tau, \tag{94}\]

where \(C\) is the capacitance.

Roughly speaking, the concept of memory in a system corresponds to the presence of a mechanism in the system that retains or stores information about input values at timesother than the current time. For example, the delay in eq. (93) must retain or store the preceding value of the input. Similarly, the accumulator in eq. (92) must "remember" or store information about past inputs. In particular, the accumulator computes the running sum of all inputs up to the current time, and thus, at each instant of time, the accumulator must add the current input value to the preceding value of the running sum. In other words, the relationship between the input and output of an accumulator can be described as

\[y[n]\,=\,\sum_{k\,=\,-\,\infty}^{n-1}x[k]\,+\,x[n], \tag{95}\]

or equivalently,

\[y[n]\,=\,y[n\,-\,1]\,+\,x[n]. \tag{96}\]

Representated in the latter way, to obtain the output at the current time \(n\), the accumulator must remember the running sum of previous input values, which is exactly the preceding value of the accumulator output.

In many physical systems, memory is directly associated with the storage of energy. For example, the capacitor in eq. (94) stores energy by accumulating electrical charge, represented as the integral of the current. Thus, the simple \(RC\) circuit in Example 8 and Figure 1 has memory physically stored in the capacitor. Similarly, the automobile in Figure 2 has memory stored in its kinetic energy. In discrete-time systems implemented with computers or digital microprocessors, memory is typically directly associated with storage registers that retain values between clock pulses.

While the concept of memory in a system would typically suggest storing _past_ input and output values, our formal definition also leads to our referring to a system as having memory if the current output is dependent on _future_ values of the input and output. While systems having this dependence on future values might at first seem unnatural, they in fact form an important class of systems, as we discuss further in Section 6.3.

#### Invertibility and Inverse Systems

A system is said to be _invertible_ if distinct inputs lead to distinct outputs. As illustrated in Figure 45(a) for the discrete-time case, if a system is invertible, then an _inverse system_ exists that, when cascaded with the original system, yields an output \(w[n]\) equal to the input \(x[n]\) to the first system. Thus, the series interconnection in Figure 45(a) has an overall input-output relationship which is the same as that for the identity system.

An example of an invertible continuous-time system is

\[y(t)\,=\,2x(t), \tag{97}\]

for which the inverse system is

\[w(t)\,=\,\frac{1}{2}\,y(t). \tag{98}\]

This example is illustrated in Figure 45(b). Another example of an invertible system is the accumulator of eq. (92). For this system, the difference between two successive values of the output is precisely the last input value. Therefore, in this case, the inverse system is

\[w[n]\,=\,y[n]-y[n-1], \tag{1.99}\]

as illustrated in Figure 1.45(c). Examples of noninvertible systems are

\[y[n]\,=\,0, \tag{1.100}\]

that is, the system that produces the zero output sequence for any input sequence, and

\[y(t)\,=\,x^{2}(t), \tag{1.101}\]

in which case we cannot determine the sign of the input from knowledge of the output.

The concept of invertibility is important in many contexts. One example arises in systems for encoding used in a wide variety of communications applications. In such a system, a signal that we wish to transmit is first applied as the input to a system known as an encoder. There are many reasons for doing this, ranging from the desire to encrypt the original message for secure or private communication to the objective of providing some redundancy in the signal (for example, by adding what are known as parity bits) so that any errors that occur in transmission can be detected and, possibly, corrected. For _lossless_ coding, the input to the encoder must be exactly recoverable from the output; i.e., the encoder must be invertible.

#### Causality

A system is _causal_ if the output at any time depends only on values of the input at the present time and in the past. Such a system is often referred to as being _nonanticipative,_ as

Figure 1.45: Concept of an inverse system for: (a) a general invertible system; (b) the invertible system described by eq. (1.97); (c) the invertible system defined in eq. (1.92).

the system output does not anticipate future values of the input. Consequently, if two inputs to a causal system are identical up to some point in time \(t_{0}\) or \(n_{0}\), the corresponding outputs must also be equal up to this same time. The \(RC\) circuit of Figure 1.1 is causal, since the capacitor voltage responds only to the present and past values of the source voltage. Similarly, the motion of an automobile is causal, since it does not anticipate future actions of the driver. The systems described in eqs. (1.92) - (1.94) are also causal, but the systems defined by

\[y[n]\,=\,x[n]-\,x[n+1] \tag{1.102}\]

and

\[y(t)\,=\,x(t+1) \tag{1.103}\]

are not. All memoryless systems are causal, since the output responds only to the current value of the input.

Although causal systems are of great importance, they do not by any means constitute the only systems that are of practical significance. For example, causality is not often an essential constraint in applications in which the independent variable is not time, such as in image processing. Furthermore, in processing data that have been recorded previously, as often happens with speech, geophysical, or meteorological signals, to name a few, we are by no means constrained to causal processing. As another example, in many applications, including historical stock market analysis and demographic studies, we may be interested in determining a slowly varying trend in data that also contain high-frequency fluctuations about that trend. In this case, a commonly used approach is to average data over an interval in order to smooth out the fluctuations and keep only the trend. An example of a noncausal averaging system is

\[y[n]\,=\,\frac{1}{2M+1}\,\sum_{k\,=\,-M}^{+M}x[n-k]. \tag{1.104}\]

## Example 1.12

When checking the causality of a system, it is important to look carefully at the input-output relation. To illustrate some of the issues involved in doing this, we will check the causality of two particular systems.

The first system is defined by

\[y[n]\,=\,x[-n]. \tag{1.105}\]

Note that the output \(y[n_{0}]\) at a positive time \(n_{0}\) depends only on the value of the input signal \(x[-n_{0}]\) at time \((-n_{0})\), which is negative and therefore in the past of \(n_{0}\). We may be tempted to conclude at this point that the given system is causal. However, we should always be careful to check the input-output relation for _all_ times. In particular, for \(n<0\), e.g. \(n\,=\,-4\), we see that \(y[-4]\,=\,x[4]\), so that the output at this time depends on a future value of the input. Hence, the system is not causal.

It is also important to distinguish carefully the effects of the input from those of any other functions used in the definition of the system. For example, consider the system

\[y(t)\,=\,x(t)\cos(t+1). \tag{1.106}\]In this system, the output at any time \(t\) equals the input at that same time multiplied by a number that varies with time. Specifically, we can rewrite eq. (1.106) as \[y(t)\,=\,x(t)g(t),\] where g(t) is a time-varying function, namely \(g(t)\,=\,\cos(t\,+\,1)\). Thus, only the current value of the input \(x(t)\) influences the current value of the output \(y(t)\), and we conclude that this system is causal (and, in fact, memoryless).

#### Stability

_Stability_ is another important system property. Informally, a stable system is one in which small inputs lead to responses that do not diverge. For example, consider the pendulum in Figure 1.46(a), in which the input is the applied force \(x(t)\) and the output is the angular deviation \(y(t)\) from the vertical. In this case, gravity applies a restoring force that tends to return the pendulum to the vertical position, and frictional losses due to drag tend to slow it down. Consequently, if a small force \(x(t)\) is applied, the resulting deflection from vertical will also be small. In contrast, for the inverted pendulum in Figure 1.46(b), the effect of gravity is to apply a force that tends to _increase_ the deviation from vertical. Thus, a small applied force leads to a large vertical deflection causing the pendulum to topple over, despite any retarding forces due to friction.

The system in Figure 1.46(a) is an example of a stable system, while that in Figure 1.46(b) is unstable. Models for chain reactions or for population growth with unlimited food supplies and no predators are examples of unstable systems, since the system response grows without bound in response to small inputs. Another example of an unstable system is the model for a bank account balance in eq. (1.86), since if an initial deposit is made (i.e., \(x[0]\,=\,\) a positive amount) and there are no subsequent withdrawals, then that deposit will grow each month without bound, because of the compounding effect of interest payments.

Figure 1.46: (a) A stable pendulum; (b) an unstable inverted pendulum.

[MISSING_PAGE_FAIL:49]

[MISSING_PAGE_FAIL:50]

[MISSING_PAGE_FAIL:51]

While the system in the preceding example has a time-varying gain and as a result is a time-varying system, the system in eq. (1.97) has a constant gain and, in fact, is time invariant. Other examples of time-invariant systems are given by eqs. (1.91)-(1.104). The following example illustrates a time-varying system.

### Example 1.16

Consider the system

\[y(t)\,=\,x(2t). \tag{1.120}\]

This system represents a time scaling. That is, \(y(t)\) is a time-compressed (by a factor of 2) version of \(x(t)\). Intuitively, then, any time shift in the input will also be compressed by a factor of 2, and it is for this reason that the system is not time invariant. To demonstrate this by counterexample, consider the input \(x_{1}(t)\) shown in Figure 1.47(a) and the resulting output \(y_{1}(t)\) depicted in Figure 1.47(b). If we then shift the input by 2--i.e., consider \(x_{2}(t)\,=\,x_{1}(t\,-\,2)\), as shown in Figure 1.47(c)--we obtain the resulting output

Figure 1.47: (a) The input \(x_{1}(t)\) to the system in Example 1.16; (b) the output \(y_{1}(t)\) corresponding to \(x_{1}(t)\); (c) the shifted input \(x_{2}(

[MISSING_PAGE_FAIL:53]

In the following examples we illustrate how the linearity of a given system can be checked by directly applying the definition of linearity.

### Example 1.17

Consider a system \(S\) whose input \(x(t)\) and output \(y(t)\) are related by

\[y(t)\,=\,tx(t)\]

To determine whether or not \(S\) is linear, we consider two arbitrary inputs \(x_{1}(t)\) and \(x_{2}(t)\).

\[x_{1}(t)\,\to\,y_{1}(t)\,=\,tx_{1}(t)\] \[x_{2}(t)\,\to\,y_{2}(t)\,=\,tx_{2}(t)\]

Let \(x_{3}(t)\) be a linear combination of \(x_{1}(t)\) and \(x_{2}(t)\). That is,

\[x_{3}(t)\,=\,ax_{1}(t)+bx_{2}(t)\]

where \(a\) and \(b\) are arbitrary scalars. If \(x_{3}(t)\) is the input to \(S\), then the corresponding output may be expressed as

\[y_{3}(t)\,=\,tx_{3}(t)\] \[\,=\,t(ax_{1}(t)+bx_{2}(t))\] \[\,=\,atx_{1}(t)+btx_{2}(t)\] \[\,=\,ay_{1}(t)+by_{2}(t)\]

We conclude that the system \(S\) is linear.

### Example 1.18

Let us apply the linearity-checking procedure of the previous example to another system \(S\) whose input \(x(t)\) and output \(y(t)\) are related by

\[y(t)\,=\,x^{2}(t)\]

Defining \(x_{1}(t)\), \(x_{2}(t)\), and \(x_{3}(t)\) as in the previous example, we have

\[x_{1}(t)\,\to\,y_{1}(t)\,=\,x_{1}^{2}(t)\] \[x_{2}(t)\,\to\,y_{2}(t)\,=\,x_{2}^{2}(t)\]

and

\[x_{3}(t)\,\to\,y_{3}(t) \,=\,x_{3}^{2}(t)\] \[\,=\,(ax_{1}(t)\,+\,bx_{2

[MISSING_PAGE_EMPTY:55]

[MISSING_PAGE_FAIL:56]

**Basic problems** emphasize the mechanics of using concepts and methods in a manner similar to that illustrated in the examples that are solved in the text.

**Advanced problems** explore and elaborate upon the foundations and practical implications of the textual material.

The first section of problems belongs to the basic category, and the answers are provided in the back of the book. The next two sections contain problems belonging to the basic and advanced categories, respectively. A final section, **Mathematical Review**, provides practice problems on the fundamental ideas of complex arithmetic and algebra.

## 1 Basic Problems With Answers

1. Express each of the following complex numbers in Cartesian form \((x+jy)\): \(\frac{1}{2}e^{j\pi}\), \(\frac{1}{2}e^{-j\pi}\), \(e^{j\pi/2}\), \(e^{-j\pi/2}\), \(e^{j5\pi/2}\), \(\sqrt{2}e^{j\pi/4}\), \(\sqrt{2}e^{j9\pi/4}\), \(\sqrt{2}e^{-j9\pi/4}\), \(\sqrt{2}e^{-j9\pi/4}\).
2. Express each of the following complex numbers in polar form \((re^{j\theta}\), with \(-\pi<\theta\ \leq\ \pi)\): \(5\), \(-2\), \(-3\)\(j\), \(\frac{1}{2}\ -\)\(j\)\(\frac{\sqrt{3}}{2}\), \(1+j\), \((1-j)^{2}\), \(j(1-j)\), \((1+j)\)/\((1-j)\), \((\sqrt{2}\ +\ j\sqrt{2})\)/ \((1\ +\ j\sqrt{3})\).
3. Determine the values of \(P_{\times}\) and \(E_{\times}\) for each of the following signals: 1. \(x_{1}(t)=e^{-2t}u(t)\) 2. \(x_{2}(t)=e^{j(2t+\pi/4)}\) 3. \(x_{3}(t)=\cos(t)\) 4. \(x_{1}[n]=(\frac{1}{2})^{n}u[n]\) 3. \(x_{2}[n]=e^{j(\pi/2n+\pi/8)}\) 3. \(x_{3}[n]=\cos(\frac{\pi}{4}n)\)
4. Let \(x[n]\) be a signal with \(x[n]=0\) for \(n<-2\) and \(n>4\). For each signal

[MISSING_PAGE_EMPTY:58]

* Is the system memoryless?
* Determine the output of the system when the input is \(A\delta[n]\), where \(A\) is any real or complex number.
* Is the system invertible?
* Consider a continuous-time system with input \(x(t)\) and output \(y(t)\) related by \[y(t)\:=\:x(\sin(t)).\]
* Is this system causal?
* Is this system linear?
* Consider a discrete-time system with input \(x[n]\) and output \(y[n]\) related by \[y[n]\:=\:\sum_{k\:=\:n\:-\:n_{0}}^{n+\:n_{0}}x[k],\] where \(n_{0}\) is a finite positive integer.
* Is this system linear?
* Is this system time-invariant?
* If \(x[n]\) is known to be bounded by a finite integer \(B\) (i.e., \(|x[n]|<B\) for all \(n\)), it can be shown that \(y[n]\) is bounded by a finite number \(C\). We conclude that the given system is stable. Express \(C\) in terms of \(B\) and \(n_{0}\).
* For each of the following input-output relationships, determine whether the corresponding system is linear, time invariant or both.
* \(y(t)=t^{2}x(t-1)\) (b) \(y[n]\:=\:x^{2}[n-2]\) (c) \(y[n]\:=\:x

**Figure P1.21 Figure P1.22 Figure P1.23 Figure P1.24 Figure P1.25 Figure P1.26 Figure P1.27 Figure P1.28 Figure P1.29 Figure P1.21 Figure P1.21 Figure P1.21 Figure P1.22

**1.23.** Determine and sketch the even and odd parts of the signals depicted in Figure P1.23. Label your sketches carefully.

**1.24.** Determine and sketch the even and odd parts of the signals depicted in Figure P1.24. Label your sketches carefully.

**1.25**.: Determine whether or not each of the following continuous-time signals is periodic. If the signal is periodic, determine its fundamental period.

**(a)**: \(x(t)=3\cos(4t+\frac{\pi}{3})\) **(b)**: \(x(t)=e^{j(\pi t-1)}\) **(c)**: \(x(t)=[\cos(2t-\frac{\pi}{3})]^{2}\) **(d)**: \(x(t)=\delta v\{\cos(4\pi t)u(t)\}\) **(e)**: \(x(t)=\delta v\{\sin(4\pi t)u(t)\}\) **(f)**: \(x(t)=\sum\limits_{n=-\infty}^{\infty}e^{-(2t-n)}u(2t-n)\)
**1.26**.: Determine whether or not each of the following discrete-time signals is periodic. If the signal is periodic, determine its fundamental period.

**(a)**: \(x[n]=\sin(\frac{6\pi}{7}n+1)\) **(b)**: \(x[n]=\cos(\frac{n}{8}-\pi)\) **(c)**: \(x[n]=\cos(\frac{\pi}{8}n^{2})\) **(d)**: \(x[n]=\cos(\frac{\pi}{2}n)\cos(\frac{\pi}{4}n)\) **(e)**: \(x[n]=2\cos(\frac{\pi}{4}n)+\sin(\frac{\pi}{8}n)-2\cos(\frac{\pi}{2}n+\frac{ \pi}{6})\)
**1.27**.: In this chapter, we introduced a number of general properties of systems. In particular, a system may or may not be

**(1)**: Memoryless

**(2)**: Time invariant

**(3)**: Linear

**(4)**: Causal

**(5)**: Stable

Determine which of these properties hold and which do not hold for each of the following continuous-time systems. Justify your answers. In each example, \(y(t)\) denotes the system output and \(x(t)\) is the system input.

[MISSING_PAGE_EMPTY:62]

input signals. Much of the remainder of this book deals with a thorough exploitation of this fact in order to develop results and techniques for analyzing and synthesizing LTI systems.

**(a)**: Consider an LTI system whose response to the signal \(x_{1}(t)\) in Figure P1.31(a) is the signal \(y_{1}(t)\) illustrated in Figure P1.31(b). Determine and sketch carefully the response of the system to the input \(x_{2}(t)\) depicted in Figure P1.31(c).
**(b)**: Determine and sketch the response of the system considered in part (a) to the input \(x_{3}(t)\) shown in Figure P1.31(d).

**ADVANCED PROBLEMS**

1.4. Let \(x(t)\) be a continuous-time signal, and let

\[y_{1}(t)\,=\,x(2t)\text{ and }y_{2}(t)\,=\,x(t/2).\]

The signal \(y_{1}(t)\) represents a speeded up version of \(x(t)\) in the sense that the duration of the signal is cut in half. Similarly, \(y_{2}(t)\) represents a slowed down version of \(x(t)\) in the sense that the duration of the signal is doubled. Consider the following statements:

If \(x(t)\) is periodic, then \(y_{1}(t)\) is periodic.

If \(y_{1}(t)\) is periodic, then \(x(t)\) is periodic.

If \(x(t)\) is periodic, then \(y_{2}(t)\) is periodic.

If \(y_{2}(t)\) is periodic, then \(x(t)\) is periodic.

For each of these statements, determine whether it is true, and if so, determine the relationship between the fundamental periods of the two signals considered in the statement. If the statement is not true, produce a counterexample to it.

1.4. Let \(x[n]\) be a discrete-time signal, and let The signals \(y_{1}[n]\) and \(y_{2}[n]\) respectively represent in some sense the speeded up and slowed down versions of \(x[n]\). However, it should be noted that the discrete-time notions of speeded up and slowed down have subtle differences with respect to their continuous-time counterparts. Consider the following statements:

1. If \(x[n]\) is periodic, then \(y_{1}[n]\) is periodic.
2. If \(y_{1}[n]\) is periodic, then \(x[n]\) is periodic.
3. If \(x[n]\) is periodic, then \(y_{2}[n]\) is periodic.
4. If \(y_{2}[n]\) is periodic, then \(x[n]\) is periodic.

For each of these statements, determine whether it is true, and if so, determine the relationship between the fundamental periods of the two signals considered in the statement. If the statement is not true, produce a counterexample to it.

1. In this problem, we explore several of the properties of even and odd signals. 1. Show that if \(x[n]\) is an odd signal, then \[\sum_{n\,=\,-\infty}^{+\infty}x[n]\,=\,0.\] 2. Show that if \(x_{1}[n]\) is an odd signal and \(x_{2}[n]\) is an even signal, then \(x_{1}[n]x_{2}[n]\) is an odd signal. 3. Let \(x[n]\) be an arbitrary signal with even and odd parts denoted by \[x_{e}[n]\,=\,\mathcal{E}_{\varPhi}\{x[n]\}\] and \[x_{o}[n]\,=\,\mathcal{O}d* Let \(x(t)\) be the continuous-time complex exponential signal \[x(t)\,=\,e^{ja_{0}t}\] with fundamental frequency \(\omega_{0}\) and fundamental period \(T_{0}\,=\,2\pi/\omega_{0}\). Consider the discrete-time signal obtained by taking equally spaced samples of \(x(t)\)--that is, \[x[n]\,=\,x(nT)\,=\,e^{ja_{0}nT}.\]
* Show that \(x[n]\) is periodic if and only if \(T/T_{0}\) is a rational number--that is, if and only if some multiple of the sampling interval _exactly equals_ a multiple of the period of \(x(t)\).
* Suppose that \(x[n]\) is periodic--that is, that \[\frac{T}{T_{0}}\,=\,\frac{p}{q},\] (P1.36-1) where \(p\) and \(q\) are integers. What are the fundamental period and fundamental frequency of \(x[n]\)? Express the fundamental frequency as a fraction of \(\omega_{0}T\).
* Again assuming that \(T/T_{0}\) satisfies eq. (P1.36-1), determine precisely how many periods of \(x(t)\) are needed to obtain the samples that form a single period of \(x[n]\).
* An important concept in many communications applications is the _correlation_ between two signals. In the problems at the end of Chapter 2, we will have more to say about this topic and will provide some indication of how it is used in practice. For now, we content ourselves with a brief introduction to correlation functions and some of their properties. Let \(x(t)\) and \(y(t)\) be two signals; then the _correlation function_ is defined as \[\phi_{x,y}(t)\,=\,\int_{-\infty}^{\infty}x(t\,+\,\tau)y(\tau)d\tau.\] The function \(\phi_{xx}(t)\) is usually referred to as the _autocorrelation function_ of the signal \(x(t)\), while \(\phi_{xy}(t)\) is often called a _cross-correlation function_.
* What is the relationship between \(\phi_{xy}(t)\) and \(\phi_{yx}(t)\)?
* Compute the odd part of \(\phi_{xx}(t)\).
* Suppose that \(y(t)\,=\,x(t\,+\,T)\). Express \(\phi_{xy}(t)\) and \(\phi_{yy}(t)\) in terms of \(\phi_{xx}(t)\).
* In this problem, we examine a few of the properties of the unit impulse function.
* Show that \[\delta(2t)\,=\,\frac{1}{2}\delta(t).\]
* _Hint_: Examine \(\delta_{\Delta}(t)\). (See Figure 1.34.)
* In Section 1.4, we defined the continuous-time unit impulse as the limit of the signal \(\delta_{\Delta}(t)\). More precisely, we defined several of the _properties_ of \(\delta(t)\) by examining the corresponding properties of \(\delta_{\Delta}(t)\). For example, since the signal

[MISSING_PAGE_EMPTY:66]

that each "behaves like an impulse" as \(\Delta\,\to\,0\) in that, if we let

\[u^{i}_{\Delta}(t)\,=\,\int_{-\infty}^{t}r^{i}_{\Delta}(\tau)d\tau,\]

then

\[\lim_{\Delta\to 0}u^{i}_{\Delta}(t)\,=\,u(t).\]

In each case, sketch and label carefully the signal \(u^{i}_{\Delta}(t)\). Note that

\[r^{2}_{\Delta}(0)\,=\,r^{4}_{\Delta}(0)\,=\,0\mbox{ for all }\Delta.\]

Therefore, it is not enough to define or to think of \(\delta(t)\) as being zero for \(t\neq 0\) and infinite for \(t\,=\,0\). Rather, it is properties such as eq. (P1.38-1) that define the impulse. In Section 2.5 we will define a whole class of signals known as _singularity functions_, which are related to the unit impulse and which are also defined in terms of their properties rather than their values.

1. The role played by \(u(t)\), \(\delta(t)\), and other singularity functions in the study of linear time-invariant systems is that of an _idealization_ of a physical phenomenon, and, as we will see, the use of these idealizations allow us to obtain an exceedingly important and very simple representation of such systems. In using singularity functions, we need, however, to be careful. In particular, we must remember that they are idealizations, and thus, whenever we perform a calculation using them, we are implicitly assuming that this calculation represents an accurate description of the behavior of the signals that they are intended to idealize. To illustrate, consider the equation

\[x(t)\delta(t)\,=\,x(0)\delta(t).\] (P1.39-1)

This equation is based on the observation that

\[x(t)\delta_{\Delta}(t)\,\approx\,x(0)\delta_{\Delta}(t).\] (P1.39-2)

Taking the limit of this relationship then yields the idealized one given by eq. (P1.39-1). However, a more careful examination of our derivation of eq. (P1.39-2) shows that that equation really makes sense only if \(x(t)\) is continuous at \(t\,=\,0\). If it is not, then we will not have \(x(t)\approx\,x(0)\) for \(t\) small.

To make this point clearer, consider the unit step signal \(u(t)\). Recall from eq. (1.70) that \(u(t)\,=\,0\) for \(t<0\) and \(u(t)\,=\,1\) for \(t>0\), but that its value at \(t\,=\,0\) is not defined. [Note, for example, that \(u_{\Delta}(0)\,=\,0\) for all \(\Delta\), while \(u^{1}_{\Delta}(0)\,=\,\frac{1}{2}\) (from Problem 1.38(b)).] The fact that \(u(0)\) is not defined is not particularly bothersome, as long as the calculations we perform using \(u(t)\) do not rely on a specific choice for \(u(0)\). For example, if \(f(t)\) is a signal that is continuous at \(t\,=\,0\), then the value of

\[\int_{-\infty}^{+\infty}f(\sigma)u(\sigma)d\sigma\]

does not depend upon a choice for \(u(0)\). On the other hand, the fact that \(u(0)\) is undefined is significant in that it means that certain calculations involving singularity functions are undefined. Consider trying to define a value for the product \(u(t)\delta(t)\)

[MISSING_PAGE_FAIL:68]

[MISSING_PAGE_EMPTY:69]

[MISSING_PAGE_FAIL:70]

* \(y[n]=\left\{\begin{array}{ll}x[n]-x[n-1]+3,&\mbox{if $x[0]\,\equiv\,0$}\\ x[n]-x[n-1]-3,&\mbox{if $x[0]<0$}\end{array}\right.\)
* The system depicted in Figure P1.47(b).
* The system depicted in Figure P1.47(c).
* Suppose that a particular incrementally linear system has a representation as in Figure 1.48, with \(L\) denoting the linear system and \(y_{0}[n]\) the zero-input response. Show that \(S\) is time invariant if and only if \(L\) is a time-invariant system _and_\(y_{0}[n]\) is constant.

## 11 Mathematical Review

The complex number \(z\) can be expressed in several ways. The _Cartesian_ or _rectangular_ form for \(z\) is

\[z\,=\,x\,+\,jy,\]

where \(j\,=\,\sqrt{-1}\) and \(x\) and \(y\) are real numbers referred to respectively as the _real part_ and the _imaginary part_ of \(z\). As we indicated earlier, we will often use the notation

\[x\,=\,\langle\mathfrak{Re}\{z\},\,y\,=\,\mathfrak{\delta}m\{z\}.\]

The complex number \(z\) can also be represented in _polar form_ as

\[z\,=\,re^{j\theta},\]

where \(r>0\) is the _magnitude_ of \(z\) and \(\theta\) is the _angle_ or _phase_ of \(z\). These quantities will often be written as

\[r\,=\,|z|,\,\theta\,=\,\,\raisebox{-1.72pt}{$\times$}z.\]

The relationship between these two representations of complex numbers can be determined either from _Euler's relation_,

\[e^{j\theta}\,=\,\cos\theta\,+\,j\sin\theta,\]

or by plotting \(z\) in the complex plane, as shown in Figure P1.48, in which the coordinate axes are \(\langle\mathfrak{Re}\{z\}\) along the horizontal axis and \(\mathfrak{\delta}m\{z\}\) along the vertical axis. With respect to this graphical representation, \(x\) and \(y\) are the Cartesian coordinates of \(z\), and \(r\) and \(\theta\) are its polar coordinates.

**Figure P1.48**

[MISSING_PAGE_FAIL:72]

[MISSING_PAGE_EMPTY:73]
## Chapter Linear Time-Invariant Systems

### 1 Introduction

In Section 1.6 we introduced and discussed a number of basic system properties. Two of these, linearity and time invariance, play a fundamental role in signal and system analysis for two major reasons. First, many physical processes possess these properties and thus can be modeled as linear time-invariant (LTI) systems. In addition, LTI systems can be analyzed in considerable detail, providing both insight into their properties and a set of powerful tools that form the core of signal and system analysis.

A principal objective of this book is to develop an understanding of these properties and tools and to provide an introduction to several of the very important applications in which the tools are used. In this chapter, we begin the development by deriving and examining a fundamental and extremely useful representation for LTI systems and by introducing an important class of these systems.

One of the primary reasons LTI systems are amenable to analysis is that any such system possesses the superposition property described in Section 1.6.6. As a consequence, if we can represent the input to an LTI system in terms of a linear combination of a set of basic signals, we can then use superposition to compute the output of the system in terms of its responses to these basic signals.

As we will see in the following sections, one of the important characteristics of the unit impulse, both in discrete time and in continuous time, is that very general signals can be represented as linear combinations of delayed impulses. This fact, together with the properties of superposition and time invariance, will allow us to develop a complete characterization of any LTI system in terms of its response to a unit impulse. Such a representation, referred to as the convolution sum in the discrete-time case and the convolution integral in continuous time, provides considerable analytical convenience in dealingwith LTI systems. Following our development of the convolution sum and the convolution integral we use these characterizations to examine some of the other properties of LTI systems. We then consider the class of continuous-time systems described by linear constant-coefficient differential equations and its discrete-time counterpart, the class of systems described by linear constant-coefficient difference equations. We will return to examine these two very important classes of systems on a number of occasions in subsequent chapters. Finally, we will take another look at the continuous-time unit impulse function and a number of other signals that are closely related to it in order to provide some additional insight into these idealized signals and, in particular, to their use and interpretation in the context of analyzing LTI systems.

### 2.1 Discrete-Time LTI Systems: The Convolution Sum

#### The Representation of Discrete-Time Signals in Terms of Impulses

The key idea in visualizing how the discrete-time unit impulse can be used to construct any discrete-time signal is to think of a discrete-time signal as a sequence of individual impulses. To see how this intuitive picture can be turned into a mathematical representation, consider the signal \(x[n]\) depicted in Figure 2.1(a). In the remaining parts of this figure, we have depicted five time-shifted, scaled unit impulse sequences, where the scaling on each impulse equals the value of \(x[n]\) at the particular instant the unit sample occurs. For example,

\[x[-1]\delta[n+1] = \left\{\begin{array}{ll}x[-1],&n=-1\\ 0,&n\neq-1\end{array}\right.,\] \[x[0]\delta[n] = \left\{\begin{array}{ll}x[0],&n=0\\ 0,&n\neq 0\end{array}\right.,\] \[x[1]\delta[n-1] = \left\{\begin{array}{ll}x[1],&n=1\\ 0,&n\neq 1\end{array}\right..\]

Therefore, the sum of the five sequences in the figure equals \(x[n]\) for \(-2\,\leq\,n\,\leq\,2\). More generally, by including additional shifted, scaled impulses, we can write

\[x[n] = \ldots + x[-3]\delta[n+3]+x[-2]\delta[n+2]+x[-1]\delta[n+1]+x[0]\delta[n]\] \[+ x[1]\delta[n-1]+x[2]\delta[n-2]+x[3]\delta[n-3]+\ldots. \tag{2.1}\]

For any value of \(n\), only one of the terms on the right-hand side of eq. (2.1) is nonzero, and the scaling associated with that term is precisely \(x[n]\). Writing this summation in a more compact form, we have

\[x[n] = \sum_{k\,=\,-\infty}^{+\,\infty}x[k]\delta[n-k]. \tag{2.2}\]

This corresponds to the representation of an arbitrary sequence as a linear combination of shifted unit impulses \(\delta[n-k]\), where the weights in this linear combination are \(x[k]\). As an example, consider \(x[n]=u[n]\), the unit step. In this case, since \(u[k]=0\) for \(k<0\) 
Figure 2.1: Decomposition of a discrete-time signal into a weighted sum of shifted impulses.

and \(u[k]=1\) for \(k\,\geq\,0\), eq. (2.2) becomes

\[u[n]\,=\,\sum_{k\,=\,0}^{+\infty}\delta[n-k],\]

which is identical to the expression we derived in Section 1.4. [See eq. (1.67).]

Equation (2.2) is called the _sifting property_ of the discrete-time unit impulse. Because the sequence \(\delta[n-k]\) is nonzero only when \(k=n\), the summation on the right-hand side of eq. (2.2) "sifts" through the sequence of values \(x[k]\) and preserves only the value corresponding to \(k=n\). In the next subsection, we will exploit this representation of discrete-time signals in order to develop the convolution-sum representation for a discrete-time LTI system.

#### The Discrete-Time Unit Impulse Response and the Convolution-Sum Representation of LTI Systems

The importance of the sifting property of eqs. (2.1) and (2.2) lies in the fact that it represents \(x[n]\) as a superposition of scaled versions of a very simple set of elementary functions, namely, shifted unit impulses \(\delta[n-k]\), each of which is nonzero (with value 1) at a single point in time specified by the corresponding value of \(k\). The response of a linear system to \(x[n]\) will be the superposition of the scaled responses of the system to each of these shifted impulses. Moreover, the property of time invariance tells us that the responses of a time-invariant system to the time-shifted unit impulses are simply time-shifted versions of one another. The convolution-sum representation for discrete-time systems that are _both_ linear and time invariant results from putting these two basic facts together.

More specifically, consider the response of a linear (but possibly time-varying) system to an arbitrary input \(x[n]\). We can represent the input through eq. (2.2) as a linear combination of shifted unit impulses. Let \(h_{k}[n]\) denote the response of the linear system to the shifted unit impulse \(\delta[n-k]\). Then, from the superposition property for a linear system [eqs. (1.123) and (1.124)], the response \(y[n]\) of the linear system to the input \(x[n]\) in eq. (2.2) is simply the weighted linear combination of these basic responses. That is, with the input \(x[n]\) to a linear system expressed in the form of eq. (2.2), the output \(y[n]\) can be expressed as

\[y[n]\,=\,\sum_{k\,=\,-\,\infty}^{+\infty}x[k]h_{k}[n]. \tag{2.3}\]

Thus, according to eq. (2.3), if we know the response of a linear system to the set of shifted unit impulses, we can construct the response to an arbitrary input. An interpretation of eq. (2.3) is illustrated in Figure 2.2. The signal \(x[n]\) is applied as the input to a linear system whose responses \(h_{-1}[n]\), \(h_{0}[n]\), and \(h_{1}[n]\) to the signals \(\delta[n+1]\), \(\delta[n]\), and \(\delta[n-1]\), respectively, are depicted in Figure 2.2(b). Since \(x[n]\) can be written as a linear combination of \(\delta[n+1]\), \(\delta[n]\), and \(\delta[n-1]\), superposition allows us to write the response to \(x[n]\) as a linear combination of the responses to the individual shifted impulses. The individual shifted and scaled impulses that constitute \(x[n]\) are illustrated on the left-hand side of Figure 2.2(c), while the responses to these component signals are pictured on the right-hand side. In Figure 2.2(d) we have depicted the actual input \(x[n]\), which is the sum of the components on the left side of Figure 2.2(c) and the actual output \(y[n]\), which, by superposition, is the sum of the components on the right side of Figure 2.2(c). Thus, the response at time \(n\) of a linear system is simply the superposition of the responses due to the input value at each point in time.

In general, of course, the responses \(h_{k}[n]\) need not be related to each other for different values of \(k\). However, if the linear system is also _time invariant_, then these responses to time-shifted unit impulses are all time-shifted versions of each other. Specifically, since \(\delta[n\,-\,k]\) is a time-shifted version of \(\delta[n]\), the response \(h_{k}[n]\) is a time-shifted version of \(h_{0}[n]\); i.e.,

\[h_{k}[n]\,=\,h_{0}[n\,-\,k]. \tag{2.4}\]

For notational convenience, we will drop the subscript on \(h_{0}[n]\) and define the _unit impulse (sample) response_

\[h[n]\,=\,h_{0}[n]. \tag{2.5}\]

That is, \(h[n]\) is the output of the LTI system when \(\delta[n]\) is the input. Then for an LTI system. eq. (2.3) becomes

\[y[n]\,=\,\sum_{k\,-\,-\,\infty}^{+\infty}x[k]h[n\,-\,k]. \tag{2.6}\]

This result is referred to as the _convolution sum_ or _superposition sum_, and the operation on the right-hand side of eq. (2.6) is known as the _convolution_ of the sequences \(x[n]\) and \(h[n]\). We will represent the operation of convolution symbolically as

\[y[n]\,=\,x[n]*h[n]. \tag{2.7}\]

Figure 2.2: Graphical interpretation of the response of a discrete-time linear system as expressed in eq. (2.3).

Note that eq. (2.6) expresses the response of an LTI system to an arbitrary input in terms of the system's response to the unit impulse. From this, we see that an LTI system is completely characterized by its response to a single signal, namely, its response to the unit impulse.

The interpretation of eq. (2.6) is similar to the one we gave for eq. (2.3), where, in the case of an LTI system, the response due to the input \(x[k]\) applied at time \(k\) is \(x[k]h[n-k]\); i.e., it is a shifted and scaled version (an "echo") of \(h[n]\). As before, the actual output is the superposition of all these responses.

Figure 2.2: Continued

## Example 2.1

Consider an LTI system with impulse response \(h[n]\) and input \(x[n]\), as illustrated in Figure 2.3(a). For this case, since only \(x[0]\) and \(x[1]\) are nonzero, eq. (2.6) simplifies to the expression

\[y[n]\,=\,x[0]h[n-0]+x[1]h[n-1]\,=\,0.5h[n]+2h[n-1]. \tag{2.8}\]

The sequences \(0.5h[n]\) and \(2h[n-1]\) are the two echoes of the impulse response needed for the superposition involved in generating \(y[n]\). These echoes are displayed in Figure 2.3(b). By summing the two echoes for each value of \(n\), we obtain \(y[n]\), which is shown in Figure 2.3(c).

Figure 2.3: (a) The impulse response \(h[n]\) of an LTI system and an input \(x[n]\) to the system; (b) the responses or “echoes,” \(0.5h[n]\) and \(2h[n-1]\), to the nonzero values of the input, namely, \(x[0]=0.5\) and \(x[1]=2\); (c) the overall response \(y[n]\), which is the sum of the echos in (b).

[MISSING_PAGE_FAIL:8]

[MISSING_PAGE_EMPTY:9]

[MISSING_PAGE_EMPTY:10]

Figure 2.6: Graphical interpretation of the calculation of the convolution sum for Example 2.3.

The operation of convolution is sometimes described in terms of "sliding" the sequence \(h[n-k]\) past \(x[k]\). For example, suppose we have evaluated \(y[n]\) for some particular value of \(n\), say, \(n=n_{0}\). That is, we have sketched the signal \(h[n_{0}-k]\), multiplied it by the signal \(x[k]\), and summed the result over all values of \(k\). To evaluate \(y[n]\) at the next value of \(n\)--i.e., \(n=n_{0}+1\)--we need to sketch the signal \(h[(n_{0}+1)-k]\). However, we can do this simply by taking the signal \(h[n_{0}-k]\) and shifting it to the right by one point. For each successive value of \(n\), we continue this process of shifting \(h[n-k]\) to the right by one point, multiplying by \(x[k]\), and summing the result over \(k\).

### Example 2.4

As a further example, consider the two sequences

\[x[n]=\left\{\begin{array}{ll}1,&0\leq n\leq 4\\ 0,&\mbox{otherwise}\end{array}\right.\]

and

\[h[n]=\left\{\begin{array}{ll}\alpha^{n},&0\leq n\leq 6\\ 0,&\mbox{otherwise}\end{array}\right..\]

These signals are depicted in Figure 2.8 for a positive value of \(\alpha>1\). In order to calculate the convolution of the two signals, it is convenient to consider five separate intervals for \(n\). This is illustrated in Figure 2.9.

Interval 1.For \(n<0\), there is no overlap between the nonzero portions of \(x[k]\) and \(h[n-k]\), and consequently, \(y[n]=0\).

Interval 2.For \(0\leq n\leq 4\),

\[x[k]h[n-k]=\left\{\begin{array}{ll}\alpha^{n-k},&0\leq k\leq n\\ 0,&\mbox{otherwise}\end{array}\right..\]

Figure 2.7: Output for Example 2.3.

Thus, in this interval,

\[y[n]\,=\,\sum_{k\,=\,0}^{n}\alpha^{n-k}. \tag{2.14}\]

We can evaluate this sum using the finite sum formula, eq. (2.13). Specifically, changing the variable of summation in eq. (2.14) from \(k\) to \(r\,=\,n\,-\,k\), we obtain

\[y[n]\,=\,\sum_{r\,=\,0}^{n}\alpha^{r}\,=\,\frac{1\,-\,\alpha^{n+1}}{1-\alpha}.\]

Interval 3.For \(n>4\) but \(n-6\,\leq\,0\) (i.e., \(4<n\,\leq\,6\)),

\[x[k]h[n\,-\,k]\,=\,\left\{\begin{array}{ll}\alpha^{n-k},&0\,\leq\,k\,\leq\, 4\\ 0,&\mbox{otherwise}\end{array}\right..\]

Thus, in this interval,

\[y[n]\,=\,\sum_{k\,=\,0}^{4}\alpha^{n-k}. \tag{2.15}\]

Once again, we can use the geometric sum formula in eq. (2.13) to evaluate eq. (2.15). Specifically, factoring out the constant factor of \(\alpha^{n}\) from the summation in eq. (2.15) yields

\[y[n]\,=\,\alpha^{n}\sum_{k\,-\,0}^{4}(\alpha^{-1})^{k}\,=\,\alpha^{n}\frac{1 \,-\,\left(\alpha^{-1}\right)^{5}}{1\,-\,\alpha^{-1}}\,=\,\frac{\alpha^{n-4} \,-\,\alpha^{n+1}}{1\,-\,\alpha}. \tag{2.16}\]

Interval 4.For \(n>6\) but \(n-6\,\leq\,4\) (i.e., for \(6<n\,\leq\,10\)),

\[x[k]h[n\,-\,k]\,=\,\left\{\begin{array}{ll}\alpha^{n-k},&(n-6)\,\leq\,k\, \leq\,4\\ 0,&\mbox{otherwise}\end{array}\right.,\]

Figure 2.8: The signals to be convolved in Example 2.4.

Figure 2.9: Graphical interpretation of the convolution performed in Example 2.4.

so that \[y[n]\,=\,\sum_{k\,=\,n\,-6}^{4}\alpha^{n\,-\,k}.\] We can again use eq. (2.13) to evaluate this summation. Letting \(r\,=\,k\,-n\,+6\), we obtain \[y[n]\,=\,\sum_{r\,=\,0}^{10-n}\alpha^{6\,-\,r}\,=\,\alpha^{6}\sum_{r\,=\,0}^{10 -n}(\alpha^{-\,1})^{\gamma}\,=\,\alpha^{6}\frac{1-\alpha^{n\,-11}}{1-\alpha^{ \,-1}}\,=\,\frac{\alpha^{n\,-4}-\alpha^{7}}{1-\alpha}.\] Interval 5.For \(n-6>4\), or equivalently, \(n>10\), there is no overlap between the nonzero portions of \(x[k]\) and \(h[n\,-\,k]\), and hence, \[y[n]\,=\,0.\] Summarizing, then, we obtain \[y[n]\,=\,\left\{\begin{aligned} & 0,& n<0\\ &\frac{1-\alpha^{n\,+1}}{1-\alpha},& 0\,\equiv\,n\,\equiv\,4\\ &\frac{\alpha^{n\,-4}-\alpha^{n\,+1}}{1-\alpha},& 4<n\,\equiv\,6\\ &\frac{\alpha^{n\,-4}-\alpha^{7}}{1-\alpha},& 6<n\,\equiv\,10\\ & 0,& 10<n\end{aligned}\right.,\] which is pictured in Figure 2.10.

## Example 2.5

Consider an LTI system with input \(x[n]\) and unit impulse response \(h[n]\) specified as follows:

\[x[n]\,=\,2^{n}u[-n], \tag{2.17}\] \[h[n]\,=\,u[n]. \tag{2.18}\]

Figure 2.10: Result of performing the convolution in Example 2.4.

The sequences \(x[k]\) and \(h[n-k]\) are plotted as functions of \(k\) in Figure 2.11(a). Note that \(x[k]\) is zero for \(k>0\) and \(h[n-k]\) is zero for \(k>n\). We also observe that, regardless of the value of \(n\), the sequence \(x[k]h[n-k]\) always has nonzero samples along the \(k\)-axis. When \(n\,\geq\,0\), \(x[k]h[n-k]\) has nonzero samples in the interval \(k\,\leq\,0\). It follows that, for \(n\,\geq\,0\),

\[y[n]\,=\,\sum_{k\,=\,-\,\infty}^{0}x[k]h[n-k]\,=\,\sum_{k\,=\,-\,\infty}^{0}2^ {k}. \tag{2.19}\]

To evaluate the infinite sum in eq. (2.19), we may use the _infinite sum formula_,

\[\sum_{k\,=\,0}^{\infty}\alpha^{k}\,=\,\frac{1}{1-\alpha},\quad 0<|\alpha|<1. \tag{2.20}\]

Changing the variable of summation in eq. (2.19) from \(k\) to \(r\,=\,-\,k\), we obtain

\[\sum_{k\,=\,-\,\infty}^{0}2^{k}\,=\,\sum_{r\,=\,0}^{\infty}\biggl{(}\frac{1}{ 2}\biggr{)}^{k}\,=\,\frac{1}{1-(1/2)}\,=\,2. \tag{2.21}\]

Thus, \(y[n]\) takes on a constant value of \(2\) for \(n\,\geq\,0\).

Figure 2.11: (a) The sequences \(x[k]\) and \(h[n-k]\) for the convolution problem considered in Example 2.5; (b) the resulting output signal \(y[n]\).

When \(n<0\), \(x[k]h[n-k]\) has nonzero samples for \(k\leq n\). It follows that, for \(n<0\),

\[y[n]\,=\,\sum_{k\,=\,-\,-\,\times}^{n}\,x[k]h[n-k]\,=\,\sum_{k\,=\,-\,\times}^{n} \,2^{k}. \tag{2.22}\]

By performing a change of variable \(l=-k\) and then \(m=l+n\), we can again make use of the infinite sum formula, eq. (2.20), to evaluate the sum in eq. (2.22). The result is the following for \(n<0\):

\[y[n]\,=\,\sum_{l\,=\,-\,n}^{\,\times}\left(\frac{1}{2}\right)^{l}\,=\,\sum_{m \,=\,0}^{\,\times}\left(\frac{1}{2}\right)^{m-n}\,=\,\left(\frac{1}{2}\right)^{ -n}\,\sum_{m\,=\,0}^{\,\times}\left(\frac{1}{2}\right)^{m}\,=\,2^{n}\cdot 2 \,=\,2^{n+1}. \tag{2.23}\]

The complete sequence of \(y[n]\) is sketched in Figure 2.11(b).

These examples illustrate the usefulness of visualizing the calculation of the convolution sum graphically. Moreover, in addition to providing a useful way in which to calculate the response of an LTI system, the convolution sum also provides an extremely useful representation for LTI systems that allows us to examine their properties in great detail. In particular, in Section 2.3 we will describe some of the properties of convolution and will also examine some of the system properties introduced in the previous chapter in order to see how these properties can be characterized for LTI systems.

### 2.2 Continuous-time LTI systems: the convolution integral

In analogy with the results derived and discussed in the preceding section, the goal of this section is to obtain a complete characterization of a continuous-time LTI system in terms of its unit impulse response. In discrete time, the key to our developing the convolution sum was the sifting property of the discrete-time unit impulse--that is, the mathematical representation of a signal as the superposition of scaled and shifted unit impulse functions. Intuitively, then, we can think of the discrete-time system as responding to a sequence of individual impulses. In continuous time, of course, we do not have a discrete sequence of input values. Nevertheless, as we discussed in Section 1.4.2, if we think of the unit impulse as the idealization of a pulse which is so short that its duration is inconsequential for any real, physical system, we can develop a representation for arbitrary continuous-time signals in terms of these idealized pulses with vanishingly small duration, or equivalently, impulses. This representation is developed in the next subsection, and, following that, we will proceed very much as in Section 2.1 to develop the convolution integral representation for continuous-time LTI systems.

#### The Representation of Continuous-Time Signals in Terms of Impulses

To develop the continuous-time counterpart of the discrete-time sifting property in eq. (2.2), we begin by considering a pulse or "staircase" approximation, \(\hat{x}(t)\), to a continuous-time signal \(x(t)\), as illustrated in Figure 2.12(a). In a manner similar to that Figure 2.12: Staircase approximation to a continuous-time signal.

[MISSING_PAGE_EMPTY:19]

Specifically, as illustrated in Figure 2.14(b), the signal \(\delta(t-\tau)\) (viewed as a function of \(\tau\) with \(t\) fixed) is a unit impulse located at \(\tau=t\). Thus, as shown in Figure 2.14(c), the signal \(x(\tau)\delta(t-\tau)\) (once again viewed as a function of \(\tau\)) equals \(x(t)\delta(t-\tau)\) [i.e., it is a scaled impulse at \(\tau\,=\,t\) with an area equal to the value of \(x(t)\)]. Consequently, the integral of this signal from \(\tau\,=\,-\infty\) to \(\tau\,=\,+\infty\) equals \(x(t)\); that is,

\[\int_{-\infty}^{+\infty}x(\tau)\delta(t-\tau)d\tau\,=\,\int_{-\infty}^{+ \infty}x(t)\delta(t-\tau)d\tau\,=\,x(t)\int_{-\infty}^{+\infty}\delta(t-\tau)d \tau\,=\,x(t).\]

Although this derivation follows directly from Section 1.4.2, we have included the derivation given in eqs. (2.24)-(2.27) to stress the similarities with the discrete-time case and, in particular, to emphasize the interpretation of eq. (2.27) as representing the signal \(x(t)\) as a "sum" (more precisely, an integral) of weighted, shifted impulses.

Figure 2.13: Graphical interpretation of eq. (2.26).

The Continuous-Time Unit Impulse Response and the Convolution Integral Representation of LTI Systems

As in the discrete-time case, the representation developed in the preceding section provides us with a way in which to view an arbitrary continuous-time signal as the superposition of scaled and shifted pulses. In particular, the approximate representation in eq. (2.25) represents the signal \(\hat{x}(t)\) as a sum of scaled and shifted versions of the basic pulse signal \(\delta_{\lambda}(t)\). Consequently, the response \(\hat{y}(t)\) of a linear system to this signal will be the superposition of the responses to the scaled and shifted versions of \(\delta_{\lambda}(t)\). Specifically, let us define \(\hat{h}_{k\Delta}(t)\) as the response of an LTI system to the input \(\delta_{\lambda}(t-k\Delta)\). Then, from eq. (2.25) and the superposition property, for continuous-time linear systems, we see that

\[\hat{y}(t)\,=\,\sum_{k\,=\,-\,\varkappa}^{+\,\times}x(k\Delta)\hat{h}_{k\Delta }(t)\Delta. \tag{2.29}\]

The interpretation of eq. (2.29) is similar to that for eq. (2.3) in discrete time. In particular, consider Figure 2.15, which is the continuous-time counterpart of Figure 2.2. InFigure 2.15: Graphical interpretation of the response of a continuous-time linear system as expressed in eqs. (2.29) and (2.30).

Figure 2.15(a) we have depicted the input \(x(t)\) and its approximation \(\hat{x}(t)\), while in Figure 2.15(b)-(d), we have shown the responses of the system to three of the weighted pulses in the expression for \(\hat{x}(t)\). Then the output \(\hat{y}(t)\) corresponding to \(\hat{x}(t)\) is the superposition of all of these responses, as indicated in Figure 2.15(e).

What remains, then, is to consider what happens as \(\Delta\) becomes vanishingly small--i.e., as \(\Delta\to 0\). In particular, with \(x(t)\) as expressed in eq. (2.26), \(\hat{x}(t)\) becomes an increasingly good approximation to \(x(t)\), and in fact, the two coincide as \(\Delta\to 0\). Consequently, the response to \(\hat{x}(t)\), namely, \(\hat{y}(t)\) in eq. (2.29), must converge to \(y(t)\), the response to the actual input \(x(t)\), as illustrated in Figure 2.15(f). Furthermore, as we have said, for \(\Delta\) "small enough," the duration of the pulse \(\delta_{\Delta}(t-k\Delta)\) is of no significance, in that, as far as the system is concerned, the response to this pulse is essentially the same as the response to a unit impulse at the same point in time. That is, since the pulse \(\delta_{\Delta}(t-k\Delta)\) corresponds to a shifted unit impulse as \(\Delta\to 0\), the response \(\hat{h}_{k\Delta}(t)\) to this input pulse becomes the response to an impulse in the limit. Therefore, if we let \(h_{\tau}(t)\) denote the response at time \(t\) to a unit impulse \(\delta(t-\tau)\) located at time \(\tau\), then

\[y(t)\,=\,\lim_{\Delta\to 0}\sum_{k\,=\,-\,-\,\infty}^{+\,\infty}x(k\Delta) \hat{h}_{k\Delta}(t)\Delta. \tag{2.30}\]

As \(\Delta\to 0\), the summation on the right-hand side becomes an integral, as can be seen graphically in Figure 2.16. Specifically, in Figure 2.16 the shaded rectangle represents one term in the summation on the right-hand side of eq. (2.30) and as \(\Delta\to 0\) the summation approaches the area under \(x(\tau)h_{\tau}(t)\) viewed as a function of \(\tau\). Therefore,

\[y(t)\,=\,\int_{-\,\infty}^{+\,\infty}x(\tau)h_{\tau}(t)d\tau. \tag{2.31}\]

The interpretation of eq. (2.31) is analogous to the one for eq. (2.29). As we showed in Section 2.2.1, any input \(x(t)\) can be represented as

\[x(t)\,=\,\int_{-\,\

[MISSING_PAGE_FAIL:24]

### Example 2.6

Let \(x(t)\) be the input to an LTI system with unit impulse response \(h(t)\), where

\[x(t)\,=\,e^{-at}u(t),\quad a>0\]

and

\[h(t)\,=\,u(t).\]

In Figure 2.17, we have depicted the functions \(h(\tau)\), \(x(\tau)\), and \(h(t-\tau)\) for a negative value of \(t\) and for a positive value of \(t\). From this figure, we see that for \(t<0\), the product of \(x(\tau)\) and \(h(t-\tau)\) is zero, and consequently, \(y(t)\) is zero. For \(t>0\),

\[x(\tau)h(t-\tau)\,=\,\left\{\begin{array}{ll}e^{-a\tau},&0<\tau<t\\ 0,&\mbox{otherwise}\end{array}\right..\]

Figure 2.17: Calculation of the convolution integral for Example 2.6.

[MISSING_PAGE_EMPTY:26]

Figure 2.19: Signals \(x(\tau)\) and \(h(t-\tau)\) for different values of \(t\) for Example 2.7.

## Example 2.8

Let \(y(t)\) denote the convolution of the following two signals:

\[x(t) = e^{2t}u(-t), \tag{2.35}\] \[h(t) = u(t-3). \tag{2.36}\]

The signals \(x(\tau)\) and \(h(t-\tau)\) are plotted as functions of \(\tau\) in Figure 2.22(a). We first observe that these two signals have regions of nonzero overlap, regardless of the value

Figure 2.20: Product \(x(\tau)h(t-\tau)\) for Example 2.7 for the three ranges of values of \(t\) for which this product is not identically zero. (See Figure 2.19.)

[MISSING_PAGE_EMPTY:29]

### Properties of Linear Time-Invariant Systems

In the preceding two sections, we developed the extremely important representations of continuous-time and discrete-time LTI systems in terms of their unit impulse responses. In discrete time the representation takes the form of the convolution sum, while its continuous-time counterpart is the convolution integral, both of which we repeat here for convenience:

\[y[n] = \sum_{k\,=\,-\infty}^{+\infty}x[k]h[n-k]\,=\,x[n]*h[n] \tag{39}\] \[y(t) = \int_{-\infty}^{+\infty}x(\tau)h(t-\tau)d\tau\,=\,x(t)*h(t) \tag{40}\]

As we have pointed out, one consequence of these representations is that the characteristics of an LTI system are completely determined by its impulse response. It is important to emphasize that this property holds in general _only_ for LTI systems. In particular, as illustrated in the following example, the unit impulse response of a nonlinear system does _not_ completely characterize the behavior of the system.

### Example 2.9

Consider a discrete-time system with unit impulse response

\[h[n] = \left\{\begin{array}{ll}1,&n\,=\,0,\,1\\ 0,&\mbox{otherwise}\end{array}\right.. \tag{41}\]

If the system is LTI, then eq. (41) completely determines its input-output behavior. In particular, by substituting eq. (41) into the convolution sum, eq. (39), we find the following explicit equation describing how the input and output of this LTI system are related:

\[y[n] = x[n]+x[n-1]. \tag{42}\]

On the other hand, there are _many_ nonlinear systems with the same response--i.e., that given in eq. (41)--to the input \(\delta[n]\). For example, both of the following systems have this property:

\[y[n] = (x[n]+x[n-1])^{2},\] \[y[n] = \max(x[n],x[n-1]).\]

Consequently, if the system is nonlinear it is not completely characterized by the impulse response in eq. (41).

The preceding example illustrates the fact that LTI systems have a number of properties not possessed by other systems, beginning with the very special representations that they have in terms of convolution sums and integrals. In the remainder of this section, we explore some of the most basic and important of these properties.

#### The Commutative Property

A basic property of convolution in both continuous and discrete time is that it is a _commutative_ operation. That is, in discrete time

\[x[n]*h[n]\,=\,h[n]*x[n]\,=\,\sum_{k\,=\,-\,-\,\gamma}^{+\,\times}h[k]x[n\,-\,k], \tag{2.43}\]

and in continuous time

\[x(t)*h(t)\,=\,h(t)*x(t)\,=\,\int_{-\,\gamma}^{+\,\times}h(\tau)x(t-\tau)d\tau. \tag{2.44}\]

These expressions can be verified in a straightforward manner by means of a substitution of variables in eqs. (2.39) and (2.40). For example, in the discrete-time case, if we let \(r\,=\,n\,-\,k\) or, equivalently, \(k\,=\,n\,-\,r\), eq. (2.39) becomes

\[x[n]*h[n]\,=\,\sum_{k\,=\,-\,-\,\gamma}^{+\,\times}x[k]h[n\,-\,k]\,=\,\sum_{r\, =\,-\,\gamma}^{+\,\times}x[n\,-\,r]h[r]\,=\,h[n]*x[n]. \tag{2.45}\]

With this substitution of variables, the roles of \(x[n]\) and \(h[n]\) are interchanged. According to eq. (2.45), the output of an LTI system with input \(x[n]\) and unit impulse response \(h[n]\) is identical to the output of an LTI system with input \(h[n]\) and unit impulse response \(x[n]\). For example, we could have calculated the convolution in Example 2.4 by first reflecting and shifting \(x[k]\), then multiplying the signals \(x[n-k]\) and \(h[k]\), and finally summing the products for all values of \(k\).

Similarly, eq. (2.44) can be verified by a change of variables, and the implications of this result in continuous time are the same: The output of an LTI system with input \(x(t)\) and unit impulse response \(h(t)\) is identical to the output of an LTI system with input \(h(t)\) and unit impulse response \(x(t)\). Thus, we could have calculated the convolution in Example 2.7 by reflecting and shifting \(x(t)\), multiplying the signals \(x(t-\tau)\) and \(h(\tau)\), and integrating over \(-\,\infty\,<\,\tau\,<\,+\,\infty\). In specific cases, one of the two forms for computing convolutions [i.e., eq. (2.39) or (2.43) in discrete time and eq. (2.40) or (2.44) in continuous time] may be easier to visualize, but both forms always result in the same answer.

#### The Distributive Property

Another basic property of convolution is the _distributive_ property. Specifically, convolution distributes over addition, so that in discrete time

\[x[n]*(h_{1}[n]\,+\,h_{2}[n])\,=\,x[n]*h_{1}[n]\,+\,x[n]*h_{2}[n], \tag{2.46}\]

and in continuous time

\[x(t)*[h_{1}(t)\,+\,h_{2}(t)]\,=\,x(t)*h_{1}(t)\,+\,x(t)*h_{2}(t). \tag{2.47}\]

This property can be verified in a straightforward manner.

The distributive property has a useful interpretation in terms of system interconnections. Consider two continuous-time LTI systems in parallel, as indicated in Figure 2.23(a). The systems shown in the block diagram are LTI systems with the indicated unit impulse responses. This pictorial representation is a particularly convenient way in which to denote LTI systems in block diagrams, and it also reemphasizes the fact that the impulse response of an LTI system completely characterizes its behavior.

The two systems, with impulse responses \(h_{1}(t)\) and \(h_{2}(t)\), have identical inputs, and their outputs are added. Since

\[y_{1}(t)\,=\,x(t)*h_{1}(t)\]

and

\[y_{2}(t)\,=\,x(t)*h_{2}(t),\]

the system of Figure 2.23(a) has output

\[y(t)\,=\,x(t)*h_{1}(t)\,+\,x(t)*h_{2}(t), \tag{2.48}\]

corresponding to the right-hand side of eq. (2.47). The system of Figure 2.23(b) has output

\[y(t)\,=\,x(t)*[h_{1}(t)\,+\,h_{2}(t)], \tag{2.49}\]

corresponding to the left-hand side of eq. (2.47). Applying eq. (2.47) to eq. (2.49) and comparing the result with eq. (2.48), we see that the systems in Figures 2.23(a) and (b) are identical.

There is an identical interpretation in discrete time, in which each of the signals in Figure 2.23 is replaced by a discrete-time counterpart (i.e., \(x(t),\,h_{1}(t),\,h_{2}(t),\,y_{1}(t)\), \(y_{2}(t)\), and \(y(t)\) are replaced by \(x[n],\,h_{1}[n],\,h_{2}[n],\,y_{1}[n],\,y_{2}[n],\) and \(y[n]\), respectively). In summary, then, by virtue of the distributive property of convolution, a parallel combination of LTI systems can be replaced by a single LTI system whose unit impulse response is the sum of the individual unit impulse responses in the parallel combination.

Also, as a consequence of both the commutative and distributive properties, we have

\[[x_{1}[n]\,+\,x_{2}[n]]*h[n]\,=\,x_{1}[n]*h[n]\,+\,x_{2}[n]*h[n] \tag{2.50}\]

and

\[[x_{1}(t)\,+\,x_{2}(t)]*h(t)\,=\,x_{1}(t)*h(t)\,+\,x_{2}(t)*h(t), \tag{2.51}\]

which simply state that the response of an LTI system to the sum of two inputs must equal the sum of the responses to these signals individually.

As illustrated in the next example, the distributive property of convolution can also be exploited to break a complicated convolution into several simpler ones.

**Example 2.10**: Let \(y[n]\) denote the convolution of the following two sequences:

\[x[n]\,=\,\left(\frac{1}{2}\right)^{n}u[n]\,+\,2^{n}u[-n], \tag{2.52}\]

\[h[n]\,=\,u[n]. \tag{2.53}\]

Note that the sequence \(x[n]\) is nonzero along the entire time axis. Direct evaluation of such a convolution is somewhat tedious. Instead, we may use the distributive property to express \(y[n]\) as the sum of the results of two simpler convolution problems. In particular, if we let \(x_{1}[n]\,=\,(1/2)^{n}u[n]\) and \(x_{2}[n]\,=\,2^{n}u[-n]\), it follows that

\[y[n]\,=\,(x_{1}[n]\,+\,x_{2}[n])*h[n]. \tag{2.54}\]

Using the distributive property of convolution, we may rewrite eq. (2.54) as

\[y[n]\,=\,y_{1}[n]\,+\,y_{2}[n], \tag{2.55}\]

where

\[y_{1}[n]\,=\,x_{1}[n]*h[n] \tag{2.56}\]

and

\[y_{2}[n]\,=\,x_{2}[n]*h[n]. \tag{2.57}\]

The convolution in eq. (2.56) for \(y_{1}[n]\) can be obtained from Example 2.3 (with \(\alpha=1/2\)), while \(y_{2}[n]\) was evaluated in Example 2.5. Their sum is \(y[n]\), which is shown in Figure 2.24.

Figure 2.24: The signal \(y[n]\,=\,x[n]*h[n]\) for Example 2.10.

#### The Associative Property

Another important and useful property of convolution is that it is _associative_. That is, in discrete time

\[x[n]*(h_{1}[n]*h_{2}[n])\,=\,(x[n]*h_{1}[n])*h_{2}[n], \tag{2.58}\]

and in continuous time

\[x(t)*[h_{1}(t)*h_{2}(t)]\,=\,[x(t)*h_{1}(t)]*h_{2}(t). \tag{2.59}\]

This property is proven by straightforward manipulations of the summations and integrals involved. Examples verifying it are given in Problem 2.43.

As a consequence of the associative property, the expressions

\[y[n]\,=\,x[n]*h_{1}[n]*h_{2}[n] \tag{2.60}\]

and

\[y(t)\,=\,x(t)*h_{1}(t)*h_{2}(t) \tag{2.61}\]

are unambiguous. That is, according to eqs. (2.58) and (2.59), it does not matter in which order we convolve these signals.

An interpretation of the associative property is illustrated for discrete-time systems in Figures 2.25(a) and (b). In Figure 2.25(a),

\[y[n] =\,w[n]*h_{2}[n]\] \[=\,(x[n]*h_{1}[n])*h_{2}[n].\]

In Figure 2.25(b),

\[y[n] =\,x[n]*h[n]\] \[=\,x[n]*(h_{1}[n]*h_{2}[n]).\]

According to the associative property, the series interconnection of the two systems in Figure 2.25(a) is equivalent to the single system in Figure 2.25(b). This can be generalized to an arbitrary number of LTI systems in cascade, and the analogous interpretation and conclusion also hold in continuous time.

By using the commutative property together with the associative property, we find another very important property of LTI systems. Specifically, from Figures 2.25(a) and (b), we can conclude that the impulse response of the cascade of two LTI systems is the convolution of their individual impulse responses. Since convolution is commutative, we can compute this convolution of \(h_{1}[n]\) and \(h_{2}[n]\) in either order. Thus, Figures 2.25(b) and (c) are equivalent, and from the associative property, these are in turn equivalent to the system of Figure 2.25(d), which we note is a cascade combination of two systems as in Figure 2.25(a), but with the order of the cascade reversed. Consequently, the unit impulse response of a cascade of two LTI systems does not depend on the order in which they are cascaded. In fact, this holds for an arbitrary number of LTI systems in cascade: The order in which they are cascaded does not matter as far as the overall system impulse response is concerned. The same conclusions hold in continuous time as well.

It is important to emphasize that the behavior of LTI systems in cascade--and, in particular, the fact that the overall system response does not depend upon the order of the systems in the cascade--is very special to such systems. In contrast, the order in which nonlinear systems are cascaded cannot be changed, in general, without changing the overall response. For instance, if we have two memoryless systems, one being multiplication by 2 and the other squaring the input, then if we multiply first and square second, we obtain

\[y[n]\,=\,4x^{2}[n].\]

However, if we multiply by 2 after squaring, we have

\[y[n]\,=\,2x^{2}[n].\]

Thus, being able to interchange the order of systems in a cascade is a characteristic particular to LTI systems. In fact, as shown in Problem 2.51, we need both linearity _and_ time invariance in order for this property to be true in general.

#### LTI Systems with and without Memory

As specified in Section 1.6.1, a system is memoryless if its output at any time depends only on the value of the input at that same time. From eq. (2.39), we see that the only way that this can be true for a discrete-time LTI system is if \(h[n]\,=\,0\) for \(n\neq 0\). In this case the impulse response has the form

\[h[n]\,=\,K\delta[n], \tag{2.62}\]

where \(K\,=\,h[0]\) is a constant, and the convolution sum reduces to the relation

\[y[n]\,=\,K\,x[n]. \tag{2.63}\]

If a discrete-time LTI system has an impulse response \(h[n]\) that is not identically zero for \(n\neq 0\), then the system has memory. An example of an LTI system with memory is the system given by eq. (2.42). The impulse response for this system, given in eq. (2.41), is nonzero for \(n\,=\,1\).

From eq. (2.40), we can deduce similar properties for continuous-time LTI systems with and without memory. In particular, a continuous-time LTI system is memoryless if \(h(t)\,=\,0\) for \(t\neq 0\), and such a memoryless LTI system has the form

\[y(t)\,=\,K\,x(t) \tag{2.64}\]

for some constant \(K\) and has the impulse response

\[h(t)\,=\,K\delta(t). \tag{2.65}\]

Note that if \(K\,=\,1\) in eqs. (2.62) and (2.65), then these systems become identity systems, with output equal to the input and with unit impulse response equal to the unit impulse. In this case, the convolution sum and integral formulas imply that

\[x[n]\,=\,x[n]*\delta[n]\]

and

\[x(t)\,=\,x(t)*\delta(t),\]

which reduce to the sifting properties of the discrete-time and continuous-time unit impulses:

\[x[n]\,=\,\sum_{k\,=\,-\infty}^{+\infty}x[k]\delta[n\,-\,k]\] \[x(t)\,=\,\int_{-\infty}^{+\infty}x(\tau)\delta(t\,-\,\tau)d\tau.\]

#### Invertibility of LTI Systems

Consider a continuous-time LTI system with impulse response \(h(t)\). Based on the discussion in Section 1.6.2, this system is invertible only if an inverse system exists that, when connected in series with the original system, produces an output equal to the input to the first system. Furthermore, if an LTI system is invertible, then it has an LTI inverse. (See Problem 2.50.) Therefore, we have the picture shown in Figure 2.26. We are given a system with impulse response \(h(t)\). The inverse system, with impulse response \(h_{1}(t)\), results in \(w(t)\,=\,x(t)\)--such that the series interconnection in Figure 2.26(a) is identical to the identity system in Figure 2.26(b). Since the overall impulse response in Figure 2.26(a) is \(h(t)*h_{1}(t)\), we have the condition that \(h_{1}(t)\) must satisfy for it to be the impulse response of the inverse system, namely,

\[h(t)*h_{1}(t)\,=\,\delta(t). \tag{2.66}\]

Similarly, in discrete time, the impulse response \(h_{1}[n]\) of the inverse system for an LTI system with impulse response \(h[n]\) must satisfy

\[h[n]*h_{1}[n]\,=\,\delta[n]. \tag{2.67}\]

The following two examples illustrate invertibility and the construction of an inverse system.

### Example 2.11

Consider the LTI system consisting of a pure time shift

\[y(t)\,=\,x(t-t_{0}). \tag{2.68}\]

Such a system is a _delay_ if \(t_{0}>0\) and an _advance_ if \(t_{0}<0\). For example, if \(t_{0}>0\), then the output at time \(t\) equals the value of the input at the earlier time \(t-t_{0}\). If \(t_{0}\,=\,0\), the system in eq. (2.68) is the identity system and thus is memoryless. For any other value of \(t_{0}\), this system has memory, as it responds to the value of the input at a time other than the current time.

The impulse response for the system can be obtained from eq. (2.68) by taking the input equal to \(\delta(t)\), i.e.,

\[h(t)\,=\,\delta(t-t_{0}). \tag{2.69}\]

Therefore,

\[x(t-t_{0})\,=\,x(t)*\delta(t-t_{0}). \tag{2.70}\]

That is, the convolution of a signal with a shifted impulse simply shifts the signal.

To recover the input from the output, i.e., to invert the system, all that is required is to shift the output back. The system with this compensating time shift is then the inverse system. That is, if we take

\[h_{1}(t)\,=\,\delta(t+t_{0}),\]

then

\[h(t)*h_{1}(t)\,=\,\delta(t-t_{0})*\delta(t+t_{0})\,=\,\delta(t).\]

Similarly, a pure time shift in discrete time has the unit impulse response \(\delta[n-n_{0}]\), so that convolving a signal with a shifted impulse is the same as shifting the signal. Furthermore, the inverse of the LTI system with impulse response \(\delta[n-n_{0}]\) is the LTI system that shifts the signal in the opposite direction by the same amount--i.e., the LTI system with impulse response \(\delta[n+n_{0}]\).

### Example 2.12

Consider an LTI system with impulse response

\[h[n]\,=\,u[n]. \tag{2.71}\]

Using the convolution sum, we can calculate the response of this system to an arbitrary input:

\[y[n]\,=\,\sum_{k\,=\,-\,\infty}^{+\,\infty}x[k]u[n-k]. \tag{2.72}\]

Since \(u[n-k]\) is 0 for \(n-k<0\) and 1 for \(n-k\,\cong\,0\), eq. (2.72) becomes

\[y[n]\,=\,\sum_{k\,=\,-\,\infty}^{n}x[k]. \tag{2.73}\]

That is, this system, which we first encountered in Section 1.6.1 [see eq. (1.92)], is a summer or accumulator that computes the running sum of all the values of the input up to the present time. As we saw in Section 1.6.2, such a system is invertible, and its inverse, as given by eq. (1.99), is

\[y[n]\,=\,x[n]-x[n-1], \tag{2.74}\]

which is simply a _first difference_ operation. Choosing \(x[n]=\delta[n]\), we find that the impulse response of the inverse system is

\[h_{1}[n]\,=\,\delta[n]-\delta[n-1]. \tag{2.75}\]

As a check that \(h[n]\) in eq. (2.71) and \(h_{1}[n]\) in eq. (2.75) are indeed the impulse responses of LTI systems that are inverses of each other, we can verify eq. (2.67) by direct calculation:

\[\begin{array}{rcl}h[n]*h_{1}[n]&=&u[n]*\{\delta[n]-\delta[n-1]\}\\ &=&u[n]*\delta[n]-u[n]*\delta[n-1]\\ &=&u[n]-u[n-1]\\ &=&\delta[n].\end{array} \tag{2.76}\]

#### Causality for LTI Systems

In Section 1.6.3, we introduced the property of causality: The output of a causal system depends only on the present and past values of the input to the system. By using the convolution sum and integral, we can relate this property to a corresponding property of the impulse response of an LTI system. Specifically, in order for a discrete-time LTI system to be causal, \(y[n]\) must not depend on \(x[k]\) for \(k>n\). From eq. (2.39), we see that for this to be true, all of the coefficients \(h[n-k]\) that multiply values of \(x[k]\) for \(k>n\) must be zero. This then requires that the impulse response of a causal discrete-time LTI system satisfy the condition

\[h[n]\,=\,0\quad\text{for $n<0$}. \tag{2.77}\]

According to eq. (2.77), the impulse response of a causal LTI system must be zero before the impulse occurs, which is consistent with the intuitive concept of causality. More generally, as shown in Problem 1.44, causality for a linear system is equivalent to the condition of _initial rest_; i.e., if the input to a causal system is 0 up to some point in time, then the output must also be 0 up to that time. It is important to emphasize that the equivalence of causality and the condition of initial rest applies only to linear systems. For example, as discussed in Section 1.6.6, the system \(y[n]=2x[n]+3\) is not linear. However, it is causal and, in fact, memoryless. On the other hand, if \(x[n]\,=\,0\), \(y[n]\,=\,3\neq 0\), so it does not satisfy the condition of initial rest.

For a causal discrete-time LTI system, the condition in eq. (2.77) implies that the convolution sum representation in eq. (2.39) becomes

\[y[n]\,=\,\sum_{k\,=\,-z}^{n}x[k]h[n\,-\,k], \tag{2.78}\]

and the alternative equivalent form, eq. (2.43), becomes

\[y[n]\,=\,\sum_{k\,=\,0}^{\times}h[k]x[n\,-\,k]. \tag{2.79}\]

Similarly, a continuous-time LTI system is causal if

\[h(t)\,=\,0\quad\text{for $t<0$}, \tag{2.80}\]

and in this case the convolution integral is given by

\[y(t)\,=\,\int_{-\times}^{t}x(\tau)h(t\,-\,\tau)d\tau\,=\,\int_{0}^{\times}h( \tau)x(t\,-\,\tau)d\tau. \tag{2.81}\]

Both the accumulator (\(h[n]\,=\,u[n]\)) and its inverse (\(h[n]\,=\,\delta[n]\,-\,\delta[n\,-\,1]\)), described in Example 2.12, satisfy eq. (2.77) and therefore are causal. The pure time shift with impulse response \(h(t)\,=\,\delta(t-t_{0})\) is causal for \(t_{0}\,\geq\,0\) (when the time shift is a delay), but is noncausal for \(t_{0}<0\) (in which case the time shift is an advance, so that the output anticipates future values of the input).

Finally, while causality is a property of systems, it is common terminology to refer to a signal as being causal if it is zero for \(n<0\) or \(t<0\). The motivation for this terminology comes from eqs. (2.77) and (2.80): Causality of an LTI system is equivalent to its impulse response being a causal signal.

#### Stability for LTI Systems

Recall from Section 1.6.4 that a system is _stable_ if every bounded input produces a bounded output. In order to determine conditions under which LTI systems are stable, consider an input \(x[n]\) that is bounded in magnitude:

\[|x[n]|<B\quad\text{for all $n$}. \tag{2.82}\]

Suppose that we apply this input to an LTI system with unit impulse response \(h[n]\). Then, using the convolution sum, we obtain an expression for the magnitude of the output:

\[|y[n]|\,=\,\left|\sum_{k\,=\,-\infty}^{+\infty}h[k]x[n\,-\,k]\right|. \tag{2.83}\]

Since the magnitude of the sum of a set of numbers is no larger than the sum of the magnitudes of the numbers, it follows from eq. (2.83) that

\[|y[n]|\,\leq\,\sum_{k\,=\,-\infty}^{+\infty}|h[k]||x[n\,-\,k]|. \tag{2.84}\]

From eq. (2.82), \(|x[n\,-\,k]|<B\) for all values of \(k\) and \(n\). Together with eq. (2.84), this implies that

\[|y[n]|\,\leq\,B\sum_{k\,=\,-\infty}^{+\infty}|h[k]|\quad\text{ for all $n$}. \tag{2.85}\]

From eq. (2.85), we can conclude that if the impulse response is _absolutely summable_, that is, if

\[\sum_{k\,=\,-\infty}^{+\infty}|h[k]|<\infty, \tag{2.86}\]

then \(y[n]\) is bounded in magnitude, and hence, the system is stable. Therefore, eq. (2.86) is a sufficient condition to guarantee the stability of a discrete-time LTI system. In fact, this condition is also a necessary condition, since, as shown in Problem 2.49, if eq. (2.86) is not satisfied, there are bounded inputs that result in unbounded outputs. Thus, the stability of a discrete-time LTI system is completely equivalent to eq. (2.86).

In continuous time, we obtain an analogous characterization of stability in terms of the impulse response of an LTI system. Specifically, if \(|x(t)|<B\) for all \(t\), then, in analogy with eqs. (2.83)-(2.85), it follows that \[|y(t)| = \left|\int_{-\infty}^{+\infty}h(\tau)x(t-\tau)d\tau\right|\] \[\leq \int_{-\infty}^{+\infty}|h(\tau)||x(t-\tau)|d\tau\] \[\leq B\int_{-\infty}^{+\infty}|h(\tau)|d\tau.\]

Therefore, the system is stable if the impulse response is _absolutely integrable_, i.e., if

\[\int_{-\infty}^{+\infty}|h(\tau)|d\tau<\infty. \tag{2.87}\]

As in discrete time, if eq. (2.87) is not satisfied, there are bounded inputs that produce unbounded outputs; therefore, the stability of a continuous-time LTI system is equivalent to eq. (2.87). The use of eqs (2.86) and (2.87) to test for stability is illustrated in the next two examples.

**Example 2.13**: Consider a system that is a pure time shift in either continuous time or discrete time. Then, in discrete time

\[\sum_{n\,=\,-\,\infty}^{+\infty}|h(n)|\,=\,\sum_{n\,=\,-\,\infty}^{+\infty}| \delta(n-n_{0})|\,=\,1, \tag{2.88}\]

while in continuous time

\[\int_{-\infty}^{+\infty}|h(\tau)|d\tau\,=\,\int_{-\infty}^{+\infty}|\delta( \tau-t_{0})|d\tau\,=\,1, \tag{2.89}\]

and we conclude that both of these systems are stable. This should not be surprising, since if a signal is bounded in magnitude, so is any time-shifted version of that signal.

Now consider the accumulator described in Example 2.12. As we discussed in Section 1.6.4, this is an unstable system, since, if we apply a constant input to an accumulator, the output grows without bound. That this system is unstable can also be seen from the fact that its impulse response \(u(n)\) is not absolutely summable:

\[\sum_{n\,=\,-\,\infty}^{\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\, \,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,response for the integrator can be found by letting \(x(t)=\delta(t)\), in which case

\[h(t)=\int_{-\infty}^{t}\delta(\tau)d\tau=u(t)\]

and

\[\int_{-\infty}^{+\infty}|u(\tau)|d\tau=\int_{0}^{+\infty}d\tau=\infty.\]

Since the impulse response is not absolutely integrable, the system is not stable.

#### The Unit Step Response of an LTI System

Up to now, we have seen that the representation of an LTI system in terms of its unit impulse response allows us to obtain very explicit characterizations of system properties. Specifically, since \(h[n]\) or \(h(t)\) completely determines the behavior of an LTI system, we have been able to relate system properties such as stability and causality to properties of the impulse response.

There is another signal that is also used quite often in describing the behavior of LTI systems: the _unit step response_, \(s[n]\) or \(s(t)\), corresponding to the output when \(x[n]=u[n]\) or \(x(t)=u(t)\). We will find it useful on occasion to refer to the step response, and therefore, it is worthwhile relating it to the impulse response. From the convolution-sum representation, the step response of a discrete-time LTI system is the convolution of the unit step with the impulse response; that is,

\[s[n]=u[n]*h[n].\]

However, by the commutative property of convolution, \(s[n]=h[n]*u[n]\), and therefore, \(s[n]\) can be viewed as the response to the input \(h[n]\) of a discrete-time LTI system with unit impulse response \(u[n]\). As we have seen in Example 2.12, \(u[n]\) is the unit impulse response of the accumulator. Therefore,

\[s[n]=\sum_{k=-\infty}^{n}h[k]. \tag{2.91}\]

From this equation and from Example 2.12, it is clear that \(h[n]\) can be recovered from \(s[n]\) using the relation

\[h[n]=s[n]-s[n-1]. \tag{2.92}\]

That is, the step response of a discrete-time LTI system is the running sum of its impulse response [eq. (2.91)]. Conversely, the impulse response of a discrete-time LTI system is the first difference of its step response [eq. (2.92)].

Similarly, in continuous time, the step response of an LTI system with impulse response \(h(t)\) is given by \(s(t)=u(t)*h(t)\), which also equals the response of an integrator [with impulse response \(u(t)\)] to the input \(h(t)\). That is, the unit step response of a continuous-time LTI system is the running integral of its impulse response, or

\[s(t)=\int_{-\infty}^{t}h(\tau)d\tau, \tag{2.93}\]and from eq. (2.93), the unit impulse response is the first derivative of the unit step response,1 or

Footnote 1: Throughout this book, we will use both the notations indicated in eq. (2.94) to denote first derivatives. Analogous notation will also be used for higher derivatives.

\[h(t)\,=\,\frac{ds(t)}{dt}\,=\,s^{\prime}(t). \tag{2.94}\]

Therefore, in both continuous and discrete time, the unit step response can also be used to characterize an LTI system, since we can calculate the unit impulse response from it. In Problem 2.45, expressions analogous to the convolution sum and convolution integral are derived for the representations of an LTI system in terms of its unit step response.

### Causal LTI systems described by differential and difference equations

An extremely important class of continuous-time systems is that for which the input and output are related through a _linear constant-coefficient differential equation_. Equations of this type arise in the description of a wide variety of systems and physical phenomena. For example, as we illustrated in Chapter 1, the response of the \(RC\) circuit in Figure 1.1 and the motion of a vehicle subject to acceleration inputs and frictional forces, as depicted in Figure 1.2, can both be described through linear constant-coefficient differential equations. Similar differential equations arise in the description of mechanical systems containing restoring and damping forces, in the kinetics of chemical reactions, and in many other contexts as well.

Correspondingly, an important class of discrete-time systems is that for which the input and output are related through a _linear constant-coefficient difference equation_. Equations of this type are used to describe the sequential behavior of many different processes. For instance, in Example 1.10 we saw how difference equations arise in describing the accumulation of savings in a bank account, and in Example 1.11 we saw how they can be used to describe a digital simulation of a continuous-time system described by a differential equation. Difference equations also arise quite frequently in the specification of discrete-time systems designed to perform particular operations on the input signal. For example, the system that calculates the difference between successive input values, as in eq. (1.99), and the system described by eq. (1.104) that computes the average value of the input over an interval are described by difference equations.

Throughout this book, there will be many occasions in which we will consider and examine systems described by linear constant-coefficient differential and difference equations. In this section we take a first look at these systems to introduce some of the basic ideas involved in solving differential and difference equations and to uncover and explore some of the properties of systems described by such equations. In subsequent chapters, we develop additional tools for the analysis of signals and systems that will add considerably both to our ability to analyze systems described by such equations and to our understanding of their characteristics and behavior.

#### Linear Constant-Coefficient Differential Equations

To introduce some of the important ideas concerning systems specified by linear constant-coefficient differential equations, let us consider a first-order differential equation as in eq. (1.85), viz.,

\[\frac{dy(t)}{dt}+2y(t)\;=\;x(t), \tag{2.95}\]

where \(y(t)\) denotes the output of the system and \(x(t)\) is the input. For example, comparing eq. (2.95) to the differential equation (1.84) for the velocity of a vehicle subject to applied and frictional forces, we see that eq. (2.95) would correspond exactly to this system if \(y(t)\) were identified with the vehicle's velocity \(v(t)\), if \(x(t)\) were taken as the applied force \(f(t)\), and if the parameters in eq. (1.84) were normalized in units such that \(b/m\,=\,2\) and \(1/m\,=\,1\).

A very important point about differential equations such as eq. (2.95) is that they provide an _implicit_ specification of the system. That is, they describe a relationship between the input and the output, rather than an explicit expression for the system output as a function of the input. In order to obtain an explicit expression, we must solve the differential equation. To find a solution, we need more information than that provided by the differential equation alone. For example, to determine the speed of an automobile at the end of a 10-second interval when it has been subjected to a constant acceleration of 1 m/sec\({}^{2}\) for 10 seconds, we would also need to know how fast the vehicle was moving at the _start_ of the interval. Similarly, if we are told that a constant source voltage of 1 volt is applied to the \(RC\) circuit in Figure 1 for 10 seconds, we cannot determine what the capacitor voltage is at the end of that interval without also knowing what the initial capacitor voltage is.

More generally, to solve a differential equation, we must specify one or more auxiliary conditions, and once these are specified, we can then, in principle, obtain an explicit expression for the output in terms of the input. In other words, a differential equation such as eq. (2.95) describes a constraint between the input and the output of a system, but to characterize the system completely, we must also specify auxiliary conditions. Different choices for these auxiliary conditions then lead to different relationships between the input and the output. For the most part, in this book we will focus on the use of differential equations to describe causal LTI systems, and for such systems the auxiliary conditions take a particular, simple form. To illustrate this and to uncover some of the basic properties of the solutions to differential equations, let us take a look at the solution of eq. (2.95) for a specific input signal \(x(t)\).2

### Example 2.14

Consider the solution of eq. (2.95) when the input signal is

\[x(t)\,=\,Ke^{x_{l}}u(t), \tag{2.96}\]

where \(K\) is a real number.

The complete solution to eq. (2.96) consists of the sum of a _particular solution_, \(y_{p}(t)\), and a _homogeneous solution,_\(y_{h}(t)\), i.e.,

\[y(t)\,=\,y_{p}(t)\,+\,y_{h}(t), \tag{2.97}\]

where the particular solution satisfies eq. (2.95) and \(y_{h}(t)\) is a solution of the homogeneous differential equation

\[\frac{d\,y(t)}{dt}\,+\,2y(t)\,=\,0. \tag{2.98}\]

A common method for finding the particular solution for an exponential input signal as in eq. (2.96) is to look for a so-called _forced response_--i.e., a signal of the same form as the input. With regard to eq. (2.95), since \(x(t)\,=\,Ke^{x_{l}}\) for \(t>0\), we hypothesize a solution for \(t>0\) of the form

\[y_{p}(t)\,=\,Ye^{x_{l}}, \tag{2.99}\]

where \(Y\) is a number that we must determine. Substituting eqs. (2.96) and (2.99) into eq. (2.95) for \(t>0\) yields

\[3Ye^{x_{l}}\,+\,2Ye^{x_{l}}\,=\,Ke^{x_{l}}. \tag{2.100}\]

Canceling the factor \(e^{x_{l}}\) from both sides of eq. (2.100), we obtain

\[3Y\,+\,2Y\,=\,K, \tag{2.101}\]

or

\[Y\,=\,\frac{K}{5}, \tag{2.102}\]

so that

\[y_{p}(t)\,=\,\frac{K}{5}\,e^{x_{l}},\quad t>0. \tag{2.103}\]

In order to determine \(y_{h}(t)\), we hypothesize a solution of the form

\[y_{h}(t)\,=\,Ae^{x_{l}}. \tag{2.104}\]

Substituting this into eq. (2.98) gives

\[Ase^{x_{l}}\,+\,2Ae^{x_{l}}\,=\,Ae^{x_{l}}(s+2)\,=\,0. \tag{2.105}\]

From this equation, we see that we must take \(s\,=\,-2\) and that \(Ae^{-2t}\) is a solution to eq. (2.98) for _any_ choice of \(A\). Utilizing this fact and eq. (2.103) in eq. (2.97), we find that the solution of the differential equation for \(t>0\) is

\[y(t)\,=\,Ae^{-2t}\,+\,\frac{K}{5}\,e^{x_{l}},\quad t>0. \tag{2.106}\]As noted earlier, the differential equation (2.95) by itself does not specify uniquely the response \(y(t)\) to the input \(x(t)\) in eq. (2.96). In particular, the constant \(A\) in eq. (2.106) has not yet been determined. In order for the value of \(A\) to be determined, we need to specify an auxiliary condition in addition to the differential equation (2.95). As explored in Problem 2.34, different choices for this auxiliary condition lead to different solutions \(y(t)\) and, consequently, to different relationships between the input and the output. As we have indicated, for the most part in this book we focus on differential and difference equations used to describe systems that are LTI and causal, and in this case the auxiliary condition takes the form of the condition of initial rest. That is, as shown in Problem 1.44, for a causal LTI system, if \(x(t)\,=\,0\) for \(t<t_{0}\), then \(y(t)\) must also equal \(0\) for \(t<t_{0}\). From eq. (2.96), we see that for our example \(x(t)\,=\,0\) for \(t<0\), and thus, the condition of initial rest implies that \(y(t)\,=\,0\) for \(t<0\). Evaluating eq. (2.106) at \(t\,=\,0\) and setting \(y(0)\,=\,0\) yields

\[0\,=\,A\,+\,\frac{K}{5},\]

or

\[A\,=\,-\,\frac{K}{5}.\]

Thus, for \(t>0\),

\[y(t)\,=\,\frac{K}{5}\left[e^{3t}\,-\,e^{-2t}\right], \tag{2.107}\]

while for \(t<0\), \(y(t)\,=\,0\), because of the condition of initial rest. Combining these two cases, we obtain the full solution

\[y(t)\,=\,\frac{K}{5}\left[e^{3t}\,-\,e^{-2t}\right]u(t). \tag{2.108}\]

Example 2.14 illustrates several very important points concerning linear constant-coefficient differential equations and the systems they represent. First, the response to an input \(x(t)\) will generally consist of the sum of a particular solution to the differential equation and a homogeneous solution--i.e., a solution to the differential equation with the input set to zero. The homogeneous solution is often referred to as the _natural response_ of the system. The natural responses of simple electrical circuits and mechanical systems are explored in Problems 2.61 and 2.62.

In Example 2.14 we also saw that, in order to determine completely the relationship between the input and the output of a system described by a differential equation such as eq. (2.95), we must specify auxiliary conditions. An implication of this fact, which is illustrated in Problem 2.34, is that different choices of auxiliary conditions lead to different relationships between the input and the output. As we illustrated in the example, for the most part we will use the condition of initial rest for systems described by differential equations. In the example, since the input was \(0\) for \(t<0\), the condition of initial rest implied the initial condition \(y(0)\,=\,0\). As we have stated, and as illustrated in 

[MISSING_PAGE_FAIL:47]

plus a solution to the homogeneous differential equation

\[\sum_{k\,=\,0}^{N}a_{k}\frac{d^{\,k}y(t)}{dt^{\,k}}\,=\,0. \tag{111}\]

The solutions to this equation are referred to as the _natural responses_ of the system.

As in the first-order case, the differential equation (109) does not completely specify the output in terms of the input, and we need to identify auxiliary conditions to determine completely the input-output relationship for the system. Once again, different choices for these auxiliary conditions result in different input-output relationships, but for the most part, in this book we will use the condition of initial rest when dealing with systems described by differential equations. That is, if \(x(t)\,=\,0\) for \(t\,\mbox{$\leq$}\,t_{0}\), we assume that \(y(t)\,=\,0\) for \(t\,\mbox{$\leq$}\,t_{0}\), and therefore, the response for \(t\,\mbox{$>$}\,t_{0}\) can be calculated from the differential equation (109) with the initial conditions

\[y\left(t_{0}\right)\,=\,\frac{dy\left(t_{0}\right)}{dt}\,=\,\ldots\,=\,\frac{d ^{N-1}y\left(t_{0}\right)}{dt^{N-1}}\,=\,0. \tag{112}\]

Under the condition of initial rest, the system described by eq. (109) is causal and LTI. Given the initial conditions in eq. (112), the output \(y(t)\) can, in principle, be determined by solving the differential equation in the manner used in Example 14 and further illustrated in several problems at the end of the chapter. However, in Chapters 4 and 9 we will develop some tools for the analysis of continuous-time LTI systems that greatly facilitate the solution of differential equations and, in particular, provide us with powerful methods for analyzing and characterizing the properties of systems described by such equations.

#### Linear Constant-Coefficient Difference Equations

The discrete-time counterpart of eq. (109) is the \(N\)th-order linear constant-coefficient difference equation

\[\sum_{k\,=\,0}^{N}a_{k}y[n\,-\,k]\,=\,\sum_{k\,=\,0}^{M}b_{k}x[n\,-\,k]. \tag{113}\]

An equation of this type can be solved in a manner exactly analogous to that for differential equations. (See Problem 32.)4 Specifically, the solution \(y[n]\) can be written as the sum of a particular solution to eq. (113) and a solution to the homogeneous equation

Footnote 4: For a detailed treatment of the methods for solving linear constant-coefficient difference equations, see _Finite Difference Equations,_ by H. Levy and F. Lessman (New York: Macmillan, Inc., 1961), or _Finite Difference Equations and Simulations_ (Englewood Cliffs, NJ: Prentice-Hall, 1968) by F. B. Hildebrand. In Chapter 6, we present another method for solving difference equations that greatly facilitates the analysis of linear time-invariant systems that are so described. In addition, we refer the reader to the problems at the end of this chapter that deal with the solution of difference equations.

\[\sum_{k\,=\,0}^{N}a_{k}y[n\,-\,k]\,=\,0. \tag{114}\]The solutions to this homogeneous equation are often referred to as the natural responses of the system described by eq. (113).

As in the continuous-time case, eq. (113) does not completely specify the output in terms of the input. To do this, we must also specify some auxiliary conditions. While there are many possible choices for auxiliary conditions, leading to different input-output relationships, we will focus for the most part on the condition of initial rest--i.e., if \(x[n]\,=\,0\) for \(n<n_{0}\), then \(y[n]\,=\,0\) for \(n<n_{0}\) as well. With initial rest, the system described by eq. (113) is LTI and causal.

Although all of these properties can be developed following an approach that directly parallels our discussion for differential equations, the discrete-time case offers an alternative path. This stems from the observation that eq. (113) can be rearranged in the form

\[y[n]\,=\,\frac{1}{a_{0}}\left\{\,\sum_{k\,=\,0}^{M}\,b_{k}\,x[n\,-\,k]-\sum_{k \,=\,1}^{N}\,a_{k}\,y[n\,-\,k]\right\}\,. \tag{115}\]

Equation (115) directly expresses the output at time \(n\) in terms of previous values of the input and output. From this, we can immediately see the need for auxiliary conditions. In order to calculate \(y[n]\), we need to know \(y[n-1]\),..., \(y[n-N]\). Therefore, if we are given the input for all \(n\) and a set of auxiliary conditions such as \(y[-N]\), \(y[-N+1]\),..., \(y[-1]\), eq. (115) can be solved for successive values of \(y[n]\).

An equation of the form of eq. (113) or eq. (115) is called a _recursive equation,_ since it specifies a recursive procedure for determining the output in terms of the input and previous outputs. In the special case when \(N\,=\,0\), eq. (115) reduces to

\[y[n]\,=\,\sum_{k\,=\,0}^{M}\left(\frac{b_{k}}{a_{0}}\right)x[n\,-\,k]. \tag{116}\]

This is the discrete-time counterpart of the continuous-time system given in eq. (110). Here, \(y[n]\) is an explicit function of the present and previous values of the input. For this reason, eq. (116) is often called a _nonrecursive equation,_ since we do not recursively use previously computed values of the output to compute the present value of the output. Therefore, just as in the case of the system given in eq. (110), we do not need auxiliary conditions in order to determine \(y[n]\). Furthermore, eq. (116) describes an LTI system, and by direct computation, the impulse response of this system is found to be

\[h[n]\,=\,\left\{\begin{array}{ll}\frac{b_{n}}{a_{0}},&0\,\,\leq\,n\,\leq\, M\\ 0,&\mbox{otherwise}\end{array}\right.\,. \tag{117}\]

That is, eq. (116) is nothing more than the convolution sum. Note that the impulse response for it has finite duration; that is, it is nonzero only over a finite time interval. Because of this property, the system specified by eq. (116) is often called a _finite impulse response (FIR) system_.

Although we do not require auxiliary conditions for the case of \(N\,=\,0\), such conditions are needed for the recursive case when \(N\,\geq\,1\). To illustrate the solution of such an equation, and to gain some insight into the behavior and properties of recursive difference equations, let us examine the following simple example:

## Example 2.15

Consider the difference equation

\[y[n]-\frac{1}{2}y[n-1]\,=\,x[n]. \tag{2.118}\]

Eq. (2.118) can also be expressed in the form

\[y[n]\,=\,x[n]+\frac{1}{2}y[n-1], \tag{2.119}\]

highlighting the fact that we need the previous value of the output, \(y[n-1]\), to calculate the current value. Thus, to begin the recursion, we need an initial condition.

For example, suppose that we impose the condition of initial rest and consider the input

\[x[n]\,=\,K\delta[n]. \tag{2.120}\]

In this case, since \(x[n]\,=\,0\) for \(n\,\leq\,-1\), the condition of initial rest implies that \(y[n]\,=\,0\) for \(n\,\leq\,-1\), so that we have as an initial condition \(y[-1]=0\). Starting from this initial condition, we can solve for successive values of \(y[n]\) for \(n\,\geq\,0\) as follows:

\[y[0]\,=\,x[0]+\frac{1}{2}y[-1]\,=\,K, \tag{2.121}\]

\[y[1]\,=\,x[1]+\frac{1}{2}y[0]\,=\,\frac{1}{2}K, \tag{2.122}\]

\[y[2]\,=\,x[2]+\frac{1}{2}y[1]\,=\,\left(\frac{1}{2}\right)^{2}\!K, \tag{2.123}\]

\[\vdots\] \[y[n]\,=\,x[n]+\frac{1}{2}y[n\,-\,1]\,=\,\left(\frac{1}{2}\right)^{\!n}K. \tag{2.124}\]

Since the system specified by eq. (2.118) and the condition of initial rest is LTI, its input-output behavior is completely characterized by its impulse response. Setting \(K\,=\,1\), we see that the impulse response for the system considered in this example is

\[h[n]\,=\,\left(\frac{1}{2}\right)^{\!n}u[n]. \tag{2.125}\]

Note that the causal LTI system in Example 2.15 has an impulse response of infinite duration. In fact, if \(N\,\geq\,1\) in eq. (2.113), so that the difference equation is recursive, it is usually the case that the LTI system corresponding to this equation together with the condition of initial rest will have an impulse response of infinite duration. Such systems are commonly referred to as _infinite impulse response (IIR) systems._

As we have indicated, for the most part we will use recursive difference equations in the context of describing and analyzing systems that are linear, time-invariant, and causal, and consequently, we will usually make the assumption of initial rest. In Chapters 5 and 10 we will develop tools for the analysis of discrete-time systems that will provide uswith very useful and efficient methods for solving linear constant-coefficient difference equations and for analyzing the properties of the systems that they describe.

#### Block Diagram Representations of First-Order Systems

Described by Differential and Difference Equations

An important property of systems described by linear constant-coefficient difference and differential equations is that they can be represented in very simple and natural ways in terms of block diagram interconnections of elementary operations. This is significant for a number of reasons. One is that it provides a pictorial representation which can add to our understanding of the behavior and properties of these systems. In addition, such representations can be of considerable value for the simulation or implementation of the systems. For example, the block diagram representation to be introduced in this section for continuous-time systems is the basis for early analog computer simulations of systems described by differential equations, and it can also be directly translated into a program for the simulation of such a system on a digital computer. In addition, the corresponding representation for discrete-time difference equations suggests simple and efficient ways in which the systems that the equations describe can be implemented in digital hardware. In this section, we illustrate the basic ideas behind these block diagram representations by constructing them for the causal first-order systems introduced in Examples 1.8-1.11. In Problems 2.57-2.60 and Chapters 9 and 10, we consider block diagrams for systems described by other, more complex differential and difference equations.

We begin with the discrete-time case and, in particular, the causal system described by the first-order difference equation

\[y[n]+ay[n-1]\,=\,bx[n]. \tag{126}\]

To develop a block diagram representation of this system, note that the evaluation of eq. (126) requires three basic operations: addition, multiplication by a coefficient, and delay (to capture the relationship between \(y[n]\) and \(y[n-1]\)). Thus, let us define three basic network elements, as indicated in Figure 2.27. To see how these basic elements can be used to represent the causal system described by eq. (126), we rewrite this equation in the form that directly suggests a recursive algorithm for computing successive values of the output \(y[n]\):

\[y[n]\,=\,-ay[n-1]+bx[n]. \tag{127}\]

This algorithm is represented pictorially in Figure 2.28, which is an example of a feedback system, since the output is fed back through a delay and a multiplication by a coefficient and is then added to \(bx[n]\). The presence of feedback is a direct consequence of the recursive nature of eq. (127).

The block diagram in Figure 2.28 makes clear the required memory in this system and the consequent need for initial conditions. In particular, a delay corresponds to a memory element, as the element must retain the previous value of its input. Thus, the initial value of this memory element serves as a necessary initial condition for the recursive calculation specified pictorially in Figure 2.28 and mathematically in eq. (127). Of course, if the system described by eq. (126) is initially at rest, the initial value stored in the memory element is zero.

Consider next the causal continuous-time system described by a first-order differential equation:

\[\frac{dy(t)}{dt}+ay(t)\,=\,b\,x(t). \tag{128}\]

As a first attempt at defining a block diagram representation for this system, let us rewrite it as

\[y(t)\,=\,-\frac{1}{a}\frac{dy(t)}{dt}+\frac{b}{a}x(t). \tag{129}\]

The right-hand side of this equation involves three basic operations: addition, multiplication by a coefficient, and differentiation. Therefore, if we define the three basic network elements indicated in Figure 2.29, we can consider representing eq. (129) as an interconnection of these basic elements in a manner analogous to that used for the discrete-time system described previously, resulting in the block diagram of Figure 2.30.

While the latter figure is a valid representation of the causal system described by eq. (128), it is not the representation that is most frequently used or the representation that leads directly to practical implementations, since differentiators are both difficult to implement and extremely sensitive to errors and noise. An alterna

Figure 2.27: Basic elements for the block diagram representation of the causal system described by eq. (126): (a) an adder; (b) multiplication by a coefficient; (c) a unit delay.

Figure 2.28: Block diagram representation for the causal discrete-time system described by eq. (126).

is much more widely used can be obtained by first rewriting eq. (2.128) as

\[\frac{dy(t)}{dt}\,=\,bx(t)-ay(t) \tag{2.130}\]

and then integrating from \(-\infty\) to \(t\). Specifically, if we assume that in the system described by eq. (2.130) the value of \(y(-\infty)\) is zero, then the integral of \(dy(t)/dt\) from \(-\infty\) to \(t\) is precisely \(y(t)\). Consequently, we obtain the equation

\[y(t)\,=\,\int_{-\infty}^{t}\big{[}\,bx(\tau)-ay(\tau)\big{]}\ d\tau. \tag{2.131}\]

In this form, our system can be implemented using the adder and coefficient multiplier indicated in Figure 2.29, together with an _integrator,_ as defined in Figure 2.31. Figure 2.32 is a block diagram representation for this system using these elements.

Figure 2.29: One possible set of basic elements for the block diagram representation of the continuous-time system described by eq. (2.128): (a) an adder; (b) multiplication by a coefficient; (c) a differentiator.

Figure 2.30: Block diagram representation for the system in eqs. (2.128) and (2.129), using adders, multiplications by coefficients, and differentiators.

Since integrators can be readily implemented using operational amplifiers, representations such as that in Figure 2.32 lead directly to analog implementations, and indeed, this is the basis for both early analog computers and modern analog computation systems. Note that in the continuous-time case it is the integrator that represents the memory storage element of the system. This is perhaps more readily seen if we consider integrating eq. (2.130) from a finite point in time \(t_{0}\), resulting in the expression

\[y(t)\,=\,y\left(t_{0}\right)+\int_{t_{0}}^{t}\left[b\,x(\tau)-ay(\tau)\right]\, d\tau. \tag{2.132}\]

Equation (2.132) makes clear the fact that the specification of \(y(t)\) requires an initial condition, namely, the value of \(y\left(t_{0}\right)\). It is precisely this value that the integrator stores at time \(t_{0}\).

While we have illustrated block diagram constructions only for the simplest first-order differential and difference equations, such block diagrams can also be developed for higher order systems, providing both valuable intuition for and possible implementations of these systems. Examples of block diagrams for higher order systems can be found in Problems 2.58 and 2.60.

### 2.5 Singularity Functions

In this section, we take another look at the continuous-time unit impulse function in order to gain additional intuitions about this important idealized signal and to introduce a set of related signals known collectively as _singularity functions_. In particular, in Section 1.4.2 we suggested that a continuous-time unit impulse could be viewed as the idealization of a pulse that is "short enough" so that its shape and duration is of no practical consequence--i.e., so that as far as the response of any particular LTI system is concerned, all of the area under the pulse can be thought of as having been applied instantaneously. In this section, we would first like to provide a concrete example of what this means and then use the interpretation embodied within the example to show that the key to the use of unit impulses and other singularity functions is in the specification of how LTI systems respond to these idealized signals; i.e., the signals are in essence defined in terms of how they behave under convolution with other signals.

#### The Unit Impulse as an Idealized Short Pulse

From the sifting property, eq. (2.27), the unit impulse \(\delta(t)\) is the impulse response of the identity system. That is,

\[x(t)\,=\,x(t)*\delta(t) \tag{2.133}\]

for any signal \(x(t)\). Therefore, if we take \(x(t)\,=\,\delta(t)\), we have

\[\delta(t)\,=\,\delta(t)*\delta(t). \tag{2.134}\]

Equation (2.134) is a basic property of the unit impulse, and it also has a significant implication for our interpretation of the unit impulse as an idealized pulse. For example, as in Section 1.4.2, suppose that we think of \(\delta(t)\) as the limiting form of a rectangular pulse. Specifically, let \(\delta_{\Delta}(t)\) correspond to the rectangular pulse defined in Figure 1.34, and let

\[r_{\Delta}(t)\,=\,\delta_{\Delta}(t)*\delta_{\Delta}(t). \tag{2.135}\]

Then \(r_{\Delta}(t)\) is as sketched in Figure 2.33. If we wish to interpret \(\delta(t)\) as the limit as \(\Delta\,\to\,0\) of \(\delta_{\Delta}(t)\), then, by virtue of eq. (2.134), the limit as \(\Delta\,\to\,0\) for \(r_{\Delta}(t)\) must also be a unit impulse. In a similar manner, we can argue that the limits as \(\Delta\,\to\,0\) of \(r_{\Delta}(t)*r_{\Delta}(t)\) or \(r_{\Delta}(t)*\delta_{\Delta}(t)\) must be unit impulses, and so on. Thus, we see that for consistency, if we define the unit impulse as the limiting form of some signal, then in fact, there is an unlimited number of very dissimilar-looking signals, all of which behave like an impulse in the limit.

The key words in the preceding paragraph are "behave like an impulse," where, as we have indicated, what we mean by this is that the response of an LTI system to all of these signals is essentially identical, as long as the pulse is "short enough," i.e., \(\Delta\) is "small enough." The following example illustrates this idea:

Consider the LTI system described by the first-order differential equation

\[\frac{d\,y(t)}{dt}\,+\,2\,y(t)\,=\,x(t), \tag{2.136}\]

together with the condition of initial rest. Figure 2.34 depicts the response of this system to \(\delta_{\Delta}(t)\), \(r_{\Delta}(t)\), \(r_{\Delta}(t)*\delta_{\Delta}(t)\), and \(r_{\Delta}(t)*r_{\Delta}(t)\) for several values of \(\Delta\). For \(\Delta\) large enough, the responses to these input signals differ noticeably. However, for \(\Delta\) sufficiently small, the responses are essentially indistinguishable, so that all of the input signals "behave" in the same way. Furthermore, as suggested by the figure, the limiting form of all of these responses is precisely \(e^{-2t}u(t)\). Since the limit of each of these signals as \(\Delta\to 0\) is the unit impulse, we conclude that \(e^{-2t}u(t)\) is the impulse response for this system.5

[FOOTNOFigure 2.34: Interpretation of a unit impulse as the idealization of a pulse whose duration is “short enough” so that, as far as the response of an LTI system to this pulse is concerned, the pulse can be thought of as having been applied instantaneously: (a) responses of the causal LTI system described by eq. (2.136) to the input \(\delta_{\Delta}(t)\) for \(\Delta=0.25\), \(0.1\), and \(0.0025\); (b) responses of the same system to \(r_{\Delta}(t)\) for the same values of \(\Delta\); (c) responses to \(\delta_{\Delta}(t)\!*\!r_{\Delta}(t)\); (d) responses to \(r_{\Delta}(t)\!*\!r_{\Delta}(t)\); (e) the impulse response \(h(t)=e^{-2t}u(t)\) for the system. Note that, for \(\Delta=0.25\), there are noticeable differences among the responses to these different signals; however, as \(\Delta\) becomes smaller, the differences diminish, and all of the responses converge to the impulse response shown in (e).

One important point to be emphasized is that what we mean by "\(\Delta\) small enough" depends on the particular LTI system to which the preceding pulses are applied. For example, in Figure 2.35, we have illustrated the responses to these pulses for different

Figure 2.35: Finding a value of \(\Delta\) that is “small enough” depends upon the system to which we are applying inputs: (a) responses of the causal LTI system described by eq. (2.137) to the input \(\delta_{\Delta}(t)\) for \(\Delta=0.025\), \(0.01\), and \(0.00025\); (b) responses to \(r_{\Delta}(t)\); (c) responses to \(\delta_{\Delta}(t)\ast r_{\Delta}(t)\); (d) responses to \(r_{\Delta}(t)\ast r_{\Delta}(t)\); (e) the impulse response \(h(t)=e^{-20t}u(t)\) for the system. Comparing these responses to those in Figure 2.34, we see that we need to use a smaller value of \(\Delta\) in this case before the duration and shape of the pulse are of no consequence.

values of \(\Delta\) for the causal LTI system described by the first-order differential equation

\[\frac{dy(t)}{dt}+20y(t)\,=\,x(t). \tag{2.137}\]

As seen in the figure, we need a smaller value of \(\Delta\) in this case in order for the responses to be indistinguishable from each other and from the impulse response \(h(t)\,=\,e^{-20t}u(t)\) for the system. Thus, while what we mean by "\(\Delta\) small enough" is different for these two systems, we can find values of \(\Delta\) small enough for both. The unit impulse is then the idealization of a short pulse whose duration is short enough for _all_ systems.

#### Defining the Unit Impulse through Convolution

As the preceding example illustrates, for \(\Delta\) small enough, the signals \(\delta_{\Delta}(t)\), \(r_{\Delta}(t)\), \(r_{\Delta}(t)*\delta_{\Delta}(t)\), and \(r_{\Delta}(t)*r_{\Delta}(t)\) all act like impulses when applied to an LTI system. In fact, there are many other signals for which this is true as well. What it suggests is that we should think of a unit impulse in terms of how an LTI system responds to it. While usually a function or signal is defined by what it is at each value of the independent variable, the primary importance of the unit impulse is not what it _is_ at each value of \(t\), but rather what it _does_ under convolution. Thus, from the point of view of linear systems analysis, we may alternatively _define_ the unit impulse as that signal which, when applied to an LTI system, yields the impulse response. That is, we define \(\delta(t)\) as the signal for which

\[x(t)\,=\,x(t)*\delta(t) \tag{2.138}\]

for any \(x(t)\). In this sense, signals, such as \(\delta_{\Delta}(t)\), \(r_{\Delta}(t)\), etc., which correspond to short pulses with vanishingly small duration as \(\Delta\to 0\), all behave like a unit impulse in the limit because, if we replace \(\delta(t)\) by any of these signals, then eq. (2.138) is satisfied in the limit.

All the properties of the unit impulse that we need can be obtained from the _operational definition_ given by eq. (2.138). For example, if we let \(x(t)\,=\,1\) for all \(t\), then

\[1\,=\,x(t) \,=\,x(t)*\delta(t)\,=\,\delta(t)*x(t)\,=\,\int_{-\infty}^{+\infty }\delta(\tau)x(t-\tau)\,d\tau\] \[\,=\,\int_{-\infty}^{+\infty}\delta(\tau)\,d\tau,\]

so that the unit impulse has unit area.

It is sometimes useful to use another completely equivalent operational definition of \(\delta(t)\). To obtain this alternative form, consider taking an arbitrary signal \(g(t)\), reversing it in time to obtain \(g(-t)\), and then convolving this with \(\delta(t)\). Using eq. (2.138), we obtain

\[g(-t)\,=\,g(-t)*\delta(t)\,=\,\int_{-\infty}^{+\infty}g(\tau-t)\,\delta(\tau) \,d\tau,\]

which, for \(t\,=\,0\), yields

\[g(0)\,=\,\int_{-\infty}^{+\infty}g(\tau)\,\delta(\tau)\,d\tau. \tag{2.139}\]Therefore, the operational definition of \(\delta(t)\) given by eq. (2.138) implies eq. (2.139). On the other hand, eq. (2.139) implies eq. (2.138). To see this, let \(x(t)\) be a given signal, fix a time \(t\), and define

\[g(\tau)\,=\,x(t-\tau).\]

Then, using eq. (2.139), we have

\[x(t)\,=\,g(0)\,=\,\int_{-\infty}^{+\infty}g(\tau)\,\delta(\tau)\,d\tau\,=\, \int_{-\infty}^{+\infty}x(t-\tau)\,\delta(\tau)\,d\tau,\]

which is precisely eq. (2.138). Therefore, eq. (2.139) is an equivalent operational definition of the unit impulse. That is, the unit impulse is the signal which, when multiplied by a signal \(g(t)\) and then integrated from \(-\infty\) to \(+\infty\), produces the value \(g(0)\).

Since we will be concerned principally with LTI systems, and thus with convolution, the characterization of \(\delta(t)\) given in eq. (2.138) will be the one to which we will refer most often. However, eq. (2.139) is useful in determining some of the other properties of the unit impulse. For example, consider the signal \(f(t)\,\delta(t)\), where \(f(t)\) is another signal. Then, from eq. (2.139),

\[\int_{-\infty}^{+\infty}g(\tau)f(\tau)\,\delta(\tau)\,d\tau\,=\,g(0)f(0). \tag{2.140}\]

On the other hand, if we consider the signal \(f(0)\,\delta(t)\), we see that

\[\int_{-\infty}^{+\infty}g(\tau)f(0)\,\delta(\tau)\,d\tau\,=\,g(0)f(0). \tag{2.141}\]

Comparing eqs. (2.140) and (2.141), we find that the two signals \(f(t)\,\delta(t)\) and \(f(0)\,\delta(t)\) behave identically when they are multiplied by any signal \(g(t)\) and then integrated from \(-\infty\) to \(+\infty\). Consequently, using this form of the operational definition of signals, we conclude that

\[f(t)\,\delta(t)\,=\,f(0)\,\delta(t), \tag{2.142}\]

which is a property that we derived by alternative means in Section 1.4.2. [See eq. (1.76).]

#### Unit Doublets and Other Singularity Functions

The unit impulse is one of a class of signals known as _singularity functions_, each of which can be defined operationally in terms of its behavior under convolution. Consider the LTI system for which the output is the derivative of the input, i.e.,

\[y(t)\,=\,\frac{dx(t)}{dt} \tag{2.143}\]

The unit impulse response of this system is the derivative of the unit impulse, which is called the _unit doublet_\(u_{1}(t)\). From the convolution representation for LTI systems, we have \[\frac{dx(t)}{dt}\,=\,x(t)*u_{1}(t) \tag{2.144}\]

for any signal \(x(t)\). Just as eq. (2.138) serves as the operational definition of \(\delta(t)\), we will take eq. (2.144) as the operational definition of \(u_{1}(t)\). Similarly, we can define \(u_{2}(t)\), the second derivative of \(\delta(t)\), as the impulse response of an LTI system that takes the second derivative of the input, i.e.,

\[\frac{d^{2}x(t)}{dt^{2}}\,=\,x(t)*u_{2}(t). \tag{2.145}\]

From eq. (2.144), we see that

\[\frac{d^{2}x(t)}{dt^{2}}\,=\,\frac{d}{dt}\left(\frac{dx(t)}{dt}\right)=\,x(t)* u_{1}(t)*u_{1}(t), \tag{2.146}\]

and therefore,

\[u_{2}(t)\,=\,u_{1}(t)*u_{1}(t). \tag{2.147}\]

In general, \(u_{k}(t)\), \(k>0\), is the \(k\)th derivative of \(\delta(t)\) and thus is the impulse response of a system that takes the \(k\)th derivative of the input. Since this system can be obtained as the cascade of \(k\) differentiators, we have

\[u_{k}(t)\,=\,\underbrace{u_{1}(t)*\cdots*u_{1}(t)}_{k\mbox{ times}}. \tag{2.148}\]

As with the unit impulse, each of these singularity functions has properties that can be derived from its operational definition. For example, if we consider the constant signal \(x(t)\,=\,1\), we find that

\[0\,=\,\frac{dx(t)}{dt} \,=\,x(t)*u_{1}(t)\,=\,\int_{-\infty}^{+\infty}u_{1}(\tau)x(t- \tau)\,d\tau\] \[\,=\,\int_{-\infty}^{+\infty}u_{1}(\tau)\,d\tau,\]

so that the unit doublet has zero area. Moreover, if we convolve the signal \(g(-t)\) with \(u_{1}(t)\), we obtain

\[\int_{-\infty}^{+\infty}g(\tau-t)u_{1}(\tau)\,d\tau\,=\,g(-t)*u_{1}(t)\,=\, \frac{dg(-t)}{dt}\,=\,-g^{\prime}(-t),\]

which, for \(t\,=\,0\), yields

\[-g^{\prime}(0)\,=\,\int_{-\infty}^{+\infty}g(\tau)u_{1}(\tau)\,d\tau. \tag{2.149}\]In an analogous manner, we can derive related properties of \(u_{1}(t)\) and higher order singularity functions, and several of these properties are considered in Problem 2.69.

As with the unit impulse, each of these singularity functions can be informally related to short pulses. For example, since the unit doublet is formally the derivative of the unit impulse, we can think of the doublet as the idealization of the derivative of a short pulse with unit area. For instance, consider the short pulse \(\delta_{\lambda}(t)\) in Figure 34. This pulse behaves like an impulse as \(\Delta\to 0\). Consequently, we would expect its derivative to behave like a doublet as \(\Delta\to 0\). As verified in Problem 2.72, \(d\delta_{\lambda}(t)/dt\) is as depicted in Figure 36: It consists of a unit impulse at \(t=0\) with area \(+1/\Delta\), followed by a unit impulse of area \(-1/\Delta\) at \(t\,=\,\Delta\), i.e.,

\[\frac{d\delta_{\lambda}(t)}{dt}\,=\,\frac{1}{\Delta}[\delta(t)-\delta(t- \Delta)]. \tag{150}\]

Consequently, using the fact that \(x(t)*\delta(t-t_{0})\,=\,x(t-t_{0})\) [see eq. (70)], we find that

\[x(t)*\frac{d\delta_{\lambda}(t)}{dt}\,=\,\frac{x(t)-x(t-\Delta)}{\Delta}\, \cong\,\frac{dx(t)}{dt}, \tag{151}\]

where the approximation becomes increasingly accurate as \(\Delta\,\to\,0\). Comparing eq. (151) with eq. (144), we see that \(d\delta_{\lambda}(t)/dt\) does indeed behave like a unit doublet as \(\Delta\to 0\).

In addition to singularity functions that are derivatives of different orders of the unit impulse, we can also define signals that represent successive integrals of the unit impulse function. As we saw in Example 2.13, the unit step is the impulse response of an integrator:

\[y(t)\,=\,\int_{-\infty}^{t}x(\tau)\,d\tau.\]

Therefore,

\[u(t)\,=\,\int_{-\infty}^{t}\delta(\tau)\,d\tau, \tag{152}\]

Figure 36: The derivative \(d\delta_{\lambda}(t)/dt\) of the short rectangular pulse \(\delta_{\lambda}(t)\) of Figure 34.

and we also have the following operational definition of \(u(t)\):

\[x(t)*u(t)\,=\,\int_{-\infty}^{t}x(\tau)\,d\tau. \tag{2.153}\]

Similarly, we can define the system that consists of a cascade of two integrators. Its impulse response is denoted by \(u_{-2}(t)\), which is simply the convolution of \(u(t)\), the impulse response of one integrator, with itself:

\[u_{-2}(t)\,=\,u(t)*u(t)\,=\,\int_{-\infty}^{t}u(\tau)\,d\tau. \tag{2.154}\]

Since \(u(t)\) equals \(0\) for \(t<0\) and equals \(1\) for \(t>0\), it follows that

\[u_{-2}(t)\,=\,tu(t). \tag{2.155}\]

This signal, which is referred to as the _unit ramp function_, is shown in Figure 2.37. Also, we can obtain an operational definition for the behavior of \(u_{-2}(t)\) under convolution from eqs. (2.153) and (2.154):

\[\begin{split} x(t)*u_{-2}(t)&\,=\,x(t)*u(t)*u(t)\\ &\,=\left(\int_{-\infty}^{t}x(\sigma)\,d\sigma\right)*u(t)\\ &\,=\,\int_{-\infty}^{t}\left(\int_{-\infty}^{\tau}x(\sigma)\,d \sigma\right)d\tau.\end{split} \tag{2.156}\]

In an analogous fashion, we can define higher order integrals of \(\delta(t)\) as the impulse responses of cascades of integrators:

\[u_{-k}(t)\,=\,\underbrace{u(t)*\cdots*u(t)}_{k\text{ times}}\,=\,\int_{- \infty}^{t}u_{-(k-1)}(\tau)\,d\tau. \tag{2.157}\]

The convolution of \(x(t)\) with \(u_{-3}(t),\,u_{-4}(t),\ldots\) generate correspondingly higher order integrals of \(x(t)\). Also, note that the integrals in eq. (2.157) can be evaluated directly (see

Figure 2.37: Unit ramp function.

Problem 2.73), as was done in eq. (2.155), to obtain

\[u_{-k}(t)\,=\,\frac{t^{k-1}}{(k-1)!}u(t). \tag{2.158}\]

Thus, unlike the derivatives of \(\delta(t)\), the successive integrals of the unit impulse are functions that can be defined for each value of \(t\) [eq. (2.158)], as well as by their behavior under convolution.

At times it will be worthwhile to use an alternative notation for \(\delta(t)\) and \(u(t)\), namely,

\[\delta(t)\,=\,u_{0}(t), \tag{2.159}\] \[u(t)\,=\,u_{-1}(t). \tag{2.160}\]

With this notation, \(u_{k}(t)\) for \(k>0\) denotes the impulse response of a cascade of \(k\) differentiators, \(u_{0}(t)\) is the impulse response of the identity system, and, for \(k<0\), \(u_{k}(t)\) is the impulse response of a cascade of \(|k|\) integrators. Furthermore, since a differentiator is the inverse system of an integrator,

\[u(t)*u_{1}(t)\,=\,\delta(t),\]

or, in our alternative notation,

\[u_{-1}(t)*u_{1}(t)\,=\,u_{0}(t). \tag{2.161}\]

More generally, from eqs. (2.148), (2.157), and (2.161), we see that for any integers \(k\) and \(r\),

\[u_{k}(t)*u_{r}(t)\,=\,u_{k+r}(t). \tag{2.162}\]

If \(k\) and \(r\) are both positive, eq. (2.162) states that a cascade of \(k\) differentiators followed by \(r\) more differentiators yields an output that is the \((k+r)\)th derivative of the input. Similarly, if \(k\) is negative and \(r\) is negative, we have a cascade of \(|k|\) integrators followed by another \(|r|\) integrators. Also, if \(k\) is negative and \(r\) is positive, we have a cascade of \(|k|\) integrators followed by \(r\) differentiators, and the overall system is equivalent to a cascade of \(|k+r|\) integrators if \(k+r<0\), a cascade of \(k+r\) differentiators if \(k+r>0\), or the identity system if \(k+r=0\). Therefore, by defining singularity functions in terms of their behavior under convolution, we obtain a characterization that allows us to manipulate them with relative ease and to interpret them directly in terms of their significance for LTI systems. Since this is our primary concern in the book, the operational definition for singularity functions that we have given in this section will suffice for our purposes.6

### Summary

In this chapter, we have developed important representations for LTI systems, both in discrete time and in continuous time. In discrete time we derived a representation of signals as weighted sums of shifted unit impulses, and we then used this to derive the convolution - sum representation for the response of a discrete-time LTI system. In continuous time we derived an analogous representation of continuous-time signals as weighted integrals of shifted unit impulses, and we used this to derive the convolution integral representation for continuous-time LTI systems. These representations are extremely important, as they allow us to compute the response of an LTI system to an arbitrary input in terms of the system's response to a unit impulse. Moreover, in Section 2.3 the convolution sum and integral provided us with a means of analyzing the properties of LTI systems and, in particular, of relating LTI system properties, including causality and stability, to corresponding properties of the unit impulse response. Also, in Section 2.5 we developed an interpretation of the continuous-time unit impulse and other related singularity functions in terms of their behavior under convolution. This interpretation is particularly useful in the analysis of LTI systems.

An important class of continuous-time systems consists of those described by linear constant-coefficient differential equations. Similarly, in discrete time, linear constant-coefficient difference equations play an equally important role. In Section 2.4, we examined simple examples of differential and difference equations and discussed some of the properties of systems described by these types of equations. In particular, systems described by linear constant-coefficient differential and difference equations together with the condition of initial rest are causal and LTI. In subsequent chapters, we will develop additional tools that greatly facilitate our ability to analyze such systems.

## Chapter 2 Problems

The first section of problems belongs to the basic category, and the answers are provided in the back of the book. The remaining three sections contain problems belonging to the basic, advanced, and extension categories, respectively.

**Extension problems** introduce applications, concepts, or methods beyond those presented in the text.

## 3 Basic Problems With Answers

Let

\[x[n]\,=\,\delta[n]+2\delta[n-1]-\delta[n-3]\quad\text{and}\quad h[n]\,=\,2 \delta[n+1]+2\delta[n-1].\]

Compute and plot each of the following convolutions:

**(a)**: \(y_{1}[n]\,=\,x[n]*h[n]\)**(b)**: \(y_{2}[n]\,=\,x[n+2]*h[n]\)**(c)**: \(y_{3}[n]\,=\,x[n]*h[n+2]\)

### Consider the signal

\[h[n]\,=\,\left(\frac{1}{2}\right)^{n-1}\{u[n+3]-u[n-10]\}.\]

Express \(A\) and \(B\) in terms of \(n\) so that the following equation holds:

\[h[n-k]\,=\,\left\{\begin{array}{ll}(\frac{1}{2})^{n-k-1},&A\,\,\leq\,k\,\leq\, B\\ 0,&\text{elsewhere}\end{array}\right..\]

### Consider an input \(x[n]\) and a unit impulse response \(h[n]\) given by

\[x[n]\,=\,\left(\frac{1}{2}\right)^{n-2}u[n-2],\]

\[h[n]\,=\,u[n+2].\]

Determine and plot the output \(y[n]\,=\,x[n]*h[n]\).

### Compute and plot \(y[n]\,=\,x[n]*h[n]\), where

\[x[n]\,=\,\left\{\begin{array}{ll}1,&3\,\,\leq\,n\,\leq\,8\\ 0,&\text{otherwise}\end{array}\right.,\]

\[h[n]\,=\,\left\{\begin{array}{ll}1,&4\,\,\leq\,n\,\leq\,15\\ 0,&\text{otherwise}\end{array}\right..\]

### Let

\[x[n]\,=\,\left\{\begin{array}{ll}1,&0\,\,\leq\,n\,\leq\,9\\ 0,&\text{elsewhere}\end{array}\right.\text{ and }&h[n]\,=\,\left\{\begin{array}{ll}1,&0\,\,\leq\,n\,\leq\,N\\ 0,&\text{elsewhere}\end{array}\right.,\]

where \(N\,\,\leq\,9\) is an integer. Determine the value of \(N\), given that \(y[n]\,=\,x[n]*h[n]\) and

\[y[4]\,=\,5,\,\,\,\,y[14]\,=\,0.\]

### Compute and plot the convolution \(y[n]\,=\,x[n]*h[n]\), where

\[x[n]\,=\,\left(\frac{1}{3}\right)^{-n}u[-n-1]\quad\text{and}\quad h[n]\,=\,u[ n-1].\]

### A linear system \(S\) has the relationship

\[y[n]\,=\,\sum_{k\,=\,-\infty}^{\infty}x[k]g[n-2k]\]

between its input \(x[n]\) and its output \(y[n]\), where \(g[n]\,=\,u[n]-u[n-4]\).

1. Determine \(y[n]\) when \(x[n]\,=\,\delta[n-1]\).
2. Determine \(y[n]\) when \(x[n]\,=\,\delta[n-2]\).
3. Is \(S\) LTI?
4. Determine \(y[n]\) when \(x[n]\,=\,u[n]\).

Determine and sketch the convolution of the following two signals:

\[x(t)\,=\,\left\{\begin{array}{ll}t+1,&0\,\,\leq\,t\,\leq\,1\\ 2-t,&1<t\,\,\leq\,2\\ 0,&\text{elsewhere}\end{array}\right.,\]

\[h(t)\,=\,\delta(t+2)+2\delta(t+1).\]

Let

\[h(t)\,=\,e^{2t}u(-t+4)\,+\,e^{-2t}u(t-5).\]

Determine \(A\) and \(B\) such that

\[h(t-\tau)\,=\,\left\{\begin{array}{ll}e^{-2(t-\tau)},&\tau<A\\ 0,&A<\tau<B\\ e^{2(t-\tau)},&B<\tau\end{array}\right..\]

Suppose that

\[x(t)\,=\,\left\{\begin{array}{ll}1,&0\,\,\leq\,t\,\leq\,1\\ 0,&\text{elsewhere}\end{array}\right.\]

and \(h(t)\,=\,x(t/\alpha)\), where \(0<\alpha\,\,\leq\,1\).

1. Determine and sketch \(y(t)\,=\,x(t)*h(t)\).
2. If \(d\,y(t)/dt\) contains only three discontinuities, what is the value of \(\alpha\)?

Let

\[x(t)\,=\,u(t-3)\,-\,u(t-5)\quad\text{and}\quad h(t)\,=\,e^{-3t}u(t).\]

1. Compute \(y(t)\,=\,x(t)*h(t)\).
2. Compute \(g(t)\,=\,(d\,x(t)/dt)*h(t)\).
3. How is \(g(t)\) related to \(y(t)\)?

Let

\[y(t)\,=\,e^{-t}u(t)*\sum_{k\,=\,-\infty}^{\infty}\delta(t-3k).\]

Show that \(y(t)\,=\,Ae^{-t}\) for \(0\,\leq\,t<3\), and determine the value of \(A\).

**2.13**.: Consider a discrete-time system \(S_{1}\) with impulse response

\[h[n]\,=\,\left(\frac{1}{5}\right)^{\!n}u[n].\]

**(a)**: Find the integer \(A\) such that \(h[n]\,-\,Ah[n-1]\,=\,\delta[n]\).
**(b)**: Using the result from part (a), determine the impulse response \(g[n]\) of an LTI system \(S_{2}\) which is the inverse system of \(S_{1}\).
**2.14**.: Which of the following impulse responses correspond(s) to stable LTI systems?
**(a)**: \(h_{1}(t)\,=\,e^{-(1-2)t}u(t)\)   **(b)**: \(h_{2}(t)\,=\,e^{-t}\cos(2t)u(t)\)
**2.15**.: Which of the following impulse responses correspond(s) to stable LTI systems?
**(a)**: \(h_{1}[n]\,=\,n\cos(\frac{\pi}{4}n)u[n]\)   **(b)**: \(h_{2}[n]\,=\,3^{n}u[-n+10]\)
**2.16**.: For each of the following statements, determine whether it is true or false:

**(a)**: If \(x[n]\,=\,0\) for \(n<N_{1}\) and \(h[n]\,=\,0\) for \(n<N_{2}\), then \(x[n]\,*\,h[n]\,=\,0\) for \(n<N_{1}\,+\,N_{2}\).
**(b)**: If \(y[n]\,=\,x[n]\,*\,h[n]\), then \(y[n-1]\,=\,x[n-1]\,*\,h[n-1]\).
**(c)**: If \(y(t)\,=\,x(t)\,*\,h(t)\), then \(y(-t)\,=\,x(-t)\,*\,h(-t)\).
**(d)**: If \(x(t)\,=\,0\) for \(t>T_{1}\) and \(h(t)\,=\,0\) for \(t>T_{2}\), then \(x(t)\,*\,h(t)\,=\,0\) for \(t>T_{1}\,+\,T_{2}\).
**2.17**.: Consider an LTI system whose input \(x(t)\) and output \(y(t)\) are related by the differential equation

\[\frac{d}{dt}y(t)\,+\,4y(t)\,=\,x(t).\] (P2.17-1)

The system also satisfies the condition of initial rest.

**(a)**: If \(x(t)\,=\,e^{(-1+3j)t}u(t)\), what is \(y(t)\)?
**(b)**: Note that \(\,\mathcal{G}\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\[S_{1}:\text{causal LTI},\] \[w[n]\,=\,\frac{1}{2}w[n-1]+x[n];\] \[S_{2}:\text{causal LTI},\] \[y[n]\,=\,\alpha\,y[n-1]+\,\beta w[n].\]

The difference equation relating \(x[n]\) and \(y[n]\) is:

\[y[n]\,=\,-\frac{1}{8}y[n-2]+\frac{3}{4}y[n-1]+x[n].\]

**(a)**: Determine \(\alpha\) and \(\beta\).
**(b)**: Show the impulse response of the cascade connection of \(S_{1}\) and \(S_{2}\).
**(a)**: Evaluate the following integrals:

**(b)**: \(\int_{0}^{5}\sin(2\pi t)\,\delta(t+3)\,dt\)
**(c)**: \(\int_{-5}^{5}u_{1}(1-\tau)\cos(2\pi\tau)\,d\tau\)

## Basic Problems

**2.21**: Compute the convolution \(y[n]\,=\,x[n]*h[n]\) of the following pairs of signals:

**(a)**: \(x[n]\,=\,\alpha^{n}u[n]\), \(h[n]\,=\,\beta^{n}u[n]\), \(\alpha\,\neq\,\beta\)
**(b)**: \(x[n]\,=\,h[n]\,=\,\alpha^{n}u[n]\)
**(c)**: \(x[n]\,=\,(-\frac{1}{2})^{n}u[n-4]\)

\(h[n]\,=\,4^{n}u[2\,\,-\,n]\)
**(d)**: \(x[n]\) and \(h[n]\) are as in Figure P2.21.

**2.22**: For each of the following pairs of waveforms, use the convolution integral to find the response \(y(t)\) of the LTI system with impulse response \(h(t)\) to the input \(x(t)\). Sketch your results.

**(a)**: \(x(t)\,=\,e^{-\alpha t}u(t)\,\) (Do this both when \(\alpha\neq\beta\) and when \(\alpha\,=\,\beta\).)

**2.23.**: Let \(h(t)\) be the triangular pulse shown in Figure P2.23(a), and let \(x(t)\) be the impulse train depicted in Figure P2.23(b). That is,

\[x(t)\,=\,\sum_{k\,=\,-\,\gamma}^{+\,\infty}\delta(t\,-\,kT).\]

Determine and sketch \(y(t)\,=\,x(t)*h(t)\) for the following values of \(T\):

**(a)**: \(T\,=\,4\qquad\)**(b)**: \(T\,=\,2\qquad\)**(c)**: \(T\,=\,3/2\qquad\)**(d)**: \(T\,=\,1\)

**2.24.**: Consider the cascade interconnection of three causal LTI systems, illustrated in Figure P2.24(a). The impulse response \(h_{2}[n]\) is

\[h_{2}[n]\,=\,u[n]\,-\,u[n-2],\]

and the overall impulse response is as shown in Figure P2.24(b).

**(a)**: Find the impulse response \(h_{1}[n]\).
**(b)**: Find the response of the overall system to the input

\[x[n]\,=\,\delta[n]\,-\,\delta[n-1].\]
Let the signal

\[y[n]\,=\,x[n]*h[n],\]

where

\[x[n]\,=\,3^{n}u[-n-1]+\left(\frac{1}{3}\right)^{n}u[n]\]

and

\[h[n]\,=\,\left(\frac{1}{4}\right)^{n}u[n+3].\]

1. Determine \(y[n]\)_without_ utilizing the distributive property of convolution.
2. Determine \(y[n]\)_utilizing_ the distributive property of convolution.

Consider the evaluation of

\[y[n]\,=\,x_{1}[n]*x_{2}[n]*x_{3}[n],\]

where \(x_{1}[n]=(0.5)^{n}u[n]\), \(x_{2}[n]=u[n+3]\), and \(x_{3}[n]=\delta[n]-\delta[n-1]\). 1. Evaluate the convolution \(x_{1}[n]*x_{2}[n]\). 2. Convolve the result of part (a) with \(x_{3}[n]\) in order to evaluate \(y[n]\). 3. Evaluate the convolution \(x_{2}[n]*x_{3}[n]\). 4. Convolve the result of part (c) with \(x_{1}[n]\) in order to evaluate \(y[n]\).

We define the area under a continuous-time signal \(v(t)\) as

\[A_{v}\,=\,\int_{-\infty}^{+\infty}v(t)\,dt.\]

Show that if \(y(t)\,=\,x(t)*h(t)\), then

\[A_{y}\,=\,A_{x}A_{h}.\]

The following are the impulse responses of discrete-time LTI systems. Determine whether each system is causal and/or stable. Justify your answers.

1. \(h[n]\,=\,(\frac{1}{5})^{n}u[n]\)
2. \(h[n]\,=\,(0.8)^{n}u[n+2]\)
3. \(h[n]\,=\,(\frac{1}{2})^{n}u[-n]\)
4. \(h[n]\,=\,(5)^{n}u[3-n]\)
5. \(h[n]\,=\,(-\frac{1}{2})^{n}u[n]+(1.01)^{n}u[n-1]\)
6. \(h[n]\,=\,(-\frac{1}{2})^{n}u[n]+(1.01)^{n}u[1-n]\)
7. \(h[n]\,=\,n(\frac{1}{3})^{n}u[n-1]\)
8. The following are the impulse responses of continuous-time LTI systems. Determine whether each system is causal and/or stable. Justify your answers. 1. \(h(t)\,=\,e^{-4t}u(t-2)\)
9. \(h(t)\,=\,e^{-6t}u(3-t)\)
10. \(h(t)\,=\,e^{-2t}u(t+50)\)
11. \(h(t)\,=\,e^{2t}u(-1-t)\)
* Consider the first-order difference equation \[y[n]+2y[n-1]\,=\,x[n].\] Assuming the condition of initial rest (i.e., if \(x[n]\,=\,0\) for \(n<n_{0}\), then \(y[n]\,=\,0\) for \(n<n_{0}\)), find the impulse response of a system whose input and output are related by this difference equation. You may solve the problem by rearranging the difference equation so as to express \(y[n]\) in terms of \(y[n-1]\) and \(x[n]\) and generating the values of \(y[0],\,\,y[+1],\,\,y[+2],\,\ldots\) in that order.
* Consider the LTI system initially at rest and described by the difference equation \[y[n]+2y[n-1]\,=\,x[n]+2x[n-2].\] Find the response of this system to the input depicted in Figure P2.31 by solving the difference equation recursively.

* Consider the difference equation \[y[n]-\,\frac{1}{2}y[n-1]\,=\,x[n],\] (P2.32-1) and suppose that \[x[n]\,=\,\left(\frac{1}{3}\right)^{\!n}u[n].\] (P2.32-2) Assume that the solution \(y[n]\) consists of the sum of a particular solution \(y_{p}[n]\) to eq. (P2.32-1) and a homogeneous solution \(y_{h}[n]\) satisfying the equation \[y_{h}[n]-\,\frac{1}{2}y_{h}[n-1]\,=\,0.\]
* Verify that the homogeneous solution is given by \[y_{h}[n]\,=\,A\left(\frac{1}{2}\right)^{\!n}\]
* Let us consider obtaining a particular solution \(y_{p}[n]\) such that \[y_{p}[n]-\,\frac{1}{2}y_{p}[n-1]\,=\,\left(\frac{1}{3}\right)^{\!n}u[n].\]

[MISSING_PAGE_EMPTY:73]

We may therefore conclude that the system under consideration is time invariant. In conjunction with the result derived in part (a), we conclude that the given system is LTI. Since this system satisfies the condition of initial rest, it is causal as well.
3. The initial rest assumption corresponds to a zero-valued auxiliary condition being imposed at a time determined in accordance with the input signal. In this problem we show that if the auxiliary condition used is nonzero or if it is always applied at a fixed time (regardless of the input signal) the corresponding system cannot be LTI. Consider a system whose input \(x(t)\) and output \(y(t)\) satisfy the first-order differential equation (P2.33-1). 1. Given the auxiliary condition \(y(1)=1\), use a counterexample to show that the system is not linear. 2. Given the auxiliary condition \(y(1)=1\), use a counterexample to show that the system is not time invariant. 3. Given the auxiliary condition \(y(1)=1\), show that the system is incrementally linear. 4. Given the auxiliary condition \(y(1)=0\), show that the system is linear but not time invariant. 5. Given the auxiliary condition \(y(0)+y(4)=0\), show that the system is linear but not time invariant.
4. In the previous problem we saw that application of an auxiliary condition at a fixed time (regardless of the input signal) leads to the corresponding system being not time-invariant. In this problem, we explore the effect of fixed auxiliary conditions on the causality of a system. Consider a system whose input \(x(t)\) and output \(y(t)\) satisfy the first-order differential equation (P2.33-1). Assume that the auxiliary condition associated with the differential equation is \(y(0)=0\). Determine the output of the system for each of the following two inputs: 1. \(x_{1}(t)=0\), for all \(t\) 2. \(x_{2}(t)=\left\{\begin{array}{ll}0,&t<-1\\ 1,&t>-1\end{array}\right.\) Observe that if \(y_{1}(t)\) is the output for input \(x_{1}(t)\) and \(y_{2}(t)\) is the output for input \(x_{2}(t)\), then \(y_{1}(t)\) and \(y_{2}(t)\) are not identical for \(t<-1\), even though \(x_{1}(t)\) and \(x_{2}(t)\) are identical for \(t<-1\). Use this observation as the basis of an argument to conclude that the given system is not causal.
5. Consider a discrete-time system whose input \(x[n]\) and output \(y[n]\) are related by \[y[n]=\left(\frac{1}{2}\right)y[n-1]+x[n].\] 1. Show that if this system satisfies the condition of initial rest (i.e., if \(x[n]=0\) for \(n<n_{0}\), then \(y[n]=0\) for \(n<n_{0}\)), then it is linear and time invariant. 2. Show that if this system does not satisfy the condition of initial rest, but instead uses the auxiliary condition \(y[0]=0\), it is not causal. [_Hint:_ Use an approach similar to that used in Problem 2.35.]

**2.37**.: Consider a system whose input and output are related by the first-order differential equation (P2.33-1). Assume that the system satisfies the condition of final rest [i. e., if \(x(t)=0\) for \(t>t_{0}\), then \(y(t)=0\) for \(t>t_{0}\)]. Show that this system is _not_ causal. [_Hint:_ Consider two inputs to the system, \(x_{1}(t)=0\) and \(x_{2}(t)=e^{t}(u(t)-u(t-1))\), which result in outputs \(y_{1}(t)\) and \(y_{2}(t)\), respectively. Then show that \(y_{1}(t)\neq y_{2}(t)\) for \(t<0\).]
**2.38**.: Draw block diagram representations for causal LTI systems described by the following difference equations:

**(a)**: \(y[n]=\frac{1}{3}y[n-1]+\frac{1}{2}x[n]\)
**(b)**: \(y[n]=\frac{1}{3}y[n-1]+x[n-1]\)
**2.39**.: Draw block diagram representations for causal LTI systems described by the following differential equations:

**(a)**: \(y(t)=-(\frac{1}{2})\,dy(t)/dt+4x(t)\)
**(b)**: \(dy(t)/dt+3y(t)=x(t)\)

## ADVANCED PROBLEMS

**2.40**.:
**(a)**: Consider an LTI system with input and output related through the equation

\[y(t)=\int_{-\times}^{t}e^{-(t-\tau)}x(\tau-2)\,d\tau.\]

What is the impulse response \(h(t)\) for this system?
**(b)**: Determine the response of the system when the input \(x(t)\) is as shown in Figure P2.40.

**2.41**.: Consider the signal

**(a)**: Sketch the signal \(g[n]=x[n]-\alpha x[n-1]\).
**(b)**: Use the result of part (a) in conjunction with properties of convolution in order to determine a sequence \(h[n]\) such that

\[x[n]*h[n]=\left(\frac{1}{2}\right)^{\!n}\{u[n+2]-u[n-2]\}.\]
**2.42**.: Suppose that the signal

\[x(t)=u(t+0.5)-u(t-0.5)\]is convolved with the signal \[h(t)\,=\,e^{j\omega_{0}t}.\] **(a)**: Determine a value of \(\omega_{0}\) which ensures that \[y(0)\,=\,0,\] where \(y(t)\,=\,x(t)*h(t)\). **(b)**: Is your answer to the previous part unique?
**2.43**.: One of the important properties of convolution, in both continuous and discrete time, is the associativity property. In this problem, we will check and illustrate this property. **(a)**: Prove the equality \[[x(t)*h(t)]*g(t)\,=\,x(t)*[h(t)*g(t)]\] (P2.43-1) by showing that both sides of eq. (P2.43-1) equal \[\int_{-\infty}^{+\infty}\int_{-\infty}^{+\infty}x(\tau)h(\sigma)g(t-\tau- \sigma)\,d\tau\,d\sigma.\] **(b)**: Consider two LTI systems with the unit sample responses \(h_{1}[n]\) and \(h_{2}[n]\) shown in Figure P2.43(a). These two systems are cascaded as shown in Figure P2.43(b). Let \(x[n]\,=\,u[n]\).

\(y[n]\,=\,x[n]*h_{1}[n]\) and then computing \(y[n]\,=\,w[n]*h_{2}[n]\); that is, \(y[n]\,=\,[x[n]*h_{1}[n]]*h_{2}[n]\). 2. Now find \(y[n]\) by first convolving \(h_{1}[n]\) and \(h_{2}[n]\) to obtain \(g[n]\,=\,h_{1}[n]*h_{2}[n]\) and then convolving \(x[n]\) with \(g[n]\) to obtain \(y[n]\,=\,x[n]*[h_{1}[n]*h_{2}[n]]\). The answers to (i) and (ii) should be identical, illustrating the associativity property of discrete-time convolution. 3. Consider the cascade of two LTI systems as in Figure P2.43(b), where in this case \[h_{1}[n]\,=\,\sin 8n\] and \[h_{2}[n]\,=\,a^{n}u[n],\,\,\,\,\,|a|<1,\] and where the input is \[x[n]\,=\,\delta[n]\,-\,a\delta[n-1].\] Determine the output \(y[n].\) (_Hint:_ The use of the associative and commutative properties of convolution should greatly facilitate the solution.)
4. If \[x(t)\,=\,0,\,\,|t|>T_{1},\] and \[h(t)\,=\,0,\,\,|t|>T_{2},\] then \[x(t)\,*h(t)\,=\,0,\,\,|t|>T_{3}\] for some positive number \(T_{3}.\) Express \(T_{3}\) in terms of \(T_{1}\) and \(T_{2}.\) 5. A discrete-time LTI system has input \(x[n],\) impulse response \(h[n],\) and output \(y[n].\) If \(h[n]\) is known to be zero everywhere outside the interval \(N_{0}\,\leq\,n\,\leq\,N_{1}\) and \(x[n]\) is known to be zero everywhere outside the interval \(N_{2}\,\leq\,n\,\leq\,N_{3},\) then the output \(y[n]\) is constrained to be zero everywhere, except on some interval \(N_{4}\,\leq\,n\,\leq\,N_{5}.\) 6. Determine \(N_{4}\) and \(N_{5}\) in terms of \(N_{0},\)\(N_{1},\)\(N_{2},\) and \(N_{3}.\) 7. If the interval \(N_{0}\,\leq\,n\,\leq\,N_{1}\) is of length \(M_{h},\)\(N_{2}\,\leq\,n\,\leq\,N_{3}\) is of length \(M_{x},\) and \(N_{4}\,\leq\,n\,\leq\,N_{5}\) is of length \(M_{y},\) express \(M_{y}\) in terms of \(M_{h}\) and \(M_{x}.\) 8. Consider a discrete-time LTI system with the property that if the input \(x[n]\,=\,0\) for all \(n\,\geq\,10,\) then the output \(y[n]\,=\,0\) for all \(n\,\geq\,15.\) What condition must \(h[n],\) the impulse response of the system, satisfy for this to be true? 9. Consider an LTI system with impulse response in Figure P2.44. Over what interval must we know \(x(t)\) in order to determine \(y(0)\)?

**2.45**.:
* Show that if the response of an LTI system to \(x(t)\) is the output \(y(t)\), then the response of the system to \[x^{\prime}(t)\,=\,\frac{dx(t)}{dt}\] is \(y^{\prime}(t)\). Do this problem in three different ways:
* Directly from the properties of linearity and time invariance and the fact that \[x^{\prime}(t)\,=\,\lim_{h\to 0}\frac{x(t)-x(t-h)}{h}.\]
* By differentiating the convolution integral.
* By examining the system in Figure P2.45.
* Demonstrate the validity of the following relationships:
* \(y^{\prime}(t)\,=\,x(t)\ast h^{\prime}(t)\)
* \(y(t)\,=\,(\int\limits_{-\infty}^{t}\!x(\tau)\,d\tau)\ast h^{\prime}(t)\,=\, \int\limits_{-\infty}^{t}\![x^{\prime}(\tau)\ast h(\tau)]d\tau\,=\,x^{\prime} (t)\ast(\int\limits_{-\infty}^{t}\!h(\tau)d\tau)\) [_Hint:_ These are easily done using block diagrams as in (iii) of part (a) and the fact that \(u_{1}(t)\ast u_{-1}(t)\,=\,\delta(t)\)._
* An LTI system has the response \(y(t)\,=\,\sin\omega_{0}t\) to input \(x(t)\,=\,e^{-5t}u(t)\). Use the result of part (a) to aid in determining the impulse response of this system.
* Let \(s(t)\) be the unit step response of a continuous-time LTI system. Use part (b) to deduce that the response \(y(t)\) to the input \(x(t)\) is \[y(t)\,=\,\int\limits_{-\infty}^{+\infty}x^{\prime}(\tau)\ast s(t-\tau)\,d\tau.\] (P2.45-1) Show also that \[x(t)\,=\,\int\limits_{-\infty}^{+\infty}x^{\prime}(\tau)u(t-\tau)\,d\tau.\] (P2.45-2)
* Use eq. (P2.45-1) to determine the response of an LTI system with step response \[s(t)\,=\,(e^{-3t}-2e^{-2t}+1)u(t)\] to the input \(x(t)\,=\,e^{t}u(t)\).
* Let \(s[n]\) be the unit step response of a discrete-time LTI system. What are the discrete-time counterparts of eqs. (P2.45-1) and (P2.45-2)?
* Consider an LTI system \(S\) and a signal \(x(t)\,=\,2e^{-3t}u(t-1)\). If \[x(t)\longrightarrow\,y(t)\] and \[\frac{dx(t)}{dt}\longrightarrow\,-3y(t)+\,e^{-2t}u(t),\] determine the impulse response \(h(t)\) of \(S\).
* We are given a certain linear time-invariant system with impulse response \(h_{0}(t)\). We are told that when the input is \(x_{0}(t)\) the output is \(y_{0}(t)\), which is sketched in Figure P2.47. We are then given the following set of inputs to linear time-invariant systems with the indicated impulse responses: \[\begin{array}{llll}&\mbox{\it Input $x(t)$}&\mbox{\it Impulse response $h(t)$}\\ \mbox{\bf(a)}&\mbox{$x(t)$}\,=\,2x_{0}(t)&\mbox{\it h(t)$}\,=\,h_{0}(t)\\ \mbox{\bf(b)}&\mbox{$x(t)$}\,=\,x_{0}(t)-x_{0}(t-2)&\mbox{\it h(t)$}\,=\,h_{0}( t)\\ \mbox{\bf(c)}&\mbox{$x(t)$}\,=\,x_{0}(t-2)&\mbox{\it h(t)$}\,=\,h_{0}(t+1)\\ \mbox{\bf(d)}&\mbox{$x(t)$}\,=\,x_{0}(-t)&\mbox{\it h(t)$}\,=\,h_{0}(t)\\ \mbox{\bf(e)}&\mbox{$x(t)$}\,=\,x_{0}(-t)&\mbox{\it h(t)$}\,=\,h_{0}(-t)\\ \mbox{\bf(f)}&\mbox{$x(t)$}\,=\,x_{0}^{\prime}(t)&\mbox{\it h(t)$}\,=\,h_{0}^{ \prime}(t)\\ \end{array}\] \[\begin{array}{llll}&\mbox{\it(Here $x_{0}^{\prime}(t)$ and $h_{0}^{\prime}(t)$ denote the first derivatives of $x_{0}(t)$ and $h_{0}(t)$, respectively.}]\\ \end{array}\]

In each of these cases, determine whether or not we have enough information to determine the output \(y(t)\) when the input is \(x(t)\) and the system has impulse response \(h(t)\). If it is possible to determine \(y(t)\), provide an accurate sketch of it with numerical values clearly indicated on the graph.

2. **2.48**.: Determine whether each of the following statements concerning LTI systems is true or false. Justify your answers. **(a)**: If \(h(t)\) is the impulse response of an LTI system and \(h(t)\) is periodic and nonzero, the system is unstable. **(b)**: The inverse of a causal LTI system is always causal. **(c)**: If \(|h[n]|\,\leq\,K\) for each \(n\), where \(K\) is a given number, then the LTI system with \(h[n]\) as its impulse response is stable. **(d)**: If a discrete-time LTI system has an impulse response \(h[n]\) of finite duration, the system is stable. **(e)**: If an LTI system is causal, it is stable. **(f)**: The cascade of a noncausal LTI system with a causal one is necessarily non-causal. **(g)**: A continuous-time LTI system is stable if and only if its step response \(s(t)\) is absolutely integrable--that is, if and only if \[\int_{-\infty}^{+\infty}|s(t)|\,dt<\infty.\] **(h)**: A discrete-time LTI system is causal if and only if its step response \(s[n]\) is zero for \(n<0\).
2. **2.49**.: In the text, we showed that if \(h[n]\) is absolutely summable, i.e., if \[\sum_{k\,=\,-\infty}^{+\infty}|h[k]|<\infty,\] then the LTI system with impulse response \(h[n]\) is stable. This means that absolute summability is a _sufficient_ condition for stability. In this problem, we shall show that it is also a _necessary_ condition. Consider an LTI system with impulse response \(h[n]\) that is not absolutely summable; that is, \[\sum_{k\,=\,-\infty}^{+\infty}|h[k]|\,=\,\infty.\] **(a)**: Suppose that the input to this system is \[x[n]\,=\,\left\{\begin{array}{ll}0,&\mbox{if }h[-n]\,=\,0\\ \frac{h[-n]}{|h[-n]|},&\mbox{if }h[-n]\neq 0\end{array}\right..\] Does this input signal represent a bounded input? If so, what is the smallest number \(B\) such that \[|x[n]|\,\leq\,B\mbox{ for all }n?\]* Calculate the output at \(n=0\) for this particular choice of input. Does the result prove the contention that absolute summability is a necessary condition for stability?
* In a similar fashion, show that a continuous-time LTI system is stable if and only if its impulse response is absolutely integrable.
* Consider the cascade of two systems shown in Figure P2.50. The first system, \(A\), is known to be LTI. The second system, \(B\), is known to be the inverse of system \(A\). Let \(y_{1}(t)\) denote the response of system \(A\) to \(x_{1}(t)\), and let \(y_{2}(t)\) denote the response of system \(A\) to \(x_{2}(t)\).
* What is the response of system \(B\) to the input \(y_{1}(t-\tau)\)?
* In the text, we saw that the overall input-output relationship of the cascade of two LTI systems does not depend on the order in which they are cascaded. This fact, known as the commutativity property, depends on both the linearity and the time invariance of both systems. In this problem, we illustrate the point.
* Consider two discrete-time systems \(A\) and \(B\), where system \(A\) is an LTI system with unit sample response \(h[n]=(1/2)^{n}u[n]\). System \(B\), on the other hand, is linear but time varying. Specifically, if the input to system \(B\) is \(w[n]\), its output is \[z[n]\,=\,nw[n].\] Show that the commutativity property does not hold for these two systems by computing the impulse responses of the cascade combinations in Figures P2.51(a) and P2.51(b), respectively.
* Suppose that we replace system \(B\) in each of the interconnected systems of Figure P2.51 by the system with the following relationship between its input \(w[n]\) and output \(z[n]\): \[z[n]\,=\,w[n]+2.\] Repeat the calculations of part (a) in this case.

Consider a discrete-time LTI system with unit sample response

\[h[n]\,=\,(n\,+\,1)\alpha^{n}u[n],\]

where \(|\alpha|<1\). Show that the step response of this system is

\[s[n]\,=\,\left[\frac{1}{(\alpha-1)^{2}}\,-\,\frac{\alpha}{(\alpha-1)^{2}}\alpha ^{n}\,+\,\frac{\alpha}{(\alpha-1)}(n\,+\,1)\alpha^{n}\right]u[n].\]

(_Hint:_ Note that

\[\sum_{k\,-\,0}^{N}(k\,+\,1)\alpha^{k}\,=\,\frac{d}{d\alpha}\sum_{k\,=\,0}^{N+ 1}\alpha^{k}.)\]

Consider the homogeneous differential equation

\[\sum_{k\,=\,0}^{N}a_{k}\frac{d^{k}y(t)}{dt^{k}}\,=\,0.\]

Show that if \(s_{0}\) is a solution of the equation

\[p(s)\,=\,\sum_{k\,=\,0}^{N}a_{k}s^{k}\,=\,0,\] (P2.53-2)

then \(Ae^{s_{0}t}\) is a solution of eq. (P2.53-1), where \(A\) is an arbitrary complex constant.
**(b)**: The polynomial \(p(s)\) in eq. (P2.53-2) can be factored in terms of its roots \(s_{1},\ldots,s_{r}\) as

\[p(s)\,=\,a_{N}(s-s_{1})^{\sigma_{1}}(s-s_{2})^{\sigma_{2}}\ldots(s-s_{r})^{ \sigma_{r}},\]

where the \(s_{i}\) are the distinct solutions of eq. (P2.53-2) and the \(\sigma_{i}\) are their _multiplicities_--that is, the number of times each root appears as a solution of the equation. Note that

\[\sigma_{1}\,+\,\sigma_{2}\,+\,\ldots\,+\,\sigma_{r}\,=\,N.\]

In general, if \(\sigma_{i}>1\), then not only is \(Ae^{s_{i}t}\) a solution of eq. (P2.53-1), but so is \(At^{j}e^{s_{i}t}\), as long as \(j\) is an integer greater than or equal to zero and less than or equal to \(\sigma_{i}-1\). To illustrate this, show that if \(\sigma_{i}\,=\,2\), then \(Ate^{s_{i}t}\) is a solution of eq. (P2.53-1). [_Hint:_ Show that if \(s\) is an arbitrary complex number, then

\[\sum_{k\,=\,0}^{N}\frac{d^{k}(Ate^{st})}{dt^{k}}\,=\,Ap(s)te^{st}\,+\,A\frac{ dp(s)}{ds}e^{st}.]\]Thus, the most general solution of eq. (P2.53-1) is

\[\sum_{i\,=\,1}^{r}\sum_{j\,=\,0}^{\sigma_{i\,-}1}A_{ij}t^{j}e^{s_{i}t},\]

where the \(A_{ij}\) are arbitrary complex constants.
**(c)**: Solve the following homogeneous differential equations with the specified auxiliary conditions:

* \(\frac{d^{2}y(t)}{dt^{2}}+3\frac{d\,y(t)}{dt}+2y(t)\,=\,0,\,\,y(0)\,=\,0,\,\,\,\,y ^{\prime}(0)\,=\,2\)
* \(\frac{d^{2}y(t)}{dt^{2}}+3\frac{d\,y(t)}{dt}+2y(t)\,=\,0,\,\,y(0)\,=\,1,\,\,\,y ^{\prime}(0)\,=\,-1\)
* \(\frac{d^{2}y(t)}{dt^{2}}+3\frac{d\,y(t)}{dt}+2y(t)\,=\,0,\,\,y(0)\,=\,0,\,\,\, \,y^{\prime}(0)\,=\,0\)
* \(\frac{d^{2}y(t)}{dt^{2}}+2\frac{d\,y(t)}{dt}+y(t)\,=\,0,\,\,y(0)\,=\,1,\,\,\,y ^{\prime}(0)\,=\,1\)
* \(\frac{d^{3}y(t)}{dt^{3}}+\frac{d^{2}y(t)}{dt^{2}}-\frac{d\,y(t)}{dt}-y(t)=0,\, \,y(0)\,=\,1,\,\,\,y^{\prime}(0)=1\), \(y^{\prime\prime}(0)=-2\)
* \(\frac{d^{2}y(t)}{dt^{2}}+2\frac{d\,y(t)}{dt}+5y(t)=0,\,\,y(0)\,=\,1,\,\,\,y^{ \prime}(0)\,=\,1\)

* Consider the homogeneous difference equation \[\sum_{k\,=\,0}^{N}a_{k}y[n\,-\,k]\,=\,0,\] (P2.54-1) Show that if \(z_{0}\) is a solution of the equation \[\sum_{k\,=\,0}^{N}a_{k}z^{-k}\,=\,0,\] (P2.54-2) then \(Az_{0}^{n}\) is a solution of eq. (P2.54-1), where \(A\) is an arbitrary constant.
* As it is more convenient for the moment to work with polynomials that have only nonnegative powers of \(z\), consider the equation obtained by multiplying both sides of eq. (P2.54-2) by \(z^{N}\): \[p(z)\,=\,\sum_{k\,=\,0}^{N}a_{k}z^{N-k}\,=\,0.\] (P2.54-3) The polynomial \(p(z)\) can be factored as \[p(z)\,=\,a_{0}(z-z_{1})^{\sigma_{i}}\ldots(z-z_{r})^{\sigma_{r}},\] where the \(z_{1},\ldots,z_{r}\) are the distinct roots of \(p(z)\). Show that if \(y[n]\,=\,nz^{n-1}\), then \[\sum_{k\,=\,0}^{N}a_{k}y[n\,-\,k]\,=\,\frac{dp(z)}{dz}z^{n-N}\,+\,(n\,-\,N)p(z )z^{n-N-1}.\] Use this fact to show that if \(\sigma_{i}\,=\,2\), then both \(Az_{i}^{n}\) and \(Bnz_{i}^{n-1}\) are solutions of eq. (P2.54-1), where \(A\) and \(B\) are arbitrary complex constants. More generally, one can use this same procedure to show that if \(\sigma_{i}\,>\,1\), then \[A\,\frac{n!}{r!(n-r)!}\,z^{n-r}\] is a solution of eq. (P2.54-1) for \(r\,=\,0,\,\,1,\ldots,\sigma_{i}\,-\,1\).7 Footnote 7: Here, we are using factorial notation—that is, \(k!\,=\,k(k-1)(k-2)\ldots(2)(1)\), where \(0!\) is defined to be \(1\). 3. Solve the following homogeneous difference equations with the specified auxiliary conditions: 1. \(y[n]+\frac{3}{4}y[n-1]+\frac{1}{8}y[n-2]=0\); \(y[0]=1,\,\,y[-1]=-6\) 2. \(y[n]-2y[n-1]+y[n-2]=0\); \(y[0]=1,\,\,y[1]=0\) 3. \(y[n]-2y[n-1]+y[n-2]=0\); \(y[0]=1,\,\,y[10]=21\) 4. \(y[n]-\frac{\sqrt{2}}{2}y[n-1]+\frac{1}{4}y[n-2]=0\); \(y[0]=0,\,\,y[-1]=1\)
2. 55. In the text we described one method for solving linear constant-coefficient difference equations, and another method for doing this was illustrated in Problem 2.30. If the assumption of initial rest is made so that the system described by the difference equation is LTI and causal, then, in principle, we can determine the unit impulse response \(h[n]\) using either of these procedures. In Chapter 5, we describe another method that allows us to determine \(h[n]\) in a more elegant way. In this problem we describe yet another approach, which basically shows that \(h[n]\) can be determined by solving the homogeneous equation with appropriate initial conditions. 1. Consider the system initially at rest and described by the equation \[y[n]-\frac{1}{2}y[n-1]\,=\,x[n].\] (P2.55-1) Assuming that \(x[n]=\delta[n]\), what is \(y[0]\)? What equation does \(h[n]\) satisfy for \(n\,\geq\,1\), and with what auxiliary condition? Solve this equation to obtain a closed-form expression for \(h[n]\). 2. Consider next the LTI system initially at rest and described by the difference equation \[y[n]-\frac{1}{2}y[n-1]\,=\,x[n]+2x[n-1].\] (P2.55-2) This system is depicted in Figure P2.55(a) as a cascade of two LTI systems that are initially at rest. Because of the properties of LTI systems, we can reverse the order of the systems in the cascade to obtain an alternative representation of the same overall system, as illustrated in Figure P2.55(b). From this fact, use the result of part (a) to determine the impulse response for the system described by eq. (P2.55-2). 3. Consider again the system of part (a), with \(h[n]\) denoting its impulse response. Show, by verifying that eq. (P2.55-3) satisfies the difference equation (P2.55-1), that the response \(y[n]\) to an arbitrary input \(x[n]\) is in fact given by the convolution sum \[y[n]\,=\,\sum_{m\,=\,-\infty}^{+\,\infty}h[n-m]x[m].\] (P2.55-3)

**(d)**: Consider the LTI system initially at rest and described by the difference equation

\[\sum_{k\,=\,0}^{N}a_{k}y[n\,-\,k]\,=\,x[n].\] (P2.55 - 4)

Assuming that \(a_{0}\neq 0\), what is \(y[0]\) if \(x[n]=\delta[n]\)? Using this result, specify the homogeneous equation and initial conditions that the impulse response of the system must satisfy.

Consider next the causal LTI system described by the difference equation

\[\sum_{k\,=\,0}^{N}a_{k}y[n\,-\,k]\,=\,\sum_{k\,=\,0}^{M}b_{k}x[n\,-\,k].\] (P2.55 - 5)

Express the impulse response of this system in terms of that for the LTI system described by eq. (P2.55 - 4).
**(e)**: There is an alternative method for determining the impulse response of the LTI system described by eq. (P2.55 - 5). Specifically, given the condition of initial rest, i.e., in this case, \(y[-N]=y[-N+1]=\ldots=y[-1]=0\), solve eq. (P2.55 - 5) recursively when \(x[n]\,=\,\delta[n]\) in order to determine \(y[0]\),..., \(y[M]\). What equation does \(h[n]\) satisfy for \(n\,\cong\,M\)? What are the appropriate initial conditions for this equation?
**(f)**: Using either of the methods outlined in parts (d) and (e), find the impulse responses of the causal LTI systems described by the following equations:

1. \(y[n]-y[n-2]\,=\,x[n]\)
2. \(y[n]-y[n-2]\,=\,x[n]+2x[n-1]\)
3. \(y[n]-y[n-2]\,=\,2x[n]-3x[n-4]\)
4. \(y[n]-(\sqrt{3}/2)y[n-1]+\frac{1}{4}y[n-2]\,=\,x[n]\)

**2.56**: In this problem, we consider a procedure that is the continuous-time counterpart of the technique developed in Problem 2.55. Again, we will see that the problem of determining the impulse response \(h(t)\) for \(t>0\) for an LTI system initially at rest and described by a linear constant-coefficient differential equation reduces to the problem of solving the homogeneous equation with appropriate initial conditions.

* Consider the LTI system initially at rest and described by the differential equation \[\frac{dy(t)}{dt}+2y(t)\,=\,x(t).\] (P2.56-1) Suppose that \(x(t)=\delta(t)\). In order to determine the value of \(y(t)\)_immediately after_ the application of the unit impulse, consider integrating eq. (P2.56-1) from \(t=0^{-}\) to \(t=0^{+}\) (i.e., from "just before" to "just after" the application of the impulse). This yields \[y(0^{+})-y(0^{-})+2\int_{0^{-}}^{0^{+}}y(\tau)\,d\tau\,=\,\int_{0^{-}}^{0^{+}} \delta(\tau)\,d\tau\,=\,1.\] (P2.56-2) Since the system is initially at rest and \(x(t)\,=\,0\) for \(t<0\), \(y(0^{-})\,=\,0\). To satisfy eq. (P2.56-2) we must have \(y(0^{+})=1\). Thus, since \(x(t)=0\) for \(t>0\), the impulse response of our system is the solution of the homogeneous differential equation \[\frac{dy(t)}{dt}+2y(t)\,=\,0\] with initial condition \[y(0^{+})\,=\,1.\] Solve this differential equation to obtain the impulse response \(h(t)\) for the system. Check your result by showing that \[y(t)\,=\,\int_{-\infty}^{+\infty}h(t-\tau)x(\tau)\,d\tau\] satisfies eq. (P2.56-1) for any input \(x(t)\).
* To generalize the preceding argument, consider an LTI system initially at rest and described by the differential equation \[\sum_{k\,=\,0}^{N}a_{k}\frac{d^{k}y(t)}{dt^{k}}\,=\,x(t)\] (P2.56-3) with \(x(t)\,=\,\delta(t)\). Assume the condition of initial rest, which, since \(x(t)\,=\,0\) for \(t<0\), implies that \[y(0^{-})\,=\,\frac{dy}{dt}(0^{-})\,=\,\ldots\,=\,\frac{d^{N-1}y}{dt^{N-1}}(0^{ -})\,=\,0.\] (P2.56-4) Integrate both sides of eq. (P2.56-3) once from \(t=0^{-}\) to \(t=0^{+}\), and use eq. (P2.56-4) and an argument similar to that used in part (a) to show that the
resulting equation is satisfied with

\[y(0^{+})\,=\,\frac{dy}{dt}(0^{+})\,=\,\ldots\,=\,\frac{d^{N-2}y}{dt^{N-2}}(0^{+})\,= \,0\] (P2.56- 5 \[a\] )

and

\[\frac{d^{N-1}y}{dt^{N-1}}(0^{+})\,=\,\frac{1}{a^{N}}.\] (P2.56- 5 \[b\] )

Consequently, the system's impulse response for \(t>0\) can be obtained by solving the homogeneous equation

\[\sum_{k\,=\,0}^{N}a_{k}\frac{d^{k}y(t)}{dt^{k}}\,=\,0\]

with initial conditions given by eqs. (P2.56-5).
**(c)**: Consider now the causal LTI system described by the differential equation

\[\sum_{k\,=\,0}^{N}a_{k}\frac{d^{k}y(t)}{dt^{k}}\,=\,\sum_{k\,=\,0}^{M}b_{k} \frac{d^{k}x(t)}{dt^{k}}.\] (P2.56- 6 )

Express the impulse response of this system in terms of that for the system of part (b). (_Hint:_ Examine Figure P2.56.)
**(d)**: Apply the procedures outlined in parts (b) and (c) to find the impulse responses for the LTI systems initially at rest and described by the following differential equations: (i) \(\frac{d^{2}y(t)}{dt^{2}}+3\frac{d\,y(t)}{dt}+2y(t)\,=\,x(t)\) (ii) \(\frac{d^{2}y(t)}{dt^{2}}+2\frac{d\,y(t)}{dt}+2y(t)\,=\,x(t)\) (e)
**(e)**: Use the results of parts (b) and (c) to deduce that if \(M\,\cong\,N\) in eq. (P2.56-6), then the impulse response \(h(t)\) will contain singularity terms concentrated at \(t\,=\,0\). In particular, \(h(t)\) will contain a term of the form

\[\sum_{r\,=\,0}^{M-N}\alpha_{r}u_{r}(t),\]

where the \(\alpha_{r}\) are constants and the \(u_{r}(t)\) are the singularity functions defined in Section 2.5.
**(f)**: Find the impulse responses of the causal LTI systems described by the following differential equations: (i) \(\frac{d\,y(t)}{dt}+2y(t)\,=\,3\frac{d\,x(t)}{dt}\,+\,x(t)\) (ii) \(\frac{d^{2}y(t)}{dt^{2}}+5\frac{d\,y(t)}{dt}+6y(t)\,=\,\frac{d^{3}x(t)}{dt^{3 }}+2\frac{d^{2}x(t)}{dt^{2}}+4\frac{d\,x(t)}{dt}\,+\,3x(t)\)
Consider a causal LTI system \(S\) whose input \(x[n]\) and output \(y[n]\) are related by the difference equation

\[y[n]\,=\,-ay[n-1]+b_{0}x[n]+b_{1}x[n-1].\]

**(a)**: Verify that \(S\) may be considered a cascade connection of two causal LTI systems \(S_{1}\) and \(S_{2}\) with the following input-output relationship:

\[S_{1}:y_{1}[n]\,=\,b_{0}x_{1}[n]+b_{1}x_{1}[n-1],\]

\[S_{2}:y_{2}[n]\,=\,-ay_{2}[n-1]+x_{2}[n].\]
**(b)**: Draw a block diagram representation of \(S_{1}\).
**(c)**: Draw a block diagram representation of \(S_{2}\).
**(d)**: Draw a block diagram representation of \(S\) as a cascade connection of the block diagram representation of \(S_{1}\) followed by the block diagram representation of \(S_{2}\).
**(e)**: Draw a block diagram representation of \(S\) as a cascade connection of the block diagram representation of \(S_{2}\) followed by the block diagram representation of \(S_{1}\).
**(f)**: Show that the two unit-delay elements in the block diagram representation of \(S\) obtained in part (e) may be collapsed into one unit-delay element. The resulting block diagram is referred to as a _Direct Form II_ realization of \(S\), while the block diagrams obtained in parts (d) and (e) are referred to as _Direct Form I_ realizations of \(S\).
**(a)**: Consider a causal LTI system \(S\) whose input \(x[n]\) and output \(y[n]\) are related by the difference equation

\[2y[n]-y[n-1]+y[n-3]\,=\,x[n]-5x[n-4].\]
**(a)**: Verify that \(S\) may be considered a cascade connection of two causal LTI systems \(S_{1}\) and \(S_{2}\) with the following input-output relationship:

\[S_{1}:2y_{1}[n]\,=\,x_{1}[n]-5x_{1}[n-4],\]

\[S_{2}:y_{2}[n]\,=\,\frac{1}{2}y_{2}[n-1]-\frac{1}{2}y_{2}[n-3]+x_{2}[n].\]
**(b)**: Draw a block diagram representation of \(S_{1}\).
**(c)**: Draw a block diagram representation of \(S_{2}\).
**(d)**: Draw a block diagram representation of \(S\) as a cascade connection of the block diagram representation of \(S_{1}\) followed by the block diagram representation of \(S_{2}\).
**(e)**: Draw a block diagram representation of \(S\) as a cascade connection of the block diagram representation of \(S_{2}\) followed by the block diagram representation of \(S_{1}\).
**(f)**: Show that the four delay elements in the block diagram representation of \(S\) obtained in part (e) may be collapsed to three. The resulting block diagram is referred to as a _Direct Form II_ realization of \(S\), while the block diagrams obtained in parts (d) and (e) are referred to as _Direct Form I_ realizations of \(S\).

2. Consider a causal LTI system \(S\) whose input \(x(t)\) and output \(y(t)\) are related by the differential equation \[a_{1}\frac{d\,y(t)}{dt}\,+\,a_{0}y(t)\,=\,b_{0}x(t)\,+\,b_{1}\frac{d\,x(t)}{dt}.\] 1. Show that \[y(t)\,=\,A\bigg{\uparrow}_{-\times}^{t}y(\tau)\,d\tau\,+\,Bx(t)\,+\,C\bigg{ \uparrow}_{-\times}^{t}x(\tau)\,d\tau,\] and express the constants \(A\), \(B\), and \(C\) in terms of the constants \(a_{0}\), \(a_{1}\), \(b_{0}\), and \(b_{1}\). 2. Show that \(S\) may be considered a cascade connection of the following two causal LTI systems: \[S_{1}:\,y_{1}(t)\,=\,Bx_{1}(t)\,+\,C\bigg{\uparrow}_{-\times}^{t}x(\tau)\,d\tau,\] \[S_{2}:\,y_{2}(t)\,=\,A\bigg{\uparrow}_{-\times}^{t}y_{2}(\tau)\,d\tau\,+\,x_{ 2}(t).\] 3. Draw a block diagram representation of \(S_{1}\). 4. Draw a block diagram representation of \(S_{2}\). 5. Draw a block diagram representation of \(S\) as a cascade connection of the block diagram representation of \(S_{1}

and express the constants \(A\), \(B\), \(C\), \(D\), and \(E\) in terms of the constants \(a_{0}\), \(a_{1}\), \(a_{2}\), \(b_{0}\), \(b_{1}\), and \(b_{2}\). 2. Show that \(S\) may be considered a cascade connection of the following two causal LTI systems: \[S_{1}:y_{1}(t) = Cx_{1}(t)+D\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\! \!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!

[MISSING_PAGE_EMPTY:91]

**Figure P2.62**

1. Determine the differential equation relating \(x(t)\) and \(y(t)\).
2. Show that the homogeneous solution of the differential equation from part (i) has the form \(e^{-at}\{K_{1}e^{jt}\) + \(K_{2}e^{-jt}\}\), and specify the value of \(a\).
3. Show that, since the force and displacement are restricted to be real, the natural response of the system is a decaying sinusoid.

2. A $100,000 mortgage is to be retired by _equal_ monthly payments of \(D\) dollars. Interest, compounded monthly, is charged at the rate of 12% per annum on the unpaid balance; for example, after the first month, the total debt equals \[\$100,000\,+\,\left(\frac{0.12}{12}\right)\$100,000\,=\,\$101,000.\] The problem is to determine \(D\) such that after a specified time the mortgage is paid in full, leaving a net balance of zero. **(a)**: To set up the problem, let \(y[n]\) denote the unpaid balance after the \(n\)th monthly payment. Assume that the principal is borrowed in month 0 and monthly payments begin in month 1. Show that \(y[n]\) satisfies the difference equation \[y[n]-\gamma y[n-1]\,=\,-D\quad n\,\geq\,1\] (P2.63-1) with initial condition \[y[0]\,=\,\$100,000,\] where \(\gamma\) is a constant. Determine \(\gamma\). **(b)**: Solve the difference equation of part (a) to determine \[y[n]\quad\mbox{for }n\,\geq\,0.\] (_Hint_: The particular solution of eq. (P2.63-1) is a constant \(Y\). Find the value of \(Y\), and express \(y[n]\) for \(n\,\geq\,1\) as the sum of particular and homogeneous solutions. Determine the unknown constant in the homogeneous solution by directly calculating \(y[1]\) from eq. (P2.63-1) and comparing it to your solution.) **(c)**: If the mortgage is to be retired in 30 years after 360 monthly payments of \(D\) dollars, determine the appropriate value of \(D\). **(d)**: What is the total payment to the bank over the 30-year period? **(e)**: Why do banks make loans?
2. One important use of inverse systems is in situations in which one wishes to remove distortions of some type. A good example of this is the problem of removing echoes from acoustic signals. For example, if an auditorium has a perceptible echo, then an initial acoustic impulse will be followed by attenuated versions of the sound at regularly spaced intervals. Consequently, an often-used model for this phenomenon is an LTI system with an impulse response consisting of a train of impulses, i.e., \[h(t)\,=\,\sum_{k\,=\,0}^{\infty}h_{k}\delta(t-kT).\] (P2.64-1) Here the echoes occur \(T\) seconds apart, and \(h_{k}\) represents the gain factor on the \(k\)th echo resulting from an initial acoustic impulse. **(a)**: Suppose that \(x(t)\) represents the original acoustic signal (the music produced by an orchestra, for example) and that \(y(t)\,=\,x(t)*h(t)\) is the actual signal that is heard if no processing is done to remove the echoes. In order to remove the distortion introduced by the echoes, assume that a microphone is used to sense \(y(t)\) and that the resulting signal is transduced into an electrical signal. We will also use \(y(t)\) to denote this signal, as it represents the electrical equivalent of the acoustic signal, and we can go from one to the other via acoustic-electrical conversion systems.

The important point to note is that the system with impulse response given by eq. (P2.64-1) is invertible. Therefore, we can find an LTI system with impulse response \(g(t)\) such that

\[y(t)*g(t)\;=\;x(t),\]

and thus, by processing the electrical signal \(y(t)\) in this fashion and then converting back to an acoustic signal, we can remove the troublesome echoes.

The required impulse response \(g(t)\) is also an impulse train:

\[g(t)\,=\,\sum_{k\,=\,0}^{\infty}g_{k}\delta(t\,-\,kT).\]

Determine the algebraic equations that the successive \(g_{k}\) must satisfy, and solve these equations for \(g_{0}\), \(g_{1}\), and \(g_{2}\) in terms of \(h_{k}\).
**(b)**: Suppose that \(h_{0}\,=\,1\), \(h_{1}\,=\,1/2\), and \(h_{i}\,=\,0\) for all \(i\,\geq\,2\). What is \(g(t)\) in this case?
**(c)**: A good model for the generation of echoes is illustrated in Figure P2.64. Hence, each successive echo represents a fed-back version of \(y(t)\), delayed by \(T\) seconds and scaled by \(\alpha\). Typically, \(0<\alpha<1\), as successive echoes are attenuated.

1. What is the impulse response of this system? (Assume initial rest, i.e., \(y(t)\,=\,0\) for \(t<0\) if \(x(t)\,=\,0\) for \(t<0\).)
2. Show that the system is stable if \(0<\alpha<1\) and unstable if \(\alpha>1\).
3. What is \(g(t)\) in this case? Construct a realization of the inverse system using adders, coefficient multipliers, and \(T\)-second delay elements.
**(d)**: Although we have phrased the preceding discussion in terms of continuous-time systems because of the application we have been considering, the same general ideas hold in discrete time. That is, the LTI system with impulse response

\[h[n]\,=\,\sum_{k\,=\,0}^{\infty}\;h_{k}\delta[n\,-\,kN]\]

is invertible and has as its inverse an LTI system with impulse response

\[g[n]\,=\,\sum_{k\,=\,0}^{\infty}g_{k}\delta[n\,-\,kN].\]

[MISSING_PAGE_EMPTY:95]

of LTI systems with \(\phi_{x,x}[n]\) as the input. (Do this by explicitly specifying the impulse response of each of the two systems.)
**(d)**: Let \(h[n]\,=\,x_{1}[n]\) in Figure P2.65, and let \(y[n]\) be the output of the LTI system with impulse response \(h[n]\) when the input \(x[n]\) also equals \(x_{1}[n]\). Calculate \(\phi_{xy}[n]\) and \(\phi_{y,y}[n]\) using the results of part (c).
**2.66**: Let \(h_{1}(t)\), \(h_{2}(t)\), and \(h_{3}(t)\), as sketched in Figure P2.66, be the impulse responses of three LTI systems. These three signals are known as _Walsh functions_ and are of considerable practical importance because they can be easily generated by digital logic circuitry and because multiplication by each of them can be implemented in a simple fashion by a polarity-reversing switch.

**Figure P2.66**:

**(a)**: Determine and sketch a choice for \(x_{1}(t)\), a continuous-time signal with the following properties:

(i) \(x_{1}(t)\) is real.

(ii) \(x_{1}(t)\,=\,0\) for \(t<0\).

(iii) \(|x_{1}(t)|\,\leq\,1\) for \(t\,\geq\,0\).

(iv) \(y_{1}(t)\,=\,x_{1}(t)*h(t)\) is as large as possible at \(t\,=\,4\).
**(b)**: Repeat part (a) for \(x_{2}(t)\) and \(x_{3}(t)\) by making \(y_{2}(t)\,=\,x_{2}(t)*h_{2}(t)\) and \(y_{3}(t)\,=\,x_{3}(t)*h_{3}(t)\) each as large as possible at \(t\,=\,4\).
**(c)**: What is the value of

\[y_{ij}(t)\,=\,x_{i}(t)*h_{j}(t),\,\,i\neq j\]

at time \(t\,=\,4\) for \(i\), \(j\,=\,1,2,3\)?The system with impulse response \(h_{i}(t)\) is known as the _matched filter_ for the signal \(x_{i}(t)\) because the impulse response is tuned to \(x_{i}(t)\) in order to produce the maximum output signal. In the next problem, we relate the concept of a matched filter to that of the correlation function for continuous-time signals.
2. The _cross-correlation function_ between two continuous-time real signals \(x(t)\) and \(y(t)\) is \[\phi_{x,y}(t)\,=\,\int_{-\infty}^{+\infty}\,x(t\,+\tau)y(\tau)\,d\tau.\] (P2.67-1) The _autocorrelation function_ of a signal \(x(t)\) is obtained by setting \(y(t)=x(t)\) in eq. (P2.67-1): \[\phi_{xx}(t)\,=\,\int_{-\infty}^{+\infty}\,x(t\,+\,\tau)x(\tau)\,d\tau.\] 1. Compute the autocorrelation function for each of the two signals \(x_{1}(t)\) and \(x_{2}(t)\) depicted in Figure P2.67 2. Let \(x(t)\) be a given signal, and assume that \(x(t)\) is of finite duration--i.e., that \(x(t)\,=\,0\) for \(t<0\) and \(t>T\). Find the impulse response of an LTI system so that \(\phi_{xx}(t\,-\,T)\) is the output if \(x(t)\) is the input. 3. The system determined in part (b) is a _matched filter_ for the signal \(x(t)\). That this definition of a matched filter is identical to the one introduced in Problem 2.66 can be seen from the following:Let \(x(t)\) be as in part (b), and let \(y(t)\) denote the response to \(x(t)\) of an LTI system with real impulse response \(h(t)\). Assume that \(h(t)=0\) for \(t<0\) and for \(t>T\). Show that the choice for \(h(t)\) that maximizes \(y(T)\), subject to the constraint that

\[\int_{0}^{T}h^{2}(t)dt\,=\,M,\text{ a fixed positive number, }\] (P2.67-2)

is a scalar multiple of the impulse response determined in part (b). [_Hint:_ Schwartz's inequality states that

\[\int_{b}^{a}u(t)v(t)dt\,\leq\left[\int_{a}^{b}u^{2}(t)dt\right]^{1/2}\left[ \int_{a}^{b}v^{2}(t)dt\right]^{1/2}\]

for any two signals \(u(t)\) and \(v(t)\). Use this to obtain a bound on y(T).]
**(d)**: The constraint given by eq. (P2.67-2) simply provides a scaling to the impulse response, as increasing \(M\) merely changes the scalar multiplier mentioned in part (c). Thus, we see that the particular choice for \(h(t)\) in parts (b) and (c) is matched to the signal \(x(t)\) to produce maximum output. This is an extremely important property in a number of applications, as we will now indicate.

In communication problems, one often wishes to transmit one of a small number of possible pieces of information. For example, if a complex message is encoded into a sequence of binary digits, we can imagine a system that transmits the information bit by bit. Each bit can then be transmitted by sending one signal, say, \(x_{0}(t)\), if the bit is a 0, or a different signal \(x_{1}(t)\) if a 1 is to be communicated. In this case, the receiving system for these signals must be capable of recognizing whether \(x_{0}(t)\) or \(x_{1}(t)\) has been received. Intuitively, what makes sense is to have two systems in the receiver, one tuned to \(x_{0}(t)\) and one tuned to \(x_{1}(t)\), where, by "tuned," we mean that the system gives a large output after the signal to which it is tuned is received. The property of producing a large output when a particular signal is received is exactly what the matched filter possesses.

In practice, there is always distortion and interference in the transmission and reception processes. Consequently, we want to maximize the difference between the response of a matched filter to the input to which it is matched and the response of the filter to one of the other signals that can be transmitted. To illustrate this point, consider the two signals \(x_{0}(t)\) and \(x_{1}(t)\) depicted in Figure P2.67(b). Let \(L_{0}\) denote the matched filter for \(x_{0}(t)\), and let \(L_{1}\) denote the matched filter for \(x_{1}(t)\).

1. Sketch the responses of \(L_{0}\) to \(x_{0}(t)\) and \(x_{1}(t)\). Do the same for \(L_{1}\).
2. Compare the values of these responses at \(t=4\). How might you modify \(x_{0}(t)\) so that the receiver would have an even easier job of distinguishing between \(x_{0}(t)\) and \(x_{1}(t)\) in that the response of \(L_{0}\) to \(x_{1}(t)\) and \(L_{1}\) to \(x_{0}(t)\) would both be zero at \(t\,=\,4\)?

**2.68**: Another application in which matched filters and correlation functions play an important role is radar systems. The underlying principle of radar is that an electro magnetic pulse transmitted at a target will be reflected by the target and will subsequently return to the sender with a delay proportional to the distance to the target. Ideally, the received signal will simply be a shifted and possibly scaled version of the original transmitted signal.

Let \(p(t)\) be the original pulse that is sent out. Show that

\[\phi_{pp}(0)\,=\,\max_{t}\phi_{pp}(t).\]

That is, \(\phi_{pp}(0)\) is the largest value taken by \(\phi_{pp}(t)\). Use this equation to deduce that, if the waveform that comes back to the sender is

\[x(t)\,=\,\alpha\,p(t-t_{0}),\]

where \(\alpha\) is a positive constant, then

\[\phi_{xp}(t_{0})\,=\,\max_{t}\phi_{xp}(t).\]

(_Hint:_ Use Schwartz's inequality.)

Thus, the way in which simple radar ranging systems work is based on using a matched filter for the transmitted waveform \(p(t)\) and noting the time at which the output of this system reaches its maximum value.

In Section 2.5, we characterized the unit doublet through the equation

\[x(t)*u_{1}(t)\,=\,\int_{-\infty}^{+\infty}x(t-\tau)u_{1}(\tau)\,d\tau\,=\,x^{ \prime}(t)\] (P2.69-1)

for any signal \(x(t)\). From this equation, we derived the relationship

\[\int_{-\infty}^{+\infty}g(\tau)u_{1}(\tau)\,d\tau\,=\,-g^{\prime}(0).\] (P2.69-2)

Show that eq. (P2.69-2) is an equivalent characterization of \(u_{1}(t)\) by showing that eq. (P2.69-2) implies eq. (P2.69-1). [_Hint:_ Fix \(t\), and define the signal \(g(\tau)\,=\,x(t-\tau)\).]

Thus, we have seen that characterizing the unit impulse or unit doublet by how it behaves under convolution is equivalent to characterizing how it behaves under integration when multiplied by an arbitrary signal \(g(t)\). In fact, as indicated in Section 2.5, the equivalence of these operational definitions holds for all signals and, in particular, for all singularity functions.

Let \(f(t)\) be a given signal. Show that

\[f(t)u_{1}(t)\,=\,f(0)u_{1}(t)\,-\,f^{\prime}(0)\delta(t)\]

by showing that both functions have the same operational definitions.

What is the value of

\[\int_{-\infty}^{\infty}x(\tau)u_{2}(\tau)\,d\tau?\]

Find an expression for \(f(t)u_{2}(t)\) analogous to that in part (b) for \(f(t)u_{1}(t)\).

**2.70**.: In analogy with continuous-time singularity functions, we can define a set of discrete-time signals. Specifically, let

\[u_{-1}[n] = u[n],\] \[u_{0}[n] = \delta[n],\] and \[u_{1}[n] = \delta[n]-\delta[n-1],\] and define \[u_{k}[n] = \underbrace{u_{1}[n]*u_{1}[n]*\cdots*u_{1}[n]}_{k\text{ times}},\,\,\,k>0\] and \[u_{k}[n] = \underbrace{u_{-1}[n]*u_{-1}[n]*\cdots*u_{-1}[n]}_{|k|\text{ times}},\,\,k<0.\] Note that \[x[n]*\delta[n] = x[n],\] \[x[n]*u[n] = \sum_{m\,=\,-\infty}^{\infty}x[m],\] and \[x[n]*u_{1}[n] = x[n]-x[n-1],\] **(a)**: What is \[\sum_{m\,=\,\infty}^{\infty}x[m]u_{1}[m]?\] **(b)**: Show that \[x[n]u_{1}[n] = x[0]u_{1}[n]-[x[1]-x[0]]\delta[n-1]\] \[= x[1]u_{1}[n]-[x[1]-x[0]]\delta[n].\] **(c)**: Sketch the signals \(u_{2}[n]\) and \(u_{3}[n]\). **(d)**: Sketch \(u_{-2}[n]\) and \(u_{-3}[n]\). **(e)**: Show that, in general, for \(k>0\), \[u_{k}[n] = \frac{(-1)^{n}k!}{n!(k-n)!}[u[n]-u[n-k-1]].\] (P2.70-1) (_Hint:_ Use induction. From part (c), it is evident that \(u_{k}[n]\) satisfies eq. (P2.70-1) for \(k\,=\,2\) and \(3\). Then, assuming that eq. (P2.70-1) satisfies \(u_{k}[n]\), write \(u_{k+1}[n]\) in terms of \(u_{k}[n]\), and show that the equation also satisfies \(u_{k+1}[n]\).)

**(f)**: Show that, in general, for \(k>0\),

\[u_{-k}[n]\,=\,\frac{(n+k-1)!}{n!(k-1)!}u[n].\] (P2.70-2)

(_Hint:_ Again, use induction. Note that

\[u_{-(k+1)}[n]-u_{-(k+1)}[n-1]\,=\,u_{-k}[n].\] (P2.70-3)

Then, assuming that eq. (P2.70-2) is valid for \(u_{-k}[n]\), use eq. (P2.70-3) to show that eq. (P2.70-2) is valid for \(u_{-(k+1)}[n]\) as well.)
**2.71.**: In this chapter, we have used several properties and ideas that greatly facilitate the analysis of LTI systems. Among these are two that we wish to examine a bit more closely. As we will see, in certain very special cases one must be careful in using these properties, which otherwise hold without qualification.
**(a)**: One of the basic and most important properties of convolution (in both continuous and discrete time) is associativity. That is, if \(x(t)\), \(h(t)\), and \(g(t)\) are three signals, then

\[x(t)*[g(t)*h(t)]\,=\,[x(t)*g(t)]*h(t)\,=\,[x(t)*h(t)]*g(t).\] (P2.71-1)

This relationship holds as long as all three expressions are well defined and finite. As that is usually the case in practice, we will in general use the associativity property without comments or assumptions. However, there are some cases in which it does _not_ hold. For example, consider the system depicted in Figure P2.71, with \(h(t)=u_{1}(t)\) and \(g(t)=u(t)\). Compute the response of this system to the input

\[x(t)\,=\,1\text{ for all }t.\]

Do this in the three different ways suggested by eq. (P2.71-1) and by the figure:

1. By first convolving the two impulse responses and then convolving the result with \(x(t)\).
2. By first convolving \(x(t)\) with \(u_{1}(t)\) and then convolving the result with \(u(t)\).
3. By first convolving \(x(t)\) with \(u(t)\) and then convolving the result with \(u_{1}(t)\)* Repeat part (a) for \[x(t)\,=\,e^{-t}\] and \[h(t)\,=\,e^{-t}u(t),\] \[g(t)\,=\,u_{1}(t)+\delta(t).\]
* Do the same for \[x[n]\,=\,\left(\frac{1}{2}\right)^{\!\!n},\] \[h[n]\,=\,\left(\frac{1}{2}\right)^{\!\!n}u[n],\] \[g[n]\,=\,\delta[n]-\frac{1}{2}\delta[n-1].\]

Thus, in general, the associativity property of convolution holds if and only if the three expressions in eq. (P2.71-1) make sense (i.e., if and only if their interpretations in terms of LTI systems are meaningful). For example, in part (a) differentiating a constant and then integrating makes sense, but the process of integrating the constant from \(t=-\infty\) and _then_ differentiating does not, and it is only in such cases that associativity breaks down.

Closely related to the foregoing discussion is an issue involving inverse systems. Consider the LTI system with impulse response \(h(t)=u(t)\). As we saw in part (a), there are inputs--specifically, \(x(t)=\) nonzero constant--for which the output of this system is infinite, and thus, it is meaningless to consider the question of inverting such outputs to recover the input. However, if we limit ourselves to inputs that do yield finite outputs, that is, inputs which satisfy

\[\left|\int_{-\infty}^{t}x(\tau)\,d\tau\right|<\infty,\] (P2.71-2)

then the system _is_ invertible, and the LTI system with impulse response \(u_{1}(t)\) is its inverse.
* Show that the LTI system with impulse response \(u_{1}(t)\) is _not_ invertible. (_Hint:_ Find two different inputs that both yield zero output for all time.) However, show that the system is invertible if we limit ourselves to inputs that satisfy eq. (P2.71-2). [_Hint:_ In Problem 1.44, we showed that an LTI system is invertible if no input other than \(x(t)=0\) yields an output that is zero for all time; are there two inputs \(x(t)\) that satisfy eq. (P2.71-2) and that yield identically zero responses when convolved with \(u_{1}(t)\)?] What we have illustrated in this problem is the following:
* If \(x(t)\), \(h(t)\), and \(g(t)\) are three signals, and if \(x(t)*g(t)\), \(x(t)*h(t)\), and \(h(t)*g(t)\) are _all_ well defined and finite, then the associativity property, eq. (P2.71-1), holds.
* Let \(h(t)\) be the impulse response of an LTI system, and suppose that the impulse response \(g(t)\) of a second system has the property \[h(t)*g(t)\,=\,\delta(t).\] (P2.71-3) Then, from (1), _for_ all inputs \(x(t)\) for which \(x(t)*h(t)\) and \(x(t)*g(t)\) are both well defined and finite, the two cascades of systems depicted in Figure P2.71 act as the identity system, and thus, the two LTI systems can be regarded as inverses of one another. For example, if \(h(t)=u(t)\) and \(g(t)=u_{1}(t)\), then, as long as we restrict ourselves to inputs satisfying eq. (P2.71-2), we can regard these two systems as inverses.

Therefore, we see that the associativity property of eq. (P2.71-1) and the definition of LTI inverses as given in eq. (P2.71-3) are valid, as long as all convolutions that are involved are finite. As this is certainly the case in any realistic problem, we will in general use these properties without comment or qualification. Note that, although we have phrased most of our discussion in terms of continuous-time signals and systems, the same points can also be made in discrete time [as should be evident from part (c)].

Let \(\delta_{\Delta}(t)\) denote the rectangular pulse of height \(\frac{1}{\Delta}\) for \(0<t\,\leq\,\Delta\). Verify that

\[\frac{d}{dt}\delta_{\Delta}(t)\,=\,\frac{1}{\Delta}[\delta(t)-\delta(t-\Delta)].\]

Show by induction that

\[u_{-k}(t)\,=\,\frac{t^{k-1}}{(k-1)!}u(t)\;\mbox{for}\;k\,=\,1,2,3\ldots\]
# Homework for week 1-2

```{note}
You are free to discuss these questions with your classmates and on
our class slack, but you must write your own solutions, including your
own source code.

All code should be uploaded to github classroom under the Assigment
"Homework (all weeks)" along with any analytic derivations, notes, etc.
```

## Differentiation

1. Following the example we did in class to find a difference
   approximation to the first derivative of $f(x)$, find an
   approximation to the _second derivative_ of $f(x)$.

   You should consider $f(x-h)$, $f(x)$, and $f(x+h)$.

   * What is the truncation error of this approximation?

   * Write a program to compute the second derivative of $f(x) =
     \sin(x)$ as a function of $h$ and print the absolute value of the
     error in your estimate compared to the analytic solution for
     several values of $h$.

   * Does the error converge as you expect?

2. Consider the function:

   $$f(x) = \sqrt{x^2 + 1} - 1$$

   When $x$ is small, roundoff error from the subtraction will
   dominate the answer.  In the limit of $x \rightarrow 0$, this
   expression takes the form:

   $$f(x) \sim \frac{1}{2} x^2$$

   * Show that by multiplying and dividing $f(x)$ by $\sqrt{x^2 + 1} +
     1$ you get an analytically equivalent expression for $f(x)$
     without any subtractions.

   * Write a program to evaluate $f(x)$ and the new version of $f(x)$
     for $x$ with the values `1.e-6`, `1.e-7`, `1.e-8`.

   * Which version is more accurate?

## Integration

1. In class we showed how Simpsons rule is derived from fitting a
   parabola to 3 points and integrating under the parabola.  Our
   composite method worked for an even number of intervals.  Now we'll
   consider the case where there is an odd number of intervals.

   If $N$ is odd, then we can use the standard composite Simpsons
   integration method for the first $N-1$ intervals (treating them in
   pairs).  For the very last interval, we need a new form of Simpsons
   rule.  Denote the last 3 points in the domain as $x_{N-2}$,
   $x_{N-1}$, $x_N$&mdash;we want to do the final integration over $x
   \in [x_{N-1}, x_N]$.

   a. Construct the form of the integral in this case by using the
      same parabolic interpolant, and evaluate it by integrating only
      over $[x_{N-1}, x_N]$.

   b. Write a general composite Simpsons rule integrator that works for
      even or odd $N$ (you can start with the code from class).

   c. Integrate
        
      $$I = \int_0^5 x \sin(2\pi x) dx$$

      from $[0, 5]$ using $N = \{3, 5, 9, 17, 33\}$ and compute the error compared
      to the analytic solution,

      $$I_\mathrm{analytic} = -\frac{5}{2\pi}$$

      How does the error converge?

2. The particles in an ideal gas a well-described by the Maxwell-Boltzmann distribution:

   $$n(p) d^3 p \rightarrow 4\pi n(p) p^2 dp = \frac{n_I}{(2\pi m_I k_B T)^{3/2}} e^{-p^2/(2m_I k_BT)} 4\pi p^2 dp$$

   The average velocity of this distribution, defined as:

   $$\langle v \rangle = \frac{1}{n_I} \int_0^\infty 4\pi n(p) p^2 \left (\frac{p}{m_I}\right ) dp$$

   Evaluate this integral numerically for a gas of protons ($m_I = m_p)$ and the conditions
   in the center of the Sun ($T = 1.5\times 10^7~\mathrm{K}$).

   Your integral should agree with the analytic result:

   $$\langle v \rangle = 2 \sqrt{\frac{2k_B T}{\pi m_I}}$$

   Be sure to vary the number of intervals in your numerical
   integration to show that you get an accurate answer (i.e., you
   converge).

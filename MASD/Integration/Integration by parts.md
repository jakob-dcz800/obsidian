Integrating the product rule for three multiplied functions gives a similar result:
 $\int _{a}^{b}uv\,dw\ =\ {\Big [}uvw{\Big ]}_{a}^{b}-\int _{a}^{b}uw\,dv-\int _{a}^{b}vw\,du$

# Integration by Parts

Integration by Parts is a special method of integration that is often useful when two functions are multiplied together, but is also helpful in other ways.

You will see plenty of examples soon, but first let us see the rule:

∫u v dx _=_ u∫v dx −∫u' (∫v dx) dx
- **u** is the function u(x)
- **v** is the function v(x)
- **u'** is the derivative of the function u(x)

![integration by parts general](https://www.mathsisfun.com/calculus/images/integral-parts-general.svg)

![integration by parts x cos(x) dx](https://www.mathsisfun.com/calculus/images/integral-parts-x-cosx.svg)

So we followed these steps:

- Choose u and v
- Differentiate u: u'
- Integrate v: ∫v dx
- Put u, u' and ∫v dx into: **u∫v dx −∫u' (∫v dx) dx**
- Simplify and solve  

In English we can say that **∫u v dx** becomes:
(u integral v) minus integral of (derivative u, integral v)
![integration by parts ln(x) on x^2](https://www.mathsisfun.com/calculus/images/integral-parts-lnx-on-x2.svg)
![integration by parts ln(x)](https://www.mathsisfun.com/calculus/images/integral-parts-lnx.svg)
![integration by parts e^x x](https://www.mathsisfun.com/calculus/images/integral-parts-ex-x.svg)
![integration by parts x e^x](https://www.mathsisfun.com/calculus/images/integral-parts-x-ex.svg)


The moral of the story: Choose **u** and **v** carefully!

Choose a **u** that gets simpler when you differentiate it and a **v** that doesn't get any more complicated when you integrate it.

A helpful rule of thumb is I LATE. Choose **u** based on which of these comes first:
- **I**: [Inverse trigonometric functions](https://www.mathsisfun.com/algebra/trig-inverse-sin-cos-tan.html) such as sin-1(x), cos-1(x), tan-1(x)
- **L**: [Logarithmic](https://www.mathsisfun.com/sets/function-logarithmic.html) functions such as ln(x), log(x)
- **A**: [Algebraic](https://www.mathsisfun.com/numbers/algebraic-numbers.html) functions such as x2, x3
- **T**: [Trigonometric functions](https://www.mathsisfun.com/sine-cosine-tangent.html) such as sin(x), cos(x), tan (x)
- **E**: [Exponential functions](https://www.mathsisfun.com/sets/function-exponential.html) such as ex, 3x
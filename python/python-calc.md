
# Table of Contents

1.  [python で 数式計算・微積分](#orgbfe3739)
    1.  [決まり事](#org875616f)
    2.  [関数の定義](#org07c6f47)
    3.  [定数 $` i, e, \pi `$](#org4de04f0)
    4.  [初等関数](#orgda8c3f0)
        1.  [三角関数の公式](#org408cd80)
    5.  [微分](#orgd99ca16)
    6.  [積分](#org72c65cd)

\#+author masayuki


<a id="orgbfe3739"></a>

# python で 数式計算・微積分

-   **参照:** [SymPy で微分積分・方程式の解 - 相対論の理解とその周辺](https://home.hirosaki-u.ac.jp/relativity/%E3%82%B3%E3%83%B3%E3%83%94%E3%83%A5%E3%83%BC%E3%82%BF%E6%BC%94%E7%BF%92/python-%E3%81%A7%E3%82%B3%E3%83%B3%E3%83%94%E3%83%A5%E3%83%BC%E3%82%BF%E6%BC%94%E7%BF%92/sympy-%E3%81%A7%E5%BE%AE%E5%88%86%E7%A9%8D%E5%88%86%E3%83%BB%E6%96%B9%E7%A8%8B%E5%BC%8F%E3%81%AE%E8%A7%A3/)


<a id="org875616f"></a>

## 決まり事

-   sympy (記号計算) パッケージの機能を使う [SymPy 1.13.1 documentation](https://docs.sympy.org/latest/index.html)
-   sympy の一文字変数 [abc - SymPy 1.13.1 documentation](https://docs.sympy.org/latest/modules/abc.html)

    
    from sympy import *
    from sympy.abc import *


<a id="org07c6f47"></a>

## 関数の定義

    
    def f(x):
        return x**2+2*x+1
    
    print(f(x))
    print(factor(f(x)))

    x**2 + 2*x + 1
    (x + 1)**2


<a id="org4de04f0"></a>

## 定数 $` i, e, \pi `$

    
    from sympy import I, pi, E

    
    print(E**(I*pi) + 1)

    0


<a id="orgda8c3f0"></a>

## 初等関数

    print(sin(pi/6))
    print(cos(pi/6))
    print(sqrt(x**2))
    print(log(sqrt(x)))
    print(exp(log(sqrt(x))))
    print(log(E**2))

    1/2
    sqrt(3)/2
    sqrt(x**2)
    log(sqrt(x))
    sqrt(x)
    2


<a id="org408cd80"></a>

### 三角関数の公式

    print (expand(sin(x+y), trig=True))
    print (expand(cos(x+y), trig=True))
    print (expand(tan(x+y), trig=True))
    
    print (expand(sin(2*x), trig=True))
    print (expand(cos(2*x), trig=True))
    print (expand(tan(2*x), trig=True))
    
    print (expand(sin(3*x), trig=True))
    print (expand(cos(3*x), trig=True))
    print (expand(tan(3*x), trig=True))

    sin(x)*cos(y) + sin(y)*cos(x)
    -sin(x)*sin(y) + cos(x)*cos(y)
    tan(x)/(-tan(x)*tan(y) + 1) + tan(y)/(-tan(x)*tan(y) + 1)
    2*sin(x)*cos(x)
    2*cos(x)**2 - 1
    2*tan(x)/(1 - tan(x)**2)
    -4*sin(x)**3 + 3*sin(x)
    4*cos(x)**3 - 3*cos(x)
    -tan(x)**3/(1 - 3*tan(x)**2) + 3*tan(x)/(1 - 3*tan(x)**2)


<a id="orgd99ca16"></a>

## 微分

    
    print(
        Eq (
            diff(x**3 + 5*x + 2, x, evaluate=False),
            diff(x**3 + 5*x + 2, x)
        )
    )

    Eq(Derivative(x**3 + 5*x + 2, x), 3*x**2 + 5)

[Simplify - SymPy 1.13.1 documentation](https://docs.sympy.org/latest/modules/simplify/simplify.html#module-sympy.simplify.hyperexpand)

    
    print(
        diff(log(x+sqrt(x**2+1)))
    )
    
    print(
        simplify (
            diff(log(x+sqrt(x**2+1))),
            rational=True
        )
    )

    (x/sqrt(x**2 + 1) + 1)/(x + sqrt(x**2 + 1))
    1/sqrt(x**2 + 1)


<a id="org72c65cd"></a>

## 積分

    print (
        integrate(x**2*cos(x) + 2*x*sin(x), x)
    )

    x**2*sin(x)

    print (
        integrate(1/(x**2+1),x)
    )
    
    print (
        integrate(1/(x**3+1),x)
    )
    
    print (
        integrate(1/(x**6+1),x)
    )
    
    print (
        diff(
            integrate(1/(x**2+1),x)
        ,x)
    )
    
    print (
        simplify(
        diff(
            integrate(1/(x**3+1),x),
            x
        ))
    )
    
    print (
        simplify(
        diff(
            integrate(1/(x**6+1),x),
            x
        ))
    )

    atan(x)
    log(x + 1)/3 - log(x**2 - x + 1)/6 + sqrt(3)*atan(2*sqrt(3)*x/3 - sqrt(3)/3)/3
    -sqrt(3)*log(x**2 - sqrt(3)*x + 1)/12 + sqrt(3)*log(x**2 + sqrt(3)*x + 1)/12 + atan(x)/3 + atan(2*x - sqrt(3))/6 + atan(2*x + sqrt(3))/6
    1/(x**2 + 1)
    1/(x**3 + 1)
    1/(x**6 + 1)


(Continued from Part A...)

### Perifocal Coordinates
Before we move on, let's come up with a system of describing the position of a planet. A natural way of describing that would be to put the Sun at the origin, and describe its coordinates with the $xy$-plane as the orbital plane. These coordinates, defined with the positive $x$ axis towards the periapsis, are called the [**perifocal coordinates**](https://en.wikipedia.org/wiki/Perifocal_coordinate_system).

<img align="left" src="https://github.com/CitruzSquared/essays/assets/23460281/84b9f828-3fc9-4dd8-a3a8-dda6d9f7c572" width="350"/> In the diagram, the orbit of a planet $A$ is shown, where $O$, the origin, is the focus, and therefore the location of the Sun, and $P$ is the perihelion. The angle $POA$ is known as the [*true anomaly*](https://en.wikipedia.org/wiki/True_anomaly), and is denoted $\nu$. This makes it such that the true anomaly is essentially $\theta$ in the polar equation for the ellipse. (True anomaly is measured in the direction of the orbit, which in this case we assume is counterclockwise.)

Using the true anomaly, the position $\left(x, y\right)$ of the planet can be fully described as:
```math
\displaylines{
\begin{align}
x_{\text{perifocal}} &= r\cos\left(\nu\right) \\
y_{\text{perifocal}} &= r\sin\left(\nu\right) \\
\therefore \nu &= \arctan\left(y_{\text{perifocal}}, x_{\text{perifocal}}\right)
\end{align}\tag{2.12}
}
```
Just like in polar coordinates.

Therefore, $r$ here is given by equation $2.7$:
```math
\begin{align}
r = \frac{a\left(1 - e^2\right)}{1 + e\cos\left(\nu\right)}.
\end{align}\tag{2.13}
```
Which we can now use to give exact coordinates for $x$ and $y$.

However, while the true anomaly represents the most intuitive and most physically grounded angle, there is another way to think of things, that will prove to be easier to deal with.

<img align="left" src="https://github.com/CitruzSquared/essays/assets/23460281/8f9a0758-fcdf-4de7-a4fc-80249d57a4fc" width="350"/> In this diagram, we have drawn a circle with radius $a$ over the ellipse. We then projected the position of the planet $A$ onto this circle and called it $A'$. Thus a new angle is defined: $PCA'$ defines the [*eccentric anomaly*](https://en.wikipedia.org/wiki/Eccentric_anomaly), and is denoted $E$.

Using $E$, the coordinates of $A$ will be much easier to determine later. Putting $C$ as the origin,
```math
\sin \left(E\right) = \frac{x}{a}
```
and because $x^2/a^2 + y^2/b^2 = 1$,
```math
\begin{align}
\left(\frac{y}{b}\right)^2 &= 1 - \left(\frac{x}{a}\right)^2\\
&= 1 - \sin^2 \left(E\right)\\
\therefore \frac{y}{b} &= \cos \left(E\right)
\end{align}
```
<br/>
<br/>

Therefore,
```math
\displaylines{
\begin{align}
x &= a\sin \left(E\right)\\
y &= b\cos \left(E\right)\\
\end{align}
} 
```
Now, translating the origin to the focus $O$,
```math
\displaylines{
\begin{align}
x_{\text{perifocal}} &= a\sin \left(E\right) - ae\\
\\
y_{\text{perifocal}} &= b\cos \left(E\right)\\
&= a\sqrt{1 - e^2}\sin \left(E\right)
\end{align}\tag{2.14}
} 
```
Additionally, by the Pythagorean theorem then,
```math
\begin{align}
r^2 &= \left(a\cos \left(E\right) - ae\right)^2 + \left(a\sqrt{1 - e^2}\sin \left(E\right)\right)^2\\
&= a^2 \cos^2 \left(E\right) - 2a^2e\cos \left(E\right) + a^2e^2 + a^2\left(1 - e^2\right) \sin^2 \left(E\right)\\
&= a^2 \cos^2 \left(E\right) - 2a^2e\cos \left(E\right) + a^2e^2 + \left(a^2 - a^2e^2\right)\left(1 - \cos^2 \left(E\right)\right) \\
&= a^2 \cos^2 \left(E\right) - 2a^2e\cos \left(E\right) + a^2e^2 + a^2 - a^2\cos^2 \left(E\right) - a^2e^2 + a^2e^2\cos^2 \left(E\right) \\
&= a^2 - 2a^2e\cos \left(E\right) + a^2e^2\cos^2 \left(E\right)\\
&= \left(a - ae\cos \left(E\right)\right)^2\\
\therefore r &= a\left(1 - e\cos \left(E\right)\right)
\end{align}\tag{2.15}
```
Let's now relate $\nu$ with $E$. Putting $C$ as the origin again,
```math
\begin{align}
\cos \left(E\right) &= \frac{x}{a} = \frac{ae + r \cos \left(\nu\right)}{a} = e\left(1 - e\cos \left(E\right)\right)\cos\left(\nu\right)\\
\therefore \cos \left(E\right) &= \frac{e + \cos\left(\nu\right)}{1 + e\cos\left(\nu\right)}
\end{align}\tag{2.16}
```
This formula for $E$ is ambiguous. If $\nu > 180\degree$, we need to take the negative arccosine value.

The true anomaly can be obtained from the eccentric anomaly by getting $x_{\text{perifocal}}$ and $y_{\text{perifocal}}$ first, then calculating $\arctan\left(y_{\text{perifocal}}, x_{\text{perifocal}}\right)$ (equation $2.12$).

### Kepler's Second Law
We have discussed Kepler's first and third laws. Now let us tackle his second law, which states that the area sweeped out by a planet over a unit time must stay constant.

The area of a sector with radius $r$ and central angle $\theta$ is given by:
```math
S = \frac{1}{2}r^2 \theta
```
And therefore the area sweeped out by a planet over a small increment $d\nu$ of true anomaly is:
```math
dS = \frac{1}{2} r^2 d\nu
```
And therefore the area sweeped out per unit time is
```math
\frac{dS}{dt} = \frac{r^2}{2}\frac{d\nu}{dt}
```
And this must stay constant.\
Because the area of an ellipse is $\pi a b$,
```math
T \frac{dS}{dt} = T\frac{r^2}{2}\frac{d\nu}{dt} = \pi a b
```
where $T$ is the orbital period.\
Therefore:
```math
r^2 \frac{d\nu}{dt} = \frac{2\pi a b}{T} 
```
now, denoting $2\pi/T$ as $n$ (this quantity is called the [mean motion](https://en.wikipedia.org/wiki/Mean_motion)), we obtain:
```math
\begin{align}
r^2 \nu' = nab = na^2\sqrt{1 - e^2}
\end{align}\tag{2.17}
```

Now, recall equation $2.15$:
```math
r = a\left(1 - e\cos \left(E\right)\right)
```
Differentiating both sides with respect to time gives us:
```math
\begin{align}
r' = ae\sin\left(E\right)E'
\end{align}\tag{2.18}
```
Now recall equation $2.13$:
```math
\begin{align}
r &= \frac{a\left(1 - e^2\right)}{1 + e\cos\left(\nu\right)} \\
\therefore\frac{1}{r} &= \frac{1 + e\cos\left(\nu\right)}{a\left(1 - e^2\right)}
\end{align}
```
Differentiating both sides of this equation we obtain:
```math
\begin{align}
-\frac{r'}{r^2} = -\frac{e \sin \left(\nu\right) \nu'}{a\left(1 - e^2\right)} \\
\therefore r' = \frac{e\sin\left(\nu\right)r^2\nu'}{a\left(1 - e^2\right)}
\end{align}\tag{2.19}
```
Now we substitute equation $2.17$ in equation $2.19$:
```math
r' = \frac{nae\sin\left(\nu\right)}{\sqrt{1 - e^2}}
```
Equating this with equation $2.18$:
```math
\begin{align}
ae\sin\left(E\right)E' &= \frac{nae\sin\left(\nu\right)}{\sqrt{1 - e^2}}\\
E' &= \frac{n\sin\left(\nu\right)}{\sqrt{1 - e^2}\sin\left(E\right)}
\end{align}
```
But $\sqrt{1 - e^2}\sin\left(E\right)$ is just $y_{\text{perifocal}}/a$ by equation $2.14$, and $y_{\text{perifocal}} = r\sin\left(\nu\right)$ by equation $2.12$, so:
```math
\begin{align}
E' &= \frac{n\sin\left(\nu\right)}{r\sin\left(\nu\right)/a}\\
\therefore rE' &= na
\end{align}
```
Now, substituting equation $2.15$ for $r$:
```math
\left(1 - e\cos \left(E\right)\right) E' = n
```
Integrating over time on both sides yields:
```math
E - e\sin\left(E\right) = nt + c.
```
If we measure $t$ from the time of periapsis, then when $t = 0$, $E - e\sin\left(E\right) = 0$ since $E = 0$ at periapsis. Therefore $c. = 0$.\
Let's also denote $nt$ as $M$. We call this quantity the [*mean anomaly*](https://en.wikipedia.org/wiki/Mean_anomaly):
```math
\begin{align}
M = nt = \frac{2\pi}{T}\cdot t
\end{align}\tag{2.20}
```
Now the equation becomes:
```math
\begin{align}
M = E - e\sin \left(E\right)
\end{align}\tag{2.21}
```
Which is known as [**Kepler's Equation**](https://en.wikipedia.org/wiki/Kepler%27s_equation). This equation allows us to relate $E$ and $M$, thus relating $E$ and $t$, which allows us to finally calculate the motion of the planets. Keep in mind that we **must use radians** for $M$ and $E$.

#### Example 2.3
<div align="center">
<table>
<tbody>
<td align="center">
<img width="2000" height="0"><br>
The orbital period of the Earth $T = 365.2422\text{ dy}$, and the eccentricity of its orbit is $0.0167$. <br/>
Additionally, when it is at periapsis, its heliocentric ecliptic longitude is $102\degree\:56'\:49.9''$. <br/>
Given that the time of perihelion in $2024$ was $\text{January 3, }2024\: 00:38$, <br/>
calculate the time of Spring Equinox in the Northern Hemisphere in $2024$.
<img width="2000" height="0">
</td>
</tbody>
</table>
</div>

Because ecliptic coordinates are based on the Earth's orbital plane, it effectively is equal to the Earth's perifocal coordinate frame, except that the $x$-axis is rotated from the direction of perihelion to the direction of Aries. Therefore, we can use our perifocal equations in the ecliptic frame without much trouble.

Spring Equinox in the Northern Hemisphere is defined as $\lambda_{\text{Sun, Geocentric}} = 0\degree$, therefore (by equation $1.5$) it occurs when $\lambda_{\text{Earth, Heliocentric}} = 180\degree$. Thus, the true anomaly of the Earth at the time of Northern Spring Equinox is:
```math
\begin{align}
\nu &= 180\degree - 102\degree\:56'\:49.9''\\
&= 77\degree\:3'\:50.1''
\end{align}
```
Now, by equation $2.16$ ($\nu < 180\degree$):
```math
\begin{align}
\cos \left(E\right) &= \frac{e + \cos\left(\nu\right)}{1 + e\cos\left(\nu\right)}\\
&= \frac{0.0167 + \cos\left(77\degree\:3'\:50.1''\right)}{1 + 0.0167\cos\left(77\degree\:3'\:50.1''\right)}\\
&= 0.239855411\\
\therefore E &= 1.3285794 \text{ rad}
\end{align}
```
Now, by Kepler's equation (equation $2.21$):
```math
\begin{align}
M &= E - e\sin \left(E\right)\\
&= 1.3285794 - 0.0167 \sin \left(1.3285794\right)\\
&= 1.3123669 \text{ rad}
\end{align}
```
Therefore, by the definition of $M$ (equation $2.20$):
```math
\begin{align}
M &= \frac{2\pi}{T}\cdot t\\
\therefore t &= \frac{TM}{2\pi}\\
&=\frac{365.2422\text{ dy} \cdot 1.3123669}{2\pi}\\
&= 76 \text{ dy}\:6h\:55m
\end{align}
```
$76\text{ dy}$ $6h$ $55m$ after $\text{January 3, }2024$ $00:38$ is $\text{March 19, }2024$ $07:33$.\
Comparing to the true time ($\text{March 20, }2024$ $03:07$), we can see that we are close. The discrepancy comes from rounding error and the fact that the motion of the Earth is not a true two body problem.\
$\blacksquare$

However what we really want is the reverse operation of example $2.3$: going from a specific time to a location. Sounds easy: $M$ is very easy to calculate, and $E$ gives us the exact coordinates $\left(x, y\right)$, and we have a relation between $M$ and $E$ by [Kepler's equation](https://en.wikipedia.org/wiki/Kepler%27s_equation) (equation $2.21$)!\
Unfortunately, Kepler's equation
```math
M = E - e\sin \left(E\right)
```
is [transcendental](https://en.wikipedia.org/wiki/Transcendental_function), which means $E$ cannot be solved for $M$ analytically.\
However, there is hope! We can solve for $E$ [*numerically*](https://en.wikipedia.org/wiki/Numerical_analysis). 

First we rearrange the equation:
```math
E - e \sin \left(E\right) - M = 0
```
We then define $f$ as a function of $E$ to be $f\left(E\right) = E - e \sin \left(E\right) - M$. Then we juse need to find the root of $f\left(E\right) = 0$.\
We use the [Newton–Raphson method](https://en.wikipedia.org/wiki/Newton%27s_method), given by the iterative equation
```math
\begin{align}
x_{n + 1} = x_n - \frac{f\left(x_n\right)}{f'\left(x_n\right)}.
\end{align}\tag{2.22}
```
Clearly, we need to find $f'\left(E\right)$.
```math
\frac{df}{dE} =  1 - e \cos \left(E\right)
```
By plugging all the values into equation $2.22$, we obtain:
```math
\begin{align}
E_{n + 1} = E_n - \frac{E_n - e\sin\left(E_n\right) - M}{1 - e\cos\left(E_n\right)}
\end{align}\tag{2.23}
```
which we can use to iteratively obtain better and better approximations of $E$, which we can then use to find the coordinates of the planet.
#### Example 2.4
<div align="center">
<table>
<tbody>
<td align="center">
<img width="2000" height="0"><br>
The Earth has orbital period $T = 365.2422\text{ dy}$, its orbit has semi-major axis $a = 149.6 \text{ Gm}$, and its eccentricity $e = 0.0167$. <br/>
Find the heliocentric ecliptic longitude of the Earth at $t = 76 \text{ dy}\:6h\:55m$ past periapsis, <br/>
given that when the Earth at periapsis, its heliocentric ecliptic longitude is $102\degree\:56'\:49.9''$
<img width="2000" height="0">
</td>
</tbody>
</table>
</div>

Due to the definition of the ecliptic coordinate frame, we can use our perifocal equations in it without much trouble. (See example $2.3$.)\
We first calculate $M$ by equation $2.20$:
```math
\begin{align}
M &= \frac{2\pi}{365.2422\text{ dy}} \cdot 76 \text{ dy}\:6h\:55m \\
&= 1.3123669\text{ rad}
\end{align}
```
We now perform the Newton iteration. We first guess $E_1 = M$, and obtain $E_2$ by equation $2.23$.
```math
\begin{align}
E_2 &= M - \frac{M - e\sin\left(M\right) - M}{1 - e\cos\left(M\right)}\\
&= 1.3285815 \text{ rad}
\end{align}
```
We perform it again, now using $E_2$ for $E_n$.
```math
\begin{align}
E_3 &= E_2 - \frac{E_2 - e\sin\left(E_2\right) - M}{1 - e\cos\left(E_2\right)}\\
&= 1.3285794 \text{ rad}
\end{align}
```
Here is the table of repetitions:
```math
\begin{array}{ccc}\hline n & & E_n \\ \hline
1 & & 1.3123669 \\
2 & & 1.3285815 \\
3 & & 1.3285794 \\
4 & & 1.3285794 \\ \hline
\end{array}
```
As we can see, $E$ has quickly converged onto $1.3285794\text{ rad}$. In general it can be assumed that $E_4$ or $E_5$ will be enough.\
We can now calculate $\left(x, y\right)$ with equation $2.14$:
```math
\begin{align}
x_{\text{perifocal}} &= a \cos \left(E\right) - ae\\
&= 149.6 \cos\left(1.3285794\right) - 149.6 \cdot 0.0167 \\
&= 33.384 \text{ Gm}\\
\\
y_{\text{perifocal}} &= b \sin \left(E\right)\\
&= a\sqrt{1 - e^2} \sin \left(E\right)\\
&= 149.6 \sqrt{1 - 0.0167^2} \sin\left(1.3285794\right)\\
&= 145.213 \text{ Gm}
\end{align}
```
Then, by equation $2.12$, the true anomaly is:
```math
\arctan\left(145.213, 33.384\right) = 77\degree\:3'\:10.27''
```
Which, when added with the ecliptic longitude of the periapsis $102\degree\:56'\:49.9''$ gives:
```math
\lambda_{\text{Earth, Heliocentric}} = 180\degree\:17''
```
Which agrees with example $2.3$. (The $17''$ is due to stray rounding error.)\
$\blacksquare$

#### Proof of Kepler's Second Law
<div align="center">
<table>
<tbody>
<td align="center">
<img width="2000" height="0"><br>
Prove that the area of an orbit sweeped out by a planet per unit time is constant. <br/>
Disclaimer: the proof is mathematically dense and there is no need to know it. <br/>
It is advised for the average reader to skip this investigation.
<img width="2000" height="0">
</td>
</tbody>
</table>
</div>

<img align="left" src="https://github.com/CitruzSquared/essays/assets/23460281/9bc1d922-bfd0-4609-9013-0a1171e846c5" width="200"/> In this diagram, the motion of a planet $P$ has been depicted. $\textbf{r}$ is its position vector, and $d\textbf{r}$ is the small change in position over a small unit time $dt$. The angle between $\textbf{r}$ and $d\textbf{r}$ has been called $s$.

The area of this triangle $dA$ well represents the small area that is sweeped out by the planet over a small time $dt$. This area is given by:
```math
dA = \frac{1}{2}rdr\sin\left(s\right)
```
where $r$ and $dr$ are the magnitudes of $\textbf{r}$ and $d\textbf{r}$ respectively. This can be written in vector form as:
```math
d\textbf{A} = \frac{1}{2}\textbf{r}\times d\textbf{r}
```
dividing by $dt$ to get the area swept out per unit time,
```math
\frac{d\textbf{A}}{dt} = \frac{1}{2}\textbf{r}\times \frac{d\textbf{r}}{dt}
```
Kepler's second law states that this quantity $d\textbf{A}/dt$ must be constant, which means that $d^2\textbf{A}/dt^2 = \textbf{0}$.\
Calculating $d^2\textbf{A}/dt^2 = 0$:
```math
\begin{align}
\frac{d^2\textbf{A}}{dt^2} &= \frac{1}{2}\left(\frac{d\textbf{r}}{dt}\times\frac{d\textbf{r}}{dt} + \textbf{r}\times \frac{d^2\textbf{r}}{dt^2}\right)\\
&= \frac{1}{2}\left(\textbf{v}\times\textbf{v} + \textbf{r}\times\textbf{a}\right)\\
&= \frac{1}{2}\textbf{r}\times\textbf{a}
\end{align}
```
where $\textbf{v}$ and $\textbf{a}$ are the velocity and acceleration of $P$ respectively.\
However, it has been shown previously (in the proof of Kepler's first law) that $\textbf{r}$ is parallel to $\textbf{a}$ and therefore
```math
\frac{d^2\textbf{A}}{dt^2} = \frac{1}{2}\textbf{r}\times\textbf{a} = \textbf{0}.
```
Which proves Kepler's second law.\
$\blacksquare$

### Orientation of Orbits in 3D Space
(Continued in Part C...)

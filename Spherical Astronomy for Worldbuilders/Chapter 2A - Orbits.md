## II. Orbits

Unlike stars that have fixed coordinates, planets orbit the Sun, and therefore move around in the sky. (In fact, this is where the word "planet" comes from.) Let us study the motion and position of the planets. The most accurate way to calculate the motion of the planets is with a numerical integrator of the equations of motion, but this can be extremely difficult to make such that it guarantees accuracy even in the very long run. In this chapter, we will learn of ways to solve for the motion of the planets *without* an integrator.

### Newton and Kepler
All planets in space obey [Newton's law of gravitation](https://en.wikipedia.org/wiki/Newton%27s_law_of_universal_gravitation). \
It tells us:
```math
\begin{align}
\textbf{F} = -\frac{G M m}{r^3} \cdot \textbf{r}
\end{align}\tag{2.1}
```
where $\textbf{F}$ is the gravitational force on the planet, $G$ is the [*gravitational constant*](https://en.wikipedia.org/wiki/Gravitational_constant), which is $6.674\cdot10^{-11}\text{ m}^3\text{ kg}^{-1}\text{ s}^{-2}$ in SI units, $M$ and $m$ are the masses of the Sun and the planet respectively, and $\textbf{r}$ and $r$ are the position vector of the planet and its magnitude (the distance between the Sun and the planet) respectively.

Turns out this equation has already been solved for the most part, and the problem of the planets in motion around the Sun, or the Moon in orbit around the Earth, can be modeled as an ideal Newtonian [two body problem](https://en.wikipedia.org/wiki/Two-body_problem). Thus they obey [Kepler's laws of planetary motion](https://en.wikipedia.org/wiki/Kepler's_laws_of_planetary_motion):
- 1. Planets orbit in an [ellipse](https://en.wikipedia.org/wiki/Ellipse) with the Sun at a [*focus*](https://en.wikipedia.org/wiki/Focus_(geometry)).
  * Thus there is a point in the orbit where it is closest to the Sun and a point where it is furthest away. These two points are diametrically opposite each other.
- 2. Planets in orbit "sweep out" the same area per unit time.
  * This tells us that the object travels faster when it is in the part of its orbit that is closer to the primary, and slower when it is further away.
- 3. The square of the orbital period ($T$) of the planet is proportional to the cube of the *semi-major axis* of the orbit of the planet.

### Kepler's First Law
Since Kepler's first law states that all orbits are ellipses, let us quickly investigate the ellipse.

<img align="left" src="https://github.com/CitruzSquared/essays/assets/23460281/bb81dcca-4a3c-4ad7-9f70-6f4eea3af818" width="350"/> In the diagram is an ellipse with center $O$. The distance $OP$ is known as the semi-major axis and is denoted $a$. ($1$ Astronomical Unit (AU) is defined by the semi-major axis of the Earth's orbit!) The distance $OB$ is known as the semi-minor axis and is denoted $b$. The ellipse can be represented algebraically using these two measures: the ellipse is the locus of all points satisfying the equation
```math
\begin{align}
\frac{x^2}{a^2} + \frac{y^2}{b^2} = 1.
\end{align}\tag{2.2}
```

Point $F$ is located at the point where the length $BF = a$. This point $F$ is known as the [focus](https://en.wikipedia.org/wiki/Focus_(geometry)) of an ellipse and this is where the Sun lies in a planetary orbit. 

<br/>

The points $P$ and $A$ then are the points closest to and furthest away from the focus, and are known as the *periapsis* and *apoapsis* respectively, and [*apses*](https://en.wikipedia.org/wiki/Apsis) (singular *apsis*) collectively. When the primary object (the object at the focus) is the Sun, these points can be called the *perihelion* and *apohelion*, and when the primary object is the Earth, they can be called the *perigee* and *apogee*.

The amount of "squishing" of an ellipse is given by the quantity $c/a$ where $c$ is the distance $OF$. This quantity is known as the [*eccentricity*](https://en.wikipedia.org/wiki/Eccentricity_(mathematics)) and is denoted $e$. When the eccentricity is $0$, the ellipse becomes a perfect circle, and when the eccentricity is greater than or equal to $1$, the ellipse breaks and becomes a [parabola](https://en.wikipedia.org/wiki/Parabola) or [hyperbola](https://en.wikipedia.org/wiki/Hyperbola). 

Because $BF = a$, $c^2 = a^2 - b^2$, and $e$ can also be written:
```math
\begin{align}
e^2 = \frac{a^2-b^2}{a^2} = 1 - \frac{b^2}{a^2}.
\end{align}\tag{2.3}
```

The periapsis distance is then
```math
\begin{align}
FP &= a - c = a - ae\\
&= a\left(1 - e\right)
\end{align}\tag{2.4}
```
and the apoapsis distance is
```math
\begin{align}
FA &= a + c = a + ae\\
&= a\left(1 + e\right)
\end{align}\tag{2.5}
```
Finding the semi-major axis length given the periapsis and apoapsis distances is trivial:
```math
\begin{align}
a = \frac{1}{2} \left(FA + FP\right)
\end{align}\tag{2.6}
```

#### Example 2.1
<div align="center">
<table>
<tbody>
<td align="center">
<img width="2000" height="0"><br>
Given that the semi-major axis of the orbit of the Earth is $149\:598\:023 \text{ km}$, and its eccentricity is $0.0167$, <br/>
Find the semi-minor axis, the perihelion distance, and the apohelion distance.
<img width="2000" height="0">
</td>
</tbody>
</table>
</div>

By rearranging equation $2.3$:
```math
\begin{align}
b &= \sqrt{a^2\left(1 - e^2\right)}\\
&= \sqrt{149\:598\:023^2\text{ km}^2 \left(1 - 0.0167^2\right)}\\
&= 149\:577\:161 \text{ km}
\end{align}
```
The periapsis distance is given by equation $2.4$:
```math
149\:598\:023\text{ km }\left(1 - 0.0167\right) = 147\:099\:736\text{ km}
```
And the apoapsis distance is given by equation $2.5$:
```math
149\:598\:023\text{ km }\left(1 + 0.0167\right) = 152\:096\:309\text{ km}
```
$\blacksquare$

Furthermore, the ellipse can also be written in polar form with the focus at the origin:
By equation $2.2$:
```math
\frac{x^2}{a^2} + \frac{y^2}{b^2} = 1
```
But remember we have put the (right) focus as the origin and therefore $x$ becomes $x + ae$:
```math
\frac{\left(x + ae\right)^2}{a^2} + \frac{y^2}{b^2} = 1
```
Substituting $b^2 = a^2\left(1 - e^2\right)$:
```math
\begin{align}
\frac{\left(x + ae\right)^2}{a^2} + \frac{y^2}{a^2\left(1 - e^2\right)} &= 1\\
\left(x + ae\right)^2 + \frac{y^2}{1 - e^2} &= a^2\\
x^2 + 2aex + a^2e^2  + \frac{y^2}{1 - e^2} &= a^2
\end{align}
```
Now we substitute $r\cos\left(\theta\right)$ and $r\sin\left(\theta\right)$ for $x$ and $y$:
```math
\left(r\cos\left(\theta\right)\right)^2 + 2ae\left(r\cos\left(\theta\right)\right) + a^2e^2  + \frac{\left(r\sin\left(\theta\right)\right)^2}{1 - e^2} = a^2
```
Which gives the following quadratic equation in $r$:
```math
\frac{1 - e^2 \cos^2\left(\theta\right)}{1 - e^2} r^2 + 2ae\cos\left(\theta\right) r - a^2\left(1 - e^2\right) = 0
```
Finally, solving for $r$ gives us
```math
\begin{align}
r &= \frac{-2ae\cos\left(\theta\right) + \sqrt{4a^2e^2\cos^2\left(\theta\right) + 4a^2\left(1 - e^2 \cos^2\left(\theta\right)\right)}}{2\frac{1 - e^2 \cos^2\left(\theta\right)}{1 - e^2}}\\
&= \frac{1 - e^2\left(-2ae\cos\left(\theta\right) + \sqrt{4a^2e^2\cos^2\left(\theta\right) + 4a^2 - 4 a^2 e^2 \cos^2\left(\theta\right)}\right)}{2 - 2e^2 \cos^2\left(\theta\right)}\\
&= \frac{1 - e^2\left(-2a e\cos\left(\theta\right) + 2a\right)}{2 - 2e^2 \cos^2\left(\theta\right)}\\
&= \frac{a\left(1 - e^2\right)\left(-e\cos\left(\theta\right) + 1\right)}{1 - e^2 \cos^2\left(\theta\right)}\\
&= \frac{a\left(1 - e^2\right)}{1 + e\cos\left(\theta\right)}
\end{align}\tag{2.7}
```

#### Proof of Kepler's First Law
<div align="center">
<table>
<tbody>
<td align="center">
<img width="2000" height="0"><br>
Prove that all planets orbit the Sun in an ellipse. <br/>
Disclaimer: the proof is mathematically dense and there is no need to know it. <br/>
It is advised for the average reader to skip this investigation.
<img width="2000" height="0">
</td>
</tbody>
</table>
</div>

[Newton's law of gravitation](https://en.wikipedia.org/wiki/Newton%27s_law_of_universal_gravitation) (equation $2.1$) tells us:
```math
\textbf{F} = -\frac{G M m}{r^3} \cdot \textbf{r}
```
This can be rewritten:
```math
\textbf{F} = -\frac{G M m}{r^2} \cdot \textbf{u}
```
where $\textbf{u}$ is the [unit vector](https://en.wikipedia.org/wiki/Unit_vector) in the direction of $\textbf{r}$.\
Furthermore, [Newton's second law of motion](https://en.wikipedia.org/wiki/Newton%27s_laws_of_motion#Second_law) tells us:
```math
\textbf{F} = m \textbf{a}
```
where $\textbf{F}$ is the force on an object, $m$ is the mass of the object, and $\textbf{a}$ is its acceleration, defined by $\textbf{a} = d\textbf{v}/dt = d^2\textbf{r}/dt^2$, where $\textbf{v}$ is the velocity of the object.

By equating the two laws we obtain:
```math
\textbf{a} = -\frac{G M}{r^3} \cdot \textbf{r}
```
which shows that $\textbf{a}$ and $\textbf{r}$ are a scalar multiple of each other (they are parallel), which means that $\textbf{a} \times \textbf{r} = \textbf{0}$.\
In addition,
```math
\begin{align}
\frac{d}{dt}\left(\textbf{r}\times\textbf{v}\right) &= \textbf{r}'\times\textbf{v}+\textbf{r}\times\textbf{v}'\\
&=\textbf{v}\times\textbf{v}+\textbf{r}\times\textbf{a}\\
&=\textbf{0}\times\textbf{0}\\
&=\textbf{0}.
\end{align}
```
By integrating both sides of this equation we obtain:
```math
\textbf{r}\times\textbf{v} = \textbf{h}
```
where $\textbf{h}$ is a constant vector. We can reasonably assume $\textbf{r}$ and $\textbf{v}$ are not parallel (that is, the planet does not move in a straight line), and thus $\textbf{h} \neq \textbf{0}$. Thus all possible $\textbf{r}$ is perpendicular to $\textbf{h}$, and since $\textbf{h}$ is constant, all $\textbf{r}$ must lie flat on a plane with $\textbf{h}$ as its normal vector.

Let us now rewrite $\textbf{h}$.
```math
\begin{align}
\textbf{h} &= \textbf{r}\times\textbf{v} = \textbf{r}\times\textbf{r}' =r\textbf{u}\times\left(r\textbf{u}\right)'\\
&=r\textbf{u}\times\left(r'\textbf{u}+r\textbf{u}'\right) =r^2\left(\textbf{u}\times\textbf{u}'\right)+rr'\left(\textbf{u}\times\textbf{u}\right)\\
&=r^2\left(\textbf{u}\times\textbf{u}'\right).
\end{align}
```
Then,
```math
\begin{align}
\textbf{a}\times\textbf{h} &= -\frac{GM}{r^2}\textbf{u}\times r^2\left(\textbf{u}\times\textbf{u}'\right)\\
&= -GM\textbf{u}\times\left(\textbf{u}\times\textbf{u}'\right)\\
&= -GM\left[\left(\textbf{u}\cdot\textbf{u}'\right)\textbf{u}-\left(\textbf{u}\cdot\textbf{u}\right)\textbf{u}'\right]
\end{align}
```
But since $\textbf{u}$ is a unit vector ($\left|\textbf{u}\right| = 1$), $\textbf{u}\cdot\textbf{u} = 1$ (a constant) and so:
```math
\begin{align}
\frac{d}{dt}\left(\textbf{u}\cdot\textbf{u}\right) &= \textbf{u}'\cdot\textbf{u}+\textbf{u}\cdot\textbf{u}'\\
&=2\textbf{u}\cdot\textbf{u}'= 0.\\
\therefore \textbf{u}\cdot\textbf{u}'&=0\\
\therefore \textbf{a}\times\textbf{h}&=GM\textbf{u}'
\end{align}
```
Therefore we can write
```math
\begin{align}
\frac{d}{dt}\left(\textbf{v}\times\textbf{h}\right)&=\textbf{v}'\times\textbf{h}+\textbf{v}\times\textbf{h}'=\textbf{v}'\times\textbf{h}\\
&=\textbf{a}\times\textbf{h} = GM\textbf{u}'
\end{align}
```
Integrating both sides of this equation gives us
```math
\begin{align}
\textbf{v}\times\textbf{h}=GM\textbf{u}+\textbf{C}
\end{align}\tag{2.8}
```
where $\textbf{C}$ is a constant vector.

Let us now choose coordinate axes such that positive $z$-axis lies in the direction of $\textbf{h}$. Thus the planet moves in the $xy$-plane.\
Now, because $\textbf{v}\times\textbf{h}$ and $\textbf{u}$ are perpendicular to $\textbf{h}$ (i.e. in the $xy$-plane), $\textbf{C}$ must be in the $xy$-plane as well. Since $\textbf{C}$ is a constant vector, we choose the positive $x$-axis to be in the direction of it, and now $r$ and the angle between $\textbf{C}$ and $\textbf{r}$ (which we call $\theta$) define $\textbf{r}$ in polar coordinates.

From equation $2.8$ we now have:
```math
\begin{align}
\textbf{r}\cdot\left(\textbf{v}\times\textbf{h}\right)&=\textbf{r}\cdot\left(GM\textbf{u}+\textbf{C}\right)\\
&=GM\textbf{r}\cdot\textbf{u}+\textbf{r}\cdot\textbf{C}\\
&=GMr\textbf{u}\cdot\textbf{u}+\left|\textbf{r}\right|\left|\textbf{C}\right|\cos\left(\theta\right)\\
&=GMr + rc\cos\left(\theta\right)
\end{align}
```
where $c = \left|\textbf{C}\right|$. Now, solving for $r$,
```math
r=\frac{\textbf{r}\cdot\left(\textbf{b}\times\textbf{h}\right)}{GM+c\cos\left(\theta\right)}
```
If we put $c/\left(GM\right)$ = $e$ (and thus $GM = c/e$),
```math
r=\frac{1}{GM}\cdot\frac{\textbf{r}\cdot\left(\textbf{v}\times\textbf{h}\right)}{1+e\cos\left(\theta\right)}=\frac{e}{c}\cdot\frac{\textbf{r}\cdot\left(\textbf{v}\times\textbf{h}\right)}{1+e\cos\left(\theta\right)}
```
But,
```math
\textbf{r}\cdot\left(\textbf{v}\times\textbf{h}\right)=\left(\textbf{r}\times\textbf{v}\right)\cdot\textbf{h}=\textbf{h}\cdot\textbf{h}=h^2
```
where $h = \left|\textbf{h}\right|$.\
Thus:
```math
r= \frac{h^2e/c}{1+e\cos\left(\theta\right)}
```
If we now set $p=h^2/c$, we obtain for $r$:
```math
r=\frac{ep}{1+e\cos\left(\theta\right)}
```
This is a perfectly good polar equation for an ellipse, using $p$, which is the distance from the focus to the [*directrix*](https://en.wikipedia.org/wiki/Conic_section#Eccentricity,_focus_and_directrix) of the ellipse.\
However, $p$ can be written as $p = a/e + ae$, thus:
```math
r=\frac{a + ae^2}{1+e\cos\left(\theta\right)}
```
Which is precisely equation $2.7$.\
$\blacksquare$

<br/>

### Kepler's Third Law

Let us now calculate the [orbital period](https://en.wikipedia.org/wiki/Orbital_period) $T$ of a planet in a circular orbit, given the orbital radius $r$.\
Newton's law of gravitation (equation $2.1$) tells us:
```math
\textbf{F} = -\frac{G M m}{r^3} \cdot \textbf{r}
```
For objects to rotate, there must be a force pointing inwards (called the [centripetal force](https://en.wikipedia.org/wiki/Centripetal_force)), and this force is given as:
```math
\textbf{F} = -\frac{mv^2}{r^2} \cdot \textbf{r}
```
Where $m$ is the mass of the rotating body, and $v$ is its speed.\
Equating the two equations,
```math
\begin{align}
-\frac{mv^2}{r^2} \cdot \textbf{r} &= -\frac{G M m}{r^3} \cdot \textbf{r}\\
v^2 &= \frac{GM}{r}\\
v &= \sqrt{\frac{GM}{r}}
\end{align}
```
Using the fact that time $=$ distance $/$ speed and that the circumference of the orbit is $2\pi r$,
```math
\begin{align}
T &= \frac{2\pi r}{v} = \frac{2\pi r}{\sqrt{GM/r}}\\
&=\sqrt{\frac{4 \pi^2 r^3}{GM}}
\end{align}\tag{2.9}
```
We can see that equation $2.9$ is essentially Kepler's third law, which states that $T^2 \propto r^3$.\
Turns out, we can generalize equation $2.9$ to elliptical orbits without issue!
```math
\begin{align}
T = \sqrt{\frac{4 \pi^2 a^3}{GM}}
\end{align}\tag{2.10}
```
If we have two objects comparable in mass, they will orbit each other about their center of mass, and the period will be:
```math
\begin{align}
T = \sqrt{\frac{4 \pi^2 a^3}{G\left(M_1 + M_2\right)}}.
\end{align}\tag{2.11}
```
Where $a$ is the sum of the two semi-major axes.

Note that period is always positive if the motion is prograde, and negative if the motion is retrograde.

#### Example 2.2
<div align="center">
<table>
<tbody>
<td align="center">
<img width="2000" height="0"><br>
Given that $G = 6.674\cdot10^{-11}\text{ m}^3\text{ kg}^{-1}\text{ s}^{-2}$, the mass of the Sun $M_S = 1.989\cdot 10^{30} \text{ kg}$, and the semi-major axis of the orbit of the Earth $a = 1.496\cdot10^{11}\text{ m}$, calculate the orbital period of the Earth.
<img width="2000" height="0">
</td>
</tbody>
</table>
</div>

By equation $2.10$:
```math
\begin{align}
T &= \sqrt{\frac{4 \pi^2 a^3}{GM}}\\
&=\sqrt{\frac{4 \pi^2 \left(1.496\cdot10^{11}\text{ m}\right)^3}{\left(6.674\cdot10^{-11}\text{ m}^3\text{ kg}^{-1}\text{ s}^{-2}\right)\left(1.989\cdot 10^{30} \text{ kg}\right)}}\\
&= 3.1554897 \cdot 10^7 \text{ s}
\end{align}
```
Converting to days:
```math
T = 365.219 \text{ dy}
```
Which is close enough to the true value of the year, $365.2422 \text{ dy}$. The difference comes from the fact that there are gravitational perturbations from other Solar System objects on the Earth, and therefore the motion of the Earth is not *exactly* a true two-body problem. The precise math is too difficult for worldbuilding purposes and therefore the perturbation effects of planets on planets will be ignored.\
$\blacksquare$

### Perifocal Coordinates
(Continued in Part B...)

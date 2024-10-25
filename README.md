# Envelope
Perhaps one of the best known examples of an [envelope of a planar family of curves](https://en.wikipedia.org/wiki/Envelope_(mathematics)) is in string art. When cross-connecting two lines of equally spaced pins, as we increase the number of pins we notice that a curved boundary, tangent to the lines, is created.

<div align="center">
  <img src="assets/EnvelopeAnim.gif" alt="description of gif" width="500"/>
</div>

Usually we obtain the equation for this curve using known properties of the envelope:

$$F\left(t,\ x,\ y\right)=0$$
$$\frac{dF}{dt}\left(t,\ x,\ y\right)=0$$

However, for this derivation, I am interested in finding a solution to the equation through a purely parametric approach.<br><br>

## Derivation
<div align="center">
  <img src="assets/desmos_1.png" alt="description of gif" width="600"/>
</div>


Let us start by defining two points $$a$$ and $$b$$ moving along the vertical and horizontal line respectively, and let vectors $$r_{a}\(t)$$ and $$r_{b}\(t)$$ represent their position. We know that these points have the same speed, and thus we have:

$$r_{a}\(t)=
\begin{bmatrix}
    x_{1}+t\left(x_{0}-x_{1}\right)\\
    y_{1}+t\left(y_{0}-y_{1}\right)
\end{bmatrix}
$$

$$r_{b}\(t)=
\begin{bmatrix}
    x_{0}+t\left(x_{2}-x_{0}\right)\\
    y_{0}+t\left(y_{2}-y_{0}\right)
\end{bmatrix}
$$

We can further simplify these vectors since we know that $$x_{0}=x_{1}$$ and $$y_{2}=y_{0}$$

$$r_{a}\(t)=
\begin{bmatrix}
    x_{1}\\
    y_{1}+t\left(y_{0}-y_{1}\right)
\end{bmatrix}
$$

$$r_{b}\(t)=
\begin{bmatrix}
    x_{0}+t\left(x_{2}-x_{0}\right)\\
    y_{0}
\end{bmatrix}
$$

Now imagine that we have two lines. The first one is formed at time $$t$$ by the points 

$$\left(x_{a}\left(t\right),\ y_{a}\left(t\right)\right),\ \left(x_{b}\left(t\right),\ y_{b}\left(t\right)\right)$$

The second one is formed from the same points at time $$t + dt$$ 

$$\left(x_{a}\left(t+dt\right),\ y_{a}\left(t+dt\right)\right),\ \left(x_{b}\left(t+dt\right),\ y_{b}\left(t+dt\right)\right)$$ 

![image](https://github.com/user-attachments/assets/b29d9e44-711f-45e1-aac8-fba3132cb5ac)

We know that these two lines intercept at some point $$\left(x_{c},y_{c}\right)$$, which we want to find. To do this, we will parametrize the lines and solve the system of equations. Let us call the points riding along the lines $$d$$ and $$e$$, and their parameters $$s$$ and $$u$$ respectively, such that

$$r_{d}\left(s\right)=r_{a}\left(t\right)+s\left(r_{b}\left(t\right)-r_{a}\left(t\right)\right)$$
$$r_{e}\left(u\right)=r_{a}\left(t+dt\right)+u\left(r_{b}\left(t+dt\right)-r_{a}\left(t+dt\right)\right)$$

We can find the position of point $$c$$ by solving for the value of the parameters $$s$$ and $$u$$ when the lines intercept.

Let's expand the vectors

$$r_{d}\(s)=
\begin{bmatrix}
    x_{1}\\
    y_{1}+t\left(y_{0}-y_{1}\right)
\end{bmatrix} + s
\big(\begin{bmatrix}
    x_{0}+t\left(x_{2}-x_{0}\right)\\
    y_{0}
\end{bmatrix} - 
\begin{bmatrix}
    x_{1}\\
    y_{1}+t\left(y_{0}-y_{1}\right)
\end{bmatrix}\big)
$$

again, we note that $$x_{0}=x_{1}$$

$$r_{d}\(s)=
\begin{bmatrix}
    x_{0}\\
    y_{1}+t\left(y_{0}-y_{1}\right)
\end{bmatrix} + s
\begin{bmatrix}
    t\left(x_{2}-x_{0}\right)\\
    (y_{0}-y_{1})-t(y_{0}-y_{1})
\end{bmatrix}
$$

$$r_{d}\(s)=
\begin{bmatrix}
    x_{0}\\
    y_{1}+t\left(y_{0}-y_{1}\right)
\end{bmatrix} + s
\begin{bmatrix}
    t\left(x_{2}-x_{0}\right)\\
    (1-t)(y_{0}-y_{1})
\end{bmatrix}
$$

$$r_{d}\(s)=
\begin{bmatrix}
    x_{0}\\
    y_{1}+t\left(y_{0}-y_{1}\right)
\end{bmatrix} +
\begin{bmatrix}
    st\left(x_{2}-x_{0}\right)\\
    s(1-t)(y_{0}-y_{1})
\end{bmatrix}
$$

$$r_{d}\(s)=
\begin{bmatrix}
    x_{0}\\
    y_{1}+t\left(y_{0}-y_{1}\right)
\end{bmatrix} +
\begin{bmatrix}
    st\left(x_{2}-x_{0}\right)\\
    (s-st)(y_{0}-y_{1})
\end{bmatrix}
$$

$$r_{d}\(s)=
\begin{bmatrix}
    x_{0}+st\left(x_{2}-x_{0}\right)\\
    y_{1}+t\left(y_{0}-y_{1}\right)+(s-st)(y_{0}-y_{1})
\end{bmatrix}
$$

$$r_{d}\(s)=
\begin{bmatrix}
    x_{0}+st\left(x_{2}-x_{0}\right)\\
    y_{1}+(s-st+t)(y_{0}-y_{1})
\end{bmatrix}
$$

Now we do the same for $$r_{e}\(t)$$

$$r_{e}\(u)=
\begin{bmatrix}
    x_{1}\\
    y_{1}+(t+dt)\left(y_{0}-y_{1}\right)
\end{bmatrix} + u
\big(\begin{bmatrix}
    x_{0}+(t+dt)\left(x_{2}-x_{0}\right)\\
    y_{0}
\end{bmatrix} - 
\begin{bmatrix}
    x_{1}\\
    y_{1}+(t+dt)\left(y_{0}-y_{1}\right)
\end{bmatrix}\big)
$$

$$r_{e}\(u)=
\begin{bmatrix}
    x_{0}\\
    y_{1}+(t+dt)\left(y_{0}-y_{1}\right)
\end{bmatrix} + u
\begin{bmatrix}
    (t+dt)\left(x_{2}-x_{0}\right)\\
    (y_{0}-y_{1})-(t+dt)\left(y_{0}-y_{1}\right)
\end{bmatrix}
$$

$$r_{e}\(u)=
\begin{bmatrix}
    x_{0}\\
    y_{1}+(t+dt)\left(y_{0}-y_{1}\right)
\end{bmatrix} + u
\begin{bmatrix}
    (t+dt)\left(x_{2}-x_{0}\right)\\
    (1-t-dt)\left(y_{0}-y_{1}\right)
\end{bmatrix}
$$

$$r_{e}\(u)=
\begin{bmatrix}
    x_{0}\\
    y_{1}+(t+dt)\left(y_{0}-y_{1}\right)
\end{bmatrix} +
\begin{bmatrix}
    u(t+dt)\left(x_{2}-x_{0}\right)\\
    u(1-t-dt)\left(y_{0}-y_{1}\right)
\end{bmatrix}
$$

$$r_{e}\(u)=
\begin{bmatrix}
    x_{0}\\
    y_{1}+(t+dt)\left(y_{0}-y_{1}\right)
\end{bmatrix} +
\begin{bmatrix}
    u(t+dt)\left(x_{2}-x_{0}\right)\\
    (u-ut-udt)\left(y_{0}-y_{1}\right)
\end{bmatrix}
$$

$$r_{e}\(u)=
\begin{bmatrix}
    x_{0}+u(t+dt)\left(x_{2}-x_{0}\right)\\
    y_{1}+(t+dt)\left(y_{0}-y_{1}\right)+(u-ut-udt)\left(y_{0}-y_{1}\right)
\end{bmatrix}
$$

$$r_{e}\(u)=
\begin{bmatrix}
    x_{0}+u(t+dt)\left(x_{2}-x_{0}\right)\\
    y_{1}+(t+dt+u-ut-udt)\left(y_{0}-y_{1}\right)
\end{bmatrix}
$$

Now let us solve the sytem of equations, starting with the x-component and solving for $$s$$

$$x_{0}+st\left(x_{2}-x_{0}\right)=x_{0}+u\left(t+dt\right)\left(x_{2}-x_{0}\right)$$

$$\big\[x_{0}+st\left(x_{2}-x_{0}\right)=x_{0}+u\left(t+dt\right)\left(x_{2}-x_{0}\right)\big\] -x_{0}$$

$$st\left(x_{2}-x_{0}\right)=u\left(t+dt\right)\left(x_{2}-x_{0}\right)$$

$$st=u\left(t+dt\right)$$

$$s=u\left(1+\frac{dt}{t}\right)$$

We do the same fot the y-component

$$y_{1}+(s-st+t)(y_{0}-y_{1}) = y_{1}+(t+dt+u-ut-udt)\left(y_{0}-y_{1}\right)$$

$$\big\[y_{1}+(s-st+t)(y_{0}-y_{1}) = y_{1}+(t+dt+u-ut-udt)\left(y_{0}-y_{1}\right)\big\] -y_{1}$$

$$(s-st+t)(y_{0}-y_{1}) = (t+dt+u-ut-udt)\left(y_{0}-y_{1}\right)$$

$$(s-st+t) = (t+dt+u-ut-udt)$$

$$\big\[s-st+t = t+dt+u-ut-udt\big\] -t$$

$$s-st = dt+u-ut-udt$$

$$s(1-t) = u(1-t-dt) + dt$$

$$s(1-t) -u(1-t-dt) = dt$$

$$s(1-t) +u(t+dt-1) = dt$$

Let us substitute $$s=u\left(1+\frac{dt}{t}\right)$$

$$u(1+\frac{dt}{t})(1-t) +u(t+dt+1) = dt$$

$$u(1-t+\frac{dt}{t}-t\frac{dt}{t})+u(t+dt+1) = dt$$

$$u(1-t+\frac{dt}{t}-t\frac{dt}{t}+t+dt+1)=dt$$

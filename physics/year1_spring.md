# physics

## 1. Measurement

### SI Units

### Changing Units

### Length

### Time

### Mass

### Density

## 2. Motion along a straight line

### Position

### Displacement

the displacement of $\Delta x$ of a particle is the change in its position
$$
\Delta x = x_2 - x_1
$$

### Average Velocity

$$
V_{avg} = \frac{\Delta x}{\Delta t} = \frac{x_2-x_1}{t_2-t_1}
$$



### Average Speed

$$
S_{avg} = \frac{total \ distance}{\Delta t}
$$



### Instantaneous Velocity

$$
v = lim_{\Delta t\rightarrow 0}\frac{\Delta x}{\Delta t} = \frac{dx}{dt}
$$

* the instantaneous velocity could be found as the slope(gradient) in the graph of x versus t
* Speed is the magnitude of instantaneous velocity
* it has direction

### Average Acceleration

$$
a_{avg} = \frac{\Delta v}{\Delta t}
$$



### Instantaneous Acceleration

$$
a = \frac{dv}{dt} = \frac{d^2x}{dt^2}
$$



### Constant Acceleration

$$
v = v_0 + at \\
x - x_0 = v_0t + \frac{1}{2}at^2 \\
v^2 = v_0^2 + 2a(x-x_0) \\
x - x_0 = \frac{1}{2}(v_0+v)t \\
x - x_0 = vt - \frac{1}{2}at^2
$$

* can't be used when a is not a constant in the serious of motion

### Free-Fall Acceleration

## 3. Vectors

### Scalars and Vectors

* scalars have only magnitude only
* vectors have both magnitude and direction

### Adding Vectors Geometrically

$$
\vec{a} + \vec{b} = \vec{b}+\vec{a} \ \ \ (commutative \ law)\\
(\vec{a}+\vec{b})+\vec{c} = \vec{a}+(\vec{b}+\vec{c}) \ \ \ (associative \ law)
$$

### Components of a Vector

the components of a vector are projections of the vector along the coordinate axes.
$$
a_x = a \cos\theta \\
a_y = a \sin \theta \\
a = \sqrt{a_x^2 + b_y^2} \\
\tan \theta = \frac{a_y}{a_x}
$$

### Unit-Vector Notation

$$
\vec{a} = a_x\hat{i}+a_y\hat{j}+a_z\hat{k}
$$

* unit vectors  $\hat{i}$,  $\hat{j}$,  $\hat{k}$ have magnitudes of unity and are directed in the positive directions of the x, y, z axes

### Adding vectors by components

consider the statement
$$
\vec{r} = \vec{a}+\vec{b}
$$
each component of $\vec{r}$ must be the same as the corresponding component of $\vec{a}+\vec{b}$ , 
$$
r_x = a_x + b_x \\
r_y = a_y + b_y \\
r_y = a_z + b_z
$$
In conclude, two vectors must be equal if their corresponding components are equal

### The scalar product

$$
\vec{a}\cdot\vec{b}=ab\cos\phi
$$

in unit vector notation
$$
\vec{a}\cdot\vec{b} = (a_x\hat{i}+a_y\hat{j}+a_z\hat{k})\cdot(b_x\hat{i}+b_y\hat{j}+b_z\hat{k})
$$

### The vector product

$$
c = ab\sin\phi
$$



## 4. Motion in two and three dimensions

### Position vector

$$
\vec{r} = x\hat{i}+y\hat{j}+z\hat{k}
$$

### Displacement

Displacement is the change of sth, for example if a particle moves so that its position vector changes from $\vec{r_1}$ to $\hat{r_2}$ , the particle's displacement $\Delta\vec{r}$ is
$$
\Delta\vec{r} = \vec{r_2} - \vec{r_1}
$$
The displacement can also be written as
$$
\Delta\vec{r} = (x_2 - x_1)\hat{i} + (y_2-y_1)\hat{j}+(z_2-z_1)\hat{k} \\
= \Delta x\hat{i}+\Delta y\hat{j}+ \Delta z \hat{k}
$$

### Average Velocity and Instantaneous velocity

$$
\vec{v}_{avg} = \frac{\Delta\vec{r}}{\Delta t}
$$

As $\Delta t$ is shrunk to 0, we can denote the instantaneous velocity as
$$
\vec{v} = \frac{d\vec{r}}{dt}
$$
which can be rewrite in unit vector notation as
$$
\vec{v} = v_x\hat{i}+v_y\hat{j}+v_z\hat{k}
$$
where $v_x = \frac{dx}{dt}$, $v_y = \frac{dy}{dt}$, $v_z=\frac{dz}{dt}$ 

### average acceleration and instantaneous acceleration

$$
\vec{a}_{avg} = \frac{\vec{v_2}-\vec{v_1}}{\Delta t}=\frac{\Delta \vec{v}}{\Delta t}
$$

as $\Delta t$ shrunk to 0, we have instantaneous acceleration $\vec{a}$ 
$$
\vec{a} = \frac{d\vec{v}}{dt}
$$
In unit vector notation
$$
\vec{a} = a_x\hat{i}+a_y\hat{j}+a_z\hat{k}
$$
where $a_x = \frac{dv_x}{dt}$,  $a_y = \frac{dv_y}{dt}$, $a_z=\frac{dv_z}{dt}$ 

### Projectile Motion(抛体运动)

projectile motion is the motion of a particle that is launched with an initial velocity $\vec{v}_0$. Its horizontal acceleration is 0 and the vertical acceleration is free-fall acceleration.

If $\vec{v}_0$ is expressed only in magnitude as $v_0$ and angle $\theta_0$ is measured from the horizontal ,we have
$$
x-x_0=(v_0\cos \theta_0)t\\
y-y_0=(v_0\sin \theta_0)t - \frac{1}{2}gt^2\\
v_y = v_0\sin\theta_0-gt\\
v^2_y = (v_0\sin\theta_0)^2-2g(y-y_0)
$$
The trajectory of a particle in projectile motion is parabolic, and is given by
$$
y =(\tan\theta_0)x-\frac{gx^2}{2(v_0\cos\theta_0)^2}
$$
if $x_0$ and $y_0$ are zero, the horizontal range of the particle, which is the horizontal distance from the starting point to the point at which particle return to the launch height is
$$
R = \frac{v_0^2}{g}\sin2\theta_0
$$

### Uniform circular motion

$$
a = \frac{v^2}{r}
$$

the time for the particle to complete a circle is 
$$
T = \frac{2\pi r}{v}
$$

### Relative motion

$$
\vec{v}_{PA} = \vec{v}_{PB}+\vec{v}_{BA}
$$


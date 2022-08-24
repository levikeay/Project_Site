---
title: Simulating Elastic Collisions in O2 Gas
layout: post
post-image: "https://user-images.githubusercontent.com/63168148/186535447-d4a7a44d-3e85-4f3f-afe5-85b25bc072e2.png"
description: Numerically modelling the energy and velocity distributions of a gas filled container

---
### Introduction
The aim of this project was to simulate elastic collisions in a gas. Then, visualize and analyze the system by the following:
1) generating an animation representing the gas particles motion
2) analyzing the speed and energy distributions of particles
3) computing the temperature of the system

See below for my solution in Python, and the results.
This project was completed for an assignment as a part of my Introduction to Computational Physics course. 

### Program function
When executed, this program generates and animation representing
the elastic collisions of a 2D gas. The simulated particles are
all assigned the same mass of  m = 2.672e-26 kg (the mass of O2).
They are assigned a random position within a 1x1 "box". They are
assigned initial velocities of equal magnitude (500 m/s) such that
the particles have 0 y velocity and either 500m/s or -500m/s
x velocity, depending on their starting position.

The underlying purpose of the simulation is to demonstrate the
development of the Maxwell- Boltzmann distribution. After running
the simulation for 1000 steps, a figure containing 2 plots is
produced (called "distributions.pdf"). One plot shows the
probability distribution of speed and the other the PD of kinetic
energy. Each plot also shows the fitted curve given by the Maxwell
-Boltzmann equations.

The temperature for the system is obtained via the fit and is
printed to a text file "collisions.txt"

### Animation
|![collisions_fast](https://user-images.githubusercontent.com/63168148/186540450-55a3226e-a252-498d-a7c1-0b5bb775d3fb.gif)|
|:--:|
|Animation showing the motion of simulated gas particles. All particles begin with equal magnitude and strictly horizontal velocities, but collisions between particles soon result in a Maxwell-Boltzman distribution of velocities.|

### Distribution Analysis
|![distributions](https://user-images.githubusercontent.com/63168148/186540631-842ae748-a3ec-45f4-82c3-72612ddcdcb1.png)|
|:--:|
| Speed and Energy distributions of simulation particles after 1000 time steps, and the fit of the theoretical Maxwell-Boltzmann distributions to the data. |

By fitting the Maxwell - Boltzmann distribution of speed the temperature of the system is found to be: 232.8775649362587 K

### Script
~~~python
import numpy as np
import matplotlib.pyplot as plt
import matplotlib.animation as animation
from itertools import combinations
from scipy.optimize import curve_fit
"""
Levi Keay
phys 210

When executed, this program generates and animation representing
the elastic collisions of a 2D gas. The simulated particles are
all assigned the same mass of  m = 2.672e-26 kg (the mass of O2).
They are assigned a random position within a 1x1 "box". They are
assigned initial velocities of equal magnitude (500 m/s) such that
the particles have 0 y velocity and either 500m/s or -500m/s
x velocity, depending on their starting position.

The underlying purpose of the simulation is to demonstrate the
development of the Maxwell- Boltzmann distribution. After running
the simulation for 1000 steps, a figure containing 2 plots is
produced (called "distributions.pdf"). One plot shows the
probability distribution of speed and the other the PD of kinetic
energy. Each plot also shows the fitted curve given by the Maxwell
-Boltzmann equations.

The temperature for the system is obtained via the fit and is
printed to a text file "collisions.txt"
"""

npoint = 400  # number of particles
nframe = 1000  # number of timesteps to run simulation
xmin, xmax, ymin, ymax = 0, 1, 0, 1  # boundaries of 2D box
Dt = 0.00002  # timestep
r = 0.0015  # particle radius
m = 2.672*10**(-26)  # particle mass
kb = 1.38*10**(-23)  # Boltzmann constant

#  create figure for simulation
fig, ax = plt.subplots()
plt.xlim(xmin, xmax)
plt.ylim(ymin, ymax)


def update_point(num):

    """
    update_point is called to produce the animation of the simulation.
    It uses global variables of positional arrays x and y, and velocity
    arrays vx and vy and updates these arrays in place by determining where
    collisions occur in the current time step and calculating the final
    velocities of these collisions.
    Note that radius r is used as a global variable, and that mass is not
    required for the calculations because the particles are all of identical
    mass.
    """
    global x, y, vx, vy, r
    # print(num)
    # account for the boundaries of the box (reverse velocities where
    # particle hits edge)
    indx = np.where((x < xmin) | (x > xmax))
    indy = np.where((y < ymin) | (y > ymax))
    vx[indx] = -vx[indx]
    vy[indy] = -vy[indy]

    # arrays of every x and y position combinations for the 400 particles
    xx = np.asarray(list(combinations(x, 2)))
    yy = np.asarray(list(combinations(y, 2)))

    # distance between every combination of particles
    dd = (xx[:, 0]-xx[:, 1])**2+(yy[:, 0]-yy[:, 1])**2

    # determine which particles are colliding by comparing distances in dd
    collision = np.where(dd <= (2*r)**2)
    inds = np.array(list(combinations(list(range(npoint)), 2)))

    # array containing pairs of colliding particles
    colliding_particle_pairs = inds[collision]

    # define p1 and p2 as a pair of colliding particles
    p1 = colliding_particle_pairs[:, 0]
    p2 = colliding_particle_pairs[:, 1]

    # 1 x 400 arrays of zeroes for change in x and y velocities.
    dvx = np.zeros(npoint)
    dvy = np.zeros(npoint)

    # Determine changes in x and y velocities for each colliding particle
    # using conservation of momentum for elastic collisions in 2D, and
    # update dvx and dvy accordingly.
    dvx[p1] = -((vx[p1]-vx[p2])*(x[p1]-x[p2]) + (vy[p1]-vy[p2])*(y[p1]-y[p2])
                ) / ((x[p1]-x[p2])**2 + (y[p1]-y[p2])**2) * (x[p1] - x[p2])

    dvx[p2] = -((vx[p2]-vx[p1])*(x[p2]-x[p1]) + (vy[p2]-vy[p1])*(y[p2]-y[p1])
                ) / ((x[p2]-x[p1])**2 + (y[p2]-y[p1])**2) * (x[p2] - x[p1])

    dvy[p1] = -((vx[p1]-vx[p2])*(x[p1]-x[p2])+(vy[p1]-vy[p2])*(y[p1]-y[p2])
                ) / ((x[p1]-x[p2])**2 + (y[p1]-y[p2])**2) * (y[p1] - y[p2])

    dvy[p2] = -((vx[p2]-vx[p1])*(x[p2]-x[p1])+(vy[p2]-vy[p1])*(y[p2]-y[p1])
                ) / ((x[p2]-x[p1])**2 + (y[p2]-y[p1])**2) * (y[p2] - y[p1])

    # change in x and y positions during current time step
    dx = Dt*vx
    dy = Dt*vy

    # new x and y positions
    x = x + dx
    y = y + dy

    # Update x and y velocities.
    # Note that dvx, dvy are at this point arrays containing non zero entries
    # only where collisions have occured in the current time step, and thus
    # only colliding particles have their velocities changed.
    vx = vx + dvx
    vy = vy + dvy

    data = np.stack((x, y), axis=-1)
    im.set_offsets(data)


x = np.random.random(npoint)  # random initial positions
y = np.random.random(npoint)
vx = -500.*np.ones(npoint)    # initial x velocities
vy = np.zeros(npoint)         # initial y velocities = 0

# reverse initial x velocities of particles on left side of box
vx[np.where(x <= 0.5)] = -vx[np.where(x <= 0.5)]
im = ax.scatter(x, y)
im.set_sizes([10])  # set animation particle size

# animate simulation using function update_point
anim = animation.FuncAnimation(fig,
                               update_point, nframe, interval=10, repeat=False)

anim.save("collisions.gif")  # save animation
plt.close()

v = np.sqrt(vx**2+vy**2)  # array of final velocities of the particles


def fv(v, T):

    """
    fv returns the probability distribution of speed and is used to fit the
    data from the simulation and determine temperature, T, of the system
    of particles.
    """
    fv = m*v/(kb*T)*np.exp(-m*v**2/(2*kb*T))
    return fv


def gE(v, T):

    """
    gE returns the probability distribution of kinetic energy and is used
    to fit the data from the simulation.
    """
    E = 0.5*m*v**2
    gE = 1/(kb*T)*np.exp(-E/(kb*T))
    return gE


# Generate normalised histogram of velocities.
plt.clf()
bin_heights, bin_borders, _ = plt.hist(v, 100, alpha=0.75, density=True)
bin_centers = bin_borders[:-1]+np.diff(bin_borders)/2

# Use curve_fit to fit fv to simulation data. initial guess for T is 273 K.
# Returns fitted temperature as popt with covariance pcov
popt, pcov = curve_fit(fv, bin_centers, bin_heights, 273)
T = float(popt)

# fit for f(v) and g(E)
fitv = np.linspace(bin_borders[0], bin_borders[-1], 10000)
fitE = 0.5*m*fitv**2

# Generate normalized speed and energy probability distributions as
# subplots on the same figure, each with their respective fitted line:

# speed distribution
plt.subplot(211)
plt.hist(v, 100, facecolor='g', alpha=0.75, density=True,
         label="Distribution")
plt.plot(fitv, fv(fitv, *popt), label="fit")
plt.title("Probability Distribution of Speed")
plt.xlabel("Speed (m/s)")
plt.ylabel("Probability")
plt.legend()

# energy distribution
plt.subplot(212)
plt.hist(0.5*m*v**2, 100, facecolor='y', alpha=0.75, density=True,
         label="Distribution")
plt.plot(fitE, gE(fitv, popt), label="fit")
plt.title("Probability Distribution of Energy")
plt.xlabel("Energy (J)")
plt.ylabel("Probability")
plt.legend()

plt.tight_layout()  # make the layout tight af
plt.savefig("distributions.png")  # Save the figure
plt.close()

# Write file "collisions.txt" containing temperature found from
# fit and description.
f = open('collisions.txt', 'w')
f.write("By fitting the Maxwell - Boltzmann distribution of speed"
        "\n the temperature of the system is found to be: {} K".format(T))
f.close()
~~~


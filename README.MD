
# DOOM Source Code Release

Here it is at long last: the official DOOM source code, now available for your **non-profit use**! Please note that this code    requires genuine DOOM data files to function. If you don’t own a copy of one of the original DOOM games, you can still use the **shareware version** of DOOM, which is freely available and contains the first episode of the game. For the full experience, you can still find the complete versions of DOOM for purchase at various software stores or digital platforms.


---

###  Acknowledgements

Special thanks to **Bernd Kreimeier** for dedicating time to clean up this project and ensure everything works as intended. Projects like these can degrade over time when left unattended, and it took effort to bring this one back to life.

---

###  Compatibility

**Important note:**  
This source code currently compiles and runs only on **Linux**. Unfortunately, we couldn't release the DOS version due to a copyrighted sound library that was used in development (a decision I regret — I've since written my own sound engine). Additionally, the Windows port, created by Microsoft, was lost over time, and I have no idea where it ended up.

---

###  Portability

Despite the compatibility limitations, the code is highly portable and can be adapted to other platforms. With some effort, you should be able to get it running on operating systems such as **Windows**, **macOS**, or even **mobile platforms**.

---

###  Reflections on the Code

This code was written a long time ago, and in hindsight, some design choices seem odd or inefficient. For example, using **polar coordinates for clipping** feels a bit unusual now, but overall, this code still serves as a solid foundation for experimentation and further development.

The rendering concept — **horizontal and vertical lines of constant Z with fixed light shading per band** — was a solid approach. However, the implementation could be optimized significantly. By collapsing the rendering process (which originally handled walls, floors, and sprites separately) into a **single front-to-back pass through the BSP tree**, you could gather information on the way down and render all the contents of a subsector on the way back up.

This would require treating **floors and ceilings as polygons** (instead of gaps between walls) and **clipping sprite billboards into subsector fragments**. Although challenging, it’s the right approach to take.

---

###  Movement and Line of Sight

One of the major shortcomings was the **movement and line-of-sight checks**. The code here is messy and prone to failure in specific cases. A much simpler (and faster) solution was overlooked at the time. While the BSP tree was used for rendering, I didn’t realize it could also be used for environment testing. Replacing the line-of-sight test with a **BSP line clip** would be a relatively simple improvement.

Sweeping volumes for movement, however, is more complex. It touches on some of the same challenges that arose later in **Quake** and **Quake II**, like handling edge bevels on polyhedrons.

---


### Some project ideas

Port it to your favorite operating system.

Add some rendering features -- transparency, look up / down, slopes,
etc.

Add some game features -- weapons, jumping, ducking, flying, etc.

Create a packet server based internet game.

Create a client / server based internet game.

Do a 3D accelerated version.  On modern hardware (fast pentium + 3DFX)
you probably wouldn't even need to be clever -- you could just draw the
entire level and get reasonable speed.  With a touch of effort, it should
easily lock at 60 fps (well, there are some issues with DOOM's 35 hz
timebase...).  The biggest issues would probably be the non-power of two
texture sizes and the walls composed of multiple textures.

---

###  Community Involvement


While I can't predict how many will dive into this project, it would be great to see a community effort take shape. Even though early projects may start as rough, isolated hacks, it would be exciting to see a **coordinated release of an improved, backward-compatible version of DOOM** that runs on multiple platforms. Imagine what could be achieved with community collaboration!


---


Have fun experimenting with the code!


Best regards,  

**John Carmack**  

*12-23-97*


---


**Copyright (c) ZeniMax Media Inc. Licensed under the GNU General Public License 2.0.**


---

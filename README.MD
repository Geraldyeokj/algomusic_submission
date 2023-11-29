# Written Reflection

## Creative Process

I wanted to musically represent a cool algorithm that produced infinitely variable outputs. I initially thought of graph traversal algorithms like DFS, Dijkstra's, and Kahn's Algorithm. I also thought of The collatz conjecture. However, I realised that it is difficult for people to use graphs as musical instruments as they get unwieldy really quickly. I also realised that the collatz conjecture would produce outputs that may be too random to be a musical instrument or an algorithmic composition.

Thus, I wanted a form of algorithm that gives players control while remaining somewhat unpredictable in its performance. This desire brought my attention to the double pendulum. I remembered my physics teacher in high school telling me about how a double pendulum is almost impossible to predict algorithmically while a simple pendulum is easily modelled. I realised that the amplitude of a pendulum's bobs can be contolled by a user while the ultimate variation in movement is incredibly hard to predict.

To increase the variation in my pendulum's movement and to add more musical layers to my instrument I increased the number of bobs from 2 to 3 to create a triple pendulum. 

Following the theme of "controllable randomness" I made the top-most bob a base bob and the bottom two pendulums follower bobs on the advice of Professor Nick Briz. The follower bobs are always a nice-sounding multiple of the base bob's frequency resulting in more pleasant tunes. I also added controllable frequencies of drifting for both the base bob and the follower bobs. Drifting controlls how frequently the frequencies of the base and follower bobs change.

## Technical Difficulties

I wanted my bobs to sound more ethereal and thus extended the length of the synths played when the bobs cross the center of the simulation. Unbeknownst to me, the initial lengths were far to long. This resulted in glitchy sounding synths if the frequency of my pendulum was too high as I think the brower cannot handle too many synths playing at the same time. To address this I reduced the length of my synths and killed the synths a certain amount of time after playing.

Following the advice of Professor Nick Briz, I decided to make the bobs play when they crossed the center line. This proved to be more difficult to implement than I thought. I initially wanted to make the bobs play when their x position was 500 (the centre of the screen). This would prove ineffective as the drawing would not refresh fast enough to catch the bobs when their x position was exactly 500. This was especially the case when the bobs were moving quickly. To address this I changed the condition for playing to be a range like 495 < x < 500. However, this would also prove to be problematic when the amplitude of the bobs was really small because they would play continuously. I ultimately solved the problem by ensuring that 2 conditions had to be true for a bob to make a sound. It would first have to be in a range close to the center of the simulation. It would also have to had reached it amplitude. To track whether the bob had reached it amplitude, I tracked the velocity of each bob and made sure that its velocity in the x direction has been both positive and negative before the bob is able to activate a synth.

Deployment was a bit harder than expected as I elected to use an S3 bucket and had difficulties creating a VPC that allowed public access to the website.



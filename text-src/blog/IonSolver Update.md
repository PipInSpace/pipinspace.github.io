I have been working on IonSolver with a friend for a while now and we've made some good progress lately!
Feature-wise we are getting closer and closer to a fully physically accurate model of plasma in strong magnetic and electric fields while also working on multi-device parallelization.
Changes include dynamic magnetic and electric fields that are directly computed from the simulated plasma as well as simulated advection of charges in the plasma.
Both were desperately needed for an accurate model and were challenging to implement but we're getting there.
Multi-device parallelization allows running the same simulation on many compute devices like GPUs and CPUs in parallel by splitting up the simulation into multiple smaller "domains".
These domains are like "mini-simulations" that each run on one compute device and are able to communicate with each other to act as one.
There is no real limit to the amount of devices used and performance is mostly proportional to the amount of devices used (synchronization between domains introduces a little overhead).
We are hoping to field-test this soon on multi-GPU hardware.

In other news, the goal of this project has been a huge success! We started working on IonSolver about a year ago for the German "Jugend Forscht" student science competition.
The contest has since started and we managed to win 1. place in the regional & state competition!
We competed in the "Physics" category and are now getting ready for the federal competition against projects from the 15 other states in Germany.

<div>
<img src="../img/blog/borat_i_go_to_bundeswettbewerb.png" alt="Borat 'I go to America!' meme with the text 'I go to Bundeswettbewerb (federal competition)!'" style="width: 100%; max-width: 400px; margin: 0 auto; display: block;">
</div><br>

Competitions like "Jugend Forscht" are such a great way to get into science and creating things and even to build early connections into academia.
Through working on this project, we have come into contact with some professionals in the field and received much needed help and support.
The opportunities this opened up for us and the learning and new experiences have been amazing. Thank you to all who have been a part of this!

Thank you for reading ❤️
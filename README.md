#Introduction

This report provides an overview of the notebook we created to simulate and analyze the electrical activity of a simplified version of the Morris-Lecar model. We implemented the model with and without stochasticity to see the impact of noise. Furthermore we decided to compare the performance of the Morris-Lecar model with the one of FitzHugh-Nagumo model. The code consists of different functions that implement these models, plot their outputs, and compare their responses to input stimuli.

#1 - Morris-Lecar Model
The Morris-Lecar model is a biophysical model that describes how the voltage across a neuron's membrane changes in response to currents. The code implements this model by solving a set of differential equations using the Euler method, we decided to use a small timestep dt=0.1 since smaller time steps increase accuracy, but there is a tradeoff since it also require more computational resources, lucky we did not encounter any issue related to computational power. This model considers the dynamics of calcium and potassium which are crucial for action potential generation. The hyperparameters include membrane capacitance and equilibrium voltage for each ion. We set the simulation length to 1000ms and we iterate over it with smaller time steps, the code also updates the membrane potential and potassium channel activation to simulate the neuron's response to an external current.

The initial condition is set to represent a resting state of the neuron. An external current I applied to the model, varying in amplitude and duration to observe different neuronal behavior, also by simulating over a sufficiently long time period we can capture various dynamics, such as resting and spiking.

We ran two simulations, each with a different input current and with a different start time and duration. We used the same values for both simulations also with the stochastic Morris-Lecar model, in this way we could clearly see the difference.

#2 - Stochastic Morris-Lecar
We decided to modify the Morris-Lecar Model by introducing a stochastic element into the  membrane potential equation of the model to simulate the effect of channel noise. By modifying the noise_density hyperparameter we can control the magnitude of the noise. We decided to set it to 0.95 and we can see some noise in the plot.

#3 - Comparison of Morris-Lecar with and without noise
In this part of the notebook we compare the two models defined before: the non-stochastic Morris-Lecar model (called morris_lecar_model) and the stochastic version (called morris_lecar_model_stochastic).

In the plot we can see the two models, one in red solid line and the other in blue dashed line. In the first subplot we plotted the input current, which was the same for both models to allow a clear comparison.

In the membrane potential instead we can see some noise while for potassium and calcium activation the noise is not present since the effects are too subtle to be seen at the current plot scale.

#4 - FitzHugh-Nagumo model
As stated before, we decided to compare the dynamics of the Morris-Lecar model with the FitzHugh-Nagumo model, to do so we implement both models and simulate them under similar conditions. 

The FitzHugh-Nagumo model is a simplified version of the Hodgkin-Huxley model that captures the essential features of neurons. It has two variables: the membrane potential v and a recovery variable w.

#5 - Comparison of Morris-Lecar with FitzHugh-Nagumo

Both models are stimulated with an input current that is represented as a rectangular pulse. The amplitude, start time, and duration of the pulse can be adjusted to simulate different experimental conditions.


A comparison between the deterministic Morris-Lecar model and FitzHugh-Nagumo models shows some differences. This is particularly evident in the provided plots where the FitzHugh-Nagumo model exhibits distinct behavior due to its simplified nature.

From a neurological perspective, the simulations provide insights into how neurons process input signals and generate action potentials. The Morris-Lecar model outputs can be interpreted as showing the neuron's rapid response to stimuli, indicated by a sharp spike in membrane potential. In contrast, the FitzHugh-Nagumo model shows a more complex graph and we believe because it depends on the chosen parameters. 





The first plot represents the input current over time, which is a simulation of an external stimulus applied to a neuron. The stimulus is modeled as a current pulse with a specific amplitude of 50 mA that begins at 200 ms and ends at 800 ms and this is analogous to an experimental setup where a neuron is injected with a current using an electrode, to observe how it reacts to such stimulation.

In the plot simulation, you can see a sharp spike in the membrane potential (blue line) that occurs shortly after the onset of the stimulus. The action potential is characterized by a rapid depolarization, followed by repolarization before the membrane potential returns to the resting state. 

#Conclusion

In conclusion, while the Morris-Lecar model posed a significant challenge due to its complexity and our lack of prior exposure, our decision to explore this unfamiliar territory proved to be a valuable learning experience. Despite initial difficulties in understanding and implementing the model, our collaborative effort and perseverance led to successful simulations and analysis. We also had some issues in interpreting the plot but we managed through it. This journey not only broadened our understanding of computational neuroscience but also strengthened our problem-solving skills. 


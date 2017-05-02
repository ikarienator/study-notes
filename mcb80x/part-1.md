Electrical Properties of the Neuron - 1.1

Link: [https://www.mcb80x.org/lessons#module-1](https://www.mcb80x.org/lessons#module-1)

## Lesson 1.1: The Resing Potential

### The History of Bioelectricity

In 1771, Luigi Galvani dissected a frog and reanimated a leg with a charged scalpel, and introduced the notion of electric fluid. Alessandro Volta, a physicist and contemporary of Galvani, repeated the experiments but doubted the electric fluid in animals. He invented the first battery, proving the similar electricity could be generated outside of a animal body. Galvani's name lived on. Volta coined the term Galvanism referring to electric phenomenon in living creatures. the many modern terms, such as galvanic, and galvanometer.

Galvani's electric fluid is not scientifically correct. But bioelectricity play a central rol in the function of nervous system.

### Introducing the Resting Potential

A typical neuron has a body named "Soma". Outside of the body, are "Axon"s and "Dendrite"s. The cell is separated from the outside by "Cell Membrane".

Even if the cell is at rest, it is not electrical neutral. this potential between the two sides of the membrane is call the "Membrane Potential". It is around -70mV, where outside of a cell is defined as zero. We'll be focusing on just a few key players, the charged ions Na<sup>+</sup>, K<sup>+</sup>, Ca<sup>2+</sup>, Cl<sup>-</sup>. They are important on generating the rest potential of a neuron.

The rest potential is induced by the diffusion of different ions with different sizes. Only some of the ions can pass through the membrane. Each side of the membrane is electrical neutral. The membrane works as a capacitor. The membrane has ion channels on the membrane. If the cell stated with balanced ions with higher density, then the ion channels opened up on the membrane only allow K<sup>+</sup> to pass-through, then the potential will become negative, because the the higher concentration of the K<sup>+</sup> will try to diffuse to the outside of the cell.

The equilibrium potential is determined by the Nernst Equation:
$$
E_{ion}=\frac{RT}{zF}\ln\frac{[Ion]_\mathrm{Extracellular}}{[Ion]_\mathrm{Intracellular}}
$$

where $T$ is temperature in Kelvin, $R$ is the Boltzmann constant, $z$ is the valence is the charge of the ion (1 for $K^+$, 2 for $Ca^{2+}$), $F$ is the  Faraday constant.
The rest potential of a neuron is closed to the Nernst Potential of Potassium.

### Driving Force

Driving force is the force that an ion is pushed out side of a membrane.

### Ion filters

Ion filter can selectively stop sodium ion but let potassium ion through. The ions in water form solvation shell with polarized water molecules. The ion channel protein simulates the concentration of the solvation shell of one type of ion.

### The Sodium/Potassium Pump

Selective ion channels are the most basic ion channels. We call them the "leakage channels" since it only allow ions to flow from higher concentrated side to lower concentrated side. In a real neuron, we have a lot of passive potassium selective channels, and fewer passive sodium channels and chlorine channel. Potassium dominate the potential.

If the this allows the ions the eventually come to equilibrium, the potential will be gone. There is another type of ion channel, that uses ATP as energy, that transports sodium ions from lower concentration side to higher concentration side. It consumes up to 70% of ATP required for a brain cell to work. About 1/3 of all the energy intake from food goes to this pump.

### GHK Equation

Permeability $P$ is the measurement of how easily an ion can pass-through a membrane. If the membrane is only permeable to potassium. The overall potential will equal to the Nernst potential of potassium. However, since the membrane is permeable to other ions, we have to correct the Nernst equation to GHK equation:
$$
E_{m,K_x,Na_{1-x},Cl} = \frac{RT}{F}\ln\left(\frac{
    P_{Na^+}[Na^+]_{out} + P_{K^+}[K^+]_{out}+ P_{Cl^-}[Cl^-]_{in}
    }{
    P_{Na^+}[Na^+]_{in} + P_{K^+}[K^+]_{in}+ P_{Cl^-}[Cl^-]_{out}
    }\right)
$$

One way we might imagine to calculate the resting potential for a whole cell would be simply sum up the contributions from each ion's Nernst potential. But we already saw how important the selective permeability of the membrane to particular ions is to maintaining the resting potential.

It is hard to change the potential by pumping sodium ions, but it is much easier to change the potential to fine tune the permeability of the ion channel.

### Bonus Content

The brain is covered in meninges.
The valleys are called sulci (Suhl-sahy) and gyri(jahy-rahy) are the mountains. Frontal cortex, we believe, is involed in control and self-monitoring and executive functions.

Dural sac, the tough tissue at the back part of the occipical skull (bottom part of the skull, where cerebellum sits), continues down the spinal cord. The bone to potect the spinal cord is called vertebrae.

Inside the meninges is the cerebral spinal fluid.

There are 31 vertebrae. 7 cervical, 12 thoracic, 5 lumbar, 5 sacral and 2 cocygeal(kok-sahy-jeez).

#### Supplemental: [UTHealth Neuroscience Online Textbook: Chapter 1](http://neuroscience.uth.tmc.edu/s1/chapter01.html)

## Lesson 1.2: Passive Membrane Properties

### Changing the membrane potential

Let discuss how fast a neuron can change its state.

Two additional analogy from electronics: resistance and capacitance. Conductance is the inverse of resistance. The higher permeable the channel is, the lower the resistance. Typically we measure the resistance of the membrane by $\Omega / mm^2$. Another important resistant quantity, is the resistance through the cytoplasm(细胞质) of the cell. The membrane also forms a capacitor.

Ohm's law:
$$
I = \frac{V}{R}
$$

The length constant $\lambda$ of transmission is defined as the distance from where the impulse voltage decreased to 36% of the original value. The constance is:
$$
\lambda = \sqrt{\frac{R_\mathrm{membrane}}{R_\mathrm{axial}}}\quad.
$$
$R_\mathrm{membrane}$ has the unit ${\Omega \cdot cm}$, and the ${R_\mathrm{axial}}$ has the unit of $\Omega/cm$.

At the same time, the capacitance of the membrane effects the response time. The time constant $\tau$ of transmission is defined as the time from where the capacitor can charge up to 63% of saturated capacity. The constant is:
$$
\tau = R_\mathrm{membrane}C_\mathrm{membrane}
$$

To increase the transmission speed of the signal, neurons needs to decrease the membrane capacitor, some neurons use a special trick called myelination to effectively wrap more layers around the membrane.

We don't always want capacitance to be lower. Sometimes we want to integrate signals across time, so it's useful to have a more slowly changing membrane potential that can average signals over time.

## Lesson 1.3: Action Potential

### Action Potential

Since there are much more potassium channels than sodium channels, the key driver for the membrane potential is the permeability of the sodium channels. There are channels that changes the permeability according to the membrane potential, called voltage gated channels.

There are voltage gated channels for both sodium and potassium. The potassium ones are slightly slower than the sodium ones. When a sodium channel opens, the membrane voltage increases; then the potassium channel opens, the voltage decreases. Both types of channels work together to regulate a temporary elevated potential into a impulse.

### Kinetics
Kinetics is the probabilistic temporal dynamics of a reaction or movement from one state to another. If the kinetics of the sodium and potassium channel are equal, there will be no action potential. The kinetics also causes a refractory period, which is the time period after one action potential where we cannot easily fire another action potential.

## Lesson 1.4: Action Potential Propagation

The reason to use action potential instead of moving substances around is speed. But like copper wires, the electric signal decays through the axon. One way to solve this, is to increase the voltage. But the -70mV is already close to the breakdown voltage of the neuron. The other way is to amplify the signal every so often.

The speed of the action potential is determined by the capacitance of the membrane and the resistance along the axon. Some animals evolved _giant axons_ to make the resistance lower. The axons in squid is as thick as 1 mm. If human hands were using axons this thick, the hand will has a diameter of over a meter. (This gives an magnitude estimation that there are 1 million neurons for each hand). Instead, some organisms uses extra insulation around the axons to decrease the capacitance of the membrane, this is called myelin. Myelins serves as barriers to ion leakage, thus increase the membrane resistance and lower the membrane capacitance.

Myelins are produced by supporting cells called Glial cells, also known as Glia. The two types of Glias to produce myelins are called Oligodendrocytes in the central nervous system, and Schwann cells in the peripheral nervous system. Apart from water, the glia is mostly made from lipids, which gives the white color of the white matter in the brain. Myelinated axons look like a string of sausages with the space in between the myelins sections contains a high density of voltage gated sodium and potassium channels. This allows for the action potential to jump from node to node. The open nodes are called the Nodes of Ranvier.

## Lesson 1.5 Rate Coding

The shape of the signal does not change, what changes is the rate of the firings.

### Neuropharmacology

Injecting nicotine increases the probability of firing (excitatory). Glutamate decreases the probability of firing (inhibitory).
(Video: [https://www.mcb80x.org/course/electrical_properties/labs/neuropharmacology](https://www.mcb80x.org/course/electrical_properties/labs/neuropharmacology). I think this experiment is quite flawed. First, we are using the same grasshopper for 3 experiments, this means the injections might interfere with each other. We have draw at least three more hypotheses: 1. too much pressure slowed the neuron down, 2. MSG neutralized the nicotine chemically, or 3. MSG contains sodium ion, which somehow made the neuron firing less intense (I suspect the opposite would happen)).

### The Electromyograph
(Recording signals to hands and cheek muscles)
(Recording a grasshopper's visual signals)
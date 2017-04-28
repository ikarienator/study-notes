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

### Action Potential
# Topology-Optimization-using-Compliiant-mechanism

The goal of this project is to extend the pyTop code written by professor Boddeti to design of compliant mechanism. 

To do this modifications were made in the code to:

1.Ability to attach springs to the 2D continuum – this requires us to add the spring stiffnesses 𝑘𝑖𝑛
and 𝑘𝑜𝑢𝑡 at appropriate locations in the global stiffness matrix.

2. The objective should be the displacement at the output node and the gradients are to be calculated 
using the adjoint method – this is implemented in the FESolver class.

3. Making these adjustments to the bisectioning algorithm that updates the Lagrange multiplier
a. Change “move” from 0.2 to 0.1
b. Change “eta” from 0.5 to 0.3
c. Modifying the convergence criteria to 𝑙2−𝑙1/𝑙1+𝑙2 > 10^−4 𝑎𝑛𝑑 𝑙2 > 10^−40
d. Unlike the minimum compliance problem, the objective gradients here are not guaranteed 
to be negative. So,
𝐵𝑘 = max(10^−10,𝐵𝑘)

The implementation is then verfied with the design of force inverter where the 
goal is to maximize 𝑢𝑜𝑢𝑡 given 𝑓𝑖𝑛. Assuming 𝐸 = 1, 𝜈 = 0.3 and the volume fraction is 0.3. Using symmetry 
in setting up the FE problem; a coarse and fine mesh are provided. Post-processing the results to get an stl
file that could be used for manufacturing

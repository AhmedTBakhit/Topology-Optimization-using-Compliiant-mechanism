# Topology-Optimization-using-Compliiant-mechanism

The goal of this project is to extend the pyTop code written by professor Boddeti to design of compliant mechanism. 

To do this modifications were made in the code to:

1.Ability to attach springs to the 2D continuum β this requires us to add the spring stiffnesses πππ
and πππ’π‘ at appropriate locations in the global stiffness matrix.

2. The objective should be the displacement at the output node and the gradients are to be calculated 
using the adjoint method β this is implemented in the FESolver class.

3. Making these adjustments to the bisectioning algorithm that updates the Lagrange multiplier
a. Change βmoveβ from 0.2 to 0.1
b. Change βetaβ from 0.5 to 0.3
c. Modifying the convergence criteria to π2βπ1/π1+π2 > 10^β4 πππ π2 > 10^β40
d. Unlike the minimum compliance problem, the objective gradients here are not guaranteed 
to be negative. So,
π΅π = max(10^β10,π΅π)

The implementation is then verfied with the design of force inverter where the 
goal is to maximize π’ππ’π‘ given πππ. Assuming πΈ = 1, π = 0.3 and the volume fraction is 0.3. Using symmetry 
in setting up the FE problem; a coarse and fine mesh are provided. Post-processing the results to get an stl
file that could be used for manufacturing

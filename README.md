# Code-for-Shape-and-Topology-Optimization-for-Elasticity-System
This repository provides the implementation used in the numerical experiments of our manuscript. It studies **compliance minimization in linear elasticity** under a volume-type constraint, using a **level-set framework** combined with **shape gradients** and **topological derivatives**.

We consider a linearly elastic body occupying a domain Ω ⊂ R^d (d = 2 or 3), whose boundary is decomposed as:

∂Ω = Γ_D ∪ Γ_N ∪ Γ,

where Γ_D is the clamped (Dirichlet) boundary, Γ_N is the traction (Neumann) boundary, and Γ denotes the free/design boundary. The displacement field u solves the standard equilibrium equations of linear elasticity with no body forces:

- −div σ(u) = 0 in Ω
- σ(u) n = g on Γ_N
- u = 0 on Γ_D
- traction-free condition on the remaining boundary

The design objective is to improve structural stiffness, measured by the **compliance**:

J(Ω) = ∫_{Γ_N} g · u ds,

subject to a volume constraint |Ω| ≤ V0. In addition, we employ a **penalized/regularized formulation** that promotes a nearly uniform strain-energy density along the design boundary, together with a stabilized descent strategy in the level-set update.

## Sensitivity information and optimization strategy

The implementation combines:

1. **Shape sensitivity (shape gradients)** derived via the speed method and an adjoint formulation, leading to a Hadamard-type boundary expression used to drive boundary motion (with an H¹-gradient flow for regularization).
2. **Topological sensitivity (topological derivatives)** based on classical topological asymptotic analysis for elasticity. Small inclusions/voids are modeled through a local perturbation ω_ε( x̂ ), and the corresponding asymptotic expansion involves a **material contrast parameter** γ and the associated (isotropic) **polarization tensor** P_γ. This provides a quantitative indicator for nucleating/removing holes and redistributing material.

We propose and compare three algorithms: a shape-gradient-only method, a topology-derivative-only method, and a hybrid alternating strategy combining both mechanisms.

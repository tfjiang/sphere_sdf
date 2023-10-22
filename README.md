# An Implemention of Reach For the Spheres: Tangency-Aware Surface Reconstruction of SDFs
## 1. Brief Info
**Title**: Reach For the Spheres: Tangency-Aware Surface Reconstruction of SDFs

**Authors**: Silvia Sellan,Christopher Batty,Oded Stein

## 2. Implementations
Given a SDF notated as $\{(p_i,s_i)|p_i\in \mathbb{R}^3, s_i\in \mathbb{R}\}$, this work will reconstruct a surface $\Omega$ which satisfy the following constraint $\phi(p_i,\Omega)=s_i, \forall i\in\{1,...,n\}$, where $\phi$ denotes the signed distance.

The surface is the solution of such optimization problem:
$$\varepsilon_\phi(\Omega)=\frac{1}{2}\Sigma_{i=1}^{n}(\phi(p_i,\Omega)-s_i)^2$$
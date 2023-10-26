# An Implemention of Reach For the Spheres: Tangency-Aware Surface Reconstruction of SDFs
## 1. Brief Info
**Title**: Reach For the Spheres: Tangency-Aware Surface Reconstruction of SDFs

**Authors**: Silvia Sellan,Christopher Batty,Oded Stein

## 2. Implementations
Given a SDF notated as $\{(p_i,s_i)|p_i\in \mathbb{R}^3, s_i\in \mathbb{R}\}$, this work will reconstruct a surface $\Omega$ which satisfy the following constraint $\phi(p_i,\Omega)=s_i, \forall i\in\{1,...,n\}$, where $\phi$ denotes the signed distance.

The surface is the solution of such optimization problem:
$$\varepsilon_\phi(\Omega)=\frac{1}{2}\Sigma_{i=1}^{n}(\phi(p_i,\Omega)-s_i)^2$$
To achieve such result, we can follow a gradient flow of the SDF energy
$$\frac{\partial \Omega}{\partial t}=-\nabla\varepsilon_\phi(\Omega)$$

By using implicit scheme, the surface sequence can be updated by:
$$\Omega^t=\Omega^{t-1}-\tau\nabla\varepsilon_\phi(\Omega^t) $$
And by using minimal movement scheme, the above equation equals
$$\Omega^t=\argmin_\Omega(\frac{1}{2\tau}\|\Omega-\Omega^{t-1}\|^2_2+\varepsilon_\phi(\Omega))$$
where $\Omega=\{V,F\}$.

$\|\Omega-\Omega^{t-1}\|^2_2$ can be discretized into $\|V-V^{t-1}\|^2_M$, where $\|\|^2_M$ is defined as $\cdot^TM\cdot$. 

The $\varepsilon$ term is not differentiable which will lead to numerical problem in minimization. The author choose a scheme to approximate it by first using distance between closet points instead of $V-V^{t-1}$.
$$\varepsilon_\phi(\Omega)=\frac{1}{2}\sum_{i=1}^n(\phi(p_i,c_i(\Omega))-s_i)^2$$
where $c_i(\Omega)$ is the closet point on the surface $\Omega$ to $p_i$
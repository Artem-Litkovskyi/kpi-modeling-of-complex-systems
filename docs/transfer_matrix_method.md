# Transfer Matrix Method

Given a system of connected 1D elements:
- $\vec{Y}^i(s)$ -- state ($N \times 1$ vector) of an $i$-th element at a point $s$.
- $\vec{Y}^i_0 = \vec{Y}^i(0)$ -- state at the beginning of an $i$-th element.
- $\vec{Y}^i_e = \vec{Y}^i(s_e)$ -- state at the end of an $i$-th element.

The system is described by such equations:
1. **Transfer equations**: the relation between $\vec{Y}^i_0$ and $\vec{Y}^i(s)$.
2. **Conjugation equations**: the relation between $\vec{Y}^i_e$ and $\vec{Y}^{i+1}_0(s)$.
3. **Boundary conditions**: $N/2$ additional equations per each boundary element.

## Transfer Equations

A state of an element at a certain point can be calculated by the transfer equation:

$$\vec{Y}^i(s) = A(s)\vec{Y}^i_0+\vec{B}(s)$$

The transfer matrix $A(t)$ and the vector $\vec{B}(t)$ are found analytically by the Krylov method for each problem individually (see `docs/krylov_method.md`).

The state at the end of the element is:

$$\vec{Y}^i_e = A(s_e)\vec{Y}^i_0+\vec{B}(s_e)$$

## Conjugation Equations

### Two Elements

To pass the state from the end of an element to the beginning of the next one a conjugation equation is used:

$$\vec{Y}^{i+1}_0 = C\vec{Y}^i_e+\vec{D}$$

The simplest case is when the state is continuous: then $C = I$ (identity matrix) and $\vec{D} = 0$.

However, for some problems (such as a beam supported at conjugation points) the matrix form of this equation can't be used. Then the single matrix equation is replaced by a system of $N$ regular  equations.

### Multiple Elements

TODO
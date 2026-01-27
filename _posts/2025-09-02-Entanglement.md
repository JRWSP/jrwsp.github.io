---
layout: post
title: Quantum entanglement verifying
date: 2025-09-02 10:00:00
description:  Numerical entanglement checking of a pure state
tags: python quantum 
categories: posts
thumbnail: assets/img/posts/2025-09-02-Entanglement/SVD.jpg
---

One day I got a question from a friend who left academic to join the industry. The question itself is quite simple and basic, however, it is fundamental to understand more complicated idea in quantum physics. So I think it would be for a benefit of mankind (okay, I might be bit over-exaggerated 🤣) to leave the note about it here. 

###  Question: given a vector of any multipartite (pure) quantum state, $\ket{\psi}$, how to verify its entanglement? <br>
Answer: To answer this I will consider only verifying whether or not the state is entangled, without distinguishing between fully and partial entanglement. Also I won't address the experimental implementation, which can be more complicated than on-paper calculation. <br>
First, consider bi-partition of the system containing $A$ and $B$ parts. A straightforward way to prove whether the pure state is entangled (between $A$ and $B$) is calculate the reduced density matrix $$\rho_{A(B)} = \text{Tr}_{B(A)}(\ket{\psi}\bra{\psi})$$ for one of the subsystem (particle, spin, qubit or whatever). Thus, looks at the number of singular value<br>

$$
\text{Rank}(\rho_{A(B)}) 
\begin{cases}
= 1, & \text{separable} \\
> 1, & \text{entangled}
\end{cases}
$$

Or by calculating the purity **of the reduced state**,

$$\text{Tr}(\rho_{A(B)}^{2})
\begin{cases}
= 1, & \text{separable}\\
< 1 & \text{entangled}
\end{cases}
$$


Then, let me show simple examples in Python. For demonstration, let us consider a quantum state of two qubits. If the state is separable, e.g. $\ket{\psi} = \ket{00}$

```python
import qutip as qt
import numpy as np
def print_state_info(state, label):
    print(f"A {label} state:\n{state.data_as()}")
    print(f"Tracing out the 2nd qubit, Tr_2({label}):\n{state.ptrace(0).data_as()}")
    print(f"Purity, {state.ptrace(0).purity()}")
```


```python
prod = qt.tensor([qt.basis(2,0)]*2)
print_state_info(prod, "|00>")
```

    A |00> state:
    [[1.+0.j]
     [0.+0.j]
     [0.+0.j]
     [0.+0.j]]
    Tracing out the 2nd qubit, Tr_2(|00>):
    [[1.+0.j 0.+0.j]
     [0.+0.j 0.+0.j]]
    Purity, 1.0


Meanwhile for entangled state, such as GHZ state or W state:


```python
ghz = qt.ghz_state(2)
print_state_info(ghz, "|00> + |11>")
```

    A |00> + |11> state:
    [[0.70710678+0.j]
     [0.        +0.j]
     [0.        +0.j]
     [0.70710678+0.j]]
    Tracing out the 2nd qubit, Tr_2(|00> + |11>):
    [[0.5+0.j 0. +0.j]
     [0. +0.j 0.5+0.j]]
    Purity, 0.5000000000000002



```python
w = qt.w_state(2)
print_state_info(w, "|10> + |01>")
```

    A |10> + |01> state:
    [[0.        +0.j]
     [0.70710678+0.j]
     [0.70710678+0.j]
     [0.        +0.j]]
    Tracing out the 2nd qubit, Tr_2(|10> + |01>):
    [[0.5+0.j 0. +0.j]
     [0. +0.j 0.5+0.j]]
    Purity, 0.5000000000000002


Another way of checking entanglement is by checking the number of singular values (i..e Schmidt rank) of $\ket{\psi}$, which can be obtained via singular value decomposition (SVD). <br>
<div class="row mt-3">
    <div class="col-sm-8 col-md-6 mx-auto mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/posts/2025-09-02-Entanglement/SVD.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

$$
\text{Schmidt Rank}(\ket{\psi}) 
\begin{cases}
= 1, & \text{separable} \\
> 1, & \text{entangled}
\end{cases}
$$

While this approach is mathematically similar to counting the rank of $\rho_{A(B)}$, it can be computationally more efficient as no density matrix is computed. Using SVD also allowing truncation of singular value which can lead to efficient approximation of the state for larger system size (as used in Matrix Product State (MPS) technique). But it is outside scope of this post. <br>
In order to calculate an SVD, $\psi$ has to be written as a matrix. This operation is called `reshape`. For 2 particle, we can convert a $d^{2}$-dimensional vector to an $(d*d)$ matrix 


```python
def print_state_svd(state, label):
    state_svd = state.full().reshape(2,2)
    svd = np.linalg.svd(state_svd)
    print(f"{label} state has dimension {state.shape}")
    print(f"The converted matrix with dimension {state_svd.shape}")
    print(f"{state_svd}")
    print(f"SVD of {label} state has schmidt rank = {len(svd[1] > 1e-10)} with singular values = {svd[1]}")
```


```python
print_state_svd(ghz, "|00> + |11>")
```

    |00> + |11> state has dimension (4, 1)
    The converted matrix with dimension (2, 2)
    [[0.70710678+0.j 0.        +0.j]
     [0.        +0.j 0.70710678+0.j]]
    SVD of |00> + |11> state has schmidt rank = 2 with singular values = [0.70710678 0.70710678]



```python
print_state_svd(prod, "|00>")
```

    |00> state has dimension (4, 1)
    The converted matrix with dimension (2, 2)
    [[1.+0.j 0.+0.j]
     [0.+0.j 0.+0.j]]
    SVD of |00> state has schmidt rank = 1 with singular values = [1. 0.]


## References

1. [QuTip](https://qutip.org/)
2. [Reduced density matrix method](https://physics.stackexchange.com/questions/70436/differences-between-pure-mixed-entangled-separable-superposed-states)
3. [SVD method](https://www.math3ma.com/blog/understanding-entanglement-with-svd)
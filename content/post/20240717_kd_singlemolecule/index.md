---
title: "Dissociation constant from single-molecule experiments"
date: 2024-07-17
---

Lets consider a simple two-state binding experiment where a protein binds a ligand, and upon binding there is a conformational change such that the bound state can be descriminated from the apo state by a single-molecule FRET experiment.

(For the smFRET initiated: we are here talking about a confocal solution based ALEX smFRET experiment)

  

#TODO mhchem

$$
P + L <-> PL
$$


$$
\ce{P + L <=>[k_{on}][k_{off}] PL}
$$
  

The differential equations for this reaction scheme are:
  

$$
\begin{eqnarray}
\frac{\partial [P]}{\partial t} = - k_{on} [P][L] + k_{off} [PL] \\
\frac{\partial [L]}{\partial t} = - k_{on} [P][L] + k_{off} [PL] \\
\frac{\partial [PL]}{\partial t} = k_{on} [P][L] - k_{off} [PL]
\end{eqnarray}
$$

We now want to find the dissociation constant $K_d$, which is defined as:
 
$$
K_d \equiv \frac{k_{off}}{k_{on}}
$$
 

There are two main properties of single-molecule experiments important for the determination of $K_d$: 
1. In the smFRET experiment, the protein $P$ is labelled and is present at low (~100 pM) concentrations. This means that the concentration of the ligand $L$ will not notably decrease upon binding the protein when forming the complex $PL$. Therefore, we can assume that the concentration ligand $[L]$ is always equal to the initial concentration ligand $[L_{0}]$.
2. In smFRET experiments, we don't measure the concentration of the labelled protein, but rather we measure the fraction of either $P$ or $PL$ with respect to the total amount of labelled protein. 

From 2), we can write down how the fractions we measure relate to concentrations:

$$
\begin{eqnarray}
P_f = \frac{[P]}{[P] + [PL]} \\ 
PL_f = \frac{[PL]}{[P] + [PL]}
\end{eqnarray}
$$

Where $P_f$ and $PL_f$ are now the fractions of apo protein and complexed protein, respectively. The denominators of the above expression is the total amount of protein and is therefore constant in time. Therefore, we can divide the differential equations above by this sum to transform the differential equations to now describe fractional populations instead of concentration. 

$$
\begin{eqnarray}
\frac{\partial P_f}{\partial t} = - k_{on} P_f[L_0] + k_{off} PL_f \\
\frac{\partial PL_f}{\partial t} = k_{on} P_f[L_0] - k_{off} PL_f
\end{eqnarray}
$$

Where we have also used the approximation that $[L] = [L_0]$ from 1). If we now further assume that the equilibrium is at steady-state, no changes in time occur anymore and we can set the left hand side of the equations to zero. Rearranging the equation then gives:

$$
\frac{k_{off}}{k_{on}} = \frac{P_f}{PL_f}[L_{0}]
$$
or 

$$
K_d = \frac{P_f}{PL_f}[L_{0}]
$$
To sanity check: if the affinity goes down, eg $k_{off}$ increases, $K_d$ becomes a bigger nummer (small $K_d$ = good binding), and the fraction of the free protein goes up as expected. 

From this equation we can see that we can find the dissociation constant from a single smFRET measurement by simply multiplying the free/bound ratios of protein with the known concentration of ligand added, and no titration is needed. Of course, for higher accuracy it is better to take multiple measurements around the $K_d$ and least-squares fit the available data. Just make sure that the concentrations are around the $K_d$.

Perhaps its 
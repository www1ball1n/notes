---
title: A Simpler Manual to Wien2k
published: 2026-07-21
description: ''
image: ''
tags: [DFT]
category: 'Technical'
draft: false 
lang: ''
---

> Just wanna write a simpler personal manual to Wien2k

# Flow of input and output files
Each program is started with such command:
```
x program -d
```
by running this, the `.def` files are automatically generated. Each program reads and writes the following files:
```
case.struct
case.inX
case.outputX
```
The programs of the SCF cycle write
```
case.scfX
program.error
```

# Master file: case.struct
:::important
use REPLACE rather than DELETE and INSERT during edit. Also the parameter R0 is element-specifically chosen.
:::

**Parameters**
RELA / NREL: relativistic or not.

NPT (in line 7): number of radial mesh points, must always be odd, no need to alter

R0: first radial mesh point, cared automatically

RMT: muffin-fin radius, or atomic sphere radius. automatically set by `setrmt_lapw`

ROTLOC: local rotation matrix. Transforms the global coordinate system into the local at the given atomic site. SYMMETRY calculate the point group symmetry and determines ROTLOC automatically. See: Appendix A & 10.3

# case.scf
-:ENE total energy

:WAR warnings

:DIS charge distance between last 2 iterations. $\int{|\rho_n-\rho_{n-1}|\mathrm{d}^3\mathbf{r}}$ , convergence test.

:FGLxxx force

:QTL partial charge

**type of calculation, parameters: also can be checked by :xxx, like :POT ..., see the according part**

:MMIxxx magnetization of atoms

:MMTOT total magnetization

:ORBxxx orbital moment, must use -so

:SPIxxx spin moment, must use -so. without -orbc

:::note
:ORB is the orbital moment of density matrixed elements.
:SPI is the spin moment of density matrixed elements
:MMI is the **spin** inside the muffin tin.
:::

best monitor several quantities, `scfmonitor_lapw` is usable.




# Initialization programs
Only note here:

NN defines RMT, if NN crashes, the `.struct` file is probably problematic.

LSTART generates free atomic densities and determines how the different orbitals are treated in the band structure calculations (i.e. as core or band states, with or without local orbitals,...).

KGEN generates k-mesh at irreducible part of the BZ

DSTART generates a starting density by a superposition of atomic densities generated in LSTART.

better follow `init_lapw -m`. 
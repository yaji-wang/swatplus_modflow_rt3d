## 1. RCH package
the boundary for recharge is set as "into the highest cell in a vertical column", namely NRCHOP=3
(1) recharge water volume: VBVL  (mf_gwf2rch7.f -> line 400 - line 407)

## 2. RIV package
need to check the specific codes for boundary condition setup

## 3. UPW package
In my case, the UPW package is used to calculate the intercell conductance (i.e., saturated thickness) using upstream weighting method. This kind of method can help avoid non-physical oscillations near the water table and imrove Newton solver convergence.
- as for unconfined layers, the thickness varies with head
- as for confined layers, the thickness remains a constant

## boundary between layers
(need to test inputs updates for rt3d if multiple layers)

# Confined layer slips: Irradiation-induced void

## Foreword

The purpose of this project is to calculate the confined layer slip (CLS) process in nanolaminated Ag and two types of Ag/Cu nanolaminates containing a void due to irradiation.

Read the following journal articles to understand how the CLS process can be calculated:

- Mahshad Fani, Wu-Rong Jian, Yanqing Su, Shuozhi Xu, [Confined layer slip process in nanolaminated Ag and two Ag/Cu nanolaminates](https://doi.org/10.3390/ma17020501), Materials 17 (2024) 501
- Weisen Ji, Wu-Rong Jian, Yanqing Su, Shuozhi Xu, Irene J. Beyerlein, [Role of stacking fault energy in confined layer slip in nanolaminated Cu](http://dx.doi.org/10.1007/s10853-023-08779-8), J. Mater. Sci. 59 (2024) 4775--4787
- Wu-Rong Jian, Shuozhi Xu, Yanqing Su, Irene J. Beyerlein, [Role of layer thickness and dislocation distribution in confined layer slip in nanolaminated Nb](http://dx.doi.org/10.1016/j.ijplas.2022.103239), Int. J. Plast. 152 (2022) 103239
- Wu-Rong Jian, Yanqing Su, Shuozhi Xu, Weisen Ji, Irene J. Beyerlein, [Effect of interface structure on dislocation glide behavior in nanolaminates](http://dx.doi.org/10.1557/s43578-021-00261-y), J. Mater. Res. 36 (2021) 2802--2815

## LAMMPS

Following [our previous project](https://github.com/shuozhixu/Materials_2024), we can build LAMMPS with MANYBODY and VORONOI packages and submit jobs on [OSCER](http://www.ou.edu/oscer.html).

63 LAMMPS simulations will be conducted in this project. Each time we run a new simulation, create a new directory.

The interatomic potential is the same one used in our previous project.

## Related to a previous project

In [our previous project](https://github.com/shuozhixu/Materials_2024), the CLS processes in nanolaminated Ag and two types of Ag/Cu nanolaminates were studied. The layer thickness for each metal was 5 nm. No cavities were involved. According to four experimental Ag/Cu nanolminates papers above, (i) there is a cavity-free zone within 20 nm from the interface in the Cu layer and (ii) the cavity can be a void or a He bubble. For cavities near the interface, they adhere to the interface in the Ag layer rather than straddling the interface in both metals. Therefore, if one were to insert a cavity in our previous 5-nm-thick model, the cavity either adheres to the interface in the Ag layer or sits at the center of the Ag layer. In addition, the cavity's diameter varies from 1 nm to 12 nm according to [Wang et al.](https://doi.org/10.1016/j.actamat.2018.09.003) While no dislocation climb was observed in our previous project, it might occur because of the void, see [this paper](https://doi.org/10.1016/j.actamat.2012.03.050).

Unfortunately, there is no interatomic potentials for Ag/He, and so we only consider void.

## Nanolaminated Ag

Our previous project considered CLS in all three different slip planes. Here, let's consider all of them.

Therefore, we need to insert a void either at the interface or the center of a Ag layer where CLS takes place. For each slip plane, let the dislocation glide through the center of the void. The insertion of the void can be done by modifying the LAMMPS input files from [our previous project](https://github.com/shuozhixu/Materials_2024). Three void diameters can be considered: 0.5 nm, 1 nm, and 2 nm. As an example, please see lines 25 to 34 of the `lmp_center.in` and `lmp_interface.in` files in this GitHub repository. They are for a void diameter of 2 nm.

Since there are three void sizes, two void locations, and three slip planes, 18 LAMMPS simulations need to be conducted.

## Ag/Cu Nanolaminate - type 1

Our previous project considered CLS in 10 different slip planes, which possess different critical stresses for CLS. Here, let's consider three planes: one with the maximum critical stress, one with the minimum critical stress, and another with the average critical stress.

As a result, 18 LAMMPS simulations need to be conducted.

## Ag/Cu Nanolaminate - type 2

Along the same line of thought, let's consider three planes here too. Similarly, another 18 LAMMPS simulations should be conducted.

## Single crystalline pure metals

There are two pure metals, Cu and Ag. To provide references, we can simulate the dislocation/void interactions in Ag, and compare results with those in nanolaminates. The dislocation line should be 5 nm, the same as those used in nanolaminates. There are two types of boundary conditions along the dislocation line direction: periodic boundary conditions and traction-free boundary conditions. For the first boundary condition, the two void positions are equivalent, and so only the three void diameters should be considered. For the second boundary condition, the two void positions are not equivalent. Thus, 9 LAMMPS simulations should be conducted in single crystalline Ag.

The dislocation/void interactions in a Cu single crystal where the periodic boundary conditions were applied along the dislocation line were modeled in [a previous paper](http://dx.doi.org/10.1088/1361-651X/ab8358), which should be studied closely.

## Reference

If you use any files from this GitHub repository, please cite

- Mahshad Fani, Luis Cervantes, Anshu Raj, Shuozhi Xu, [Effects of irradiation-induced voids on confined layer slips in metallic nanolaminates](https://doi.org/10.1063/5.0241799), J. Chem. Phys. 161 (2024) 214702
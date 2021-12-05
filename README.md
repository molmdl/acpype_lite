# ACPYPE

![GitHub](https://img.shields.io/github/license/alanwilter/acpype?style=plastic)
![GitHub release (latest by date)](https://img.shields.io/github/v/release/alanwilter/acpype?display_name=tag&logo=github&style=plastic)
![GitHub Release](https://img.shields.io/github/release-date/alanwilter/acpype?style=plastic&logo=github)<!-- ![GitHub All Releases](https://img.shields.io/github/downloads/alanwilter/acpype/total?style=plastic) -->
![Docker Pulls](https://img.shields.io/docker/pulls/acpype/acpype?style=plastic&logo=docker)
![Docker Image Size (tag)](https://img.shields.io/docker/image-size/acpype/acpype/latest?style=plastic&logo=docker)
![Conda Version](https://img.shields.io/conda/vn/conda-forge/acpype.svg?style=plastic&logo=conda-forge)
![Conda Downloads](https://img.shields.io/conda/dn/conda-forge/acpype.svg?style=plastic&logo=conda-forge)<!-- ![Conda](https://img.shields.io/conda/pn/conda-forge/acpype?logo=conda-forge&style=plastic) -->
![PyPI](https://img.shields.io/pypi/v/acpype?style=plastic&logo=pypi)
![PyPI - Downloads](https://img.shields.io/pypi/dm/acpype?style=plastic&logo=pypi)
![GitHub Workflow Status](https://img.shields.io/github/workflow/status/alanwilter/acpype/check_acpype)
<!-- ![Scrutinizer code quality (GitHub/Bitbucket)](https://img.shields.io/scrutinizer/quality/g/alanwilter/acpype) -->
<!-- ![Scrutinizer coverage (GitHub/BitBucket)](https://img.shields.io/scrutinizer/coverage/g/alanwilter/acpype) -->

## AnteChamber PYthon Parser interfacE

A tool based in **Python** to use **Antechamber** to generate topologies for chemical
compounds and to interface with others python applications like CCPN and ARIA.

`acpype` is pronounced as _**ace + pipe**_

Topologies files to be generated so far: CNS/XPLOR, GROMACS, CHARMM and AMBER.

**NB:** Topologies generated by `acpype/Antechamber` are based on General Amber Force
Field (GAFF) and should be used only with compatible forcefields like AMBER and
its variant.

Several flavours of AMBER FF are ported already for GROMACS (see [ffamber](http://ffamber.cnsm.csulb.edu/)) as well as to XPLOR/CNS (see [`xplor-nih`](http://ambermd.org/xplor-nih.html)) and [CHARMM](https://www.charmm.org/).

This code is released under **[GNU General Public License V3](https://www.gnu.org/licenses/gpl-3.0.en.html)**.

### **NO WARRANTY AT ALL**

It was inspired by:

- `amb2gmx.pl` (Eric Sorin, David Mobley and John Chodera)
  and depends on `Antechamber` and `OpenBabel`

- [YASARA Autosmiles](http://www.yasara.org/autosmiles.htm) (Elmar Krieger)

- `topolbuild` (Bruce Ray)

- `xplo2d` (G.J. Kleywegt)

For Non-uniform 1-4 scale factor conversion (e.g. if using **GLYCAM06**), please cite:

> BERNARDI, A., FALLER, R., REITH, D., and KIRSCHNER, K. N. ACPYPE update for
nonuniform 1–4 scale factors: Conversion of the GLYCAM06 force field from AMBER
to GROMACS. SoftwareX 10 (2019), 100241. doi: 10.1016/j.softx.2019.100241

For `Antechamber`, please cite:
>
> 1. WANG, J., WANG, W., KOLLMAN, P. A., and CASE, D. A. Automatic atom type and
     bond type perception in molecular mechanical calculations. Journal of Molecular
     Graphics and Modelling 25, 2 (2006), 247–260. doi: 10.1016/j.jmgm.2005.12.005
> 2. WANG, J., WOLF, R. M., CALDWELL, J. W., KOLLMAN, P. A., and CASE, D. A.
     Development and testing of a General Amber Force Field. Journal of Computational
     Chemistry 25, 9 (2004), 1157–1174. doi: 10.1002/jcc.20035

If you use this code, I am glad if you cite:

> SOUSA DA SILVA, A. W. & VRANKEN, W. F.
ACPYPE - AnteChamber PYthon Parser interfacE.
BMC Research Notes 5 (2012), 367 doi: [10.1186/1756-0500-5-367](http://www.biomedcentral.com/1756-0500/5/367)

and (optionally)

> BATISTA, P. R.; WILTER, A.; DURHAM, E. H. A. B. & PASCUTTI, P. G. Molecular
Dynamics Simulations Applied to the Study of Subtypes of HIV-1 Protease.
Cell Biochemistry and Biophysics 44 (2006), 395-404. doi: 10.1385/CBB:44:3:395

Alan Silva, D.Sc.

alanwilter _at_ gmail _dot_ com

#### How To Use ACPYPE

##### Introduction

We now have an up to date *webservice* at **[Bio2Byte](http://bio2byte.be/acpype/)** (but it **does not** have the `amb2gmx` functionality).

To run `acpype`, locally, with its all functionalities, you need **ANTECHAMBER** from package
[AmberTools](http://ambermd.org/) and
[Open Babel](http://openbabel.org/wiki/Main_Page) if your input files are of PDB
format.

However, if one wants `acpype` just to emulate *amb2gmx.pl*, one needs nothing
at all but *[Python](http://www.python.org)*.

There are several ways of obtaining `acpype`:

1. Via **[CONDA](https://anaconda.org/search?q=acpype)**:

   *(It should be wholesome, fully funcional, all batteries included)*

   ```bash
   conda install -c conda-forge acpype
   ```

2. Via **[PyPI](https://pypi.org/project/acpype/)**:

   *(Make sure you  have `AmberTools` and, optionally but highly recommended, `OpenBabel` )*

   ```bash
   # You can use conda to get the needed 3rd parties for example
   conda create -n acpype --channel conda-forge ambertools openbabel

   # Or for Ubuntu 20:
   apt-get install -y openbabel python3-openbabel libarpack++2-dev libgfortran5

   pip install acpype

   # or if you feel daring

   pip install git+https://github.com/alanwilter/acpype.git
   ```

3. By downloading it via `git`:

   *(Make sure you  have `AmberTools` and, optionally but highly recommended, `OpenBabel` )*

   ```bash
   # You can use conda to get the needed 3rd parties for example
   conda create -n acpype --channel conda-forge ambertools openbabel

   # Or for Ubuntu 20:
   apt-get install -y openbabel python3-openbabel libarpack++2-dev libgfortran5

   git clone https://github.com/alanwilter/acpype.git
   ```

   **NB:** Using this mode, CHARMM topology files will not be generated.

4. Via **[Docker](https://hub.docker.com/repository/docker/acpype/acpype/)**:

   *(It should be wholesome, fully functional, all batteries included)*

   If you have Docker installed, you can run `acpype_docker.sh` by:

   NOTE: first time may take some time as it pulls the `acpype` docker image.

   On Linux / MacOS:

   ```bash
   ln -fsv "$PWD/acpype_docker.sh" /usr/local/bin/acpype_docker

   ```

   On Windows:
   Using Command Prompt:

    In the directory where the `acpype_docker.bat` file is found:

   ```bash
   setx /M path "%path%;%cd%"
   ```

   Commands:

   ```bash
   acpype_docker -i CCCC

   acpype_docker -i tests/DDD.pdb -c gas
   ```

**NB:**

- By installing via `conda` or using via `docker` you get `AmberTools v.21.11` and `OpenBabel v3.1.1`. Our `AmberTools v.21.11` is a stripped version from the original containing only the necessary binaries and libraries and comes with the `charmmgen` binary from `AmberTools17` in order to generate CHARMM topologies.
- By installing via `pip` you get `AmberTools` (as described above) embedded. However, the included binaries may not work in your system (library dependencies issues) and with only provide binaries for Linux (Ubuntu20) and macOS (Intel).

##### To Test, if doing via `git`

At folder `acpype/`, type:

```bash
./run_acpype.py -i test/FFF.pdb
```

It'll create a folder called *FFF.acpype*, and inside it one may find topology
files for GROMACS and CNS/XPLOR.

or using a molecule in [SMILES](https://archive.epa.gov/med/med_archive_03/web/html/smiles.html) notation:

```bash
./run_acpype.py -i CCCC # smiles for C4H6 1,3-Butadiene compound
```

It'll create a folder called *smiles_molecule.acpype*.

To get help and more information, type:

```bash
./run_acpype.py -h
```

##### To Install

At folder `acpype/`, type:

```bash
  ln -fsv "$PWD/run_acpype.py" /usr/local/bin/acpype
```

Then re-login or start another shell session.

If via `conda` or `pip`, `acpype` should be in your `$PATH`.

##### To Verify with GMX

GROMACS < v.5.0

```bash
cd FFF.acpype/
grompp -c FFF_GMX.gro -p FFF_GMX.top -f em.mdp -o em.tpr
mdrun -v -deffnm em
# And if you have VMD
vmd em.gro em.trr
```

GROMACS > v.5.0

```bash
cd FFF.acpype/
gmx grompp -c FFF_GMX.gro -p FFF_GMX.top -f em.mdp -o em.tpr
gmx mdrun -v -deffnm em
# And if you have VMD
vmd em.gro em.trr
```

##### For MD, do

GROMACS < v.5.0

```bash
grompp -c em.gro -p FFF_GMX.top -f md.mdp -o md.tpr
mdrun -v -deffnm md
vmd md.gro md.trr
```

GROMACS > v.5.0

```bash
gmx grompp -c em.gro -p FFF_GMX.top -f md.mdp -o md.tpr
gmx mdrun -v -deffnm md
vmd md.gro md.trr
```

#### To Emulate `amb2gmx.pl`

For any given *prmtop* and *inpcrd* files (outputs from AMBER LEaP), type:

```bash
acpype -p FFF_AC.prmtop -x FFF_AC.inpcrd
```

The output files `FFF_GMX.gro` and `FFF_GMX.top` will be generated inside folder *FFF_GMX.amb2gmx*

#### To Verify with CNS/XPLOR

At folder *FFF.acpype*, type:

```bash
cns < FFF_CNS.inp
```

#### To Verify with NAMD

- see [TutorialNAMD](../../wiki/Tutorial-NAMD)

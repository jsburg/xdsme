> # XOalign - Calculate possible 3-axis goniometer settings to realigne crystal axes. #


## USAGE: ##

> XOalign.py  OPTIONS **FILE**

> FILE**is the file containing the crystal orientation information.
> > Supported types are:**

  1. Denzo dot.x reflection file.
  1. Mosflm matrix files (.umat or .mat).
  1. XDS output files (CORRECT.LP, IDXREF.LP, GXPARM.XDS, XPARM.XDS)


> NOTE:
> > The Mosflm matrix file does not contain the space groupe
> > information. In that case, when using the -p otion, for
> > adding point group permutations, one need to specify the
> > crystal symmetry using the -s option.

## OPTIONS: ##


> -d
> --debug
> > Turn on debug mode.


> -D angle1,angle2,angle3
> --datum angle1,angle2,angle3
> > Specify the goniometer "datum" (setting) corresponding to the
> > inputted crystal orientation. The three angles are given in degree.
> > For exemple: -D -15.4,121.55,0
> > Default datum is 0,0,0.


> -h
> --help
> > Print this help message.


> -p
> --pg-permutations
> > Use the allowed point group permutations.
> > Given the crystal symmetry information (taken from the Denzo or XDS
> > crystal orientation file, or given by the -s option), the equivalent
> > crystal orientations are used to calculate all possible goniometers
> > settings. This is the default.


> -n
> --no-pg-permutations
> > Do not use the allowed point group permutations.


> -m mode\_name
> --mode mode\_name
> > Specify the crystal frame to laboratory frame alignement mode.
> > There are at present two possible mode:


> Mode "MAIN": Crystal vector 1 is aligned along the first
> > goniometer axis (Omega). Crystal vector 2
> > is placed in the plane containing the beam and
> > and the first goniometer axis.

> Mode "CUSP": Crystal vector 1 is aligned perpendicular to
> > both the beam vector and the first
> > goniometer axis (Omega). Crystal vector 2
> > is placed in the plane containing crystal vector 1
> > and the first goniometer axis.


> Default mode is "MAIN"
> Exemple: -m maine or -m cusp

> -s name\_or\_number
> --space-group name\_or\_number
> > Specify the crystal space group. The space group name or number
> > can be used. For exemple: -s p21212 or -s 18 or -s I213.


> -V crystal\_vector1
> --aligned-crystal-vector-1 crystal\_vector1
> > Specify the first crystal vector to be aligned. The "gonset"
> > notation is used to define these vectors:


> These may be given as a principle axis:
> > "a", "b", "c", "a`*`", "b`*`", or "c`*`"

> or as a reciprocal space vector enclosed in brackets:
> > "(h k l)",

> or a real space vector in square brackets:
> > "`[`a b c`]`"


> For exemple: -V a or -V "a`*`" or -V "`[`1 0 0`]`" or -V "(0 1 1)"
> Default first angle is: "a`*`"

> -W crystal\_vector2
> --aligned-crystal-vector-2 crystal\_vector2
> > Specify the second crystal vector to be aligned.
> > For exemple: -W b or -W "b`*`" or -W "`[`0 1 0`]`" or -W "(1 1 0)"
> > Default second angle is: "b`*`"


> -O  xo,yo,zo
> --rotation-axis-1  xo,yo,zo
> > Specify the first rotation axis of the goniometer, corresponding
> > to the "Omega" axis on a "Kappa" goniometer.
> > It is important that there is no space between comas.
> > For exemple: -O 0.,0.,1 (this is the default).


> -K  xk,yk,zk
> --rotation-axis-2  xk,yk,zk
> > Specify the second rotation axis of the goniometer, corresponding
> > to the "Kappa" axis on a "Kappa" goniometer.
> > It is important that there is no space between comas.
> > For exemple: -K -0.76604444311897801,0.,0.64278760968653936
> > > (this is the default, which correspond to an 50deg alpha angle).


> -P  xp,yp,zp
> --rotation-axis-3  xp,yp,zp
> > Specify the third rotation axis of the goniometer, corresponding
> > to the "Phi" axis on a "Kappa" goniometer.
> > It is important that there is no space between comas.
> > For exemple: -P 0.,0.,1 (this is the default).


## EXAMPLE: ##


> XOalign.py -V b`*` -W c`*` CORRECT.LP

## AUTHORS: ##
> Python version:
> > Pierre Legrand  Proxima1 SOLEIL
> > E-mail: pierre legrand at synchrotron-soleil fr

> Besed on a the gonset fortran program from:
> > Phil Evansc MRC LMB, Cambridge
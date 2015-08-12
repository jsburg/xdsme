# xdsconv.py: A command line front-end for running xdsconv #

> ## USAGE: ##

```
  xdsconv.py  FILE  OPTIONS  [free_hkl_to_inherit] [nSites] [atomType]  EXPORT_MODE
```

> _FILE_ is a XDS or XSCALE reflection file (usually XDS\_ASCII.HKL).

> _EXPORT MODE_ can be one of these:

> CCP4, CNS, SHELX, SOLVE, EPMR, CRANK, AMORE, SHARP, PHASER, REPLACE



> ## OPTIONS: ##
    * -a:
> > > Force anomal output (Friedel's law = False)
    * -n:
> > > Force normal output (Friedel's law = True)
    * -m:
> > > Force merged output
    * -u:
> > > Force unmerged output
    * -f:
> > > Force generation of free reflection flag
    * -nf:
> > > Force no generation of free reflection flag
    * Default for anomalous and merging:
> > > Is keeping the XDS input file settings.
    * -l label, or -l=label:
> > > In case of CCP4 export, give a new label columns.
> > > The defaults labels: FP, SIGFP, DANO, SIGDANO, ISYM with
> > > -l pk or -l=pk becomes:
> > > FP\_pk, SIGFP\_pk, DANO\_pk ... in CCP4 mode
> > > FP\_pk, SIGFP\_pk, F(+)_pk, SIGF(+)_pk, ... in PHASER mode
    * free\_hkl\_to\_inherit:
> > > Is a reflection file containing a previously
> > > selected set of free reflection to be kept in the newly
> > > exported reflection file for calculation of unbiased Rfree.
> > > The accepted format are: SHELX, CNS and MTZ (with the
> > > following labels:  FP=FP SIGFP=SIGFP FREE=FreeR\_flag).
    * nSites:
> > > Integer describing the number of heavy atom sites expected.
    * atomType:
> > > Symbol of the heavy atom type expected. Only one or two
> > > letters symbols are recognised (like I, Se, S, Hg).


> ## NOTES: ##

  1. Keywords free\_hkl\_to\_inherit, nSites, atomeType and EXPORT\_MODE can be given in any  order.
  1. Cell parameters, space group number and wavelength are taken from the XDS reflection file header.
  1. If Friedel's law == False and heavy atom type is not given, a guess is made base on the wavelength closest atome type edge.
  1. All the exported files are created in a new local directory named after the requested mode (./ccp4, ./phaser, ./solve...).
  1. In most modes, custom bash scripts are created to allow a rapid interactive exploration of data processing.

> ## EXAMPLES: ##
```
          xdsconv.py XDS_ASCII.HKL shelx 12 Se
          xdsconv.py solve XDS_ASCII.HKL Se 12
          xdsconv.py 12 Se phaser XDS_ASCII.HKL
          xdsconv.py XDS_ASCII.HKL ccp4 -n FreeR_reference.mtz
          xdsconv.py XDS_ASCII.HKL ccp4 Se 12 -l=peak FreeR_reference.mtz
```
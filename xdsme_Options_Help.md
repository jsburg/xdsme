# xdsme is a command line helper for running XDS automaticaly #

This is the help message obtain with the command:
```
xdsme -h
```

> ## USAGE: ##
> `xdsme  OPTION  FILES`

> _FILES_ is for one or multiple diffraction image files.

> ## OPTIONS: ##

-h,  --help
> Print this help message.

-1,-2,-3,-4,-5
> Go directly to a particular step:
  1. XYCOOR + INIT `[DEFAULT]`
  1. COLSPOT
  1. IDXREF
  1. DEFPIX + INTEGRATE
  1. CORRECT

-i,  --xds-input
> Give direct XDS Keyword input.
> For example: -i "DETECTOR\_DISTANCE= 167.0 JOB= IDXREF AIR= 0.002"

-a,  --anomal
> Distinguishes Friedel paires for scaling, strategy and completeness
> statistics. Default is no anoulous contribution.

-A,  --Anomal
> Like -a, but also set "STRICT\_ABSORPTION\_CORRECTION" to True.
> It usualy gives better scaling statistics with redunduncy > 2.

-r,  --high-resolution
> Set a high resolution cutoff. Default is 0 (no cutoff).

-R,  --low-resolution
> Set a low resolution cutoff. Default is 45.

-b,  --beam-center-optimize-i
> Starting from the initial given values, search and optimize the beam
> center coordinates (given by -x, -y or extracted form the header).
> Best solution is chosen after i-score ranking.

-B,  --beam-center-optimize-z
> Like -b/--beam-center-optimize-i, but best solution is chosen with after
> a z-score ranking.

-d,  --distance
> Set the detector to crystal distance.

-c,  --cell
> Set the expected cell.
> For example: -c "79 79 38 90 90 90"

-f,  --reference FILE
> Defines a reference data set used during the XPLAN and CORRECT steps.
> For example: -f ../ref/XDS\_ASCII.HKL

-O,  --oscillation
> Set frame oscillation range in degree.
> For example: -c 0.5

-p,  --project
> Set the project name. The default is the prefix taken from
> image names. The working directory will be: xds\_process_"project"_

-s,  --spg
> Set the expected space group using either the space group number
> or simple string.
> For example: -s 18 or -s P21212

-S, --strategy
> Force to go for calculating strategy (XPLAN) and then stops.

-x,  --beam-x
> Set a new value for ORGX: X-coordinates (in pixels) of the
> detector origin. It may be given in mm if the value is directly
> ended by "mm", (e.g. -x 109.1mm).

-y,  --beam-y
> Set a new value for ORGY: Y-coordinates (in pixels) of the
> detector origin. It may be given in mm if the value is directly
> ended by "mm", (e.g. -y 106.4mm).

-v,  --verbose
> Turn on verbose output.

-w, --wavelength
> Set the x-ray wavelength.

--slow,
> Set parameters to process either more accurately.

--weak,
> Set parameters to index in case of weak spots.
xdsme is a collection of python scripts made to simplify the processing of crystal diffraction images with the Wolfgang Kabsch's **XDS** Program (X-ray Detector Software, http://xds.mpimf-heidelberg.mpg.de/). Provided that the diffraction parameters are well recorded in the diffraction image headers, XDS data processing can be started with a simple command line like:
```
 $ xdsme pos1_1_???.img
```

Supported detector image format include: [ADSC](http://www.adsc-xray.com/), [Rayonix/MARCCD](http://www.mar-usa.com/), [MAR345](http://www.marresearch.com/products.mar345.html), [Rigakus/SATURN](http://www.rigaku.com/smc/saturn-system.html), [Rigakus/RAXIS](http://www.rigaku.com/protein/raxis-iv.html) and minicbf format of [Dectris/PILATUS](http://dectris.com/). There is an experimental support for the [MAR555](http://www.marresearch.com/products.mar555.html) detectors (limited by lack of test images).

The main utilities are:
  * [xdsme](http://code.google.com/p/xdsme/wiki/xdsme_Options_Help) (formerly XDS.py), xscale.py for the data processing and scaling.
  * [xdsconv.py](http://code.google.com/p/xdsme/wiki/xdsconv_command_line_options) a command line helper for file format conversion using xdsconv.
  * [XOalign.py](http://code.google.com/p/xdsme/wiki/XOalign_command_line_options) for the goniometer setting calculation (can be set to work with different type of goniometer including Kappa, mini-Kappa, Euler...).
  * [xds2mos.py](http://code.google.com/p/xdsme/wiki/From_XDS_to_MOSFLM) or xds2dnz.py ... (for convertion of orientation matrices)
  * xio\_info (get info from diffraction image headers, see also xio\_info _-xds_)

Specific features:
  * Possible processing of compressed images (gz or bz2) is supported by both xds and xdsme.
  * If it is available, xdsme can use the pointless program (from Phil Evans) to help in selection the proper Pointgroup/Spacegroup (since version 0.4.9).
  * All scripts are pure python code, so the only dependency are Python (or Jython) version >= 2.2 and xds.
  * Export of XDS reflection files to various other format (shelx, ccp4, solve/resolve, cns...) together with bash command files.

INSTALLATION: It should work on any linux or mac-osx directly after unpacking and by adding the xdsme/bin/noarch directory location to your PATH variable (and of course, you should have installed the XDS package).

A typical session will look like that:
```
 $ xdsme  col1_1_*.img 
 $ xdsme  -a -3 -s P3121 -c  “59 59 123 90 90 120” col1_1_*.img 
 $ cd  xds_process_col1_1 
 
 $ xscale2.py  XDS_ASCII.HKL ../xds_process_lowres/XDS_ASCII.HKL 
 $ xdsconv.py  XSCALE.HKL  8  Se shelx 
 $ xdsconv.py  XSCALE.HKL  8  Se solve 
 $ xdsconv.py  XSCALE.HKL  8  Se ccp4 shelx/XDS_ASCII_F4.hkl 
 $ xdsconv.py  XSCALE.HKL  8  Se phaser ccp4/XDS_ASCII.mtz 
 $ xdsconv.py  XSCALE.HKL  cns 
```

For most scripts, there is an in-line help aviable with the argument -h ([xdsme \_-h\_](http://code.google.com/p/xdsme/wiki/xdsme_Options_Help), [xdsconv.py \_-h\_](http://code.google.com/p/xdsme/wiki/xdsconv_command_line_options)). I am happy to read any comments, suggestions or report of problems for installing or using these scripts. If you come across bugs, please raise it in the issue tracker and I will try to fix it.

The xdsme package include the pycgtypes module from the [cgkit project](http://cgkit.sourceforge.net) for geometrical calculations.

These scripts have beam developed and are used regularly on the [Synchrotron-SOLEIL Proxima1 beamline](http://www.synchrotron-soleil.fr/Recherche/LignesLumiere/PROXIMA1).
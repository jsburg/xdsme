#How to convert XDS orientation matrix to the Mosflm convention.

# Introduction #

Once you have indexed/integrated your data with **XDS**, you may want to see how it look in **Mosflm**. This can be interesting, for example, if you need to check indexation on some specific frames, or if you are curious to compare integration in **XDS** and **Mosflm**. The base of the calculation is taken from a fortran program written by [Richard Kahn (IBS - Grenoble)](http://www.ibs.fr/auteur/richard-kahn) and named wk2al.f.

# Details #

For that purpose, you can use the **xds2mos.py** utility using the IDXREF.LP or CORRECT.LP as input:

```

$ xds2mos.py IDXREF.LP
$ xds2mos.py CORRECT.LP

```

This utility will create two files named after the frame template, one containing the UB matrix and one containing a mosflm command file. You can even start ipmosflm directly using the -s option:

```
$ xds2mos.py -s CORRECT.LP
```

A typical output will look like this:

```

   xds2mos version: 0.4.9

   Extracting data from:		CORRECT.LP

   Calculated 2theta:        0.38 degree

   Mosflm UB:

     0.0130960     0.0003568     0.0024705
     0.0014796    -0.0117365    -0.0061484
     0.0020102     0.0063138    -0.0115686

   New Mosflm matix file:  run2_1_00001.xds2mos.umat
   New Mosflm input file:  run2_1_00001.xds2mos.inp

   Use -s or --start-mosflm option to start 'ipmosflm < run2_1_00001.xds2mos.inp'

```

Then, in the ipmosflm GUI you can click on the PREDICT button and zoom to check prediction on specific portion of an image.

Some help can be obtain with the -h option:

```
$ xds2mos.py -h

   Converting XDS crystal orientation informations to Mosflm format.

   A program to convert the orientation matix, extract information
   from XDS output files and write a mosflm input file:

   USAGE:   xds2mos.py  [OPTION]... FILE
    
      FILE can be one of these XDS output files:
      
         XPARM.XDS, GXPARM.XDS, IDXREF.LP, CORRECT.LP
    
   OPTIONS:
    
   -a
   --angles
         Writes out the crystal orientation in xds2mos.umat as
         setings angles (default is as a U matrix)
         
   -h
   --help
         Print this help message.

   -s
   --start-mosflm
         Start "ipmosflm < dnz2mos.inp". Than clic on the "Predict" buton
         to verify predictions.


```
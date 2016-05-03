## Adding a new Package ##

  * Create new directory, say 'foopack, for the package. Create a file called "foopack-readme.txt". This file should have PMTKtitle, PMTKauthor, PMTKurl, and PMTKdate [tags](http://code.google.com/p/pmtk3/wiki/PMTKtags). Follow [this](http://code.google.com/p/pmtksupport/source/browse/trunk/graphViz4Matlab/graphViz4Matlab-readme.txt) as  example.

  * Check [this list](http://code.google.com/p/pmtksupport/wiki/compatibility) for changes you need to make to ensure the package 'plays nicely' with other pmtk packages on the path.

  * Check the package into the [svn repository](http://code.google.com/p/pmtksupport/source/checkout). It must live in its own subdirectory.

  * Run this PMTK command: `refreshZipFiles('support', 'foopack')`. This will download the files to a local directory, and create a zip file out of them.

  * Check the zip file into the [svn repository](http://code.google.com/p/pmtksupport/source/checkout).

  * Update the online list of packages by running [generateSupportReport](http://pmtk3.googlecode.com/svn/trunk/pmtkTools/supportTools/generateSupportReport.m). See [here](http://code.google.com/p/pmtk3/wiki/updatingDocumentation) for details.

  * Test auto-downloading by running [downloadAllSupport](http://pmtk3.googlecode.com/svn/trunk/pmtkTools/supportTools/downloadAllSupport.m), which will download and unzip the packages to the [external](http://pmtk3.googlecode.com/svn/trunk/external) directory.

  * Make sure the new package hasn't shadowed existing files by running [shadowedFilesReport](http://pmtk3.googlecode.com/svn/trunk/matlabTools/metaTools/shadowedFilesReport.m)
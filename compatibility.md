Below we list (in)compatibilities between different packages and pmtk/ matlab,
and steps taken to resolve these. _These constitute changes to the source packages which will need to be repeated if a new version of these packages is installed._

### markSchmidt ###

  * markSchmidt/misc/sampleDiscrete has different interface to pmtk's sampleDiscrete. His code assumes N=1, whereas pmtk lets you draw multiple samples. It has been removed.

  * KPM directory has many duplicates - these were all removed, (the most important of these is process\_options.m; Mark's version does not call prepareArgs).

  * Foreign/randraw.m was removed; its already in pmtkSupport as its own package.

  * Foreign/lars.m was removed; its already in pmtkSupport as its own package.

  * Foreign/minimize.m was removed; its already in gpml-matlab.

  * Added a file called lbfgsC.m, which just calls lbfgs.m. This is needed in case `lbfgsC.mex*` is not available for the user's system.

  * Added max\_mult.m as a backup for users without the appropriate `max_mult.mex*`. Note backup m-files must live in the same directory as the .mex files.

### lightspeed ###

  * There are many duplicate mostly identical files between lightspeed and fastfit. These, were removed from fastfit.

  * we do not call install\_lightspeed.m as this shadows a number of built in functions, instead we use installLightspeedPMTK.m.

  * randgamma.m - original version just errors if randgamma.mex is not found. The change is to add this line instead: `x = randg(a);`. randg is a stats toolbox function that also exists in Octave. It has the same interface as randgamma.

  * gammaln.mexw32 shadows built-in function. It has been removed.

  * repmat.mexw32 shadows built-in function. It has been renamed repmatLS.mexw32.

  * normpdf.m shadows built-in function. it has been renamed normpdfLS.

  * rows.m  aliases built-in Octave 'rows' function causing very obscure errors in apparently unrelated functions. It has been renamed to rowsLS.

  * glob.m aliases built-in Octave glob.m function causing path errors. It was renamed to globLS.m

  * argmax.m behaves differently than PMTK's argmax.m. It was renamed argmaxLS.m

  * argmin.m behaves differently than PMTK's argmax.m. It was renamed argmaxLS.m

  * digamma.m renamed to digammaLS.m. Matlab now has builtin psi function, which our digamma calls.

  * ind2subv.m renamed ind2subvLS. A new bsxfun version lives in matlabTools.

  * logdet.m renamed logdetLS.m, (almost the same as our except for error condition).

  * setdiag.m renamed setdiagLS.m.

### libsvm-mat-2.9.1 ###

  * libsvm-mat-2.9.1\svmtrain.c and libsvm-mat-2.9.1\svmtrain.mex32 are aliased by the bioinformatics toolbox svmtrain.m function. These have been renamed libsvmTrain.c and libsvmTrain.mex32.

### liblinear-1.5.1 ###

  * liblinear-1.51 train and predict files were renamed libLinearTrain and libLinearPredict to avoid name conflicts. This needs to be done for both the .mexw32 files in the windows subdirectory and the .mexglx files in the matlab subdirectory, (for use in linux).

### gpml-matlab ###

  * gpml-matlab - removed solve\_chol.c which does not compile. There is a .m version.

### libdai ###

  * libdai will need to be recompiled according to [these instructions](http://code.google.com/p/pmtk3/wiki/compilingLibdai).

### GGM-GWishart ###

  * Their cov2cor.m is functionally identical to ours. It was removed

  * Duplicate logsumexp.m function removed.

  * normalizeLogspace.m removed, (same as ours except for repmat -> bsxfun)

### bayes\_logit\_0.1.2 ###

  * renamed logdet.m to logdetBL.m.

### general notes ###

  * Many external packages have `.mex*` files, which may have to be regenerated under various operating systems if a package is updated.

  * If multiple files exist on the path, the one at the beginning will shadow the others.



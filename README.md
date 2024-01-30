# PyAstroCal
### Python3 Astrophotography Image Bias &amp; Flat Calibrations
This project is a usage of the astropy and ccdproc Python packages.
Astropy is utilized to access and manipulate FITS files, including FITS headers.
Ccdproc is utilized to "stack" bias images into a "master" bias frame, "median average" flat images into a master flat frame, and then "subtract" the background of these master bias and flat frames from the light images.
The main code is written for JupyterLab execution.

# Prerequisites/Installation

## Packages required:
* matplotlib
* astropy
* ccdproc

## Additional Installation:
Visual Basic Studio (for ccdproc)

## Installation Instructions (Windows):
* Install the packages and verify that they work.
* Copy the code file to your main JupyterLab directory.  Move your raw images folder to your main JupyterLab directory.

The file structure is as follows:

# Project Tree

 * [Main JupyterLab Directory]
   * [AstroPyCal.ipynb]
   * [RawImageFolder]
     * [LightImage1.fits]
     * [LightImage2.fits]
     * [...]
     * [BiasImage1.fits]
     * [BiasImage2.fits]
     * [...]
     * [FlatImage1.fits]
     * [FlatImage2.fits]
     * [...]
#Usage
Once users copy the file into their main JupyterLab directory, they then take their raw image folder and place it into the main JupyterLab directory (as seen in the Project Tree).
The only work on the user's side is changing the [raw_path] and [object_name] variables in the first cell, and then running the entire code.  The raw path should match the folder/directory name of the raw images, and the object name is up to user input.
# Explanation of Code Output
* The first cell is package and folder inputs.
* The second cell stacks the bias frames using ccdproc's "average" method from the ccdp.combine function ([https://ccdproc.readthedocs.io/en/latest/api/ccdproc.combine.html#ccdproc.combine]).
    * This outputs a master bias frame called [combined_bias.fit] into the raw images folder; this also outputs an image of the master bias frame into the Python output.
* The third cell stacks the flat frames using ccdproc's "median average" method from the ccdp.combine function.
    * This outputs a master flat frame called [combined_flat.fit] into the raw images folder; this also outputs an image of the master flat frame into the Python output.
* The fourth cell gathers the light frames.
    * This outputs an image of the last-gathered light frame into the Python output.
* The fifth cell calibrates the light frames using the newly-created master bias and flat frames.
    * This creates a folder called "calibrated" in the raw images folder.  It then outputs these calibrated light frames of the naming convention stacked_OBJECTNAME_FILTERNAME_calibrated1.fit into this "calibrated" folder.
    * Additionally, it outputs the last calibrated light frames into the Python output.

# Project Tree (Post-Code Run)

 * [Main JupyterLab Directory]
   * [AstroPyCal.ipynb]
   * [RawImageFolder]
     * [calibrated]
       * [stacked_OBJECTNAME_FILTERNAME_calibrated1.fit]
       * [stacked_OBJECTNAME_FILTERNAME_calibrated2.fit]
       * [...]
     * [combined_bias.fit]
     * [combined_flat.fit]
     * [LightImage1.fits]
     * [LightImage2.fits]
     * [...]
     * [BiasImage1.fits]
     * [BiasImage2.fits]
     * [...]
     * [FlatImage1.fits]
     * [FlatImage2.fits]
     * [...]

# Credits and Further Reading:
* [https://ccdproc.readthedocs.io/en/latest/api/ccdproc.combine.html]
* [https://www.astropy.org/ccd-reduction-and-photometry-guide/v/dev/notebooks/05-04-Combining-flats.html]
* [https://ccdproc.readthedocs.io/en/latest/api/ccdproc.ImageFileCollection.html#ccdproc.ImageFileCollection.files_filtered]
* [https://docs.astropy.org/en/stable/api/astropy.nddata.CCDData.html]
* [https://ccdproc.readthedocs.io/en/latest/getting_started.html]
* [https://ccdproc.readthedocs.io/en/latest/api/ccdproc.subtract_bias.html#ccdproc.subtract_bias]
* [https://ccdproc.readthedocs.io/en/latest/api/ccdproc.flat_correct.html]

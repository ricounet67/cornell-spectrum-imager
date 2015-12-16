#FrequentlyAskedQuestions
[Home](Home.md)
# Introduction #




# Importing and Exporting Data #

## <font color='gray'> How do I read a Gatan <code>.dm3</code> or FEI/Emispec <code>.ser</code> file?</font> ##
Click on the `Open Spectrum` Icon on the ImageJ CSI toolset bar (the yellow folder icon).  You can also use the plugins directly at the menu `Plugins..CSI..` if you have another toolset active.  At present, ImageJ's own `File..Open` menu is not smart enough to read the Spectrum Image versions of Gatan or FEI files.

## <font color='gray'> How do I save a spectrum image? </font> ##
A Spectrum Image is a calibrated image stack.  To avoid losing information, we recommend saving it as a TIFF file.  From the ImageJ menu, select `FILE..Save As..Tiff..`.  The file can now be read back into ImageJ.   Digital Micrograph can also read the file, but will lose the calibration data.

## <font color='gray'>How do I read a spectrum image back into Digital Micrograph?</font> ##
Gatan has not yet chosen to disclose the internal format of  .dm3 files.  Until they do, we recommend saving your spectrum image as Tiff.  This can then be read (slowly) into Digital Micrograph, where they will appear as image stacks.  You will then have to select from the DM menu `Spectrum..Convert Data to..EELS`, and then calibrate the energy axis.

## <font color='gray'>How do I save a single spectrum?</font> ##
Click on the `Save...` Button below the plot in the CSI:Cornell Spectrum Imager Window.  This will save the energy axis and all plotted lines as a tab-separated text file.

# Principal Components Analysis (PCA) #

## <font color='gray'>Why is it taking so long?</font> ##
We are using [UJMP](http://www.ujmp.org/)'s Singular  Value Decomposition for our PCA.  For a window with N channels, this diagonalizes a matrix with 2N dimensions, an operation that scales as O(N^3).  This means that doubling the window size will take 8 times as long and increasing the window size by a factor of 10 will take 1000 times as long.  The lesson is to start with a small window (<20 channels) and see how long it takes, before getting ambitious.   There are faster algorithms for extracting the first few PCA's and someday we may implement them.

# General Troubleshooting #

## <font color='gray'>I click on a button and nothing happens</font> ##

ImageJ is likely out of memory, and not able to add new windows.  You should increase the amount of memory available to imageJ by selecting [Edit>Options>Memory](http://rsb.info.nih.gov/ij/docs/menus/edit.html#memory), increasing the allocated memory and restarting the program.  For very large data sets be sure to use the 64-bit version (e.g ImageJ64.app on the Mac), which is found in the ImageJ program folder.
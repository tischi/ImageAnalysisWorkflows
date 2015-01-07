#### Image 

Drag and Drop the folder with the data to be analysed.


#### NamesAndTypes 

The ending of the image filenames is important (and case sensitive). It must match the settings in the NamesAndTypes module of CellProfiler.

#### IdentifyPrimaryObjects

- Explore different "Thresholding Methods"
- If you feel that one method gives a decent threshold, but always slightly too high or low, you can adapt the "Threshold correction factor"
- Explore different "Methods to distinguish clumped objects". Note that this uses the "Typical diameter of objects" that you entered above (Read the help inside CP).

#### IdentifySecondaryObjects and IdentifyTertiaryObjects

As there is no dedicated staining for the Cytoplasm, we construct a "ring" around the nucleus to measure the intensity of the transfected protein.

- Change the "Number of pixels by which to expand the primary objects" to change the size of the cytoplasmic ring.

#### RescaleIntensity

Only for better display! This is not used for measurements!


#### DisplayDataOnImage

- Check the numbers here and decide on a threshold value above which you consider cells as transfected. You should have negative control images without transfected cells and take the "brightest" (most autofluorescent) cell of those samples as a threshold.


#### SaveImages

- You may adapt how and where the output images are stored.


#### ExportToSpreadsheet

Count_TransfectedNuclei: Number of transfected cells in this image
Count_Nuclei: Number of all cells in this image


## Important advice

- Always check all the output images to see whether the software did what you expected it to do. Tip: you can load all output images at once into ImageJ using [File>Import>Image Sequence..] with "File name contains" set to jpeg.
- If something is not OK in the output images you have to go back to the CP pipeline and adapt it!

## Typical troubleshooting 

- Not all nuclei are found: you probably have to change the Thresholding in IdentifyPrimaryObjects or change the "Typical diameter of objects" (If "Discard objects outside the diameter range" is active).














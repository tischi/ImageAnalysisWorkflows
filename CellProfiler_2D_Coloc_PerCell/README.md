#
# 2-D colocalisation in cells using CellProfiler
#

The workflow computes cell-based colocalisation of two stainings in 2-D images. Both pixel- and object-based readouts are provided and the pros and cons are shortly discussed below. 


## Input data

each image set contains stainings for

- Nucleus
- Protein 1 (P1)
- Protein 2 (P2)

## Workflow

### Nucleus segmentation

### Grow nuclei ROIs to encompass the whole cell

### Identify pixels positive for protein 1, protein 2, and protein 1&2

### Compute pixel-based readout in each cell

For each cell, measure the number of pixels
 
- positive for P1
- positive for P2
- positive for P1&P2 (Coloc)

### Identify objects in each cell 

For each cell, measure the number of "objects" in P1, P2 and Coloc.
Connected pixels are counted as one object, independent of their size.
If wished, one could also split (big) objects into several smaller objects using some shape or intensity criteria.

### Compute object-based readout in each cell

For each cell measure the number P1, P2 and Coloc objects.

## Readouts 

### Pixel-based readouts

For each cell we can compute the fraction of co-localizing pixels either with respect to protein 1 or 2: 

	Coloc/P1
	Coloc/P2

In the output Cells.csv table the respective colums are named:

	Coloc = Intensity_IntegratedIntensity_ColocBW
	P1 = Intensity_IntegratedIntensity_P1BW
	P2 = Intensity_IntegratedIntensity_P2BW
  
### Object-based readouts

For each cell we can compute the fraction of co-localizing objects either with respect to protein 1 or 2: 

	ObjectsColoc/ObjectsP1
	ObjectsColoc/ObjectsP2

In the output Cells.csv table the respective colums are named:

	ObjectsColoc = Children_Coloc_Count
	ObjectsP1 = Children_P1_Count
	ObjectsP2 = Children_P2_Count


## Discussion

### Pixel vs. object-based readouts

In an object based analysis there is the issue of partial overlap. Basically, how do you want to score an object that partially colocalises (note that this is no problem in the pixel-based quantification). In the pipeline as presented here, even a partial overlap will produce a Coloc object and will thus be counted as 1 object. One could easily change the current pipeline to for instance implement a logic such as: For each P1 object I require that at least 50% of its pixels are also positive for P2 (note that this is not symmetric, i.e., you may get different results if you switch P1 and P2 in above sentence!).

Another issue is object size. In the object-based method a very small object will contribute the same "statistical weight" to the final result as a super large object. This is different in the pixel-based method, where large areas of pixels positive for P1, P2 or Coloc will contribute a large statistical weight (basically the number of pixels in such an area).

There is no general right or wrong to deal with above issues, but decisions have to be based on the underlying biological system and research question.




 
 
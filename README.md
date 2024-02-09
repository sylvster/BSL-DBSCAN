# BSL-DBSCAN

An implementation of scikit-learn's Density-Based Spatial Clustering of Applications with Noise, applied to the Berkeley Seismology Laboratory's Probability Density Functions (PDFs) retrieved from California's stations.

This project was designed in an attempt to extract an ideal training dataset for BSL-ML, a machine-learning algorithm for detecting erroneous PDFs and classifying them into sub-categories based on their shapes.
In order to ease the labeling of 14,000 PDF files, this DBSCAN algorithm was implemented in order to separate files that are to be labeled valid, which share common characteristics that minimize their distance 
between one another. The distance function is as follows:

$$||A - B||_1$$

where A and B are both two-dimensional PDF files comprised of 122 by 151 values between 0 and 1.

The notebook currently supports two main functions: visualization of the Probability Density Functions, and the DBSCAN algorithm.

## Visualization of the Probability Density Function

`plotPDF(path)` plots the PDF file into a two-dimensional colormap through Matplotlib.

<img width="578" alt="plotPDF" src="https://github.com/sylvster/BSL-DBSCAN/assets/107962641/43a08cfa-f748-4c9c-b3a0-5ff322789116">

`plotCompiled(path)` plots the PDF file in a lower quality, with dimensions reduced by four times. This is mainly an experimental feature used in an attempt to lower the memory cost of the training data 
supplied to BSL-ML.

<img width="538" alt="plotCompiled" src="https://github.com/sylvster/BSL-DBSCAN/assets/107962641/14f1412c-57bd-4edd-bf7d-c3b5beeb3ff4">

## DBSCAN Algorithm

Currently, the DBSCAN algorithm has been tested to process around 1000 PDF files and separate them into an arbitrary number of groups, based on the value returned by the distance function.
Data is separated into groups 1, 2, ... k based on the features of the data, while group -1 will contain all outliers. An epsilon value of 26 has been found to give the best boundaries
over 1000 PDF files. They must be adjusted for a DBSCAN involving more or fewer files.

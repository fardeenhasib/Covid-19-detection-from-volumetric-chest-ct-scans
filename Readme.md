This is a possible README.md file summarizing the current report:

# COVID-19 Diagnosis with 3D CNN and Lung-CT Segmentation

This repo presents a method for diagnosing COVID-19 from lung CT scans using 3D convolutional neural networks (CNNs) and lung segmentation. The report describes the data, preprocessing, methodology, and findings of the method.

## Data

The data consists of 306 lung CT scans from the SPGC COVID-19 dataset, which includes 170 COVID-19 positive samples, 60 community acquired pneumonia (CAP) samples, and 76 healthy samples. The data is highly non-uniform and has structural differences in terms of number of slices, Hounsfield unit range, pixel spacing, and slice thickness.

## Preprocessing

The preprocessing steps include:

- Data splitting: The data is split into 80-10-10 (train-validation-test) partitions, with 55 samples from each category for training (40 for training and 15 for validation) and 5 samples from each category for testing.
- HU range setting: The Hounsfield unit range is set to -1000 to 400, as values outside this range are not relevant for diagnosing COVID-19.
- Data normalization: The Hounsfield unit values are normalized to 0 to 1, where values closer to 0 represent air or non-infected regions, and values closer to 1 represent infected regions.
- Lung segmentation and cropping: The lungs are segmented and cropped using a boundary and contour detection network (BCDU-net) to reduce noise and focus on the regions of interest.
- Data resizing: The 3D images are resized to (50, 128, 128) before passing to the 3D CNN model.

## Model Architecture

- 3D CNN model: The 3D CNN model has four segments of two 3D CNN layers followed by a 3D max pooling layer. The kernel size of the 3D CNN layers is (3, 3, 3) and the activation function is ReLU. The pooling size of the max pooling layer is (2, 2, 2). After these, there are two dense layers with 32 and 3 nodes, respectively. The activation function of the last dense layer is softmax, as there are three classes. A dropout layer is used between the dense layers to avoid overfitting.

## Findings

The findings include:

- Segmentation with BCDU-net on cropped lungs results in better and more effective diagnosis, as it gives fewer false negatives.
- The method needs better and more effective segmentation process to differentiate between CAP and COVID-19, to increase accuracy.


## Future Work

The future work includes:

- Exploring more segmentation networks, such as U-Net++, SegNet, LinkNet, PSPNet, etc⁶[6].
- Exploring more 3D CNN networks suitable for the data.
- Optimizing the threshold levels of HU to increase efficiency.
- Resizing the data to bigger units before passing to the networks.

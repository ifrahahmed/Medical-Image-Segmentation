# Medical-Image-Segmentation

Medical Image analysis is a very interesting topic and currently there are a lot of research in this area. Image segmentation is specially ineteresting because it showes clinical information like the weight or volume of an object inside our bodies. It has been shown the lung weight can be used as a measure for Pulmonary Edema, excess fluid in the lung, which makes it very difficult to breath. It's also an indication for heart problems. The amoung of air in each lung is also an inportant measure of lung functionality. All of these measures are made possible by accurate lung segmentation.

Here in this project, we try to understand the distribution of the pixels intensities of the lungs from CT scans and try to train a model to automatically segment the lung region. We used simple fully connected neural netwrok (fcnn), U-Net, and Resnet.

An extension for this project is to accuratly segment the airways, the vasculatures, or the injured lung. The hardest part is to first manually segment these regions to get the training dataset. In this project, we only have the dataset with whole lung region segmentation.

We worked on lung segmentation from CT images. We have 18 3D images and their masks, each one has around 500 coronal slices, thats around 9000 images and 9000 masks. These images are saved in a nifti file format. We used nibabel library to load these kind of images. First, we noticed that the patients have long subject IDs. We ecoded them in a dictionary with simpler new IDs, 0 to 18. Each new 2D slice is saved as patientID_sliceNumber.png/tiff. The masks are 8 bit unsinged numbers with ones and zeros, and so are saved in a png format, lossless compression. The images are saved in tiff format because they are 16bits.

The pixel intensities for the CT images are based on the Hounsfield unit, HU. The scanners should be calibrated so that the air pixels are -1000, water is 0, and bones positive numbers around 200-6000. This makes the segmentation tasks particulary easy because of the contrast between the body tissues (0 intensities) and the lung tissue (-700 to - 1000). If the lung is injured, then the contrast is no longer strong here. In this case, deep learning is very useful for lung segmentation. Unfortuantly, the biggest task is to manually segment the injured lung to create the dataset

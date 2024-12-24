# Early_MS_Detection: Project Motivation
This project aims to investigate data gathered from retinal images through the development of machine learning (ML) and DL models, in an effort to differentiate healthy individuals and those with early signs of MS. By detecting cases early, patients can receive
treatment early to prevent the aggravation of their condition. This project is inspired by a coursework set by Dr. Kafieh of Durham Bioengineering. 

**Technical Details**

The code provided here is a segment of the project, and only focuses on image segmentation. This Python script aims to preprocess SLO images obtained from the FIVES dataset, and to train a U-Net to identify the location of blood vessels, which serve as anatomical landmarks.

The initial U-net consists of an encoder (four downsample blocks, 64, 128, 256, 512) connected
to a bottleneck, with two convolutional layers with 1024 filters. This is subsequently connected
to a decoder (four upsample blocks with decreasing number of filters: 512, 256, 128, 64), and
finally an output layer with 1 × 1 kernel size and sigmoid activation. This enables 1 channel
for binary segmentation, in this case the separation of vessels from background.
Initial training demonstrates promising convergence. An epoch number of 50 is chosen, with
early stopping (patience = 5) used as a regularisation technique. A validation set is created
by partitioning the train set into a 80:20 split. The generalisation gap between training and
validation is minimal, meaning the model is proficient at segmenting unseen data from the
validation set. The training loss selected is the binary cross entropy loss, which is a common
approach within binary segmentation tasks [Janthakal and Hosalli (2021)].
To assess the model performance on the validation set, the DICE similarity coefficient is used,
which compares the spatial overlap between two binary masks. Early stopping is enforced
at epoch 40 (Fig. 6a), where the DICE is found to be 0.935, signifying good segmentation
performance. Training beyond epoch 40 shows a plateauing of val loss, yet train loss keeps
decreasing, signalling overfitting.



**How To Run**

Simply download the .ipynb file and run it on Google Colab or Jupyter Notebook!

**Data Availability:**

FIVES dataset:  https://doi.org/10.6084/m9.figshare.19688169.v1

Jin, K., Huang, X., Zhou, J. et al. FIVES: A Fundus Image Dataset for Artificial Intelligence based Vessel Segmentation. Sci Data 9, 475 (2022). https://doi.org/10.1038/s41597-022-01564-3 

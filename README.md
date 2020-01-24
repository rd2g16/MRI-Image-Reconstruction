# MRI-Image-Reconstruction

  -Credits to PhD Jinming Duan University of Birmingham for the 'MRI Tutorial' and 'functions' code-

  Data was acquired from an MRI scanner in the form of complex-valued k-space data, where k-space represents the spatial 
frequency information (Fourier coefficients) of an object imaged. In order to reconstruct the images, the inverse 
discrete Fourier transform (DFT) is applied to the k-space data. However, it takes the MRI scanner a relatively 
long time to acquire these fully sampled k-space data. To reduce scanning time, undersampling strategies are often used.
 
  Cartesian Undersampling trajectory was the undersampling strategy used in this scenario, generating and applying two random 
mask functions on the k-space data, which in turn led to MRI images obtained using only 1/4 of the k-space data, or 1/8 respectively,
meaning the scans could be performed 4 or 8 times faster. 
 
  The deep learning task was to train a model to reconstruct the incomplete 4-fold and 8-fold images using their 
corresponding fully sampled images. 
 
  A ResNet architecture has been implemented and trained for the purpose of reconstructing the images. The final
implementations had 8 residual blocks of 2 layers and 4 residual blocks of 3 layers. They have been trained on a batch size of 1 due
to low GPU memory unable to fit a larger batch. Adam has been used as the optimizer and the loss function chosen for the training
was the L1 Loss. The 4-fold model has been trained for 20 epochs on a learning rate of 0.002 while the 8-fold model has been 
trained for 40 epochs on a learning rate of 0.003. AlexNet and GAN are two other architectures that have been considered however,
they led to inferior results compared to ResNet. 
  
  The result for the 4-fold model was an improvement of ~6% on the quality of the 4-fold test images, from a baseline 64.9% accuracy,
as measured by the Structural Similarity Index (SSIM), to 70.7%. The 8-fold model achieved an improvement of over 8.6%, from a baseline
55.5% SSIM to 64.1%.

  The test data and test image reconstructions are available thorugh the google drive link provided in the Final_Code. The early code is the mode messy version however, it shows some of the images before and after the reconstruction. 

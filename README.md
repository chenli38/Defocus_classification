# Deep learning-based autofocus method enhances image quality in light-sheet fluorescence microscopy
a deep learning-based autofocus framework that can estimate the position of the objective-lens focal plane relative to the light-sheet, based on two defocused images.  
Source code for paper (https://doi.org/10.1364/BOE.427099)  
A example dataset is provided for data organization purposes (https://doi.org/10.6084/m9.figshare.18515108)  
## Autofocus pipeline
<!--![image](/images/Picture1.png "Running Autofocus")   -->
<img src="images/Picture1.png" width="600" height="660">  

## Required packages
pytorch, torchvision, matplotlib, numpy, random, skimage, scipy  



## Function of scipts
**train_model.py**: 
 - loading dataset, network model and hyperparameters setting, training

**test_all.py**:
 - comparing network train and test losses under different configurations from loss(train_model.py) for example, numbers of input images, different zspacing
 - input: .txt, .pt(model)
 - output: graphs

**pred_img_6nm.py**
 - analysis defocus infomation of single image (large 5128*512) or image patch (small 64*64)
 - input: image (large or small), model
 - output: network prediction and certainty value
 - a example pretrained model is provided in 'saved_models/selfmade_net_6nm_20000.pt'
   
**measure_img.m**
 - source code for traditional image quality metrics (DCTS,LAPD, TENV et.al.) written in MATLAB
 - input parameters : image, method_name

**Trad_test_stack**
 - measure images using tradition image metrics
 - input: test image full stacks
 - output: the absolute distance between the predicte value and the ground truth
 - 
**DNN_test_stack**
 - measure images using neural network 
 - input: test image full stacks
 - output: the absolute distance between the predicte value and the ground truth

**model/dataloader.py**
 - load image data and data preprocessing
 - input: image directory

**model/data_test.py**
 - input: test data (single image or test dataloader)
 - generate confusion matrix for the test dataloader
 - generate graphical image predictions (color borders)

**model/model.py**
  - define neural network model structures

  
## Contact
cli38@ncsu.edu

## References
- Li, Chen, et al. "Deep learning-based autofocus method enhances image quality in light-sheet fluorescence microscopy." Biomedical Optics Express 12.8 (2021): 5214-5226.
- Royer, Loïc A., et al. "Adaptive light-sheet microscopy for long-term, high-resolution imaging in living organisms." Nature biotechnology 34.12 (2016): 1267-1278.




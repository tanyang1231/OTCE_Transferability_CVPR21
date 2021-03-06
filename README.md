## Usage of OTCE Demo Code

Thanks for your attention to our work "OTCE: A Transferability Metric for Cross-Domain Cross-Task Representations".

Arxiv link: https://arxiv.org/pdf/2103.13843.pdf 

CVF link: https://openaccess.thecvf.com/content/CVPR2021/papers/Tan_OTCE_A_Transferability_Metric_for_Cross-Domain_Cross-Task_Representations_CVPR_2021_paper.pdf 

### 1. Install Dependencies

The dependencies of this demo code includes PyTorch, pot, geomloss, numpy and math. For pot and geomloss libraries, you can install them using following commands:

```
# pot is a python library used for solving optimal transport problem.
pip install pot 

# geomloss is a library for computing the cost.
pip install geomloss
```

### 2. Usage

In the code, we randomly generate an instance of testing data, which contains 10 categories and the feature dimension is 512. You can directly replace the testing data with your own data following the same data structure. 

Here we recommend using the simplified version OT-based NCE score (introduced in the Appendix) to evaluate transferability, since the OTCE score requires auxiliary tasks with known transfer accuracy for learning a linear combination of domain difference and task difference. Consequently, it is more convenient for you to only take the task difference (OT-based NCE) to evaluate the transferability of your current task. Note that the conditional entropy shows negative correlation with the transfer performance, thus you can take the negative conditional entropy for indication.  

In our experiments, we randomly select 1,000 samples from source and target data respectively for computation. You can adjust the sample size according to your setting. When the sample size grows, you may need more iterations for solving the OT problem. Therefore, when you see the message "RESULT MIGHT BE INACURATE" which means the max number of iteration is reached, you should set a greater number of max iterations (default 100,000) for OT solver as follow: 

```
# Line 13 in compute_otce_demo.py
ot.emd(ot.unif(X_src.shape[0]), ot.unif(X_tar.shape[0]), C, numItermax=100000)
```

### 3. Citation

Please cite our paper if you find it is interesting. 

```
@InProceedings{Tan_2021_CVPR,
author    = {Tan, Yang and Li, Yang and Huang, Shao-Lun},    
title     = {OTCE: A Transferability Metric for Cross-Domain Cross-Task Representations},    
booktitle = {Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)},    
month     = {June},    
year      = {2021},    
pages     = {15779-15788} 
}
```


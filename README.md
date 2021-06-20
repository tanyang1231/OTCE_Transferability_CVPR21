## Usage of OTCE Demo Code

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




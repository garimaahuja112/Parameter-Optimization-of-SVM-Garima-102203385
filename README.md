# Parameter Optimization of SVM
This project performs a parameter optimization analysis on the Dry Bean Dataset to explore different SVM models (`SVC` and `NuSVC`) and kernel types (`linear`, `rbf`, `poly`) using a randomized search strategy to identify the best configuration for accurate multi-class classification.

## Dataset
The dataset used in this project is ```Dry_Bean_Dataset.xlsx```, sourced from the UCI Machine Learning Repository, a Dry Bean multi-classification dataset. The dataset contains 13,611 rows and 17 columns, including features such as Area, Perimeter, MajorAxisLength, MinorAxisLength, AspectRation, Eccentricity, ConvexArea, Extent, Solidity, Roundness, Compactness, etc., and a target variable (Class) which represents the type of dry bean and includes seven categories: SEKER, BARBUNYA, BOMBAY, CALI, HOROZ, SIRA, and DERMASON.

## Workflow
****1. Data Loading and Preprocessing****
- Loads the dataset and displays basic information about it.
- Encodes the class labels using LabelEncoder.
- Standardizes the feature values using StandardScaler.
  
****2. Train-Test Split****
- Splits the dataset into training and testing sets using a 70-30 stratified split .
- Uses 10 different random seeds (samples) for robustness.
  
****3. Parameter Optimization****
- Randomly samples hyperparameters for SVC and NuSVC, including:
  - Kernel type (linear, rbf, poly)
  - C values (for SVC) and nu values (for NuSVC)
  - Degree (for polynomial kernel)
  - Gamma (scale, auto)

- Tests 100 random parameter combinations for each of the 10 samples.

****4. Performance Evaluation****
- Calculates accuracy scores on the test set for each combination.
- Tracks and records the best accuracy and parameters per sample.

****5. Results****
- Displays the best accuracy and optimal hyperparameters for each of the 10 samples.
- Generates a convergence plot for the best-performing sample to visualize accuracy over iterations.
- Saves all accuracy scores and parameter combinations in ```SVM_optimization_results.csv```.

# Observations
- The RBF kernel consistently yielded the best accuracy across most samples.
- SVC generally outperformed NuSVC, particularly when using higher values of C.
- Polynomial kernel also achieved competitive results in some samples but was less consistent.

# Conclusion
The overall best configuration across all samples was achieved by **Sample S6**, obtaining the highest accuracy of **0.9425** using the **SVC model** with an **RBF kernel**, **C = 3.39**, **gamma = 'scale'**, and **degree = 2**.

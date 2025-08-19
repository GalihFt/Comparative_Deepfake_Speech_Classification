# A Comparative Analysis of Feature-based and Image-based Approaches for Deepfake Speech Detection

This repository contains the documentation and code implementation for the final thesis titled **"A Comparative Analysis of Feature-based and Image-based Approaches for Deepfake Speech Detection"**.

---

## Introduction
The advancement of artificial intelligence technology, particularly in *deepfake speech*, has enabled the synthesis of audio that closely resembles genuine human speech with a high degree of realism. Despite its various positive applications, this technology also carries a significant potential for misuse, such as in fraud and the spread of disinformation. Therefore, the development of effective detection methods is crucial to mitigate these risks. This research investigates and compares two fundamental approaches in *deepfake speech* detection to determine the most optimal methodology.

---

## Abstract
This study compares the effectiveness of two approaches for *deepfake speech* detection: a *feature-based* approach and an *image-based* approach. The *feature-based* approach utilizes the extraction of numerical audio features, which are then classified using *Support Vector Machine* (SVM) and *Random Forest* (RF) models. Meanwhile, the *image-based* approach transforms the audio signal into a visual Mel-spectrogram representation for classification by a *Convolutional Neural Network* (CNN) and a *CNN-Long Short-Term Memory* (CNN-LSTM) model. The evaluation results indicate that the CNN model delivers superior classification performance, achieving an accuracy of 91.43%. Conversely, the SVM model demonstrates the highest processing time efficiency, making it the superior choice from a computational standpoint.

---

## Dataset
The data source used in this research is the **ASVspoof 2019** dataset, which is the standard benchmark for evaluating speaker verification systems against *spoofing* attacks.
* **Scenario**: This research focuses on the *Logical Access* (LA) scenario, which includes data from synthesized audio (*Text-to-Speech*) and *Voice Conversion* attacks.
* **Specifications**: The audio data is in WAV format with a sampling frequency of 16,000 Hz.
* **Data Pre-processing**: An *undersampling* process was applied to the *training*, *validation*, and *testing* subsets to achieve a more balanced ratio between the *bonafide* (genuine) and *spoofed* (fake) classes.

---

## Research Methodology
The research workflow is organized into the following two primary approaches:

#### 1. Feature-based Approach
This approach focuses on extracting a series of statistical features from the time and frequency domains of the audio signal.
* **Feature Extraction**: The extracted features include Chroma (1-12), *Mel-Frequency Cepstral Coefficients* (MFCC, 1-20), *Spectral Centroid*, *Spectral Spread*, *Spectral Rolloff*, *Zero Crossing Rate*, and *Root Mean Square* (RMS).
* **Feature Selection**: The *Recursive Feature Elimination* (RFE) method was used to identify and select the most discriminative set of features.
* **Classification Models**: *Support Vector Machine* (SVM) and *Random Forest* (RF).

#### 2. Image-based Approach
This approach converts the one-dimensional audio signal into a two-dimensional image representation.
* **Feature Representation**: Audio signals are transformed into Mel-spectrograms, which are then resized to 128x128 pixels.
* **Classification Models**: *Convolutional Neural Network* (CNN) and *Convolutional Neural Network - Long Short-Term Memory* (CNN-LSTM).

---

## Repository Structure
The project's directory structure is organized as follows to ensure modularity and ease of navigation.
    
    .
    ├── data/
    │   ├── output      # output data
    │   └── processed   # processed input data
    ├── model/          # trained models
    ├── notebooks/      
    ├── reports/        # reporting materials and documents
    ├── requirements.txt
    └── README.md

---

## Installation and Usage
The following steps detail the procedure for replicating the environment and running the analysis.

#### Prerequisites
* Python (version 3.10 or newer)
* `pip` package manager

#### Installation Steps
1.  **Clone the Repository**:
    ```bash
    git clone [https://github.com/username/your-repo-name.git](https://github.com/username/your-repo-name.git)
    cd your-repo-name
    ```
2.  **Install Dependencies**:
    Install all required libraries using the `requirements.txt` file.
    ```bash
    pip install -r requirements.txt
    ```

#### Usage Procedure
The entire research workflow, from data pre-processing to final model evaluation, is implemented entirely within Jupyter Notebooks.

To replicate the analysis, execute the notebooks located in the notebooks/ directory sequentially, from 1 through 9. Each notebook represents a specific stage in the research.

---

## Results and Evaluation
The following table summarizes the performance comparison of the four evaluated models on the test data.

| Model | Accuracy (Test) | Recall (Spoofed) | Feature Extraction Time (s) | Training Time (s) | Prediction Time/instance (s) |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **SVM** | 67.66% | 53.51% | 0.0285 | **2.15** | **0.0010** |
| **RF** | 80.85% | 74.91% | 0.0285 | 5.99 | 0.0046 |
| **CNN** | **91.43%** | **88.56%** | 0.0082 | 1,243.26 | 0.1148 |
| **CNN-LSTM** | 89.76% | 85.13% | **0.0081** | 1,524.06 | 0.1184 |

### Conclusion
Based on the analysis, several key conclusions can be drawn:
* **Superior Accuracy**: The **CNN** model demonstrated superiority in accuracy and generalization capability, achieving an accuracy of **91.43%**. This indicates that the extraction of spatial features from Mel-spectrograms is a highly effective approach for this problem.
* **Superior Efficiency**: The **SVM** model proved to be the most efficient in terms of computational time, both in the training and inference stages.
* **Implications**: There is a significant *trade-off* between classification accuracy and computational efficiency. The selection of an optimal model must be based on the application's priorities, whether the primary factor is high accuracy or processing speed.

---

## License
This project is distributed under the terms of the **MIT License**. Further information regarding the license can be found in the `LICENSE` file.
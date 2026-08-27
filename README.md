# DL-Lab-4


# Experiment 4 – Comparative Study of Deep CNN Architectures Using Transfer Learning

## Shiv Nadar University Chennai

**CS3807 – Deep Learning Laboratory**
**Experiment 4**

---

## 1. Experiment Title

**Comparative Study of Deep Convolutional Neural Network Architectures Using Transfer Learning**

---

## 2. Objective

The objectives of this experiment are:

* To study the evolution of deep CNN architectures.
* To understand LeNet-5, AlexNet, VGG16, GoogleNet and ResNet.
* To understand the concept of transfer learning.
* To implement transfer learning using a pretrained CNN.
* To fine-tune a pretrained CNN model.
* To compare the classification performance using different evaluation metrics.

---

## 3. Dataset

The experiment uses the **CIFAR-10 dataset**.

### Dataset Details

| Property          | Value       |
| ----------------- | ----------- |
| Training Images   | 50,000      |
| Testing Images    | 10,000      |
| Number of Classes | 10          |
| Image Size        | 32 × 32 × 3 |

### Classes

1. Airplane
2. Automobile
3. Bird
4. Cat
5. Deer
6. Dog
7. Frog
8. Horse
9. Ship
10. Truck

The CIFAR-10 images are normalized to the range **[0, 1]** before training.

---

## 4. CNN Architectures Studied

The experiment discusses the evolution of CNN architectures:

| Architecture | Year | Major Contribution                     |
| ------------ | ---: | -------------------------------------- |
| LeNet-5      | 1998 | First practical CNN                    |
| AlexNet      | 2012 | ReLU, Dropout and GPU training         |
| VGG16        | 2014 | Uniform 3 × 3 convolution filters      |
| GoogleNet    | 2014 | Inception modules                      |
| ResNet       | 2015 | Residual learning and skip connections |

---

## 5. Transfer Learning Model

For the implementation, **MobileNetV2** is used as the pretrained CNN model.

MobileNetV2 is initialized with **ImageNet pretrained weights**.

### Transfer Learning Workflow

```text
CIFAR-10 Dataset
       ↓
Preprocess and Normalize Images
       ↓
Resize Images
       ↓
Pretrained MobileNetV2
       ↓
Freeze Convolutional Base
       ↓
Global Average Pooling
       ↓
Dense Layer (128 units, ReLU)
       ↓
Output Layer (10 units, Softmax)
       ↓
Train Classifier
```

The original classification layer of the pretrained model is not used. A new classifier is added for the 10 CIFAR-10 classes.

---

## 6. Model Configuration

The initial model is trained using the following settings:

| Parameter          | Value                            |
| ------------------ | -------------------------------- |
| Pretrained Model   | MobileNetV2                      |
| Pretrained Weights | ImageNet                         |
| Optimizer          | Adam                             |
| Learning Rate      | 0.001                            |
| Batch Size         | 32                               |
| Epochs             | 10                               |
| Loss Function      | Sparse Categorical Cross Entropy |
| Evaluation Metric  | Accuracy                         |
| Dense Units        | 128                              |
| Output Classes     | 10                               |

---

## 7. Fine-Tuning

After initial transfer learning, fine-tuning is performed.

### Fine-Tuning Procedure

1. The pretrained MobileNetV2 model is initially frozen.
2. The newly added classifier is trained.
3. The last few layers of MobileNetV2 are then unfrozen.
4. A smaller learning rate of **0.0001** is used.
5. The model is trained for another **5 epochs**.
6. Test accuracy before and after fine-tuning is compared.

### Fine-Tuning Workflow

```text
Frozen MobileNetV2
       ↓
Train New Classifier
       ↓
Unfreeze Last Layers
       ↓
Reduce Learning Rate
       ↓
Fine-Tune Model
       ↓
Compare Performance
```

---

## 8. Evaluation Metrics

The trained model is evaluated using:

* Accuracy
* Precision
* Recall
* F1-score
* Confusion Matrix
* Classification Report
* Training Time
* Total Number of Parameters

### Metric Definitions

**Accuracy:** Measures the percentage of correctly classified images.

**Precision:** Measures how many of the images predicted as a particular class actually belong to that class.

**Recall:** Measures how many actual images of a class were correctly identified.

**F1-score:** Provides a combined measure of precision and recall.

---

## 9. Required Plots

The following plots are generated as required by the laboratory manual:

1. Sample CIFAR-10 images
2. Training Accuracy
3. Validation Accuracy
4. Training Loss
5. Validation Loss
6. Confusion Matrix

An additional plot of misclassified images can also be generated.

Each figure should be accompanied by a brief **2–3 line inference** in the laboratory report.

---

## 10. Hyperparameter Study

The experiment includes a study of different hyperparameter settings.

The laboratory manual specifies the following values:

| Hyperparameter | Values        |
| -------------- | ------------- |
| Learning Rate  | 0.001, 0.0001 |
| Batch Size     | 16, 32, 64    |
| Epochs         | 10, 20        |
| Optimizer      | Adam, SGD     |
| Dense Units    | 128, 256      |
| Frozen Layers  | All, Partial  |

A smaller set of configurations can be compared experimentally to study their effect on classification performance.

---

## 11. Project Structure

```text
Experiment-4/
│
├── Experiment_4.ipynb
│
├── README.md
│
└── results/
    ├── sample_images.png
    ├── training_accuracy.png
    ├── validation_accuracy.png
    ├── training_loss.png
    ├── validation_loss.png
    ├── confusion_matrix.png
    └── misclassified_images.png
```

The `results` folder is optional if the notebook itself contains all the generated plots.

---

## 12. Dependencies

Install the following Python libraries if they are not already available:

```bash
pip install tensorflow
pip install numpy
pip install matplotlib
pip install seaborn
pip install scikit-learn
pip install pandas
```

For Google Colab, most of these packages are already pre-installed.

---

## 13. How to Run

### Using Google Colab

1. Open Google Colab.
2. Create a new notebook.
3. Copy the experiment code into separate cells.
4. Run the import and dependency cell.
5. Load the CIFAR-10 dataset.
6. Run the preprocessing and visualization cells.
7. Build the MobileNetV2 transfer-learning model.
8. Train the frozen model.
9. Evaluate the model.
10. Perform fine-tuning.
11. Evaluate the fine-tuned model.
12. Generate the required plots.
13. Perform the hyperparameter study.
14. Record the final results in the laboratory report.

### Recommended Hardware

A GPU-enabled Google Colab runtime is recommended to reduce training time.

---

## 14. Expected Output

After execution, the notebook should provide:

```text
✓ CIFAR-10 dataset dimensions
✓ Sample CIFAR-10 images
✓ MobileNetV2 model summary
✓ Training accuracy
✓ Validation accuracy
✓ Training loss
✓ Validation loss
✓ Testing accuracy
✓ Fine-tuning accuracy
✓ Precision
✓ Recall
✓ F1-score
✓ Classification report
✓ Confusion matrix
✓ Training time
✓ Total parameters
✓ Hyperparameter comparison
```

---

## 15. Results Table

The final results can be recorded using the following format:

| Metric            |  Value |
| ----------------- | -----: |
| Training Accuracy | ______ |
| Testing Accuracy  | ______ |
| Precision         | ______ |
| Recall            | ______ |
| F1-score          | ______ |
| Training Time     | ______ |
| Total Parameters  | ______ |

### Fine-Tuning Comparison

| Model Stage        | Accuracy |
| ------------------ | -------: |
| Before Fine-Tuning |   ______ |
| After Fine-Tuning  |   ______ |
| Improvement        |   ______ |

---

## 16. Architecture Comparison

The laboratory manual also requires comparison of major CNN architectures:

| Model     | Parameters | Accuracy (%) | Training Time |
| --------- | ---------: | -----------: | ------------: |
| LeNet-5   |     ______ |       ______ |        ______ |
| AlexNet   |     ______ |       ______ |        ______ |
| VGG16     |     ______ |       ______ |        ______ |
| GoogleNet |     ______ |       ______ |        ______ |
| ResNet50  |     ______ |       ______ |        ______ |

The values should be filled using the results obtained from the corresponding implementations/experiments.

---

## 17. Important Concepts for Viva

### LeNet-5

A relatively small CNN originally designed for handwritten digit recognition. It uses convolution, average pooling and fully connected layers.

### AlexNet

A deep CNN that introduced important techniques such as ReLU activation, Dropout, GPU-based training and data augmentation.

### VGG16

A deep CNN that mainly uses small **3 × 3 convolution filters** and increases network depth.

### GoogleNet

Uses **Inception modules**, where different convolution operations are performed in parallel to extract features at multiple scales.

### ResNet

Uses **skip connections** and residual learning to make training very deep networks easier.

### Transfer Learning

Uses a model that has already been trained on a large dataset and adapts it to a new task.

### Fine-Tuning

Unfreezes some layers of the pretrained model and trains them along with the new classifier so that the learned features can adapt to the new dataset.

### Dilated Convolution

Increases the receptive field by introducing gaps between kernel elements without proportionally increasing the number of parameters.

### Transpose Convolution

Performs learnable upsampling and increases the spatial dimensions of feature maps.

---

## 18. Conclusion

This experiment demonstrates how CNN architectures have evolved from LeNet-5 to deeper architectures such as ResNet. Transfer learning using a pretrained MobileNetV2 model allows a CNN to be adapted to CIFAR-10 without training the entire network from scratch. Fine-tuning selected pretrained layers can further adapt the learned features to the target dataset.

---

## 19. Reference

The experiment is based on the **CS3807 – Deep Learning Laboratory Experiment 4** manual provided by Shiv Nadar University Chennai.

The manual references the original works on LeNet, AlexNet, VGG, GoogleNet and ResNet, along with TensorFlow and Keras documentation.

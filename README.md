# ECG Vision Transformer Training and Evaluation Script

This script trains and evaluates a Vision Transformer (ViT) model on an Electrocardiogram (ECG) dataset. 

## Table of Contents
- [Requirements](#requirements)
- [Dataset](#dataset)
- [Usage](#usage)
  - [Setting up Session Path](#setting-up-session-path)
  - [Model Initialization](#model-initialization)
  - [Creating Custom Callbacks](#creating-custom-callbacks)
  - [Model Compilation](#model-compilation)
  - [Model Training](#model-training)
  - [Loading Trained Model](#loading-trained-model)
  - [Model Evaluation](#model-evaluation)
  - [Prediction with Model](#prediction-with-model)
  - [Logging Results](#logging-results)
- [License](#license)

## Requirements

This script uses the following Python libraries:
- TensorFlow and Keras for model creation and training
- Numpy for numerical operations
- Matplotlib and Seaborn for visualization
- sklearn.metrics for evaluation metrics
- os for file and directory operations
- re for regular expressions


## Dataset

Our project employs the well-established MIT-BIH Arrhythmia Dataset, a rich resource for the detection and classification of cardiac arrhythmias. The dataset, contributed by the Massachusetts Institute of Technology and Boston's Beth Israel Hospital, comprises ECG recordings, each lasting approximately 30 minutes, from 47 subjects.

The ECG signals in the dataset are subjected to windowing, a procedure that frames a span of 198 samples around the label, or point of interest. This windowing operation helps us efficiently focus on specific portions of the signal related to each heart rhythm anomaly, allowing us to extract salient features for subsequent analysis and prediction.

After windowing, we partition the dataset using a 70-10-20 % scheme for training, validation, and testing, respectively. This approach ensures a balanced and unbiased evaluation of the model's performance during the learning process and when facing unseen data.

## Usage

The workflow for training and evaluating the Vision Transformer (ViT) model on the ECG dataset proceeds as follows:

1. **Setting up Session Path**: This is the directory where all outputs, model weights, and log files will be saved. Ensure you set a path that exists in your filesystem.

2. **Model Initialization**: Initialize the Vision Transformer (ViT) model by calling the `ViT` function. This function will construct the model structure using the specified settings.

3. **Creating Custom Callbacks**: These are methods that get called at certain points in the training process, such as at the beginning or end of each epoch. In this script, callbacks are used to save model weights that yield the highest validation accuracy or lowest validation loss.

4. **Model Compilation**: The model is compiled using the Adam optimizer and the categorical cross-entropy loss function. This is a preparatory step for training.

5. **Model Training**: Begin training the model by calling the `fit` function on the ViT model. The training takes place for a specified number of epochs, using the provided training and validation data. During training, the learning rate adjustment callback will reduce the learning rate by a factor of 0.8 if the validation loss does not decrease for 5 consecutive epochs.

6. **Loading Trained Model**: After training, load the model with the highest validation accuracy using the `load_model` function.

7. **Model Evaluation**: Evaluate the model's performance on the test set using the `evaluate` function.

8. **Prediction with Model**: Use the model to make predictions on the test set by calling the `predict` function. This will give you the model's predictions for each sample in the test set.

9. **Logging Results**: Lastly, write the model's prediction results and performance metrics into text files for later analysis.

## License

This project is open-source, made available under the [MIT License](LICENSE).

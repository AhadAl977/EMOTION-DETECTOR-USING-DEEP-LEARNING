# Emotions Detector Via Tone of Voice Using Deep-Learning Final Report
## Abstract
The main goal of this project is to analyze the voices of men and women to identify the emotions of the speaker  
using deep learning concepts and algorithms to solve this problem.

## Data Description
The dataset was collected from [RAVDESS](https://zenodo.org/record/1188976) which contains **1441** file inputs from 24 different actors split between male and female, In each actor there are **60** voice recordings of all the emotions. Such as:
- Happy
- Neutral
- Sad
- Angry
- Calm
- Fearful
- Disgust

Performed data augementation methods to increase the size of data. The implemented methods are:
- Pitch
- Noise
- Stretch
- Shift
Data was then increased to 7200 recordings.

## Algorithms
1. Exploratory Data Analysis was done to the dataset.
  - Cleaning
    - Established sample & sample rate from all recordings.
    - Extrated information from the name of the file that were later on added as columns in the data frame. For example:
      - **03-01-05-01-02-01-16.wav**

        Modality -> (01 = full-AV, 02 = video-only, 03 = audio-only).

        Vocal channel -> (01 = speech, 02 = song).

        Emotion -> (01 = neutral, 02 = calm, 03 = happy, 04 = sad, 05 = angry, 06 = fearful, 07 = disgust, 08 = surprised).

        Emotional intensity -> (01 = normal, 02 = strong). NOTE: There is no strong intensity for the 'neutral' emotion.

        Statement -> (01 = "Kids are talking by the door", 02 = "Dogs are sitting by the door").

        Repetition -> (01 = 1st repetition, 02 = 2nd repetition).

        Actor -> (01 to 24. Odd numbered actors are male, even numbered actors are female).

2. Data Preprocessing
  Took the raw audio into a journey to trasform it in a meaningful matter. The transformation started with:
  - Transforming raw audio into spectrograms.
  - Transforming spectrogram into mel spectrograms.
  - Extracting features from mel spectrograms by using MFCC

4. Classification 
   - Two baseline models:
     - Decision Tree Classifier:
       - Train: 1.0
       - Validation: 0.33
       - Train + Validation: 0.80
     - KNN Classifer:
       - Train: 0.03
       - Validation: 0.025
       - Train + Validation: 0.28
   - Feed-Forward Models:
      Model|Simple NN | Complex NN |
      ------ | ---------|------------|
      Layers  | 4 |9
      Activation  | relu,softmax |relu,softmax
      Epoch | 50 |50
      Batch Size | 64 |64
      Number of Classes | 16 | 16
      Metrics | Categorical Accuracy | Categorical Accuracy
      Train | 0.14 | 0.067
      Validation | 0.12 | 0.72
      
    - CNN Models:
      Model|Simple CNN | Complex CNN 1 |Complex CNN 3
      ------ | ---------|------------|-------|
      Layers  | 3 |9|5
      Activation  | relu,softmax,padding |relu,softmax,padding,maxpooling,batchnorm,dropout|relu,softmax,padding,maxpooling,batchnorm,dropout,kernel size,stride
      Epoch | 50 |50|50
      Batch Size | 64 |64|30
      Number of Classes | 16 | 16|16
      Metrics | Categorical Accuracy | Categorical Accuracy|Categorical Accuracy
      Train | 0.21 | 0.32|0.52
      Validation | 0.19 | 0.29|0.55
      
     - LSTM Models:
  
        Model |   LSTM   | LSTM overfit solution # 1 (Reduced Model)  | LSTM overfit solution # 2 (regularized Model)| LSTM overfit solution # 3 (Dropout Model)|
        -----------------|----------|-----------------------------------------------------------|--------------------|------------------------------------------|
        Layers           | 4        |                3                                          | 4                                                                   |4
        Activation       | relu,softmax,padding,maxpooling,batchnorm,dropout,kernel size,stride |relu,softmax,padding,maxpooling,batchnorm,dropout,kernel size,stride |relu,softmax,padding,maxpooling,batchnorm,dropout,kernel size,stride + **L2**|relu,softmax,padding,maxpooling,batchnorm,dropout(.6/.8/.9),kernel size,stride
        Epoch            | 50       |50                                                         | 50                                                                  |50
        Batch Size       | 30       |30                                                         | 30                                                                  |30
        Number of Classes| 16       | 16                                                        | 16                                                                  |16
        Metrics          | Categorical Accuracy | Categorical Accuracy                                                |Categorical Accuracy                        |Categorical Accuracy
        Train | 0.73 | 1.0|0.99|0.53
        Validation | 0.59 | 0.67|0.43
      
     - Feed-Forward Models:
        Model|VGG16 (Chosen Model)|
        ------|---------|
        Layers  | Freezed first 19 layers and added 3 extra
        Activation  | relu,softmax,dropout
        Epoch | 10
        Batch Size | 30
        Number of Classes | 16 | 16
        Metrics | Accuracy
        Train | 0.87 
        Validation | 0.89 
        Test | 0.70

      


   
## Tools
Here the basic tools that will be used: <br/>
Technologies: python, and Jupyter Notebook with python libraries:
- For Exploratory Data Analysis:
  - pandas
  - matplotlib
  - numpy
  - seaborn
- For Audio Processing:
  - scikit-learn
  - Librosa
  - PyAudio
- For Classification:
  - VGG16
  - Scipy
- For Saving
  - Pickle 
  
## Conclusion
People's way of speaking tells a lot about how they feel. I know if someone is happy or sad as a human, but computers are having a hard time. Deep learning algorithms help translate this important element of  communication. The main goal of this project is to use 
deep learning algorithms to identify the  gender and emotions of the speaker.

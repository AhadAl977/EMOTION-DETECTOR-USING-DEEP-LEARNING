# Emotion Detector Through Audio Using Deep-Learning MVP

### 
#### Goal of the project
The main focus of this project is to analyze the undertone of males and females to determine the emotion of the speaker by using deep-learning concepts and algorithms
to tackle this issue.

#### Exploratory data analysis
After performing the initial EDA which included:
1. Established sample and sampling rate from all recordings. The sample is a snapshot of an audio wave at a certain time specifying the amplitude.
2. Added needed columns like Gender, Emotion, Intensity, Duration, Statement and Path of the file.
3. Labled the emotions accoring to the corresponding recording.

#### Data Preprocessing
The data preprocessing process included:
1. Converted waveform into spectrogram.
2. Converted spectrogram into Mel spectrogram.
3. Converted Mel spectrogram into MFCC.
4. Extracted features using MFCC (Mel Frequency Cepstral Coefficents)
5. Performed augumentation methods on raw audio like, pitching, stretching, and adding noise on the recordings.<br><br>
All of the data manipulation above resulted in **7200 rows** and **324 columns**.


#### Deep-Learning Classification 
Before starting with applying classification models and building neural networks, a few steps were taken beforehand:
- The **y** was hot encoded.
- Data was split into 80% for training and 20% for both validation and testing.
- A new dimension was added to all X's (X_train, X_val and X_test).<br><br>

Two classification models were built as a base line:
1. Knearest Neighbor.
  - Training Score: 0.0296
  - Validation Score: 0.0256
  - Training + Validation Score: 0.0286
  - Testing Score: 0.0131
2. Decision Tree.
  - Training Score: 1.0
  - Validation Score: 0.331
  - Training + Validation Score: 0.832
  - Testing Score: 0.3458
 #### Neural Networks
 2 Traditional baselines were built. First one is simple and it contains 4 neurons and the other one is a bit more complex it contains up to 9 neurons.
 - 1st TNN (Traditional Neural Network) accuracy = 0.1354
 - 2nd TNN (Traditional Neural Network) accuracy = 0.2389 <br>
 
2 CNN models were built. First one is simple (as a baseline) and it contains 2 neurons and the other one is a bit more complex it contains up to 8 neurons.

 - 1st CNN (Convolutional Neural Network) accuracy = 0.1454
 - 2nd CNN (Convolutional Neural Network) accuracy = 0.2515 <br>
 
Another CNN model was built with more activation, dropout functions and more parameters.<br>
 
 - 3rd CNN (T Neural Network) accuracy = 0.6298 <br>
 
LSTM Model was also built with reulting accuracy of 0.4365
 
<br><br>

<img src="https://github.com/amjadalth/Emotions-Detector-DeepLearning/blob/main/raw-spec.png" width="600"/><br>
<img src="https://github.com/amjadalth/Emotions-Detector-DeepLearning/blob/main/mel-spec.png" width="600"/><br>
<img src="https://github.com/amjadalth/Emotions-Detector-DeepLearning/blob/main/mfcc.png" width="600"/><br>
<img src="https://github.com/amjadalth/Emotions-Detector-DeepLearning/blob/main/pitched-audio.png" width="500"/><br>

All the above graphs show the roadmap of transformation of the raw audio to spectrogram to mel spectrogram to MFCC lastly to aa augmented audio by applying one of the
augmentation methods eg.pitch.

#### Futrue Work
- Introducing **transfer learning** into the project.




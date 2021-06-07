# Audio-Preprocessing

Any machine learning problem consists of three types of tasks: 
(1) data preprocessing (data collection & cleaning, and feature extraction), 
(2) data model building  (training machine learning models), and 
(3) evaluation (measuring the "quality" of the model). 

Here we address a problem of data preprocessing, mnore specifically of feature extraction.

When data is audio, besides the usual problems of filtering noise and interferences of background sounds, there is a recurrent problem with the most frequently used feature source, the Mel-spectrogram (Mel-frequency spectrogram), which shows how the power vs frequency spectrum of the signal (obtained with embedded discrete fast Fourier transform)  changes with time. 

The problem consists that, while the number of rows is given by the number of frequency channels used for describing the signal, a constant parameter of the method, the number of columns of the calculated spectrogram matrix is linearly proportional to the length of the audio input. For example, see how the number of columns of the output spectogram matrix increases with audio length below.

audio length  2.86 (s)  Spectogram shape  (50, 247)

audio length  3.81 (s)  Spectogram shape  (50, 329)

In this case, the number of frequency channels was 50.

This causes difficulties to build pipelines for machine learnign models which are designed for a fixed number of features as input.

To circumvent this situation there have been used two different approaches: 
(1) summarizing the spectral power over time, calculating the average and higher-order momenta of the data for each frequency channels, which losses the temporal dynamics, or 
(2) seeking for the shortest audio and then truncating all input signals to that length or creating multiple samples of the shortest audio size from larger inputs.  


Here, we propose a method based on calibrating one of the several parameters of the Mel-spectrogram function, which allows controlling the number of columns of the output matrix independent of the length of the input audio.   

audio length  0.95 (s)      Spectogram shape  (50, 51)

 audio length  1.9 (s)      Spectogram shape  (50, 51)

 audio length  2.86 (s)     Spectogram shape  (50, 51)

 audio length  3.81 (s)     Spectogram shape  (50, 51)
 

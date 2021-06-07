# Audio-Preprocessing

Any machine learning problem consists of three types of tasks: 
(1) data preprocessing (data collection & cleaning, and feature extraction), 
(2) data model building  (training machine learning models), and 
(3) evaluation (measuring the "quality" of the model). 


When data is audio, besides the usual problems of filtering noise and interferences of background sounds, there is a recurrent problem with the most frequently used feature source, the Mel-spectrogram (Mel-frequency spectrogram), which shows how the power vs frequency spectrum (obtained with embedded discrete fast Fourier transform)  of the signal changing over time. 

The problem consists that, while the number of rows is given by the number of frequency channels used for describing the signal, a constant parameter of the method, the number of columns of the calculated spectrogram matrix is linearly proportional to the length of the audio input.

To circumvent this situation there have been used two different approaches: 
(1) summarizing the spectral power over time, calculating the average and higher-order momenta of the data for each frequency channels, which losses the temporal dynamics, or 
(2) seeking for the shortest audio and then truncating all input signals to that length or creating multiple samples of the shortest audio size from larger inputs.  


Here, we propose a method based on calibrating one of the several parameters of the Mel-spectrogram function, which allows controlling the number of columns of the output matrix independent of the length of the input audio.   

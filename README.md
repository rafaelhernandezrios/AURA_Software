# Aura: User Manual

Welcome to Aura! Our latest biosensing system, developed with meticulous attention to user experience, offers an intuitive and powerful way to interact with your EEG cap data.

## Overview

Aura consists of a biosensing board and an EEG cap designed under a unified design direction. This system provides an enhanced user experience through on-screen printing on the cap, which indicates the position of each electrode, and a more durable and thinner 3D-printed SLS (selective laser sintering) biosensing enclosure.

## Usage Tutorial

### Live Connection

This will be your main panel. From here, you can start a live connection by clicking the "Connection" button.

<img src=https://github.com/edgarhernandez94/ANUIES/blob/main/WAVEX/AURA_SDK/AuraTutorial1/AuraTutorial_1.png  width="60%">

1. **Select the Identified COM Port**: Select your identified COM port for Aura and click "Connect". Within a few seconds, you will begin receiving live data.

<img src=https://github.com/edgarhernandez94/ANUIES/blob/main/WAVEX/AURA_SDK/AuraTutorial1/AuraTutorial_2.png width="60%">

### Electrode Configuration

Make sure your electrodes are properly connected and positioned.

1. **Electrode Configuration**: Click "File" -> "Configure Electrodes" to open the configuration panel. You can also click the Quick Settings icon in the upper-left corner of the brain.

<img src=https://github.com/edgarhernandez94/ANUIES/blob/main/WAVEX/AURA_SDK/AuraTutorial1/AuraTutorial_3.png width="60%">

2. **Adjust Electrode Channel Numbers**: Move the electrode channel numbers to reflect your actual Aura headset configuration. Then save the position configuration with the button on the scalp.

<img src=https://github.com/edgarhernandez94/ANUIES/blob/main/WAVEX/AURA_SDK/AuraTutorial1/AuraTutorial_4.png width="60%">

3. **Real-Time Contact Quality Indicators**: While adjusting the electrodes on the scalp, the contact quality indicators will gradually turn "good". Red indicates a poor connection between the scalp and the corresponding electrode for that channel number, so more conductive gel may be required.

<img src=https://github.com/edgarhernandez94/ANUIES/blob/main/WAVEX/AURA_SDK/AuraTutorial1/AuraTutorial_5.png width="60%">

### Recording

1. **Start Recording**: Simply click the "Record" button to begin recording.

<img src=https://github.com/edgarhernandez94/ANUIES/blob/main/WAVEX/AURA_SDK/AuraTutorial1/AuraTutorial_7.png width="60%">

2. **Generated Files Directory**: During a live connection, files are automatically generated in your computer's Documents folder, under ...Users\[ you ]\Documents\Aura EEG Records. You can choose your own destination folder by going to "File" -> "Settings" or by clicking the Save icon above the Record button.

<img src=https://github.com/edgarhernandez94/ANUIES/blob/main/WAVEX/AURA_SDK/AuraTutorial1/AuraTutorial_8.png width="60%">

3. **Event Logging**: During recording, you can press the spacebar on your keyboard to log an event in your CSV file for future reference. This will be indicated by a color change in the Event light.

 <img src=https://github.com/edgarhernandez94/ANUIES/blob/main/WAVEX/AURA_SDK/AuraTutorial1/AuraTutorial_9.png width="60%">

### Streaming

While a live connection is active, you can enable or disable the "LSL Stream Out" checkbox. This will send your raw signals over the network. It also works with your recorded sessions.

<img src=https://github.com/edgarhernandez94/ANUIES/blob/main/WAVEX/AURA_SDK/AuraTutorial1/AuraTutorial_11.png width="60%">

#### Advanced Usage: LSL and Python Integration

This section explains the steps to obtain raw data from the Aura software via the Lab Stream Layer (LSL) protocol using the Python programming language. For more information about LSL, see: [Lab Stream Layer Documentation](https://labstreaminglayer.readthedocs.io/).

**Steps:**

1. Open the Aura software and start reading EEG signals.

2. Click the "LSL" checkbox located above the graphs to start streaming raw EEG data. The Aura software automatically generates an LSL stream layer called "AURA".

3. To visualize raw EEG data, run the following file: `1_LSL_read_raw_data.py`.

4. To filter raw data from the 'AURA' LSL stream, run the following file: `2_LSL_filter_raw_data.py`. This script will read the raw data, filter it, and generate a new stream called "AURAFilteredEEG" and "AURAKalmanFilteredEEG".

5. To use only 3 channels and compute spectral frequency power (PSD), run the file `4_LSL_3channel_Banpower`. This script will take only the first three electrodes and compute the PSD to obtain EEG_Bandpower, creating a new stream called "AURAPSD".

6. To visualize "AURAFilteredEEG" and "AURAKalmanFilteredEEG", you can run `5_LSL_Graphic`.

7. To compute band power from the filtered data, run the following file:

   This file receives an LSL stream of eight EEG channels with filtered EEG data called "AURAFilteredEEG". The output is a 40-channel stream called 'EEG_BANDPOWER_X' containing normalized band power values from the input signals in the following form:

   - Delta CH1
   - Delta CH2
   - ...
   - Delta CH8

   - Theta CH1~CH8
   - Alpha CH1~CH8
   - Beta CH1~CH8
   - Gamma CH1~CH8

### Playback

1. **Load a Previously Recorded CSV File**: Click "File" -> "Load Dataset". For example, you can load a demo sample by clicking "Next".

<img src=https://github.com/edgarhernandez94/ANUIES/blob/main/WAVEX/AURA_SDK/AuraTutorial1/AuraTutorial_12.png width="60%">

2. **Explore Playback Features**: Experiment with all the scales and filters for the signals. For example, try the smoothness slider in the FFT panel.

<img src=https://github.com/edgarhernandez94/ANUIES/blob/main/WAVEX/AURA_SDK/AuraTutorial1/AuraTutorial_13.png width="60%">

3. **Visualize Data on the 3D Brain Model**: You can rotate the 3D brain model and select which band you want to visualize with the buttons below the scalp.

<img src=https://github.com/edgarhernandez94/ANUIES/blob/main/WAVEX/AURA_SDK/AuraTutorial1/AuraTutorial_14.png width="60%">

### Accelerometer and Gyroscope

You can also view your Aura's accelerometer and gyroscope signals by clicking this tab.

<img src=https://github.com/edgarhernandez94/ANUIES/blob/main/WAVEX/AURA_SDK/AuraTutorial1/AuraTutorial_15.png width="60%">

This will display the following visualization panel.

<img src=https://github.com/edgarhernandez94/ANUIES/blob/main/WAVEX/AURA_SDK/AuraTutorial1/AuraTutorial_16.png width="60%">

---

We hope this manual helps you get the most out of Aura! If you have any questions or suggestions, feel free to contact our support team. Enjoy exploring Aura's capabilities integrated into Wavex!


 
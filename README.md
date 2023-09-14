# Tugas 1 Sinyal

Screenshoot A
![A](https://github.com/rsydfddn/tugas-sinyal/assets/139645166/ee8b11d7-d507-457c-be12-ddf3b2271340)

Screenshoot B
![B](https://github.com/rsydfddn/tugas-sinyal/assets/139645166/0274f2bf-6429-4d03-b161-792db0b7ed94)
```
import numpy as np
import matplotlib.pyplot as plt

# Generate a sine wave signal
fs = 1000  # Sampling frequency (Hz)
t = np.linspace(0, 1, fs, endpoint=False)  # Time vector from 0 to 1 second
frequency = 5  # Frequency of the sine wave (Hz)
amplitude = 1  # Amplitude of the sine wave
sine_wave = amplitude * np.sin(2 * np.pi * frequency * t)

# Plot the original signal
plt.figure(figsize=(10, 4))
plt.subplot(2, 1, 1)
plt.plot(t, sine_wave)
plt.title('Original Sine Wave Signal')
plt.xlabel('Time (s)')
plt.ylabel('Amplitude')

# Perform some signal processing (e.g., filtering)
# Example: Apply a low-pass Butterworth filter
from scipy.signal import butter, lfilter

def butter_lowpass(cutoff, fs, order=5):
    nyquist = 0.5 * fs
    normal_cutoff = cutoff / nyquist
    b, a = butter(order, normal_cutoff, btype='low', analog=False)
    return b, a

def butter_lowpass_filter(data, cutoff, fs, order=5):
    b, a = butter_lowpass(cutoff, fs, order=order)
    y = lfilter(b, a, data)
    return y

# Define filter parameters
cutoff_frequency = 20  # Cutoff frequency for the low-pass filter (Hz)
filter_order = 6  # Filter order

# Apply the low-pass filter to the signal
filtered_signal = butter_lowpass_filter(sine_wave, cutoff_frequency, fs, order=filter_order)

# Plot the filtered signal
plt.subplot(2, 1, 2)
plt.plot(t, filtered_signal)
plt.title('Filtered Sine Wave Signal')
plt.xlabel('Time (s)')
plt.ylabel('Amplitude')

# Display the plots
plt.tight_layout()
plt.show()
```

Screenshoot C
![C](https://github.com/rsydfddn/tugas-sinyal/assets/139645166/f3b0ff42-47b7-493a-bfa0-1830fd033607)

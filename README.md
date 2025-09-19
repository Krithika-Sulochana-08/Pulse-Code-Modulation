# Pulse-Code-Modulation
# Aim
Write a simple Python program for the modulation and demodulation of PCM, and DM.
# Tools required
# Program
import matplotlib.pyplot as plt 
import numpy as np

sampling_rate = 5000 
frequency = 50 
duration = 0.1 
quantization_levels = 16

t = np.linspace(0, duration, int(sampling_rate * duration), endpoint=False)

message_signal = np.sin(2 * np.pi * frequency * t)

clock_signal = np.sign(np.sin(2 * np.pi * 200 * t))

quantization_step = (max(message_signal) - min(message_signal)) / quantization_levels 
quantized_signal = np.round(message_signal / quantization_step) * quantization_step

pcm_signal = (quantized_signal - min(quantized_signal)) / quantization_step 
pcm_signal = pcm_signal.astype(int)

plt.figure(figsize=(12, 10))

plt.subplot(4, 1, 1) 
plt.plot(t, message_signal, label="Message Signal (Analog)", color='blue') 
plt.title("Message Signal (Analog)") 
plt.xlabel("Time [s]") 
plt.ylabel("Amplitude") 
plt.grid(True)

plt.subplot(4, 1, 2) 
plt.plot(t, clock_signal, label="Clock Signal (Increased Frequency)", color='green') 
plt.title("Clock Signal (Increased Frequency)") 
plt.xlabel("Time [s]") 
plt.ylabel("Amplitude") 
plt.grid(True)

plt.subplot(4, 1, 3) 
plt.step(t, quantized_signal, label="PCM Modulated Signal", color='red') 
plt.title("PCM Modulated Signal (Quantized)") 
plt.xlabel("Time [s]") 
plt.ylabel("Amplitude") 
plt.grid(True)

plt.subplot(4, 1, 4) 
plt.plot(t, quantized_signal, label="Signal Demodulation", color='purple', linestyle='--') 
plt.title("Signal Without Demodulation") 
plt.xlabel("Time [s]") 
plt.ylabel("Amplitude") 
plt.grid(True)

plt.tight_layout() 
plt.show()
# Output Waveform
<img width="1557" height="612" alt="image" src="https://github.com/user-attachments/assets/502b2c9a-79f8-4cdf-8ebd-b67985b874b6" />
<img width="1511" height="621" alt="image" src="https://github.com/user-attachments/assets/133766b8-ceff-449d-869e-d5665e72b0dd" />

# Results
The result is a set of plots that visualize the original analog message signal, the clock signal used for sampling, the quantized PCM signal, and the reconstructed signal after demodulation.


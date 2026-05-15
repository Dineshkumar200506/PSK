# PSK AND QPSK
# NAME : NABISHA A
#REG NO : 212223060177
# Aim
Write a simple Python program for the modulation and demodulation of PSK and QPSK.
# Tools required :
GOOGLE CO-LAB
# Program
```
PSK
import numpy as np
import matplotlib.pyplot as plt
# ---------------- PARAMETERS ----------------
fs = 1000 # sampling frequency
Tb = 1 # bit duration
fc = 5 # carrier frequency
data = [1,0,1,1,0,1]
t = np.arange(0, Tb, 1/fs)
# ---------------- MESSAGE ----------------
message = np.repeat(data, len(t))
time = np.arange(len(message)) / fs
# ---------------- CARRIER ----------------
carrier = np.sin(2*np.pi*fc*time)
# ---------------- PSK MODULATION ----------------
# 1 -> +1 , 0 -> -1
polar_data = 2*message - 1
psk = polar_data * carrier
# ---------------- DEMODULATION ----------------
demod = psk * carrier
reconstructed = (demod > 0).astype(int)
# ---------------- PLOTS ----------------
plt.figure(figsize=(12,8))
plt.subplot(4,1,1)
plt.plot(time, message)
plt.title("Message Signal")
plt.ylim(-0.5,1.5)
plt.grid()
plt.subplot(4,1,2)
plt.plot(time, carrier)
plt.title("Carrier Signal")
plt.grid()
plt.subplot(4,1,3)
plt.plot(time, psk)
plt.title("PSK Modulated Signal")
plt.grid()
plt.subplot(4,1,4)
plt.plot(time, reconstructed)
plt.title("Demodulated Signal")
plt.ylim(-0.5,1.5)
plt.grid()
plt.tight_layout()
plt.show()
```
# Program :
```
QPSK
import numpy as np
import matplotlib.pyplot as plt
# -------- PARAMETERS --------
fs, Tb, fc = 1000, 1, 5
data = [1,0, 0,1, 1,1, 0,0] # even bits
t = np.arange(0, Tb, 1/fs)
# -------- MESSAGE --------
I = np.repeat(data[0::2], len(t))
Q = np.repeat(data[1::2], len(t))
time = np.arange(len(I))/fs
# -------- CARRIERS --------
c1 = np.cos(2*np.pi*fc*time)
c2 = np.sin(2*np.pi*fc*time)
# -------- QPSK MODULATION --------
qpsk = (2*I-1)*c1 + (2*Q-1)*c2
# -------- DEMODULATION --------
I_rec = (qpsk*c1 > 0).astype(int)
Q_rec = (qpsk*c2 > 0).astype(int)
reconstructed = np.ravel(np.column_stack((I_rec, Q_rec)))
# -------- PLOTS --------
plt.figure(figsize=(12,8))
plt.subplot(4,1,1)
plt.plot(time, I)
plt.title("Message Signal")
plt.ylim(-0.5,1.5); plt.grid()
plt.subplot(4,1,2)
plt.plot(time, c1)
plt.title("Carrier Signal")
plt.grid()
plt.subplot(4,1,3)
plt.plot(time, qpsk)
plt.title("QPSK Modulated Signal")
plt.grid()
plt.subplot(4,1,4)
plt.plot(time, reconstructed[:len(time)])
plt.title("Demodulated Signal")
plt.ylim(-0.5,1.5); plt.grid()
plt.tight_layout()
plt.show()


# Output Waveform
PSK:
<img width="609" height="409" alt="image" src="https://github.com/user-attachments/assets/d297f091-f4e1-4eaa-aa01-c64b803b2a43" />
QPSK :
<img width="640" height="403" alt="image" src="https://github.com/user-attachments/assets/f60395c2-0668-46b4-b799-6e07ad4233b9" />

# Result :


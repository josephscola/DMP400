# Analyse sonore

Traitement numérique d'un signal audio acquis depuis le flux audio de l'appareil.

## Modules utilisés
- [matplotlib](https://matplotlib.org/)
- [librosa](https://librosa.org/doc/latest/index.html)
- [tkinter](https://docs.python.org/3/library/tkinter.html) (_after_, _mouse event_)

## Paramètres d'entrée
- fréquence d'échantillonnage
- durée du segment affiché
- taille du tronçon d'analyse
 
## Fonctionnalités 
- Acquisition en temps réel du flux de la carte son.
- Affichage en temps réel
	- de l'intensité sonore en décibels (non calibré)
	- de la hauteur du son principale
	- du [tempo](https://librosa.org/doc/latest/tutorial.html#quickstart)
- Représentations graphiques :
	+ de la forme d'onde 
	+ de la transformée de Fourier 
	+ du diagramme temps-fréquences
	+ séparation des composantes [harmoniques et percussives](https://librosa.org/doc/latest/auto_examples/plot_hprss.html#sphx-glr-auto-examples-plot-hprss-py)
 
## Matériel 
- carte son Raspberry Pi

## Amorce de code
```python
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
"""
Created on Fri Mar 31 15:18:50 2023

@author: https://stackoverflow.com/questions/48653745/continuesly-streaming-audio-signal-real-time-infinitely-python
"""

import pyaudio
import numpy as np

import time
import sys
import matplotlib.pyplot as plt


RATE = 11025
updates_per_s = 2
CHUNK = int(RATE/updates_per_s) # RATE / number of updates per second

def soundplot(stream, DATA, ax):
  
   t1=time.time()
   #use np.frombuffer if you face error at this line
   data = np.fromstring(stream.read(CHUNK),dtype=np.int16)
   DATA += list(data)
   nfft = 1024
   max_length = RATE * updates_per_s * 4
   if len(DATA) > max_length:
       DATA = DATA[-max_length:]
   ax.specgram(DATA, NFFT=nfft, Fs=RATE, window=np.hamming(nfft), noverlap=0, mode='magnitude')
   plt.pause(1/updates_per_s)
   return None

if __name__=="__main__":
    p=pyaudio.PyAudio()
    fig, ax = plt.subplots()
    DATA = []
    stream=p.open(format=pyaudio.paInt16,channels=1,rate=RATE,input=True,
                  frames_per_buffer=CHUNK)
    for i in range(15 * updates_per_s):
        soundplot(stream, DATA, ax)
    stream.stop_stream()
    stream.close()
    p.terminate()
```

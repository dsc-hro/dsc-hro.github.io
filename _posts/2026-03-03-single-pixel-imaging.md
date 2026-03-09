---
layout: post
title:  "Single Pixel Cameras and Compressed Sensing"
date:   2026-02-24 20:00:00 +0000
categories: jekyll update
author: chillerb
---

## Introduction

What makes a camera good?
When talking about digital cameras, the first thing that comes to mind is probably a high resolution, which translates into a high number of photodiodes aranged as a sensor array.
At first glance, a single-pixel camera therefore feels a bit silly: Sure, the "The Lord of the Rings" movies are pretty decent, but even they would be visually unappealing if every frame only has a single pixel.

![lotr-movie-barcode](/assets/figures/lotr-movie-barcode.png)

Shoutout to Hannes Grunert and his presentation [*"Errate den Streifen!"*][grunert]

However, cameras with a single pixel also have some useful properties:

- Since we only need a single sensor, single-pixel cameras can be cheaper. Especially for non-visible wavelengths like infrared, high-resolution cameras are expensive.
- We can get a much higher frame rate.

*Single-Pixel Imaging* (SPI) was introduced in 2008 by Duarte et al. in [*"Single-Pixel Imaging via Compressive Sampling"*][duarte], so let's take a closer look at the paper!

## Single-Pixel Imaging

The core idea of SPI is to take *multiple* single-pixel measurements from the same scene under different lighting conditions, which - with some *mathemagics* involved - will eventually allow us to reconstruct the actual image that we would have obtained when using a normal camera.
While not much hardware is required for SPI, the complexity is instead shifted to the software side.

Classical SPI setups have 3 main components:

1. A Spatial Light Modulator
2. A single light detector
3. The scene under view

Using the *Spatial Light Modulator* (SLM), we can modulate the intensity of the light beam according to control signal.
A reflective SLM is given by the *Digital Micromirror Device* (DMD).
A DMD is basically an array of mirrors, except that each mirror has a size comparable to a bacterium.
Each mirror can be configured individually to be rotated into one of two possible orientations for reflecting light.

Mathematically, the $m$-th measurement $y_m$ taken by the single-pixel camera can be considered as the inner product

$$
    y_m = \langle x, \phi_m \rangle,
$$

where $x \in \mathbb{R}^{N}$ is a vector that holds $N$-samples of the scene's light-field, and $\phi_m \in \{0, 1\}^N$ is the $m$-th *test function*.
While in this equation, $x$ is represented as $N = W\cdot H$ dimensional vector for the inner product, note that you could *reshape* $x$ into a $(H, W)$ matrix, where each element corresponds to a pixel in the desired image of the scene under view.
Therefore, $x$ is the desired image that we want to reconstruct from our $m$ single-pixel measurements $y$!
Similarly, each element of $\phi_m$ corresponds to a mirror in the 2D mirror array of the DMD, and controls its orientation.
If the element in $\phi_m$ is one, the respective mirror will redirect the light *towards* the sensor - but if the element is zero, it will reflect the light *away* from the sensor instead.
Therefore, the product $\langle x, \phi_m \rangle$ at its core is just the sum of all the light coming from the scene $x$, with some pixels being "turned off" in a controlled manner by the DMD via the test function $\phi_m$, resulting in the measured voltage $y_m$ at our single-pixel camera.

> How do we define test functions $\phi_m$?
    - can just use random matrices
> Why do we use the Hadamard Transform?



where $x$ is the N-pixel sampled version 

## Compressive Sampling

- traditional approach to digital data acquisition: sample analog signal at or above Nyquist rate
- $x = \Psi \alpha$
- this is actually just lasso regression!


## References


- [Duarte et al.: "Single-pixel imaging via compressive sampling" (2008)][duarte]
- [Veritasium: "What happens if you keep slowing down?"][veritasium]

[duarte]: https://doi.org/10.1109/MSP.2007.914730
[veritasium]: https://www.youtube.com/watch?v=P-4pbFcERnk
[grunert]: https://www.ief.uni-rostock.de/studieninteressierte/fuer-schulen-klassen-gruppen/rent-a-professional/informatik/errate-den-streifen/


# Single Pixel Imaging and Compressed Sensing

- Single Pixel Imaging (SPI)
    - Räumliche Kodierung von Lichtsignalen
- Compressed Sensing (CS)
    - Mathematische


## Funktionsweise Klassischer Kameras

- 2D Pixel-Arrays im Sensor
- Jedes Pixel einzeln gemessen
- Große Datenmengen
- > Rolling Shutter Effect
- verzerrung von bewegten Objekten

## Alternative Laserscanner

- funktionsweise
    - laser tastet punkt für punkt ab

- wenn jedes Pixel nacheinander gemessen wird, brauchen wir überhaupt Pixel Array

## Klassisches SPI-System

- Komponenten
1. Strukturierte Beleuchtung "Spatial Light Modulation"
2. Einzelner Detektor
3. Scene/Objekt/Bild


## Digital Micromirror Devices (DMD)

- array von kippbaren spiegeln

## Experimenteller Aufbau

- Lichtquelle (Laser)
- Spatial Light Modulator (DMD)
- Lichtdetektor (Photodiode)
- Linsen zur Fokussierung des Lichts

## Beleuchtungsmuster

- Arten von Mustern
    - Hadamard-Matrizen
    - Kosinus-/Sinusmuster
    - Zufallsmuster
    - weiter, wie zum Beispiel Deep Learning Muster

## Messung und Signalfluss

- verschiedene Lichtmuster projizieren und Summe des Lichts messen: Messvektor
- mögliche Gewichtung der Messungen
- Rekonstruktion

## Single-Pixel Imaging (SPI)

$$
    y = Ax
$$

- y ist Messvektor
- A ist Messmatrix
- x ist originalbild
- DC-Korrektur: 


- Hadamard matrix: either 0 or 1
- fourier matrix: between 0 and 1


## Takeaways

- Single-Pixel Imaging bringt Komplexit#t von Hardware zur Software
- Compressed Sensing ermöglicht weniger Messungen als Pixel
- Abwägung zwischen Qualität, Geschwindigkeit und zeitlicher Auflösung
- vielfältige Anweundungsbereiche mit kontinuierlicher Entwicklung
- für bestimmte Zwecke besser geignet als klassische Kameras

- Comparison of Common Algorithms for Single-Pixel Imaging via compressed sensing
- Single-Pixel Imaging via Compressive Sensing
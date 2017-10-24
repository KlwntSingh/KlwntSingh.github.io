---
layout: post
title:  "Networking Basics - Hardware Level?"
date:   2017-10-24 1:13:00 -0300
categories: data communication, electromagnetic waves, networking, radiowaves, microwaves
tags: cables, data communication, microwaves, networking, radiowaves
---
This article briefly introduces **Data Communication**. It tries to answer **How Communication happens between two systems?** .
The whole communication process is divided into steps-described below.

## 1. Data in wires
Data travels as electromagnetic waves. These electromagnetic waves are generated when current runs through the wire.
There are two types of electromagnetic signals.
a. Analog Signals
b. Digital Signals

Radiowaves and Microwaves etc are more popular electromagnetic waves for data communication but we can use electromagnetic waves of different and variable  frequencies.   
Signals need a medium to travel. Two types of medium exist.   
**a.** **Guided Medium** - means Physical wires like *twisted pair cables*, *coaxial cables* and *optical fibers*. Usually, Waves of lower frequency(or, higher wavelength) are used. Lightwave is used in optical fibers.  
**b.** **Unguided Medium** - means wireless communication. Radiowaves or Microwaves are used.

### Difference Between Analog and Digital 
*Analog Signals* are continuous waveforms represented by sine or cosine graphs. 
*Digital Signals* are discrete waves and represent only two values one and zero.

Back in time, Data Communication started with analog signals but soon communication started using digital signals.
Couple of reasons for that:
a. Analog signals are more prone to errors
b. Analog signals can carry only limited amount of data.
c. Analog data is stored on magnetic tapes while digital data can be stored on disk drives hence their access is fast.

## 2. Conversion from data to signals or Vice Versa
There are certain techniques to convert signal/data from one form to another. 

`a.` Following Encoding Techniques are used to convert digital/analog data to digital signals. 
* NRZ
* NRZI
* Manchester
* Differential Manchester
* Bipolar-AMI
* Pseudoternary

`b.` Following Modulation techniques are used to digital/analog data to analog signals like 
* Amplitude Shift Key
* Frequency Shift Key
* Phase Shift Key


### Some Important Terms
**a.** **Bandwidth** - Bandwidth is the range of frequencies used in a signal. A Signal can have waves of different frequencies. Media put constraints on bandwidth limit used for sending signals. More noise is added when frequencies used are above or below bandwidth range. 

**b.** **Data Rate** - Rate at which bits travel in form of signals. Each signal element or pulse usually represent one bit. But there are certain techniques in which we can represent more than one bit on a single signal element.

 Data travel from one station to another station through long wires. Usually, these long wires are shared by multiple stations at same time. To achieve this, we use the concept of **multiplexing**. There are Couple of multiplexing techniques like 
* FDM(Frequency Diving Multiplexing)
* TDM(Time Division Multiplexing)


## 3. Last Step ie. **Error Detection and Error Correction**

After signals have reached the other end, there is a chance of distortion and attenuation which would result in the wrong decoding of waves to digital data. Hence, Certain error detection and error correction techniques help resolves the issue.

* **Error detection** - Error detection works by sending redundant data like *parity bits* and *CRC(cyclic redundancy check*) bits.  
* **Error Correction** - After error detection, It is sometimes possible to correct the errors. One of the technique to correct errors is *hamming code*. 

After Signals have reached the destination station and decoding of electromagnetic waves to bits is done(usually by the **physical layer** of networking layered architecture), Errors will be detected and if possible, bits will be recovered(by **Logical Link control** layer in **Data Link Control** layer i.e second layer). There are 7 layers in **OSI model** and each layer have different functionality. In this post, we have discussed the functionality of **Physical Layer** and part of **Data Link layer**. 

Hope you found the post useful. More complex technologies in networking and Data communication are built upon above technologies and techniques. This article is inspired from book **Data and Computer Communications by William Stallings 10th edition.**

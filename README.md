# MIT AJL Team 10

## Members
Neha Kotturu - https://github.com/neha-kotturu

Annanta Budhathoki - https://github.com/annantab 

Helena Fu - https://github.com/helena-f 

Winnie Chuma - https://github.com/winniechuma

Tishya Kasliwal - https://github.com/tishyakasliwal 

Mukhlisa Nematova - https://github.com/mukhlisanematova


## Project Overview
This Kaggle competition, Equitable AI for Dermatology, is presented by the Algorithmic Justice League (AJL) and Break Through Tech AI. The main goal of the competition is to develop an ML model to classify skin conditions across diverse skin tones. This helps advance equity in healthcare by centering those historically excluded in AI. Within the competition, we are competing against 400+ students in 73 different teams in the 2025 UCLA, MIT, and remote BreakThrough Tech fellows.

The higher level objective of this challenge is to accurately identify skin conditions across diverse skin colors. On a more technological level, the main goal is to develop skills in data augmentation, processing, model development, and validation to create fair, inclusive, and robust models.

This technology can help improve the efficiency and effectiveness of skin disease diagnoses, acting as a crutch for dermatologists and reducing potential human error/inaccuracies, in various skin tones. It can also lead to equitable healthcare, bringing diagnostic tools to people who may not have the access to specialized care.


## Dataset Used
For this competition, we were provided with a subset of the FitzPatrick17k dataset, which is a labeled collection of about 17,000 images depicting a variety of serious (e.g., melanoma) and cosmetic (e.g., acne) dermatological conditions with a range of skin tones scored on the FitzPatrick skin tone scale (FST). The dataset has about 4500 images, representing 21 skin conditions out of the 100+ in the full FitzPatrick set.


## Data Exploration
We explored the data by analyzing the distributions of the training data, including distributions of skin tones and disease labels. In order to combat an unbalanced model, we injected extra data of underrepresented conditions and skin tones.

Since darker skin tones have different values and representations in images, we applied different preprocessing based on the fitzpatrick level for the clearest and most useful image data ie. contrast, gaussian level, etc.

We wanted to normalize the images so we decided to crop the images to be a set size, we contrasted the image tones, rotated the images, did random vertical and horizontal rotations and we decided to grayscale the images. 


## Data Visualization
![unnamed (1)](https://github.com/user-attachments/assets/f1c643f0-1b0a-4324-af99-7a734c3aa0f9)
![unnamed](https://github.com/user-attachments/assets/3d438e20-7fc5-4432-85ff-d0e16f854c55)

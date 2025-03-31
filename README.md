# MIT AJL Team 10

## Members
- [Neha Kotturu](https://github.com/neha-kotturu)  
- [Annanta Budhathoki](https://github.com/annantab)  
- [Helena Fu](https://github.com/helena-f)  
- [Winnie Chuma](https://github.com/winniechuma)  
- [Tishya Kasliwal](https://github.com/tishyakasliwal)  
- [Mukhlisa Nematova](https://github.com/mukhlisanematova)  


## Project Overview
This Kaggle competition, Equitable AI for Dermatology, is presented by the Algorithmic Justice League (AJL) and Break Through Tech AI. The main goal of the competition is to develop an ML model to classify skin conditions across diverse skin tones. This helps advance equity in healthcare by centering those historically excluded in AI. Within the competition, we are competing against 400+ students in 73 different teams in the 2025 UCLA, MIT, and remote BreakThrough Tech fellows.

The higher level objective of this challenge is to accurately identify skin conditions across diverse skin colors. On a more technological level, the main goal is to develop skills in data augmentation, processing, model development, and validation to create fair, inclusive, and robust models.

This technology can help improve the efficiency and effectiveness of skin disease diagnoses, acting as a crutch for dermatologists and reducing potential human error/inaccuracies, in various skin tones. It can also lead to equitable healthcare, bringing diagnostic tools to people who may not have the access to specialized care.

## Setup & Execution
To begin our project, we first downloaded the training and testing data from Kaggle onto our local machines. All the code was executed within a Jupyter notebook in VSCode. The machine included an AMD Radeon RX 7900 XT GPU, which allowed us to significantly speed up the image processing, ensuring efficient and smooth execution.

## Dataset Used
For this competition, we were provided with a subset of the FitzPatrick17k dataset, which is a labeled collection of about 17,000 images depicting a variety of serious (e.g., melanoma) and cosmetic (e.g., acne) dermatological conditions with a range of skin tones scored on the FitzPatrick skin tone scale (FST). The dataset has about 4500 images, representing 21 skin conditions out of the 100+ in the full FitzPatrick set.


## Data Exploration
We explored the data by analyzing the distributions of the training data, including distributions of skin tones and disease labels. In order to combat an unbalanced model, we injected extra data of underrepresented conditions and skin tones.

Since darker skin tones have different values and representations in images, we applied different preprocessing based on the fitzpatrick level for the clearest and most useful image data ie. contrast, gaussian level, etc.

We wanted to normalize the images so we decided to crop the images to be a set size, we contrasted the image tones, rotated the images, did random vertical and horizontal rotations and we decided to grayscale the images. 


## Data Visualization
![unnamed (1)](https://github.com/user-attachments/assets/f1c643f0-1b0a-4324-af99-7a734c3aa0f9)
![unnamed](https://github.com/user-attachments/assets/3d438e20-7fc5-4432-85ff-d0e16f854c55)

## Model Development
The model development was quite an intensive iterative process. Given the high dimensional image data and the variance in the samples, we had to go through many model architectures before landing on one that was best able to capture the patterns within the classes. 
To start with a baseline model, we built a custom pytorch convolution neural network (CNN) model, and evaluated it against the dataset. This gave us a solid starting point for evaluation, but simply was not strong enough to truly understand patterns in the data. 
Next, we explored a variety of pre-trained models including ResNet50, ResNet18, and EfficientNet; however, we still did not see satisfactory performance. After further looking into state-of-the-art architectures, we turned to evaluating Vision Transformers (ViTs) with which we were seeing better accuracies. After evaluating a few, including Data-efficient Image Transformer (DeiT), Swin, and Google’s ViT, we landed on ConvNeXt V2, which ended up being our final model. We used the ConvNeXt V2 model with pretrained weights, and employed CrossEntropyLoss and Adam optimizer to minimize the loss function. 


## Results & Key Findings:
The primary metrics we used was the validation accuracy with 10 epochs. An epoch represents one complete pass through the training dataset and multiple epochs allow the model to iteratively improve its performance. At epoch 1, the validation score was 45.37%, which increased to 70.28% by epoch 4. Afterwards, the validation accuracy dropped to 69.93% and remained in that range between epoch 5 and 7, then went back to 70.98% at epoch 8 and 9, before ending epoch at epoch 10 with 69.58%. In addition, we saw that there was a steady decline in the training loss starting at 2.0790 at epoch 1 to 0.6191 at epoch 10. 

#### Some key insights:
Quick Improvement: The model improved quickly in the early epochs, showing that it picked up the important patterns fast.
Stabilization: After epoch 4, the validation accuracy stayed around 70%, suggesting the model has mostly settled.
Loss Reduction: The steady drop in training loss confirms that the model is learning well.
Fluctuations: Small ups and downs in the validation accuracy might be due to natural variation in the data or a little overfitting; tweaking the hyperparameters could help smooth these out.

A simple visual representation to better demonstrate:

![training graph](https://github.com/user-attachments/assets/7b135a28-3d8b-432f-82df-a2e6a4075ab2)

## Impact Narrative:
Throughout the project, we confronted a deeply relevant real-world challenge: how can AI be used not only to identify dermatological conditions but also to do so equitably across all skin tones, particularly those historically excluded from training datasets?

We began by evaluating a wide range of model architectures from custom CNNs, ResNets, EfficientNets, and Vision Transformers. After extensive experimentation, we found that our best results using ConvNeXt V2 large model pre-trained on ImageNet, coupled with augmentation strategies tailored to enhance generalization and reduce bias ,reached around 70% accuracy, showing that it could effectively learn important patterns from the data. 

While accuracy was important, our broader goal was to ensure that the model worked for everyone–especially those with darker skin tones, which is often overlooked in healthcare technology, and performance gaps are stark due to biased datasets. 

To address this, we also explored the dataset itself. We experimented with injecting additional examples of conditions and skin tones that were less prevalent in the original data. By integrating preprocessing adjustments based on Fitzpatrick skin tone levels, such as contrast enhancement and grayscale normalization, we took initial steps toward fairer representation in our pipeline. Although these adjustments didn't always boost accuracy in the short term, they offered us critical insights into how skin tone-specific features interact with model performance. These findings will guide our future work as we continue to develop more fairness-aware pipelines.

Ultimately, our project shows the importance of building AI systems that are not just technically strong but also ethically grounded. We aim to support dermatologists by reducing diagnostic biases and improving access to quality care—particularly in communities that have long been underserved. Looking ahead, we plan to integrate fairness metrics, improve data augmentation for darker skin tones, and use model interpretability tools to ensure our AI models are transparent and inclusive. By doing so, we hope to help make healthcare more equitable for everyone.

## Next Steps & Improvements

In future development, we plan to focus on:

### 1. Fairness Metrics Integration  
Incorporating metrics like demographic parity and subgroup accuracy to better identify performance gaps and reduce bias.

### 2. Skin Tone-Aware Augmentation  
Oversampling and augmenting data from underrepresented skin tones to create a more balanced dataset and improve model performance.

### 3. Explainability & Interpretability  
Using tools like Grad-CAM and SHAP to understand how the model makes decisions and ensure it's learning fair and meaningful representations.

Additionally, we would like to explore how our improved model can fit into real-world diagnostic frameworks to improve patient outcomes.

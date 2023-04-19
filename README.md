# Transformers4knapperskills
This study seeks to combine DIA and deep learning methods to evaluate if debitage assemblages from knappers with different expertise levels vary significantly. We collected debitage from knappers with varying levels of expertise ranging between 1-20 years of experience.  

## Background
+ Autoencoders- technique that uses encoder-decoder architecture to  learn how to compress and reconstruct data. It is mainly used for unsupervised learning.  
   + Computer vision: autoencoding can be used to remove noise from images, generate new images, or find hidden patterns in images.
+  Masked autoencoders (MAE): removes a portion of the data so the model can learn to predict the removed information. Masked auto encoding has been successfully applied to train generalizable NLP models (e.g BERT).  The authors, He and colleagues, argue that masked autoencoder models can be succesfully applied to computer vison. 

## Research Question
+ What makes masked autoencoding different between vision and language? 
   + Architecture
      +  Vision architecture used to be predominantly convolutional neural networks (CNN), which made integrating mask tokens and positional embeddings more difficult.
            + That changed with Vision Transformers (ViT)! 
            + Transformer architecture- Applying mask tokens and positional embeds more feasible. 
   +  Information density
      + Language is information dense and packed with meaning- masking a few word is enough of a challenge 
     + Images are heavy in spatial redundancy- masking can reduce redundancy and presents a more challenging task. 
   + Decoder
      + Language- predicts words
      + Image- reconstructs pixels

+ What is the best performing method for applying MAE to vision?
   
## Approach 

+  2 key parts to achieve self supervised learning with MAE:
  + Novelty of approach is assymetric encoder-decoder architecture
  + Masking a large portion of the image is the most effective to learning
   + Image divided into non-overlapping patches => sample a subset of patches and mask the rest. 

## Architecture Overview
 + ViT 
   + Encoder operates on the patches without mask tokens (below we see the patches with the flamingo visible are going into the encoder)
   + Embeds patches using linear projection and encodes positional embeds  
   + Output is a latent vector representation 
+ Decoder
   + Pre-training only
   + Input- all tokens, masked patches and encoded visible patches
   + Mask tokens signal a missing patch to be predited
   + positional embeds added to all tokens
   + Full input image is reconstructed with predicted pixel values for masked squares. 
+ Differences between input image and reconstruction are measured and used as loss (mean sq. error)
+ After pre-training decoder is discarded and encoder is kept for fine tuning, later used downstream tasks 

Q1: what are the positional embeddings for? 
+ Guide Q: What are they for in NLP models?

Q2: What is the advantage of the assymetric architecture? What about the masking ratio?
+ Guide Q: how much data is the encoder working with compared to the decoder? What is the main issue images v language?

   
  ![image](https://user-images.githubusercontent.com/80427603/222825277-991b51be-050f-4fa6-a72d-2e7dbc30cde9.png)

## Key Results
Image with mask tokens, reconstructed image, original image

![image](https://user-images.githubusercontent.com/80427603/223009216-00b5c5a3-597b-4224-8e5f-bbb50080c8fe.png)

![image](https://user-images.githubusercontent.com/80427603/223009302-ad59be13-7681-4f59-8e22-be8c309f39a5.png)

 Key results
   + 75% masking (BERT 15%)
   + Decoder can be lightweight and independent from encoder- large encoder for downstream tasks 
   + Encoder with mask tokens does not perform as well
   + Random sampling is optimal sampling strategy
   
![image](https://user-images.githubusercontent.com/80427603/223475154-c3d780a5-2761-492d-b3f8-cf41365f29b6.png)

![image](https://user-images.githubusercontent.com/80427603/223462902-286da5df-c9f8-4bfe-b87f-0cb6056b6687.png)

  + Performs well with and without data augmentation- role is done by random masking
  
![image](https://user-images.githubusercontent.com/80427603/223469167-8b285c58-f969-47ec-a820-5a2b4945a321.png)

  + increase in image reconstruction accuracy 
  + faster training (3x faster) than a whole image
  
+ Performance of MAE is tested on downstream tasks

![image](https://user-images.githubusercontent.com/80427603/223478348-cc410082-609e-44c5-b669-92cfd2a28b14.png)
![image](https://user-images.githubusercontent.com/80427603/223478509-34a6ff0e-a267-4f43-ac9b-842f6d31fac9.png)
   + Tables 5 and 4 compare MAE to DINO, MoCov3 and BEiT performance
   + Table 6 shows scaling behavior: accuracy improves with bigger models (ViT Huge) , applied to INaturalist and Places  
   + Table 7 shows comparison of pixel and token reconstruction. Pixel based reconstruction works fine (if normalized)

## Code Demo time!
+ The two senior authors created a repo with this demo (https://colab.research.google.com/drive/1NXe-zBSYKZTDugepN9_uFRDT8Ti708Vk#scrollTo=4573e6be-935a-4106-8c06-e467552b0e3d)

## Critical Analysis

+ Archaeologist’s approach to identifying novice work can be based on assumptions - novice/apprentice craftspeople are assumed to produce low quality products. 
“poor quality” is relative and unclear  (Wendrich 2013). DIA and deep learning models like ViT may provide a method to avoid this unreliable term along with other assumptions on how to identify novice and expert craftsmanship in the archaeological reocrd. 


## Additional Resources 
+ Intro to autoencoders video (https://www.youtube.com/watch?v=qiUEgSCyY5o&ab_channel=IBMTechnology)
+ This is a link to a Chen and He's repo on Github: (https://github.com/facebookresearch/mae)
+ ViT paper: An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale (https://arxiv.org/abs/2010.11929)
+ Vison transformers compared in paper: DINO (https://arxiv.org/abs/2104.14294) MoCov3 (https://paperswithcode.com/method/moco-v3) BEiT (https://arxiv.org/abs/2106.08254)
+ Proposed modification of MAE paper with github link: (https://openreview.net/pdf?id=qm5LpHyyOUO)

## Questions?

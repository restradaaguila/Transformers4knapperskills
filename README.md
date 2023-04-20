# Transformers4knapperskills
This study seeks to combine DIA and deep learning methods to evaluate if debitage assemblages from knappers with different expertise levels vary significantly. We collected debitage from knappers with varying levels of expertise ranging between <1-15 years of experience.  

## My Research- Skill and Craftspeople in the Past 

+ Knapping- process of chipping stone to produce tools like scrapers, knives, points (aka arrowheads), or can be non functional. 
   + Knapping communities of the past and skill acquisition in ancient Maya society 
+ While flintknapping studies in archaeology have always been present and popular within the discipline, recent research on flintknapping reflects a growing interest in the connection between artifact variability and the skill of past craft workers. Integral to these investigations is the development of methods to identify the material “signatures” of novice and expert  manufacturers. 
+  However, archaeological research on craft and skills is faced with the challenge of identifying craftsmanship and skill acquisition in the material record (Roddick and Stahl 2016:7, Wendrich 2013, Milne 2013). To bridge the gap between past craft production and present interest in these topics, archaeologusts can turn to living craftspeople replicating ancient techniques and technologies (experimental archaeology). 

![Figure 2_Volunteer_knapper](https://user-images.githubusercontent.com/80427603/233222699-6fbd0a22-167d-4e1a-a1ec-78499defad63.jpg)
![Debitage pic](https://user-images.githubusercontent.com/80427603/233234557-d92cbcbd-8ac3-4435-ac9c-99eb4090020d.png)
+ Debitage- byproduct of knapping; Microdebitage- flintknapping debris smaller than about a 1/4 inch long. They are fairly difficult to analyze because of their small size, but because of that microdebitage is less likely to be moved, modified, disposed by people. 
   
## Approach 
+   Comapring CNN and Vision transformer
![Figure3_PartAn3D_analyzer](https://user-images.githubusercontent.com/80427603/233233767-3ada0aaa-bb21-4b1a-b8dd-0f6bf7011fc5.jpg)
+   Comapring CNN and Vision transformer
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
  
## Results
Image with mask tokens, reconstructed image, original image



## Code Demo time!
+ https://colab.research.google.com/drive/1NmxwBfK5MkQQ521gnCyHvofEMKbTvxG-#scrollTo=LSnQ0eX0t1bd

## Critical Analysis

+ Archaeologist’s approach to identifying novice work can be based on assumptions - novice/apprentice craftspeople are assumed to produce low quality products. 
   + “poor quality” is relative and unclear (Wendrich 2013). DIA and deep learning models, like ViT, may provide a method to avoid this unreliable term along with other assumptions on how to identify novice and expert craftsmanship in the archaeological reocrd. 
+ What's next?
   + 


## Additional Resources 
+ Intro to autoencoders video (https://www.youtube.com/watch?v=qiUEgSCyY5o&ab_channel=IBMTechnology)
+ This is a link to a Chen and He's repo on Github: (https://github.com/facebookresearch/mae)
+ ViT paper: An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale (https://arxiv.org/abs/2010.11929)
+ Vison transformers compared in paper: DINO (https://arxiv.org/abs/2104.14294) MoCov3 (https://paperswithcode.com/method/moco-v3) BEiT (https://arxiv.org/abs/2106.08254)
+ Proposed modification of MAE paper with github link: (https://openreview.net/pdf?id=qm5LpHyyOUO)

## Questions?

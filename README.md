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
   
## Dataset Information and Classification
   + The chert debitage collected for this study was produced from experimental knapping collected from Tennessee knap-ins between July and October 2021. The debitage collected represents two experience levels chosen to train the models: Novice and Expert. These categories are based on the years of experience of the knapper. The data on experience was gathered from the short surveys and brief interviews. Debitage was gathered from three volunteer knappers with varying years of experience. The novice knapper had less than a year of experience and the two volunteers classified under expert have 7 and 15 years of knapping experience. 

# The Models
+Comapring CNN and Vision transformer
![Figure3_PartAn3D_analyzer](https://user-images.githubusercontent.com/80427603/233233767-3ada0aaa-bb21-4b1a-b8dd-0f6bf7011fc5.jpg)
+   Comapring CNN and Vision transformer
+ Transformer 
  + 8004 images were fed to the transformer model 
## Architecture Overview
 + ViT 
   + Fine tuning
 + CNN and Resnet 
   + The code for the deep learning model used here is adapted from Johnson et al. which was modified from Practical Deep Learning for Coders course on Fast.ai (see Resources). The images were analyzed using pre-trained CNN models from Fast.ai and were  resized to 128x128. Four CNN models were used on the debitage photos, each with an increased number of “layers” which were expected to increase accuracy. The images were initially analyzed with ResNet18, followed by ResNet34, ResNet50, ResNet101, and ResNet152.
   + The number of epochs, the number of times the training data is passed through the CNN, was increased from the initial 4 of the original code to 8 epochs.

  
## Results
+ 



## Code Demo time!
+ https://colab.research.google.com/drive/1NmxwBfK5MkQQ521gnCyHvofEMKbTvxG-#scrollTo=LSnQ0eX0t1bd

## Critical Analysis

+ Archaeologist’s approach to identifying novice work can be based on assumptions - novice/apprentice craftspeople are assumed to produce low quality products. 
   + “poor quality” is relative and unclear (Wendrich 2013). DIA and deep learning models, like ViT, may provide a method to avoid this unreliable term along with other assumptions on how to identify novice and expert craftsmanship in the archaeological reocrd. 
+ This preliminary study is the first step in applying transformer and CNN models to identify skill level in debitage assemblages. Our method, once refined and tested with archaeological samples, has the implications to impact  how archaeologists approach and identify skill in the lithic archaeological record. 

+ What's next?
   + Controlling the data- Factors outside of skill level that may have contributed to our results. These factors might be raw material type or heat treatment, and reduction technique. One aspect of this study that can be improved is the consistency of the raw material of the debitage. The knappers in this preliminary study used different chert varieties and one knapper worked with heat treated stone, while the others did not. The next phase of the research is to ensure that the material used to produce the debitage samples are similar (same stone type, treatment, and knapping techniques).  This step would help minimize any other factors linked to the material and technique that can contribute to the CNN and transformer results.
   + Applying larger vision models to see if accuracy is improved 

## Additional Resources 
+ Intro to fast.ai https://arxiv.org/abs/2002.04688
   + Fast.ai vision tutorial and code https://docs.fast.ai/tutorial.vision.html
+ 
## Questions?

# Transformers4knapperskills
This study seeks to combine Dynamic Image Analysis and deep learning methods to evaluate if debitage assemblages from knappers with different expertise levels vary significantly. I collected debitage from knappers with varying levels of expertise ranging between <1-15 years of experience.  

## My Research- Skill and Craftspeople in the Past 

+ Knapping- process of chipping stone to produce tools like scrapers, knives, points (aka arrowheads), or can be non functional. 
   + Knapping communities of the past and skill acquisition in ancient Maya society 
+ Setting up the Problem:
   + While flintknapping studies in archaeology have always been present and popular within the discipline, recent research on flintknapping reflects a growing interest in the connection between artifact variability and the skill of past craft workers. Integral to these investigations is the development of methods to identify the material “signatures” of novice and expert  manufacturers (Amick and Mauldin 1989, Clark 1997 AND 2003, Shelley 1990). 
   +  However, archaeological research on craft and skills is faced with the challenge of identifying craftsmanship and skill acquisition in the material record (Roddick and Stahl 2016:7, Wendrich 2013, Milne 2013). To bridge the gap between past craft production and present interest in these topics, archaeologists can turn to living craftspeople replicating ancient techniques and technologies (experimental archaeology). But, analysis of debitage is subjective, non-standardized, and extremely time consuming using traditional methods. 
+  My Method 
   +  Using experimental samples collected from contemporary flintknappers with different skill levels 
   +  Particle analyzer and Dynamic Image Analysis to provide images for image classification
   +  Deep learning methods to identify skill level and variation between individual knappers. 
      +  Comparing CNN and Vision tranformer performance
   +  Not focusing on the product, but on the byproduct!
+  The Task
   +   Image classification: Can a vision transformer accurately identify the debitage assemblage to the knapper who made it?  Can it identify the "signatures" of Novice knapper from the Experts that might elude the human eye?
 

![Figure 2_Volunteer_knapper](https://user-images.githubusercontent.com/80427603/233222699-6fbd0a22-167d-4e1a-a1ec-78499defad63.jpg)
![Debitage pic](https://user-images.githubusercontent.com/80427603/233234557-d92cbcbd-8ac3-4435-ac9c-99eb4090020d.png)
+ Debitage- byproduct of knapping; Microdebitage- flintknapping debris smaller than about a 1/4 inch long. They are fairly difficult to analyze because of their small size, but because of that microdebitage is less likely to be moved, modified, disposed by people. 
   
## Dataset Information and Classification
   + The chert debitage collected for this study was produced from experimental knapping collected from Tennessee knap-ins between July and October 2021. The debitage collected represents two experience levels chosen to train the models: Novice and Expert. These categories are based on the years of experience of the knapper. The data on experience was gathered from the short surveys and brief interviews. Debitage was gathered from three volunteer knappers with varying years of experience. The novice knapper had less than a year of experience and the two volunteers classified under expert have 7 and 15 years of knapping experience. 
   + Particle analyzer and Dynamic Image Analysis- Dynamic Image Analysis (DIA) is a method shown to identify lithic particles in soil samples. DIA produces raw data from particles in the form of digital photographs and measurement data for individual particles. This method is accomplished through the use of a particle analyzer to process the samples. 

![Figure3_PartAn3D_analyzer](https://user-images.githubusercontent.com/80427603/233233767-3ada0aaa-bb21-4b1a-b8dd-0f6bf7011fc5.jpg)
![Screenshot 2023-04-20 001215](https://user-images.githubusercontent.com/80427603/233264364-463b1714-9cc9-494b-be0b-444754d659d7.png)

+ 8000 images were fed into the vision transformer- 5000 from the Expert category and 3000 from the Novice category

# The Models
+ Vision Transformer
![image](https://user-images.githubusercontent.com/80427603/233266971-7779a9d0-2d30-4837-8251-06479ecc8398.png)
![the-transformer-block-vit](https://user-images.githubusercontent.com/80427603/233422356-58456d66-18c3-4dff-9889-1967935084d8.png)
*Illustrations from Dosovitskiy el al (2020)

 + Proposed in An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale by  Dosovitskiy et al  (2020) (See Resources). 

 + I used ViT base and large models
 	+ Pre-trained on ImageNet-21k, 14 million images, 21,843 classes at resolution 224x224
   + Images are fed to the model as a sequence of fixed size, non-overlapping patches (resolution 16x16), which are linearly embedded. Positional embeddings and classification tokens (used for classification tasks) are added. The sequence then passes through  a Transformer encoder. Linear layer, MLP head, is used for final classification.  
   + Images are resized/rescaled to the same resolution (224x224)
   + normalized across the RGB channels with mean (0.5, 0.5, 0.5) and standard deviation (0.5, 0.5, 0.5).

 ![image](https://user-images.githubusercontent.com/80427603/233260210-a744c511-a526-439b-9f0c-c0741957151d.png)
 
  + Fast.ai for Vision
   + The code for the deep learning model used here is modified from Practical Deep Learning for Coders course on Fast.ai (see Resources). Fast.ai is a deep learning library. Its vision module contains all the needed functions to define a dataset and train a pre-trained model for custom vision tasks. The images were analyzed using pre-trained CNN models from Fast.ai and were resized to 128x128. Four CNN models were used on the debitage photos, each with an increased number of “layers” which were expected to increase accuracy. The images were initially analyzed with ResNet18, followed by ResNet34, ResNet50, ResNet101, and ResNet152.
   + The number of epochs, the number of times the training data is passed through the CNN, was increased from the initial 4 of the original code to 8 epochs.

## Code Demo time!
+ https://colab.research.google.com/drive/1NmxwBfK5MkQQ521gnCyHvofEMKbTvxG-#scrollTo=vMUkg0mndL0t
  
## Results
+ ViT base-size
   + 3 epochs

![ViTtrainingresults](https://user-images.githubusercontent.com/80427603/233410620-d6bf03b0-9548-4a9a-bafd-214eec2f0d0e.png)

![confusionmatrixViT](https://user-images.githubusercontent.com/80427603/233378449-09656102-d19e-4ef7-b02e-38a5b28f216b.png)

    + 5 epochs
    
![5 epochs](https://user-images.githubusercontent.com/80427603/233378722-0fcc10da-c7cf-45fd-867b-8a571420758f.png)
![confusionmatrix_5epochs](https://user-images.githubusercontent.com/80427603/233378743-048b2d4e-272f-4ac7-a3cf-0b0764498166.png)

+ ViT large-size 

   + 3 epochs
   
![Screens![Screenshot 2023-04-20 092006](https://user-images.githubusercontent.com/80427603/233396439-3629bed4-d20a-4d7a-980e-906534374884.png)
hot 2023-04-20 091907](https://user-images.githubusercontent.com/80427603/233396387-1fb18026-8516-4110-bb93-13e2670baa7b.png)
![Screenshot 2023-04-20 092006](https://user-images.githubusercontent.com/80427603/233399092-316d1383-c6d5-4e92-962e-8825b94958cc.png)

   + 4 epochs 
   
![4 epochs](https://user-images.githubusercontent.com/80427603/233403763-30080303-1081-4213-b326-772532980ef3.png)

![4 epoch confusion](https://user-images.githubusercontent.com/80427603/233403787-29944ed6-f4da-4151-9082-4d95abd9b47d.png)


Lets compare that to the CNN model using ResNet101 and 152 at 8 epochs
![4](https://user-images.githubusercontent.com/80427603/233383000-fd3afc8e-96c0-4f3f-9776-13cdf51b652f.png)

![2](https://user-images.githubusercontent.com/80427603/233383033-37a86e72-6c8c-41e0-8d4c-1c774a7ce20e.png)

## Critical Analysis

+ Archaeologist’s approach to identifying novice work can be based on assumptions - novice/apprentice craftspeople are assumed to produce low quality products. 
   + “poor quality” is relative and unclear (Wendrich 2013). DIA and deep learning models, like ViT, may provide a method to avoid this unreliable term along with other assumptions on how to identify novice and expert craftsmanship in the archaeological reocrd. 
+ This preliminary study is the first step in applying transformer and CNN models to identify skill level in debitage assemblages. Our method, once refined and tested with archaeological samples, has the implications to impact  how archaeologists approach and identify skill in the lithic archaeological record. 

+ What's next?
   + Controlling the data- Factors outside of skill level that may have contributed to our results. These factors might be raw material type or heat treatment, and reduction technique. One aspect of this study that can be improved is the consistency of the raw material of the debitage. The knappers in this preliminary study used different chert varieties and one knapper worked with heat treated stone, while the others did not. The next phase of the research is to ensure that the material used to produce the debitage samples are similar (same stone type, treatment, and knapping techniques).  This step would help minimize any other factors linked to the material and technique that can contribute to the CNN and transformer results.
   + Applying more tweaks to the ViT to see if accuracy is improved- The ViT Large at 4 epochs results are comparable to the Resnet152 at 8 epochs. Time to get the results is longer with the Resnet because it has to go through 8 epochs. 
   + What other categories related to flintknapping can be identified? 

## Additional Resources 
+ Intro to fast.ai https://arxiv.org/abs/2002.04688
   + Fast.ai vision tutorial and code https://docs.fast.ai/tutorial.vision.html
+ ViT paper,  An Image is Worth 16x16 Words: https://arxiv.org/abs/2010.11929
+  Huggingface ViT large model: https://huggingface.co/google/vit-large-patch16-224-in21k#vision-transformer-large-sized-model
   + base model: https://huggingface.co/google/vit-base-patch16-224-in21k
+ Rogge github with notebook: https://github.com/NielsRogge/Transformers-Tutorials/blob/master/VisionTransformer/Fine_tuning_the_Vision_Transformer_on_CIFAR_10_with_the_%F0%9F%A4%97_Trainer.ipynb
+ Other notebook used: https://github.com/huggingface/notebooks/blob/main/examples/image_classification.ipynb
+ Literature cited 
   + Wendrich, Willeke
2013	Recognizing Knowledge Transfer in the Archaeological RecordIn Archaeology and Apprenticeship : Body Knowledge, Identity, and Communities of Practice, edited by Willeke Wendrich. University of Arizona Press, Tucson.
   + Milne, S. Brooke 
2013	Lithic Raw Material Availability and Palaeo- Eskimo Novice Flintknapping. In Archaeology and Apprenticeship : Body Knowledge, Identity, and Communities of Practice, edited by Willeke Wendrich. University of Arizona Press, Tucson. 
   + Roddick, Andrew P.; Stahl, Anne B. 
2016	Introduction: Knowledge in Motion. In Knowledge in motion : constellations of learning across time and place. Edited by Andrew Roddick and Anne P. Stahl. University of Arizona Press, Tucson.
   + Shelley, P. H. 
1990	Variation in Lithic Assemblages: An Experiment. Journal of Field Archaeology 17(2):187-193.
   + Amick, D. S. and R. P. Mauldin
 1989 	Experiments in Lithic Technology. BAR International Series 528, Oxford. 
   + Clark, John E. 
1997	Prismatic Blademaking, Craftsmanship, and Production: An analysis of obsidian refuse from Ojo de Agua, Chiapas, Mexico. Ancient Mesoamerica 8: 137-159.
       + 2003	Craftsmanship and Craft Specialization. In Mesoamerican Lithic Technology: Experimentation and Interpretation, edited by K.G. Hirth. Salt Lake City: University of Utah Press, Salt Lake City. 

## Questions?

#   H 1 - A F 
=============
[TOC]

Ann-K working repo for AI4Goodlab
-- aim for Segmentation of Amniotic Fluid, by machine learning on Ultrasound image - UNet. 
But we are modular approach. my current contribution is on doing a random forest regression between pixel size and head circumstance, 
and manual annotation for fetal ultrasound that we can retrieve.

Not all of the AF discovery team's code are here, as we run our Unet code in Google Collab.

---------------

### The whole training pipeline :

 [ Ultrasound Image ]  --> [    Unet   ] -->  [ Binary Image of Unet annotation ]   

                                                                                        |

​											  v

​									 [] Pixel count 	of Unet annotation ]									

​		

​       [ pixel size field in CSV  ]  ---->             Random Forest Regressor

​                                                                                          |

​											  V

​									Predicted HC (head circumference)

---------------------------------------------------------------------

Validate with Ground Truth - HC field in CSV

​     



-----

### Data Sources:

We did attempts to seek more sources of ultrasound image dataset that are relevant in segmenting amniotic fluid 
-- both researchers and clinical training program for sonographers.

Our team use the data from https://hc18.grand-challenge.org/.  The data themselves are downloaded from Zenodo.  
[DOI 10.5281/zenodo.1322001](https://doi.org/10.5281/zenodo.1322000) 

The images from HC18 are taken in specific cross section of the fetal head, which is called the **standard plane**. 

Total images:  a total of 1334 two-dimensional (2D) ultrasound images of the standard plane.  Training set: 999, Test set: 335.

The set also contains two CSV files which has pixel size (mm) for each images.

The training set has manual annotation of head circumference, by trained clinical professional (sonographer).

Some of them were made during same echoscope examination. those images with name _2HC.png are those additional images.

------------

We have also looked at FRU23 dataset (FPUS23: An Ultrasound Fetus Phantom Dataset with Deep Neural Network Evaluations for Fetus Orientations, Fetal Planes, and Anatomical Features, https://arxiv.org/abs/2303.07852) which has 4 planes for such cases, but there is no ground truth on structure.

We have also looked into manually annotating the image dataset, but we feel that we do not have enough expertise to do so, and the images wre not in the DICOM or other medical imaging format that the software - ITK-SNAP - can support.

----

### My background as relevent to AI4Good

"As a soon-to-graduate Master of Science student in Interactive Arts and Technology at Simon Fraser University, my background is highly relevant to this health-related AI4Good project. With a background as a medical technologist and health informatics practitioner, I bring a unique perspective to the table. Additionally, I am severely hard of hearing and have recently been diagnosed with Autism Spectrum Disorder. These personal experiences have fueled my passion for using technology and AI for the greater good. Joining the AI4Good lab provides me with an opportunity to enhance my technical skills and stay up-to-date with the latest machine learning concepts. Through my own research in electronic health records, I have shifted my focus towards an art-oriented activist community approach and empathy-driven design. This change is partly influenced by the challenges in accessing clinical data and the shifting priorities in the clinical realm due to the impact of COVID-19. I would like to express my gratitude to AI4Good for fully supporting my special needs as a person with a disability.

The duration of the 3-week project might seem short, but for me, it strikes a good balance. The project is around the similar size and scope as a typical 2-day hackathon, but having 3 weeks allows us to take our pace to troubleshoot and apply the new skills. Since many of us are no longer young, full of energy individuals, but rather someone who lives with burdens, this time frame lets us take care of ourselves and other obligations while still dedicating time to learning and working on the project."

-----------------

### References

- Thomas L. A. van den Heuvel, Dagmar de Bruijn, Chris L. de Korte and Bram van Ginneken. Automated measurement of fetal head circumference using 2D ultrasound images. *PloS one*, 13.8 (2018): e0200412.

- Thomas L. A. van den Heuvel, Dagmar de Bruijn, Chris L. de Korte and Bram van Ginneken. Automated measurement of fetal head circumference using 2D ultrasound images [Data set]. Zenodo. <http://doi.org/10.5281/zenodo.1322001>

- arXiv:2303.07852 [eess.IV]  https://doi.org/10.48550/arXiv.2303.07852

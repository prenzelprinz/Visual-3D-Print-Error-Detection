# Visual-3D-Print-Error-Detection
This repository is for a Course tittled "Learning from Images" at BHT. Our Project is to detect if a 3D-Print has failed with the help of Cameras,CNN and Domain shifting.

# Preface
This Idea ist not new and also has been done before but we and my colleague want to implent it ourself. We are trying to use an allready labeld Dataset from Kaggle where the Camera is directly mounted to the Nozzle which is maybe not Ideal for detecting failes of the whole Print but it could be used for first layer print fail detection. Further more what could be also done with this setup is tuneing in the Printing paramtes live (this has also be doen befoere)

# Camera Mount 
The Camera is how i allready mentioned directly mounted to the print-head via a 3D-Printed mount https://www.printables.com/de/model/17993-prusa-mk3s-55mm-nozzle-camera-mount 

This mount may be not the perfect mount for the camera postion and image we generate trough that. There are many alternatives on Printables and if none of them match our Requierments we could design one ourself 

# 3D-Printer
The Printing is done on one of our own upgraded Prusa MK3S+. As a Filament we gonna use White PLA from FilaFarm because it gives the best contrast to the green printbed and the gold like nozzle.  

# Data Sets
How allready mentioend we are using an Kaggle dataset which has around 100k images which should be enough for this type of work. another dataset which we maybe gonna use is the cambridge one. This one has arround 1.25 mio images in its dataset which are also classifed into more labels then the KAglle one they have more diffrent describign aspects liek temperaturea nd speed to it. These details make it more suited for the live adjusting paramter programm.

# Code
Our Plan right now is it too solve our Error-Detection with CNNs and doamin shifitng 

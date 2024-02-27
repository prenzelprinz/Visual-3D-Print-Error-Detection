# Visual-3D-Print-Error-Detection
This repository is for a Course tittled "Learning from Images" at BHT. Our Project is to detect if a 3D-Print has failed with the help of Cameras,CNN and Domain shifting.

# Preface
This Idea ist not new and also has been done before but we and my colleague want to implent it ourself. We are trying to use an allready labeld Dataset from Kaggle where the Camera is directly mounted to the Nozzle which is maybe not Ideal for detecting failes of the whole Print but it could be used for first layer print fail detection. Further more what could be also done with this setup is tuneing in the Printing paramtes live (this has also be doen befoere)

# Camera Mount 
The Camera is how i allready mentioned directly mounted to the print-head via a 3D-Printed mount https://www.printables.com/de/model/17993-prusa-mk3s-55mm-nozzle-camera-mount 

![prusa_i3_mk3s_endocamera_mount_17993](https://github.com/prenzelprinz/Visual-3D-Print-Error-Detection/assets/132297533/261fa786-227b-4fea-8149-536212d40aad)

This mount may be not the perfect mount for the camera postion and image we generate trough that. There are many alternatives on Printables and if none of them match our Requierments we could design one ourself 

We tried another setup because it matched more the angel and generell type of pictures of the Kaggle dataset.
![endoholder](https://github.com/prenzelprinz/Visual-3D-Print-Error-Detection/assets/132297533/51e9bb7a-48fd-4496-a051-a5fb4b7486bd)

In the end we went back to the original mount becasue its image and angle turend out to be the best.Nonetheless we used the enhanced version of it with a screw which secures agianst rotation of the camera which asures a stable image. 

# Camera & Lights 
The Camnera itself is a endoscope type camera whit some leds in the lens. The camera was not very expensiv which si the mainr eason we chossed it and also it size and capibilty to be mounted close to the nozzle. 

The Problem occured as we vied the images. There Qualitiy was ok in bright enviroments but lacked in dark enviroments .The light at the end of the endoscope reflected on the lens and created artefacts furthermore the resolution was also very low which was recognizable in the dark. 

The lighting in whole was of the very delicated matter.As i mentioned before there are tinx led lights at the end of the lens. Those are dimmebel which helps but i cann only use them with 25 to 50 % of the capacity because after that they make lens artefacts. I also have lights mouted in the enclosre of the printer. One might think that would help but they just trhow shadows on the print bed and the nozlle which makes the dettection of erros even harder.

# 3D-Printing
The Printing is done on one of our own upgraded Prusa MK3S+. As a Filament we gonna use White PLA from FilaFarm because it gives the best contrast to the green printbed and the gold like nozzle. We are using a standard profile with 0.2mm layerhight and a print speed of 100% (Standard prusa speed ???) and 0.4 Nozzle. Those Settings are the most widlyused settigns in the 3D-Printign Community.

In later stages we tried to use green filament becuase of the reflectiv properties of the white filament which maybe cused problems. Suprigsily there was also used very little white filament in the datasets and more green for example. 
Grenn didn't seem to improve the recognition. We are gonna try blue Filament now of which there was abondens in the dataset.  

# Data Sets
How allready mentioend we are using an Kaggle dataset which has around 100k images which should be enough for this type of work. another dataset which we maybe gonna use is the cambridge one. This one has arround 1.25 mio images in its dataset which are also classifed into more labels then the Kaggel one they have more diffrent describign aspects liek temperaturea nd speed to it. These details make it more suited for the live adjusting paramter programm.

After further investigation it appeard that the Kaggle dataset is not focused on a geenral fail like bed addhesion or stringing or jsut awful print starts. It is focused on underextrusion. this is not in particualr a problem but under extrusion is problem or fale typ that doenst occur unless the user did something majorly wrong. Under extrusion only happens wehn paremters liek feeding rate or clogging come into affect but Problems liek bed adhesion are a way more on the day Problem for a User. It is not as easy to recreate the Problem as well. For under extrussion u have to force baly try to trun the extrsuin parmeters down for bed addhesion you just touch the bed and thats enough.

# Code
Our Plan right now is it too solve our Error-Detection with CNNs mainly. The Problem that occurs with the under extrusion dataset is that domain shifitng, alteast how it looks right now, is gonna be required. First test showed that the recorded prints of our printer are not getting recognized. Which could have multiple reason like camera and light problems which we tried to mitigate trough using grayscale. This didnt really seem to help. 

It works great with the test images from the dataset. we dont know exactly what our feuarte map looks like which makes it difficult for us

We also integrated a function for taking a live camera image which comes form the endoscope camera and also controlling the printer 

#Octoprint integration
The printer is controlled over a rasberry pie 3b+ with octoprint isntalled on it. this makes conrtolling the pretty easy. On problem is tho that recording the footage for the neural net. the way we do it that i stream the cmaera image to the octoprint browser control iamge and from there i record it with OBS on my PC. the reason for why we dont record it directly to the rasbery pie ist that the fiel sizes are to big for the small sd card also to interactwith the code and the fottage its eazier to that directly on the pc.




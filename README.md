# Climatevision: Disaster Forecsting
There are four aspects of comouter vision that could be applied to climate environmetns:

1- Climate classification

2- Climate object detection/ Segmentation 

3- climnate change

4- Climate forecasting 

1- Climate classification:
The purpose of this type is to receive climate images and train an image processing model and after trianing being able to classify objects/sectors/ areas of a cliamte. This could be categorized in the image classficaition. There should be enough images for each object othervise the model would be biased towards the objects having more images in the training set. 

2- Climate object detection (Image Segmentation): 
The purpose of thsi type is to receive climate images and train an object detection model capable of detecting desired objects in the cliamte environment. In the agricultral domain, one very demanding service is an object detection model which can process a landcover ( a crop filed or a pasture) and detect the weeds. The weeds are a seriouse problem for diary farmers. Every year they need to spend tons of dollars and tens of hours to investigate their pastures and detect weeds. They also assign tremendouse amount of time and energy for weed destroying. 

![1](https://user-images.githubusercontent.com/47879342/230290452-4117af94-b9c0-4b5c-827f-1fe340250a47.png)
![5](https://user-images.githubusercontent.com/47879342/230290484-8daa44d7-46e8-436e-a34e-e903d99fd291.png)

![1](https://user-images.githubusercontent.com/47879342/230290529-5a58f21d-ae0f-4fd8-8b8d-c9b707d1d0d9.png)
![5](https://user-images.githubusercontent.com/47879342/230290800-d71e5fc0-12fa-4e95-85a2-c368f094c5ee.png)

The above photos show the image segmentation output of a MaskRCNN model that has being trained for pasture based images. The photos show theresults based on plant and leave objects. If we want to hsow the resutls of whole plants we need to train the models based on whole plants. For the leave based we need to create our dataset based on individual leaves. 

We used the following methodlogy for creating our synthetic dataset and training mdoel: 

1- Photo taking from the land
2- Extracting the desired objects from the photos
3- Creating a synthetic dataset based on the photos
4- Creating annotations for mask and labels
5- Defining a proper configuration for the training model
6- Training the model
7- Model evaluation and testing

The following figure shows the schematic diagram of the abovementioned steps: 

![method](https://user-images.githubusercontent.com/47879342/230292740-a32ae9b6-b70f-41d1-b481-221f5a37444e.png)

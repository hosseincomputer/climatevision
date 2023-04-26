# Climatevision: A Technical Comparison Between SAM and MaskRCNN
There are four aspects of comouter vision that could be applied to climate environmetns:

## 1- Climate classification

## 2- Climate object detection/ Segmentation 

## 3- Climnate change

## 4- Climate forecasting 

## 1- Climate classification:
The purpose of this type is to receive climate images and train an image processing model and after trianing being able to classify objects/sectors/ areas of a cliamte. This could be categorized in the image classficaition. There should be enough images for each object othervise the model would be biased towards the objects having more images in the training set. 

## 2- Climate object detection (Image Segmentation): 
The purpose of thsi type is to receive climate images and train an object detection model capable of detecting desired objects in the cliamte environment. In the agricultral domain, one very demanding service is an object detection model which can process a landcover ( a crop filed or a pasture) and detect the weeds. The weeds are a seriouse problem for diary farmers. Every year they need to spend tons of dollars and tens of hours to investigate their pastures and detect weeds. They also assign tremendouse amount of time and energy for weed destroying. 

<img src="https://user-images.githubusercontent.com/47879342/230290452-4117af94-b9c0-4b5c-827f-1fe340250a47.png" alt="before" width="400"/> <img src="https://user-images.githubusercontent.com/47879342/230290484-8daa44d7-46e8-436e-a34e-e903d99fd291.png" alt="before" width="400"/>
<img src="https://user-images.githubusercontent.com/47879342/230290529-5a58f21d-ae0f-4fd8-8b8d-c9b707d1d0d9.png" alt="before" width="400"/>
<img src="https://user-images.githubusercontent.com/47879342/230290800-d71e5fc0-12fa-4e95-85a2-c368f094c5ee.png" alt="before" width="400"/>

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

<img src="https://user-images.githubusercontent.com/47879342/230292740-a32ae9b6-b70f-41d1-b481-221f5a37444e.png" alt="method" width="400"/>

We have evaluated our climate images by the SAM model which has been released by the Facebook vision team. Throught our test we experimented several images from simple to fuzzy/complex. We played by several factors but interestingly the IOE threshold play a great role in mask detection. 

### The model comparison
When it comes to the functionalities of MaskRCNN and SAM, both operate on pixel-wise images and generate masks for the objects they can recognize within an image. However, there is a significant distinction between the two. MaskRCNN is trained by targeting a specific object within an image, whereas SAM can detect any object present in an image.

Another key difference is the size of their trained models. MaskRCNN's model size is 200MB, while SAM's is approximately 2.5GB, which could potentially cause latency issues during model transfer and deployment in real-world applications.

### The Training Time and Inference Time 
The training time of MaskrCNN is much lower than SAM. This is also true about the inference time. For high resolution images you might receive a RAM crash message. (I received this several times :))

### The output

### SAM segements study by UOI prediction
This section aims to demonstrate the impact of UoI on the number of detected masks. The chart displays that increasing the prediction ratio of UoI leads to a more conservative model, resulting in fewer detected masks. Conversely, a lower prediction ratio will lead to more masks being detected, as the model becomes less strict in its criteria. The following chart illustrates this trend, and the subsequent two images display the model's output for different UoI prediction ratios. By setting a low UoI prediction ratio of 0.74, the model detects around 500 masks. In contrast, setting a higher prediction ratio of 0.92 results in the detection of only 100 masks. This highlights the importance of studying and properly setting parameters such as UoI in determining the model's behavior.
![image](https://user-images.githubusercontent.com/47879342/234497624-cd5d7ab6-fe5f-48a0-a0b0-9d209169bcc6.png)


<img src="https://user-images.githubusercontent.com/47879342/234495649-ed2df3cf-735d-4c3c-a675-7dfbc4a85521.png" alt="before" width="400"/><img src="https://user-images.githubusercontent.com/47879342/234495665-b332f19c-631f-4e90-b4b4-e2fa33b427e1.png" alt="before" width="400"/>


### Image resolution study ====> image resolution vs running time

### Studying of image complexity: 
In the following section, I demonstrate how SAM performs on various images with different levels of complexity. The complexity is defined by the presence of foreground and background elements, such as single or multiple objects in a simple or fuzzy background. The following subsections show how I increased the images complexity: 

#### 1- An object on a simple background
<img src="https://user-images.githubusercontent.com/47879342/234499088-4abcb2ca-3825-4534-92aa-0687fb89e2f1.jpg" alt="before" width="400"/><img src="https://user-images.githubusercontent.com/47879342/234499097-2eba37eb-87c1-40f8-8ece-0d3a4f3368b7.png" alt="before" width="400"/>

#### 2- Two objects on a simple background
<img src="https://user-images.githubusercontent.com/47879342/234499411-7d0256e3-9d2c-4e43-8053-06bcb1bbf30d.jpg" alt="before" width="400"/><img src="https://user-images.githubusercontent.com/47879342/234499422-06c4cf5a-9f1d-4e44-901c-5697807fd2be.png" alt="before" width="400"/>


#### 3- Two objects on a fuzzy background

<img src="https://user-images.githubusercontent.com/47879342/234499638-5a406e55-cf68-4c5c-9dab-01e22610b8a9.jpg" alt="before" width="400"/><img src="https://user-images.githubusercontent.com/47879342/234499648-2e5b84cd-ca0c-454c-a323-f556341df32e.png" alt="before" width="400"/>



#### 4- Two objectes on a complex background

<img src="https://user-images.githubusercontent.com/47879342/234500073-ac7b287d-c2dc-4e90-8b96-d176417c5f33.jpg" alt="before" width="400"/><img src="https://user-images.githubusercontent.com/47879342/234500081-7a1bad90-07fd-4975-a5ab-8b1f1b254203.png" alt="before" width="400"/>





#### 5- A colorful background
#### 6- Putting glassy objects 
#### 7- Multiple objects on a simple background
#### 8- Multiple objects on a fuzzy background
#### 9- Various objects on a fuzzy background
#### 10- Multiple objects on a fuzzy background

2- two objects
3- multiple objects
4- fuzzy background
4- fuzzy foreground and fuzzy background

## 3- Climate change detection
These type of models work on detecting any changes to a specific area based on processign the sattelite images. The simple case is to compare two images and detect any changes of the area that could be : adding buildings, land coverage and water invasion and flooding with the focus of climate disaster detection. Following are some examples of iamge detection. 

Example 1: 

<img src="https://github.com/ChaymaBouzaidii/Change-detection-in-multitemporal-satellite-images/blob/master/images/Argentina/Argentina_01131994.jpg" alt="before" width="500"/>

<img src="https://github.com/ChaymaBouzaidii/Change-detection-in-multitemporal-satellite-images/blob/master/images/Argentina/Argentina_01202014.jpg" alt="after" width="500"/>

Example 2: 

<img src="https://github.com/ChaymaBouzaidii/Change-detection-in-multitemporal-satellite-images/blob/master/images/ArcadiaLake/ArcadiaLake1986.jpg" alt="after" width="500"/>

<img src="https://github.com/ChaymaBouzaidii/Change-detection-in-multitemporal-satellite-images/blob/master/images/ArcadiaLake/ArcadiaLake2011.jpg" alt="after" width="500"/>

    

One potential work here is to to train a model to receive the sequence of images and forecast the future shape of area. The following pipeline could be considered here: 
Image sequence----> finding the incremental changes between each two images in sequence ----> forecasting the next image
Also based on flooding area and after detecting the potential flooding areas, forecasting the damage of flooding to different areas. 

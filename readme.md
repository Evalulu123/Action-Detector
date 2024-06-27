## Action Detector
My projet is a classification model that can classify different actions.

![texting](https://github.com/Evalulu123/Action-Detector/assets/173275376/d8502129-69df-4830-a761-a6f75abdd653)


## ResNet-18
 I downloaded the Jetson Inference Library, and used ResNet-18. ResNet-18 is a convolutional neural network (CNN) architecture that belongs to the family of Residual Networks (ResNets) that is 18 layers and designed for image classification tasks.
 
 ![image](https://github.com/Evalulu123/Action-Detector/assets/173275376/722706cb-8665-4f15-a305-f2b2906a40dd)
 
## The Algorithm
  For my project I decided to train an Aftifical Intellegence to classify different actions. Classification AI categorizes different images into predefined classes or categories based on data that it given to it. I decided on 3 different actions; texting, pouring water, and fixing your hair. I took images of me completeing each of these actions and imput them into my Jetson Nano. I then trained the model to classify each image into its correct class. 
  Training a model involves feeding the correctly labeled data into the chosen algorithm. The algorithm learns from the data to create a model that, in my case, correctly clissifies different images of diffeerent actions into their respective classes. This process involves adjusting the model to minimize the errors. 
    After the AI is trained, we test it. The model's performance is evaluated using a separate set of data called the validation (val) or test set. Once trained and evaluated, the model can be used to make predictions on images it's never seen before. The input features are fed into the model, which then outputs the predicted class based on what it's already learned. To run my re-trained ResNet-18 model for testing I needed to convert it into ONNX format. ONNX is an open model format that supports many popular machine learning frameworks, and it simplifies the process of sharing models between tools. 
    In conclution, the algorithm teaches computers to sort things into the correct classes by showing them lots of examples. It learns from these examples and then makes predictions about new things based on what it learned. In my project, the AI classified different actions.
  For example, we originally retrained a model that classified cats and dogs. 
    First we would show the robot many cats and dogs, telling it which is which.
    Then, we let the robot learn from these examples, by training in.
    Finally, we test the robot with new pictures of cats and dogs it hasn't seen to see if it can correctly identify and classify them.
    
## Running this project

Steps:
1. Make sure you have a Jetson Nano (from NVIDIA) and log into pyhton with your Jetson Interface Nano
     1a) you have to use an app called PuTTY to connect to your Jetson Nano, once your nano is connected to your device you can connect it to the wifi through your devices hotspot. You can check the connection by tyoing 'nmcli device'.
     1b) when it is connected you can use the command 'config wlan0' to check you IP address
2. Next you can connect to Visual Studio Code using your IP address.To begin, open a new terminal in Visual Studio, this is where we will code.
3. When everything is set up, make sure you have installed Jetson Inference and Docker Image from : http://github.com/dusty-nv/jetson-interface/blob/master/docs/building-repo-2.
4. Change directories into 'jetson-inference/python/training/classification/data' and then run this command to download the dataset.  
'wget https://nvidia.box.com/shared/static/o577zd8yp3lmxf5zhm38svrbrv45am3y.gz -O v-actions.tar.gz'
    4a) Next run this command to unzip the file you downloaded "tar xvzf v-actions.tar.gz'
5. Then, cd back to nvidia/jetson-inference/ and run this in your terminal when you're in your jetson-inference directory to ensure your system overcommits memory which allows it to have more memory for the task: 'echo 1 | sudo tee /proc/sys/vm/overcommit_memory'.
6. Once that has run and you're still back in the jetson-inference folder, run './docker/run.sh' to run the docker container. Then inside the Docker container, change directories so you are in jetson-inference/python/training/classification.
7. Run the training script to re-train the network where the model-dir argument is where the model should be saved and where the data is. Run: 'python3 train.py --model-dir=models/v-actions data/v-actions', you can also add '--batch-size=NumberOfBatchFiles --workers=NumberOfWorkers --epochs=NumberOfEpochs' to alter the epochs and batch size.
8. Next, we will export the network. Make sure you are in the docker container and in 'jetson-inference/python/training/classification' and run the onnx export script: 'python3 onnx_export.py --model-dir=models/v-actions'
    8a) Now look in the 'jetson-inference/python/training/classification/models/v-actions' folder to see if there is a new model called 'resnet18.onnx' there. That is your re-trained model!
   
    ![image](https://github.com/Evalulu123/Action-Detector/assets/173275376/ffad5760-0c9c-4f27-aabf-b760f723e2da)
10. To process the image, exit the docker container by pressing 'Ctl + D' and navigate to the 'jetson-inference/python/training/classification' directory.
    9a) Use ls models/v-actions/ to make sure that the model is on the nano. You should see a file called 'resnet18.onnx'.
    9b) Next, set the NET and DATASET variables: 'NET=models/v-actions' and 'DATASET=data/v-actions'
11. Now we can test our AI! Run this command to see how it operates on an image from the fixinghair folder: imagenet.py --model=$NET/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/labels.txt $DATASET/test/fixinghair/fix_hair_1.jpg fixinghair.jpg

## Video 
Here is a video explanation:


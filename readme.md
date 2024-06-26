## Action Detector
My projet is a classification model that can classify different actions.

![add image descrition here](direct image link here)

## The Algorithm
  For my project I decided to train an Aftifical Intellegence to classify different actions. Classification AI categorizes different images into predefined classes or categories based on data that it given to it. I decided on 3 different actions; texting, pouring water, and fixing your hair. I took images of me completeing each of these actions and imput them into my Jetson Nano. I then trained the model to classify each image into its correct class. 
  Training a model involves feeding the correctly labeled data into the chosen algorithm. The algorithm learns from the data to create a model that, in my case, correctly clissifies different images of diffeerent actions into their respective classes. This process involves adjusting the model to minimize the errors. 
    After the AI is trained, we test it. The model's performance is evaluated using a separate set of data called the validation (val) or test set. Once trained and evaluated, the model can be used to make predictions on images it's never seen before. The input features are fed into the model, which then outputs the predicted class based on what it's already learned. 
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
4. When everything is set up, make sure you have installed Jetson Inference and Docker Image from : http://github.com/dusty-nv/jetson-interface/blob/master/docs/building-repo-2.



[View a video explanation here](video link)

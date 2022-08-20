# iOS App template for CSML App Studio

**iOS Versions Supported:** iOS 12.0 and above.
**Xcode Version Required:** 10.0 and above

## Overview

This is a iOS App template for [CSML App Studio](https://sites.google.com/ucsc.edu/csmlappstudio/detection). This app is an original work that used resources from the following github repositiories,

- https://github.com/tensorflow/examples/tree/master/lite/examples/object_detection/ios

- https://github.com/imaginary-cloud/CameraManager




The app detects the objects (bounding boxes and classes) in the frames seen by your device's back camera, using a quantized [MobileNet SSD](https://github.com/tensorflow/models/tree/master/research/object_detection) model trained on your custom dataset using the CSML App Studio. These instructions walk you through building and running the app on an iOS device.

## Prerequisites

* You must have Xcode installed on a Apple Mac computer.

* You should have a valid Apple Developer ID to distribute the app.

* The demo app requires a camera and must be executed on a real iOS device. You can build it and run with the iPhone Simulator but the app raises a camera not found exception.

* You don't need to build the entire TensorFlow library to run the demo, it uses CocoaPods to download the TensorFlow Lite library.

* You'll also need the Xcode command-line tools:
 ```xcode-select --install```
 If this is a new install, you will need to run the Xcode application once to agree to the license before continuing.

## Building the iOS App

1. Start by downloading/cloning this github repo to your local Mac machine. Install CocoaPods if you don't have it.
```sudo gem install cocoapods```
If this command fails to install the cocoapods (which you may understand in the next step), they to isntall it using home brew.
```brew install cocoapods```

Optional: you can rename the ```CitizenScienceApp1.xcodeproj``` inside the ```csapptemplate1``` directory and the new name will reflect in the next steps.

2. Install the pod to generate the workspace file by running the following command from inside the ```csapptemplate1``` directory:
```arch -x86_64 pod install``` (if m1/m2 based Mac) or ```pod install``` (if Intel based Mac)
  If you have installed this pod before and that command doesn't work, try
```arch -x86_64 pod update``` (if m1/m2 based Mac) or ```pod update``` (if Intel based Mac)
At the end of this step you should have a file called ```CitizenScienceApp1.xcworkspace```

3. Open **CitizenScienceApp1.xcworkspace** in Xcode. (Warning: Do not open the **CitizenScienceApp1.xcodeproj**. It will fail if you try to build!)

4. Please change the Bundle Identifier to a unique identifier and select your development team in **'General->Signing'** before building the application if you are using an iOS device. Also, change the Display Name to the name you want to see with your app icon.

![alt text](general.png?raw=true)
![alt text](signing.png?raw=true)

5. This app includes a default a MobileNet SSD model trained on [COCO dataset](http://cocodataset.org/). The input image size required is 300 X 300 X 3. You can download the model [here](https://storage.googleapis.com/download.tensorflow.org/models/tflite/coco_ssd_mobilenet_v1_1.0_quant_2018_06_29.zip). You can find more information on the research on object detection [here](https://github.com/tensorflow/models/tree/master/research/object_detection). You need to replace the detect.tflite and labelmap.txt with your custom trained detect.tflite and labelmap.txt.

6. Build and run the app in Xcode. You'll have to grant permissions for the app to use the device's camera. Point the camera at various objects and enjoy seeing how the model detects the objects of interest for your project.

## Customizing GUI (Optional)

7. For adding custom icon and logo for the app, you need to replace the files in the ```csapptemplate1 >> ObjectDetection >>  Assets.xcassets``` folder. A python script (create_icon_logo.py) is provided for that. Put your icon and logo images (.bmp, .jpg, or .png) in the Assets.xcassets and run the puthon script as follows,

```python create_icon_logo.py <name of your icon file> <name of your logo file>```

The python script will autometically replace the icons and logos with your images.

8. If you want to change the text, color, etc., of various buttons in the app, you can do that in the "Main" in Xcode, as shown below.

![alt text](gui_color.png?raw=true)

9. You may provide some short information in the slideable info panel in the camera view with ML detection within the app (as shown in the image below). This information file can be provided by replacing/updating the "info.html" in the ```csapptemplate1 >> ObjectDetection >>  ViewControllers >> files``` folder.

**Tip:** Html files can be edited without writing code using simple and free online tools like https://onlinehtmleditor.dev/

![alt text](info_panel.png?raw=true)

10. You may provide an offline help file in the app connected to the HELP button in the main menu. This help file can be provided by replacing/updating the "help.html" in the ```csapptemplate1 >> ObjectDetection >>  ViewControllers >> files``` folder. 

11. If you want to connect the app to your website with more detailed help, the link can be provided in "line 4" of the "data.txt" file in the ```csapptemplate1 >> ObjectDetection >>  ViewControllers >> files``` folder.

12. If you want to connect the app to a website where users can upload images/videos captured by the app, the link can be provided in "line 2" of the "data.txt" file in the ```csapptemplate1 >> ObjectDetection >>  ViewControllers >> files``` folder. This link will be connected to the UPLOAD button in the main menu.

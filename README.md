# Senior Project: Real-time Edge-powered Facial Recognition and Object Detection
Senior Project using TensorFlow Lite on a Coral Dev Board to leverage edge-analytics for facial recognition and object detection. 

## Project Information
Below is a quick outline of relevant information for the project.

#### About Me
* Name: Tom Hood
* Majors: Applied Mathematics & Computer Science
    * Minors: Data Analytics
* Semester: Spring 2020

#### Goals of Project
This project sets out with the goal to develop scripts using Python and TensorFlow on a portable Coral Dev Board. Specifically, these scripts will be used for real-time human pose and face recognition. The Coral Dev Board will be using an attached camera to stream in video data and use real-time analytics to estimate and gauge poses and faces. Because this device is both sensing/collecting and analyzing data it is considered an edge analytics device. 

#### Other Documents 
Below is a list of other documents that are to be included in the final project/
* Summaries & Critiques
   * You can find the *Summaries & Critiques* [here](https://github.com/thood21/SeniorProject/tree/master/Summaries%26Critiques)
* Annotated Bibliography
   * You can find the *Annotated Bibliography* [here](https://github.com/thood21/SeniorProject/tree/master/AnnotatedBibliography)
* Glossary
   * This is a collection of definitions and explanations for commonly used jargon and libraries in this project.
   * You can find the *Glossary* [here](https://github.com/thood21/SeniorProject/tree/master/Glossary)
* Getting Familiar with the Coral Dev Board
   * This is useful for those who have never worked with the Coral Dev Board before. This includes a guide for setting up and running a demo.
   * You can find the *documentation* [here](https://github.com/thood21/SeniorProject/tree/master/GettingFamiliarWithCoral)
   
## My Project
The below sections are pertinent to my own senior project, which is using the Coral Dev Board and TensorFlow lite to run software to detect human pose and faces

#### Warm-Up: Image Processing
Before I began working on the code for facial recognition, I wanted to begin with a more basic form of image processing and recognition. I found a guide to help me build a model for classifying birds using the Coral Dev Board and TensorFlow lite Python API. My process is outlined below:

1. Download the example code from GitHub:
   - Open the terminal and enter in `sudo apt-get install git` to install git.
   - Next, create and enter a new directory with `mkdir coral && cd coral`. I chose the name "coral," but you are welcome to use your own.
   - Clone the git repository containing example code and needed documentation with `git clone https://github.com/google-coral/tflite.git`
2. Download the bird classifier model, labels file, and a bird photo:
    - Move into the newly downloaded repository on your machine with `cd tflite/python/examples/classification`
    - Install all requirements with `bash install_requirements.sh`
3. Start developing
   - From here you are ready to start developing.
   - Using the API, I developed a model that could classify various birds.
4. My bird model
   - The code for my model is contained in `classify_bird.py`
      - You can view the code [here](https://github.com/thood21/SeniorProject/blob/master/Code/BirdClassification/classify_bird.py)
   - I began with an input image of a parrot, specifically a Scarlet Macaw.
   ![](etc/parrot.png)
   - I then called my script to begin classifying the image. The script takes in 3 arguments: `model`, `labels`, and `input`.
   ![](etc/script_call.png)
   - The results from the classification were a successful. The model correctly identified the bird with over 75% accuracy!
   ![](etc/model_results.png)

#### Facial Recognition
Facial recognition is an increasingly popular use case for machine learning. Many sophisticated security systems use facial detection software to identity humans who may be committing a crime or other offense. New advancements in artificial intelligence are trying to incorporate facial recognition into their robots to increase their capabilities for communicating with humans. Facial recognition lays the foundations for more advanced actions such as emotion detection, eye-contact, and facing active speakers. I developed code that is able to accurately indentify human faces, even amidst noisy backgrouds. The process is outlined below:

1. Set session variables
   - Open the terminal and create a variable with `export DEMO_FILES="$HOME/demo_files"`
2. Download models to be used for training and testing
   - You are welcome to find your own models. This is strongly advised, as different models have different strengths and weaknesses.
   - There are default models that can be used by running the following:
      - `wget -P ${DEMO_FILES}/ https://github.com/google-coral/edgetpu/raw/master/test_data/mobilenet_v2_1.0_224_quant_edgetpu.tflite`
      - `wget -P ${DEMO_FILES}/ https://github.com/google-coral/edgetpu/raw/master/test_data/imagenet_labels.txt`
      - `wget -P ${DEMO_FILES}/ https://github.com/google-coral/edgetpu/raw/master/test_data/mobilenet_ssd_v2_face_quant_postprocess_edgetpu.tflite`
3. Gather peripherals
   - I used a monitor with an HDMI input, USB hub, USB camera, mouse, and keyboard
   ![](etc/camsetup.jpeg)
4. Fetch camera specs
   - In the terminal enter `v4l2-ctl --list-formats-ext --device /dev/video1` to fetch the specs for your camera.
      - This should return a page similar to below (exact results vary by webcam used):
   ![](etc/cam_specs.png)
   - Take note of the Pixel Format, Size, and FPS values. Depending on the model you develop, you may need to pass those into the model arguments.
5. Classifying
   - I called the script and passed in arguments
   ![](etc/facial_script_call.png)
6. Results
    - The results were great. My software was able to detect my face amidst a very noisy background in rather poor lighting. Images of the results are shown below:
    ![](etc/facial1.jpeg)
    ![](etc/facial2.jpeg)
    ![](etc/facial3.jpeg)
    ![](etc/facial4.jpeg)
7. Conclusions
   - I noticed that the classifier did better in more "optimal" conditions, which includes factors such as proper lighting, minimal image noise, and high contrast background/foreground.
   - Another factor that increased classifier accuracy was distance and orientation towards the camera. Being closer to the camera yielded better results, and tilting your face in different angles or having it too high above or below the camera's plane would decrease accuracy.
   - The code for this project is available [here](https://github.com/thood21/SeniorProject/blob/master/Code/FacialRecognition.py)

#### Object Classifier
Creating accurate machine learning models capable of localizing and identifying multiple objects in a single image remains a core challenge in computer vision. The TensorFlow Object Detection API is an open source framework built on top of TensorFlow that makes it easy to construct, train and deploy object detection models. This library was constructed by and is currently maintained by Google. 

   1. This software uses several pre-existing modules such as `TensorFlow` and `NumPy` as well as special libraries for object
   detection such as `object_detection.utils`
      - TensorFlow Object Detection API depends on the following libraries:
         - `Protobuf 3.0.0`
         - `Python-tk`
         - `Pillow 1.0`
         - `lxml`
         - `tf Slim`
         - `Matplotlib`
         - `Cython`
         - `contextlib2`
         - `cocoapi `
      - For detailed steps to install Tensorflow, follow the [Tensorflow installation instructions](https://www.tensorflow.org/install/).; however a typical user can install Tensorflow using one of the following commands:
         - For CPU:
            - pip install tensorflow
         - For GPU:
            - pip install tensorflow-gpu
   2. Now you will need to create your own model for classification. When creating a model there are a plethora of things to consider, so I would recommend reading documentation on [defining your own model architecture](https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/defining_your_own_model.md).
      - My code for the classifier can be found [here](https://github.com/thood21/SeniorProject/blob/master/Code/ObjectClassifier.py).
      
#### Video Demonstrations
For demonstration purposes, I have incuded pre-recorded videos of me using software. There are demos for both the facial recognition software as well as the object classifier. The Coral Dev Board does not have any sort of screen recording software, so all captures are done externally with my cell phone. Videos can be watched [here](https://github.com/thood21/SeniorProject/tree/master/VideoDemos).

# Video Demonstrations
Below I have incuded video demonstrations of the software in action. There are demos for both the facial recognition software as well as the object classifier. The Coral Dev Board **does not** have any sort of screen recording software, so all captures are done externally with my cell phone.

## Facial Recognition
This is a quick video demonstration of the facial recognition software. As you can see, the software detects faces well and the model updates its accuracy in real-time. This is seen with how the accuracy increases/decreases as I move around. 

   ![](../etc/videos/facial_classifier_demo.mov)
   - The model has an inference time of `~10-12 milliseconds`
   - Notice how the model returns lower accuracy results from frames with high movement or noisy backgrounds.
   - The box around my face (ie the facial detection) moves with me as I move my head around.
   - Performance:
      - Up close, head on level plane with camera, neutral face, high contrast: `91-98%`
      - Up close, head on level plane with camera, long face, head tilted up, high contrast: `50-69%`
      - Up close, head on level plane with camera, neutral face, high contrast, waving: `69-83%`
      - Up close, head on level plane with camera, long face, high contrast, thumbs-up: `50-83%`
        
## Object Classifier
The below videos are a few short demonstrations of the object classifier. This software also takes in a live video stream and the model attempts to classify the object(s) in the frames based on the training dataset it was provided. For these examples, I fed the model a "generalist" dataset that includes a wide variety of object, however nothing very specific. This means that while I might show a "yellow pencil" to the camera, the model will simply classify it as "pen," etc. The model will return the classifcations with the highest accuracy and inference time (the delay it takes to actually process the stream). I ran the demos under one of two conditions: 1) clean background 2) noisy background. Clean background demos are shown with a solid purple sheet at the background for the object, while noisy background were shown with no background given (background was simply whatever was behind the object in the room).

#### Tennis Shoe Classification
   ![](../etc/videos/shoe_classifier_demo.mov)
   - The model has an inference time of `~6.8 milliseconds`
   - The model struggles to correctly classify my shoe. The closest result is `Sandal` with an acuracy of up to `0.70%`
   - Top results:
      - `Sombrerro   (5.1%)`
      - `Sandal   (0.71%)`
      - `Television, Television System   (0.39%)`
      - `Cowboy Hat, 10-gallon Hat   (0.37%)`
      - `Cup   (0.33%)`
      - `Screen, CRT Screen   (0.30%)`
      - `Corn   (0.26%)`
      - `Ear, Spike, Capitulum   (0.13%)`
      
#### Computer Mouse Classification
   ![](../etc/videos/mouse_classifier_demo.mov)
   - The model has an inference time of `~10 milliseconds`
   - The model *is* able to correctly classify the computer mouse rather well. It reports `Mouse, Computer Mouse` with an accuracy of up to `9.8%`.
   - Top results:
      - `Mouse, Computer Mouse   (9.8%)`
      - `Pool Table, Billiard Table, Snooker Table   (0.60%)`
      - `Switch, Electric Switch, Electrical Switch  (0.37%)`
#### Red Pen Classification
   ![](../etc/videos/pen_classifier_demo.mov)
   - The model has an inference time of ~15-20 milliseconds
   - The model struggles to correctly classify the red pen. The closest it gets is a classification of `Rubber Eraser, Rubber, Pencil Eraser` with an accuracy of `0.84%`
   - Top results:
      - `Paintbrush   (4.82%)`
      - `Syringe   (4.17%)`
      - `Rubber Eraser, Rubber, Pencil Eraser   (0.84%)`
      - `Eft   (0.75%)`
      
#### Self & Noisy Background Classification
   ![](../etc/videos/self_classifier_demo.mov)
   - The model has an inference time of `~12-18 milliseconds`
   - The model struggles to correctly classify anything. Because there are so many objects captured in the video stream, the classifier jumps all over the place. 
   - Top results:
      - `Laptop, Laptop Computer   (2.18%)`
      - `Television, Television System   (2.14%)`
      - `Studio Couch, Day Bed   (1.49%)`
      - `Banjo   (1.29%)`
      

# Senior Project: Coral Dev Board Real-time Edge Analytics of Human Pose and Emotion
Senior Project using TensorFlow Lite on a Coral Dev Board to leverage edge analytics on human pose and emotion recognition and detection.

## Information
All pre-requisites and prior information needed will be detailed in the below sections.

### About Me
* Name: Tom Hood
* Majors: Applied Mathematics & Computer Science
    * Minors: Data Analytics
* Semester: Spring 2020

### Goals of Project
This project sets out with the goal to develop scripts using Python and TensorFlow on a portable Coral Dev Board. Specifically, these scripts will be used for real-time human pose and emotion recognition. The Coral Dev Board will be using an attached camera to stream in video data and use real-time analytics to estimate and gauge poses and emotion. Because this device is both sensing/collecting and analyzing data it is considered an edge analytics device. 

### Annotated Bibliography
Before beginning this project, I sought out sources that did similar projects, used similar methodologies, or used similar hardware. The purpose of this is to aggregate information from disparate sources to synthesize a blend of information into a single source to serve as a guide for future users.

1. _Aloufi, Ranya, Hamed Haddadi and David Boyle. "Emotion Filtering at the Edge." Association for Computing Machinery (2019): 1-6. Digital Article._
    * This article outlines the implementation and evaluation of emotion filtering using a Raspberry Pi 4. Because the Raspberry Pi is used as a sensor to collect data and also analyze it, it is an edge analytics device. Edge analytics has gained immense popularity recently, fueling a wave of real-time analytics as devices are able to now sensor/poll external stimuli and immediately analyze it and output results or reactions. Filtering human emotions at the edge involves devices that are able to detect changes on hosts and analyze minute changes and chain these changes together into an ultimately change in emotion. Small actions such as wrinkles around the mouth, angling of eye brows, open eye width, voice pitch, decible levels, and hesitation are a few of the many changes used to diagnose emotion. In the pursuit of creating AI, human emotion detection is a necessity, making this research an important cornerstone. Finally, this article shows that performance accuracy is not hindered by edge analytics when compared to more powerful cloud-based approaches. Traditional systems stream data back from sensors and analyze data in the cloud, which is less efficient and sometimes slower. In essence, this article demonstrates the capabilities and accuracy of edge analytics, while also pressing forward by making advances for human emotion detection. 
    
2. _Antonini, Mattia, et al. "Resource Characterisation of Personal-Scale Sensing Models on Edge Accelerators." Association for Computing Machinery (2019): 49-55. Digital Article._
    * Edge acceleration is a new class of cutting edge purpose-built or job-specific System on a Chip (SoC) for running deep learning models efficientl on edge devices. The accelerators offer a plethora of benefits such as ultra-low latency, sensitive data protection via cryptography, and extreme data availability via locality. Edge accelerators are creating opportunities for builing real-time sensory systems in the real world, and leading scientists to rethink traditional and existing solutions for IoT, wearables, and other sensory devices. This article examines the performance of a set of edge accelerators in running scaled sensory deep learning models, benchmarking a total of 8 unique models with varying architectures and tasks (motion, audio, vision) across seven platform configurations with three distinct accelerators including the Google Coral (our device), Nvidia Jetson Nano, and Intel Neural Compute Stick. The article then reports on the execution performance concerning metrics such as latency, memory usage, and power consumption while discussing the workflows and respective limitations.
    
3. _Coral. "Dev Board Datasheet." January 2020. Coral AI Docs. System Report. January 2020._
    * The datasheet outlines component specifications, capabilities, and potential use cases. The Coral Dev Board is a single-board computer that's ideal for performing fast machine learning (ML) inferencing in a small form factor. Like other boards, it's widely used for edge analytics and real-time data crunching, and can be used to prototype various embedded system and then scale to production using the on-board Coral System-on-Module (SoM) combined with any number of custom PCB hardware. The module itself provides a fully-integrated system including: an iMX 8M chip, eMMC memorym LPDDR4 RAM, Bluetooth, and Wi-Fi. However, the biggest draw to this system is the specialized Google "Edge TPU coprocessor," a small ASIC engineered by Google for extreme performance ML inferencing with power power consumption (energy efficient). The SoM provides a fully-integrated system, including NXP's iMX 8M system-on-chip (SoC), eMMC memory, LPDDR4 RAM, Wi-Fi, and Bluetooth, but its unique power comes from Google's Edge TPU coprocessor. The Edge TPU is a small ASIC designed by Google that provides high performance ML inferencing with a low power cost. On the board itself there is a healthy endowment of I/O such as: USB 2.0/3.0 ports, DSI display interface, CSI-2 camera interface, Ethernet port, speaker terminals, and a 40-pin I/O header. The key benefits of this device are as follows: complete Linux system (Mendel, derivative of Debian), prototyping capabilities, and high-speed and energy efficient ML inferencing.
    
4. _Ding, Changxing and Dacheng Tao. "A Comprehensive Survey on Pose-Invariant Face Recognition." Association for Computing Machinery (2016): Article 37. Digital Article._
    * This article studies facial recognition with unchanging (invariant) poses; this translates to analyzing still images of human faces. This type of human facial recognition is useful in certain applications such as facial biometrics recognition, but useless in others such as real-time facial recognition. Pose invariant facial recognition (PIFR) is typically grouped into four distinct categories: pose-robust feature extraction approaches, multiview subspace learning approaches, face synthesis approaches, and hybrid approaches. This article discusses the motivations, strategies, pros/cons, and performance of representative approaches and details directions for future research. Ultimately, the capacity to recognize faces under varied poses is a fundamental human ability that presents a unique challenge for computer vision systems, which spurred this group of researches to delve into a separate area of study - PIFR. 

5. _Kejariwal, Arun, Sanjeev Kulkarni and Karthik Ramasamy. "Real Time Analytics: Algorithms and Systems." Association for Computing Machinery (2015): 2040–2041. Digital Article._
    *  This article outlines example use cases of streaming analytics and notes how it powers a lot of the everyday functions we do/use. Business metrics, healthcare reports, e-commerce tracking, telecommunications, government services, and more all utilize streaming analytics. This article also presents a various applications, algorithms, and platforms for streaming analytics, as well as the evolution of the field and current challenges. Common challenges include turnover time between capture data and presenting it in analytics, efficiently handling and streaming massive amounts of data ("Big Data"), maintaining data quality standards, and making use of data you collect (otherwise, why waste resources storing useless data). In essence, the article examines the implications and effects of the "3 V's" of daya analytics - Velocity/Veracity, Volume, and Variety.

6. _Shotton, Jamie, et al. "Real-Time Human Pose Recognition in Parts from Single Depth Images." Association for Computing Machinery (2013): 116-124. Digital Article._
    * This article outlines research methods used to report real-time human pose recognition via prediction from 3D positioning of body parts and joints obtained from single depth images. While this methodology discussed is strongly remeniscent of current object recognition strategies, it does differentiate itself by utilizing an algorithm that does not depend on information from preceding image frame data. The proposed methodology breaks down images into recognizable body parts and then further into pixels, enabling per-pixel machine learning techniques to efficiently analyze data. The algorithm is able to estimate body part labels invariant to pose, body shape, clothing, and other irrelevancies. The proposed system runs in uner 5ms on the Xbox 360 (system configuration used for specific benchmarking purposes). 
    
## Process
Below I will outline steps and tutorials for set up, running a demo, and then my own process for real-time edge analytics for human pose recognition and emotion detection.

### Set up
Before beginning, there is some mandatory set up. While the Coral online documentation recommends using MacOS or Linux for this process, I configured this to work for Windows 10 machines, since that is the OS most students will use. Please ensure you have the following:
1. Computer running Windows 10 - *laptop would be ideal*
2. The Coral Dev Board kit - *if you are getting this from Dr. Anwar, it should be just the board with nothing else additional*
3. x1 USB-C power delivery cable w/ 5w power brick - *an Android USB-C charger will probably work, this is used to power the Coral Dev Board, be careful not to use a power source that delivers more than 5w as you can damage the board*
4. x1 USB-C data delivery cable - *yes, you need two distinct USB-C cables, another Android USB-C charger will probably work, this is used to flash Linux onto the Coral Dev Board*
5. x1 Micro-B cable - *an old Android charger will work, this is for serial communication between your laptop and the Coral Dev Board*
6. Download and install [these drivers](https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers), which are required to enable your computer's USB port to function as a Virtual COM Port to facilitate host communication between your computer and the Dev Board
[](etc/uart_drivers.png)
7. Download and unzip [this folder](https://developer.android.com/studio/releases/platform-tools.html#download), place it somewhere convenient for you, and then store that file path location in your Environment and/or System PATH variable(s). For example, I unzipped the folder and placed it in my Program Files folder, so I added the following to my System Variables PATH: `C:\Program Files\platform-tools_r29.0.5-windows\platform-tools`
9. A serial console application or utility - *I use PuTTY, which is free to download*
10. (OPTIONAL) a micro-sd card - *this would enable a larger storage capacity for the dev board which might be important depending on what your use case is (ie: analyzing large datasets of images, installing large libraries and modules, etc.)*

#### Recap & Troubleshooting
When it's all said and done, you should have downloaded the USB-to-UART drivers, FastBoot drivers, and have an equipment setup [similar to this](https://github.com/thood21/SeniorProject/blob/master/etc/equipment.PNG "Required Equipment") *minus the Raspberry Pi*.
Additionally, please find helpful links, sources, and documentation that I used along my process below:
1. Coral Dev Board [official documentation](https://coral.ai/docs/dev-board/get-started/)
2. Online blog for [connecting a Coral Dev Board to a Windows 10 machine](https://blog.questionable.services/article/coral-edge-tpu-windows/) - If you are confident in your own ability to troubleshoot and want to go at your own pace, this guide is all you need really, and you can ignore the rest of my guide. In essence, I am rehashing this guide and adding in a few steps that worked in my case.
3. Troubleshooting post from StackOverflow - [FastBoot errors](https://stackoverflow.com/questions/57776655/fastboot-devices-not-listing-coral-dev-board)

### Running a demo
Next, we will quickly run a demo that showcases what the Coral Dev Board is capable of. Before running, we will want to install a few more packages and ensure we are connected to the internet (while these are not needed to run the demo, these will be needed later on down the line).
1. At this point you are now able to use the Coral Dev Board like a portable computer, so use an HDMI to connect to an external monitor, and find a USB hub as well to connect a mouse, keyboard, and other USB devices (flashdrives, webcams, etc.). Once all accessories are connected, plug in your power cable and you should see a boot screen, followed by a blue-ish ocean desktop background. Only the terminal is able to be opened, which is located in the top-left corner.
2. Open a terminal and run the command `nmtui` to bring up the connection manager interface. Use the keyboard to navigate through, and add a connection. You can use either ethernet or Wi-Fi, but note that because this device lacks a browser, you will not be able to use networks that require a sign-in to access the internet.
3. To ensure you have established a connection, run `nmcli connection show`, which should show the Name, UUID, and Device for your active connections. Wi-Fi will display `wlan0` under Device, while ethernet should show `eth0`.
4. Update the software by running `sudo apt-get update`, and after this finishes, run `sudo apt-get dist-upgrade`
5. Now we want to install [TensorFlow lite for Python](https://www.tensorflow.org/lite/guide/python). I encountered some issues here, however it could have been from typos as there is no efficient way to copy/paste URLs to/from the Coral Dev Board. First, ensure you have Python3 install by running `python3 -V`. This is going to print out the version number of your Python3 distribution; it is crucial that you use the correct version number when downloading the TensorFlow Lite package. My version number is 3.5.3, so I will be running the command for 3.5.xxx. If you are encountering errors, ensure you are typing the command in correctly. If this does not work, try going [here](https://github.com/tensorflow/tensorflow/issues/9722) and reading through similar issues - notably, try this command: `python3 -c "import wheel.pep425tags as w; print(w.get_supported())" | sed -zE 's/\),/),\n/g'`, which should print out your supported .whl types. 
6. One last thing we want to change is the fan control. If your experience is similar to mine, the fan is not spinning, causing the heatsink to get very hot, ultimately leading to thermal throttling. To remedy this, we will be editting a variable hidden deep within /sys. Begin by entering `sudo nano ~/.bashrc`, which opens your bashrc file, which we can use to load variables into the shell environment each time it is launched - this is crucial because instead of using `cd my/really/long/path/to/file/here`, we can just reference a variable to pull it up instantly. Right under #for examples in the the bashrc, make a few new lines and enter in `export fan="/sys/class/thermal/thermal_zone0/trip_point_4_temp"` then press ctrl+O, enter, ctrl+X, then in your terminal enter command: `source ~/.bashrc` which refreshes your bashrc file. To ensure this worked, enter `echo $fan`, which should print out that path we just stored in the bashrc. Now enter command: `sudo nano $fan`, which pulls up a file with a number in it - mine shows 65000. Change this to a much smaller number - I always do 5000, then ctrl+O, enter, ctrl+X. Your fan should kick on. This fix is not persistent after reboots, meaning when your machine turns off this change is lost, so you will want to rerun the `sudo nano $fan` command and change the number each time after reboot. 
7. Now we can run our demo. Assumming you are connected to a monitor, from your terminal run command: `edgetpu_demo --device`. It is possible to stream the demo over SSH, however I did not do that so I won't be giving instruction on how to do that (instructions are shown on the Coral Dev Board Online documentation). A video should now display on your screen showing cars driving on a highway. This is demonstrating a model that is attempting to identify cars, with a given percentage showing the "confidence" in classifying the object as a car.

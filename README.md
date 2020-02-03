# SeniorProject
Senior Project using coral dev board and TensorFlow

## About Me
* Name: Tom Hood
* Majors: Applied Mathematics & Computer Science
* Minors: Data Analytics
* Semester: Spring 2020

### Set up
Before beginning, there is some mandatory set up. While the Coral online documentation recommends using MacOS or Linux for this process, I configured this to work for Windows 10 machines, since that is the OS most students will use. Please ensure you have the following:
1. Computer running Windows 10 - *laptop would be ideal*
2. The Coral Dev Board kit - *if you are getting this from Dr. Anwar, it should be just the board with nothing else additional*
3. x1 USB-C power delivery cable w/ 5w power brick - *an Android USB-C charger will probably work, this is used to power the Coral Dev Board, be careful not to use a power source that delivers more than 5w as you can damage the board*
4. x1 USB-C data delivery cable - *yes, you need two distinct USB-C cables, another Android USB-C charger will probably work, this is used to flash Linux onto the Coral Dev Board*
5. x1 Micro-B cable - *an old Android charger will work, this is for serial communication between your laptop and the Coral Dev Board*
6. Download and install [these drivers](https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers), which are required to enable your computer's USB port to function as a Virtual COM Port to facilitate host communication between your computer and the Dev Board
7. Download and unzip [this folder](https://developer.android.com/studio/releases/platform-tools.html#download), place it somewhere convenient for you, and then store that file path location in your Environment and/or System PATH variable(s). For example, I unzipped the folder and placed it in my Program Files folder, so I added the following to my System Variables PATH: `C:\Program Files\platform-tools_r29.0.5-windows\platform-tools`
9. A serial console application or utility - *I use PuTTY, which is free to download*
10. (OPTIONAL) a micro-sd card - *this would enable a larger storage capacity for the dev board which might be important depending on what your use case is (ie: analyzing large datasets of images, installing large libraries and modules, etc.)*

When it's all said and done, you should have downloaded the USB-to-UART drivers, FastBoot drivers, and have an equipment setup [similar to this](https://github.com/thood21/SeniorProject/blob/master/etc/equipment.PNG "Required Equipment").
Additionally, please find helpful links, sources, and documentation that I used along my process below:
1. Coral Dev Board [official documentation](https://coral.ai/docs/dev-board/get-started/)
2. Online blog for [connecting a Coral Dev Board to a Windows 10 machine](https://blog.questionable.services/article/coral-edge-tpu-windows/)
3. Troubleshooting post from StackOverflow - [FastBoot errors](https://stackoverflow.com/questions/57776655/fastboot-devices-not-listing-coral-dev-board)

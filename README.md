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

When it's all said and done, you should have downloaded the USB-to-UART drivers, FastBoot drivers, and have an equipment setup [similar to this](https://github.com/thood21/SeniorProject/blob/master/etc/equipment.PNG "Required Equipment") *minus the Raspberry Pi*.
Additionally, please find helpful links, sources, and documentation that I used along my process below:
1. Coral Dev Board [official documentation](https://coral.ai/docs/dev-board/get-started/)
2. Online blog for [connecting a Coral Dev Board to a Windows 10 machine](https://blog.questionable.services/article/coral-edge-tpu-windows/) - If you are confident in your own ability to troubleshoot and want to go at your own pace, this guide is all you need really, and you can ignore the rest of my guide. In essence, I am rehashing this guide and adding in a few steps that worked in my case.
3. Troubleshooting post from StackOverflow - [FastBoot errors](https://stackoverflow.com/questions/57776655/fastboot-devices-not-listing-coral-dev-board)

### Running a demo
Next, we will quickly run a demo that showcases what the Coral Dev Board is capable of. Before running, we will want to install a few more packages and ensure we are connected to the internet (while these are not needed to run the demo, these will be needed later on down the line).
1. At this point you are not able to use the Coral Dev Board like a portable computer, so use an HDMI to connect to an external monitory and a usb hub to connect a mouse and keyboard. Once all accessories are connected, plug in your power cable and you should see a boot screen, followed by a blue-ish ocean desktop background. Only the terminal is able to be opened, which is located in the top-left corner. 
2. Open a terminal and run the command `nmtui` to bring up the connection manager interface. Use the keyboard to navigate through, and add a connection. You can use either ethernet or Wi-Fi, but note that because this device lacks a browser, you will not be able to use networks that require a sign-in to access the internet.
3. To ensure you have established a connection, run `nmcli connection show`, which should show the Name, UUID, and Device for your active connections. Wi-Fi will display `wlan0` under Device, while ethernet should show `eth0`.
4. Update the software by running `sudo apt-get update`, and after this finishes, run `sudo apt-get dist-upgrade`
5. Now we want to install [TensorFlow lite for Python](https://www.tensorflow.org/lite/guide/python). I encountered some issues here, however it could have been from typos as there is no efficient way to copy/paste URLs to/from the Coral Dev Board. First, ensure you have Python3 install by running `python3 -V`. This is going to print out the version number of your Python3 distribution; it is crucial that you use the correct version number when downloading the TensorFlow Lite package. My version number is 3.5.3, so I will be running the command for 3.5.xxx. If you are encountering errors, ensure you are typing the command in correctly. If this does not work, try going [here](https://github.com/tensorflow/tensorflow/issues/9722) and reading through similar issues - notably, try this command: `python3 -c "import wheel.pep425tags as w; print(w.get_supported())" | sed -zE 's/\),/),\n/g'`, which should print out your supported .whl types. 
6. One last thing we want to change is the fan control. If your experience is similar to mine, the fan is not spinning, causing the heatsink to get very hot, ultimately leading to thermal throttling. To remedy this, we will be editting a variable hidden deep within /sys. Begin by entering `sudo nano ~/.bashrc`, which opens your bashrc file, which we can use to load variables into the shell environment each time it is launched - this is crucial because instead of using `cd my/really/long/path/to/file/here`, we can just reference a variable to pull it up instantly. Right under #for examples in the the bashrc, make a few new lines and enter in `export fan="/sys/class/thermal/thermal_zone0/trip_point_4_temp"` then press ctrl+O, enter, ctrl+X, then in your terminal enter command: `source ~/.bashrc` which refreshes your bashrc file. To ensure this worked, enter `echo $fan`, which should print out that path we just stored in the bashrc. Now enter command: `sudo nano $fan`, which pulls up a file with a number in it - mine shows 65000. Change this to a much smaller number - I always do 5000, then ctrl+O, enter, ctrl+X. Your fan should kick on. This fix is not persistent after reboots, meaning when your machine turns off this change is lost, so you will want to rerun the `sudo nano $fan` command and change the number each time after reboot. 

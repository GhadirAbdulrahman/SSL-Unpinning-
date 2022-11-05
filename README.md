# SSL-pinning
# What is the ssl pinning 
The process of SSL certificate pinning connects a host to a certificate or public key. It is regarded as a security procedure for protecting applications from man-in-the-middle attack . 
This article may assist the pen tester to bypass SSL Pinning ( Andriod emulator &amp; burpsuite with frida) 
# Requirements:
1- Install emulator your prefer, I installed the noxplayer.  *make sure the root mode is on. 

2- Install burp suite tool. 

3- Install python

# Windows cmd :
1- pip install frida

2- pip install frida-tools

3- pip install objection


 * please make sure script Frida is installed in the Environment Variables.

![WhatsApp Image 2022-11-05 at 4 57 58 PM](https://user-images.githubusercontent.com/49320536/200123494-154fed0b-01f4-44f6-b7bc-3bb169ea1751.jpeg)

for me it was :
 C:\Users\#\AppData\Local\Packages\PythonSoftwareFoundation.Python.3.10_qbz5n2kfra8p0\LocalCache\local-packages\Python310\Scripts

4- to check the frida is installed type:

 frida --version

![image](https://user-images.githubusercontent.com/49320536/200121276-5a4e0ae1-b11e-49b8-a76e-12af4b090211.png)

5- Then go to emulator directory, for me it was on C:\Program Files (x86)\nox\bin  

*this step to integrate frida server with nox emulator.

6- Turn on the NoxPlayer 

![image](https://user-images.githubusercontent.com/49320536/200121816-2e07efb2-9ff1-4b11-aec1-9b10044a390a.png)

7- To see which device connected , type this command :

adb devices 

![image](https://user-images.githubusercontent.com/49320536/200121871-651e4f9d-917d-4f7f-ae47-0725271d4c62.png)

8- You should be know of the Android device's version; by: .\nox_adb.exe shell getprop ro.product.cpu.abi

9-Download your version's compatible Frida server from: 
 https://github.com/frida/frida/releases


10-After that unzip the server ,and Upload frida-server to your emulator by this commands :

10.1.adb push frida-server-16.0.2-android-x86 /data/local/tmp

![image](https://user-images.githubusercontent.com/49320536/200122387-e7d3a5a9-043f-4164-b629-eaeb6fdcae02.png)


10.2.adb shell

11- Then change the permissions to make it executable

chmod +x frida-server-16.0.2-android-x86

12- finally turn on the server ./frida-server-16.0.2-android-x86 & 

and type the ps command to verify that the server is uploaded. 

![image](https://user-images.githubusercontent.com/49320536/200122476-dede591b-971f-433e-ba37-db519caa8ba7.png)

![image](https://user-images.githubusercontent.com/49320536/200122494-0717bbfe-c1f6-49a9-9ef6-0e766d6adaf8.png)


# Burpsuite Proxy with NoxPlayer

1-Open CMD and type ipconfig , and configure with burp  proxy > options > edit Proxy Listener > spicfic address  your ip:your port

![image](https://user-images.githubusercontent.com/49320536/200132887-831435b2-347b-4b56-b4be-355844815da6.png)

![image](https://user-images.githubusercontent.com/49320536/200133341-9ae03010-d7d3-4487-8b0f-3f201b3b7815.png)


2- modify your network in the emulator > advance options > change proxy to manual > add your ip & port  *make sure its same in the burpsuite.

![image](https://user-images.githubusercontent.com/49320536/200133135-94d8a853-8cd6-4537-b561-ee412037d27a.png)


3-donwload the burpsuite’s certificate and change the extention to .cer

![image](https://user-images.githubusercontent.com/49320536/200133126-b63a9f1f-b826-4578-8a63-460ad1ba8516.png)


# SSL pinning bypass 
In this section, I will try to bypass application .

1- download your app 

2- In cmd type frida-ps -Uai

Every applications on your Android device will be displayed

![image](https://user-images.githubusercontent.com/49320536/200125595-795375a2-eb52-4a9b-ae77-ddb3e0b3ef31.png)


3- Open new cmd then type this commands to start the bypass:

3.1- objection -g your application explore

![image](https://user-images.githubusercontent.com/49320536/200123652-9ae06d5c-b83f-47d3-ab1a-6a51070b0355.png)



3.2-android sslpinning disable. 

![WhatsApp Image 2022-11-05 at 4 57 19 PM](https://user-images.githubusercontent.com/49320536/200123523-6c3240ed-17ca-4865-b0d9-e7aee997ce4f.jpeg)


Thank you for reading!

I  hope this article was helpful



# References:

https://github.com/frida/frida/releases

https://github.com/frida/frida/issues/1000

https://frida.re/docs/installation/

https://www.youtube.com/watch?v=10f8lrChtzU





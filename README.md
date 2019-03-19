# LXRA-IoT
Walkthrough guide for connecting MXChip board to IoT Central

## TO DO
- [ ] Fix images
- [ ] Check image links
- [ ] @NexGenOne: Can you please review for flow/accuracy?

## Objectives
This guide will walkthrough connecting the Azure IoT Dev Kit to IoT Central. Throughout the session, you'll learn how to:
- Create and IoT Central application
- Add and configure a new device
- Load the credentials onto the Azure IoT Dev Kit

## Tools Required
- A Windows Live Account for access IoT Central
- Access to the internet over wifi
- A computer running Windows, Mac OSX,
- 1 x MXChip Development Board
- A text editor to temporarily copy your credentials
  - Notepad on Windows or TextEditor on Mac is perfect

## References
The instructions in this guide are taken from several sources:
- [Connect MXChip to IoT Central](https://docs.microsoft.com/en-us/azure/iot-central/howto-connect-devkit)
- [Microsoft IoTAA Lab Walkthrough](https://github.com/mjksinc/IoTAA-MSFT-Lab)

## Instructions

### Creating your IoT Central Application
The first step is to deploy a trial version of Azure IoT Central. These instructions below are an abridged version of our full [walkthrough online](https://docs.microsoft.com/en-au/azure/iot-central/howto-create-application)

#### Step 1 - Access and Registration
- Head to the [Azure IoT Central](https://azure.microsoft.com/en-us/services/iot-central/) Main page and select the "Get started" button
![IoT Central Main Page](https://github.com/mjksinc/IoTAA-MSFT-Lab/blob/master/Reference_Images/IoTCentral_mainPage.PNG)

- Next, you'll need to sign into your Microsoft account. If you don't have one, you can create one for free using the "Create one!" link.
![Sign in pop up from IoT Central](https://github.com/mjksinc/IoTAA-MSFT-Lab/blob/master/Reference_Images/Sign-in_Page.PNG)

#### Step 2 - Create New Application
- Once you're all signed in, we'll now need to deploy a trial version of IoT Central. This instance will only last for 7 days but you won't be charged for the deployment. Amazing! You can always extend the trial to a paid version if you'd like to continue using the application. 
- Select the "New Application" Icon. In the pop-up, make sure to select the "Free" payment plan and the "Sample Dev Kit" template. Fill in the rest of the details and select "Create". Easy.
![New Application Button](https://github.com/mjksinc/IoTAA-MSFT-Lab/blob/master/Reference_Images/CreateApp_1.PNG)
![Create Application View](https://github.com/mjksinc/LXRA-IoT/blob/master/Images/1.CreateCentralApp.jpg)
- You should now see the front page of your very own IoT Central Application!
![IoT Central Front Page](https://github.com/mjksinc/LXRA-IoT/blob/master/Images/2.CentralFrontPage.jpg)

#### Step 3 - Adding a new device
- On the left of the screen, you'll see some menu icons. Click on the "Device Explorer" tab.
- You'll notice that several simulated devices are already available in the menu. IoT Central will automatically create simulations of new device types within the application so you can easily see how the data will flow from a real device. We'll now create a new device according to one of these pre-built templates:
  - Select *MXChip* under *Templates*  
  - Click on the *"+"* dropdown and select *Real*
![Add real device](https://github.com/mjksinc/LXRA-IoT/blob/master/Images/3.CreateNewDevice.jpg)
  - A pop-up will appear for you to enter a device id and device name. Enter these details and select *Create*
![New Device Credentials](https://github.com/mjksinc/LXRA-IoT/blob/master/Images/4.DetailsForNewDevice.jpg)
- After a few seconds, this device will be created and you'll be redirected to the device's configuration page. You'll now need to copy the connection credentials so your real device knows where to send the data!
![Device Conf Page](https://github.com/mjksinc/LXRA-IoT/blob/master/Images/4.5.NewDeviceScreen)
  - Select *Connect* at the top of the page
  - A new box will appear. Copy and paste the *Scope ID*, *Device ID* and *Primary Key* in to a blank text file to use later.
  - Click *Close* once copied
![Device Credentials](https://github.com/mjksinc/LXRA-IoT/blob/master/Images/5.DeviceConnectionCredentials.jpg)

That's all for configuring your IoT Central Application! Let's know swap to the MXChip board to start streaming data.

### Configuring and Connecting your MXChip Board
Now we'll need to activate the dev board to connect to the internet and start sending data to the IoT Central Application you just created.

#### Step 1 - Power on your Dev Board
- Plug in you Dev Kit using the usb cable provided. The lights on the board should turn on and the screen should show something similar to this text:
```HTML
    Connect HotSpot:
    AZ3166_??????       //Hotspot Name
    go-> 192.168.0.1    //IP Address
    PIN CODE xxxxx      //Pin Code
```

#### Step 2 - Connect and configure your Dev Board through a browser
- The device has created a wifi hotspot which we'll now need to connect to. On your computer, open the wifi settings and connect ot the new network name displayed on your device (*"AZ3166_XXXXXX"*) **NOTE -** This will temporarily disconnect you from the internet. 
- Once connected, open up your web browser and go to the IP address displayed on the device (*"192.168.0.1"*)
- A new screen will appear and you'll be prompted to enter the details copied when you created earlier:
![Browser Configuration](https://github.com/mjksinc/LXRA-IoT/blob/master/Images/6.2.DeviceWebpageConf.jpg)

  - Find the name of your WiFi network 
  - Enter the password for the WiFi Network
  - The PINCODE is displayed on the Dev Board
  - The *Scope Id*, *Device Id*, and *Primary key* that you copied in a previous step 
  - Keep all the measurements selected
  - Click "Configure Device"
  - That's it! The webpage will notify you that the device is configured

![Configured Device](https://github.com/mjksinc/LXRA-IoT/blob/master/Images/6.3.deviceconfigured.png)

- After several resets, the Dev Board show now have all lights set to green, *"-- Connected --"* should be displayed, and the message count should increment.

![Device connected](https://github.com/mjksinc/LXRA-IoT/blob/master/Images/7.DeviceConnected.JPG)

- Reconnect your computer to the internet and head back over to your IoT Central application [apps.azureiotcentral.com/](apps.azureiotcentral.com/)

### View data in IoT Central
Let's check out the data being streamed from the device.

- Click on the "Device Explorer" tab and navigate to the device you created previously. Click the device name to see the information page.
![Device Information page](https://github.com/mjksinc/LXRA-IoT/blob/master/Images/8.NavigateToDevice.jpg)

- You should now see some data visualised on the graph (if not, wait a few seconds or ask one of teh facilitators for help). Try experimenting with the board!
  - What happens when you presss the "A" button?
  - What happens when you press the "B" button?
  - Can you influence the measurements?

  ![Data Visualisation](https://github.com/mjksinc/LXRA-IoT/blob/master/Images/9.VisualisedData.jpg)

### Next Steps
What now? This is just the beginning of what is capable through the IoT Central Application. Try some of the following if you feel like exploring more of the features:
- [Create a telemetry rule](https://docs.microsoft.com/en-us/azure/iot-central/howto-create-telemetry-rules)
- [Customise the images in your app](https://docs.microsoft.com/en-us/azure/iot-central/howto-prepare-images)
- [Congifure your homepage](https://docs.microsoft.com/en-us/azure/iot-central/howto-configure-homepage)
- [Find out more about Azure IoT](https://azure.microsoft.com/en-au/overview/iot/?site=mscom_iot)

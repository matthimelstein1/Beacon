# Beacon
###An implementation of iBeacon technology to take ticket information, verify that the information exists in a database and display the result

I'll break this down by file. If there are any questions/issues, feel free to drop me a line.

##iBeaconWrite_V2_7.js
The highest up in the file heirarchy of the program. This is where the magic happens. This portion has three main tasks:
1. Performing two shell commands that reset the bluetooth daemon of the Edison
2. Beginning the intialiazation of the rest of the files in the heirarchy
3. Initalizing and managing the iBeacon and BLE services and events of the beacon


## UUID_Strings.txt
An example file of the structures necessary to read ticket strings with the SdSearch module

##Images
The necessary images for the OledDisplay module

##Node_Indicators
The OLED driver and bindings

##node_modules
* **Bleno**:
  The javascript beacon API
* **line-reader**:
  As it sounds, used in SdSearch to 
* **png-to-lcd**:
  Used to convert png images to lcd compatible bitmaps
* **replace**:
  Used to aid the unimplemented SDReplaceFunction
* **segfault-handler**:
  Used to catch and manage unexpected segfaults
* **exec**:
  Used to execute shell commands from within the script
* **machina**:
  State machine--overall controller for state changes


#Future suggestions
See the issues section


#Relevant Documentation 

Maxsonar EZ: http://www.maxbotix.com/documents/HRLV-MaxSonar-EZ_Datasheet.pdf

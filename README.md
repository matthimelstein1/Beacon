# Beacon
###An implementation of iBeacon technology to take ticket information, verify that the information exists in a database and display the result--Updated from Tfly_Beacon

I'll break this down by file. If there are any questions/issues, feel free to drop me a line.

##BeaconMachineManager
The highest up in the file heirarchy of the program. This is where the magic happens. It initiates, manages and listens to all of the different processes (indicators, bluetooth, ultrasonic, etc.) depending on the state of the machine. A more thorough documentation frill follow.

#### A brief rundown of the states, events and functions (anonymous and not) of BeaconMachineManager

|State Name     |Description   | Note    |
|---------------|--------------|---------|
|none  |Initial state of the machine before being initialized |Cannot be returned to after starting the machine  |
|init  |The beacon initializes itself and all of its peripherals | Cannot be returned to after starting the machine  |
|default  |The manager monitors the bluetooth for a received ticket-string, it also monitors the ultrasonic for a deviation  |N/A  | 
|checkingDatabase  |Checks the SD card database for a ticket-string found in the default state  |N/A  | 
|admitVIP  |Displays the VIP admit indicators and returns to default  |N/A   | 
|admitGEN  |Displays the admit indicators and returns to default  |N/A   |  
|noAdmitVOI  |Displays the no admit-Void indicators and returns to default  |N/A   | 
|noAdmit  |Displays the no admit indicators and returns to default  |N/A   | 



|Event Name     |Description   | Note    |
|---------------|--------------|---------|
|start  |moves the machine from the `none` state to the `init` state  |N/A  |  
|beginDefault  |moves the machine from the `init` state to the `default` state  |N/A  | 
|toCheckDatabase  |moves the machine from the `default` state to the `checkingDatabase` state  |N/A  | 
|toAdmitGeneral  |moves the machine from the `checkingDatabase ` state to the `admitGEN` state  |N/A  | 
|returnToDefault  |  |N/A  |  
|toAdmitVIP  |moves the machine from the `checkingDatabase ` state to the `admitVIP` state  |N/A  |  
|toNoAdmitVOI  |moves the machine from the `checkingDatabase ` state to the `noAdmitVOI` state  |N/A  |  
|noAdmitNormal  |moves the machine from the `checkingDatabase ` state to the `noAdmit` state  |N/A  |  
|cutToNoAdmit  |moves the machine from the `default` state to the `noAdmit` state  |N/A  |  
|cutToCheckDatabase  |moves the machine from the `noAdmit` state to the `checkingDatabase` state  |N/A  |  


|Function Name     |Description   |Arguments      | Returns     | Note    |
|--|--|--|--|--|
|__endFlagMarker()  |Used to mark that the indicators have been on long enough for the noAdmit state and that the manager should return to the default state  |N/A  |N/A  |N/A  |
|ondefault  |  |N/A  |N/A  |**Cannot be called in the script, as it is an anonymous function** |
|oncheckingDatabase  |  |N/A  |N/A  |**Cannot be called in the script, as it is an anonymous function**   |
|onadmitGEN  |  |N/A  |N/A  |**Cannot be called in the script, as it is an anonymous function**   |
|onadmitVIP  |  |N/A  |N/A  |**Cannot be called in the script, as it is an anonymous function**   |
|onnoAdmitVOI  |  |N/A  |N/A  |**Cannot be called in the script, as it is an anonymous function**   |
|onnoAdmit  |  |N/A  |N/A  |**Cannot be called in the script, as it is an anonymous function**   |
|onleavedefault  |  |N/A  |N/A  |**Cannot be called in the script, as it is an anonymous function**   |
|onleavecheckingDatabase  |  |N/A  |N/A  |**Cannot be called in the script, as it is an anonymous function**   |
|onleaveadmitGEN  |  |N/A  |N/A  |**Cannot be called in the script, as it is an anonymous function**   |
|onleaveadmitVIP  |  |N/A  |N/A  |**Cannot be called in the script, as it is an anonymous function**   |
|onleavenoAdmitVOI | |N/A |N/A |**Cannot be called in the script, as it is an anonymous function**  |
|onleavenoAdmit | |N/A |N/A |**Cannot be called in the script, as it is an anonymous function**  |

##Images
The necessary images for the OledDisplay module

##Indicators
Oled, LED and buzzer control functions. See the directory for its specific README

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
* **javascript-state-machine**:
  State machine--overall controller for state changes

#Future suggestions
See the issues section

#Relevant Documentation 
Maxsonar EZ: http://www.maxbotix.com/documents/HRLV-MaxSonar-EZ_Datasheet.pdf

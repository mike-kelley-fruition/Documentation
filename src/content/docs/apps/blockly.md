---
title: Blockly
layout: onboarding.hbs
columns: one
order: 7
---

# {{title}}

Blockly is a block-based, visual programming language editor that runs in your browser.

**Note:** We recommend the following browsers for running Blockly with Misty: Chrome, Safari, Firefox, and Microsoft Edge (latest versions).

![Blockly](../../../assets/images/blockly_1.png)

## Blockly Controls

The following controls are available on Misty's Blockly editor.

![Blockly controls](../../../assets/images/menu_blockly_2.png)

* **Robot IP Address**: Enter your Misty's IP address here; you can get this value from the Misty companion app.
* **Connect/Connected button**: Indicates whether Blockly can communicate with Misty. After entering Misty's IP address, click the **Connect** button. When Misty is connected to Blockly, the button changes to **Connected**.
* **Run**: Runs the blocks on the workspace.
* **Abort**: Stops the currently running Blockly project. **Important! Abort stops the project after the current block completes and before the next block begins; it doesn't stop the actions of the current block.**
* **Save Project**: Saves the blocks on the workspace as "blockly.txt" to your computer's **Downloads** folder.
* **Show JavaScript**: Displays the JavaScript code generated by the blocks on the workspace.
* **Load Project**: Opens a saved Blockly file onto the workspace.

## Set up Blockly

Follow the steps below to set up Blockly with Misty.

**Note:** It's not generally recommended for multiple users to each use a separate instance of Blockly to connect with and send commands to a single Misty robot. If more than one person does connect to Misty at the same time, as in a class or group development environment, people will need to take turns sending commands, or Misty may appear to respond unpredictably.

**Important!** Blockly does not display the complete collection of Misty’s command blocks until after you establish a Wi-Fi connection between Blockly and your robot. If you notice missing command blocks, follow the steps below to make sure a connection exists between your robot and Blockly.

1. Make sure Misty and your computer are on the same Wi-Fi network and that your computer has Bluetooth turned on.
2. [Open up Blockly](http://sdk.mistyrobotics.com/blockly) in a browser window.
3. Enter the IP address of your robot in Blockly and click **Connect**. You can get Misty's IP address from the **Info** tab in the companion app. The **Connect** button should change to **Connected**. **Note:** If you cannot connect, double-check that Misty and your computer are on the same Wi-Fi network. If necessary, reload the page.
4. Open your browser's JavaScript console. Misty has some Blockly commands for which the results are shown in the console. For Chrome, select **View** > **Developer** > **JavaScript Console**. For Safari, go to **Preferences...**, then click the checkbox for **Show Develop menu in menu bar**, then go to the **Develop** menu and select **Show JavaScript Console**. If the Blockly controls disappear when you open the JavaScript console, select the icon in the upper left side of the page to display them again. ![Blockly window showing hamburger menu and open JavaScript console](../../../assets/images/blockly_js_console.png)
5. Select a simple Misty-specific block such as "ChangeEyes" (in the "Display" category).
6. Test that Blockly is set up by clicking **Run** and seeing how Misty reacts. **Note:** After clicking **Run**, there may be a short delay before Misty initially reacts. When multiple block commands are run in a row, by default there is no delay between commands. You can use the "Pause" block to add a delay between commands when running multiple commands in a row.


## Experiment with Blockly

Try the following quick "programs" to start controlling Misty with Blockly.

**Note:** After clicking **Run**, there may be a short delay before Misty initially reacts. When multiple block commands are run in a row, by default there is no delay between commands. You can use the "Pause" block to add a delay between commands when running multiple commands in a row.

**Important!** **Abort** stops the project after the current block completes and before the next block begins; it doesn't stop the actions of the current block.


### Change the Color of Misty's LED

Want to change the light behind the logo on Misty's chest? Try this.

1. Choose the "ChangeLEDColor" block and click to select a color.
2. Click **Run**.


### Change the Image on Misty's Face

Are Misty's eyes looking a bit tired? Try uploading your own image to Misty's screen. It's a two-part process, but each part is very easy!

_Note: Misty's screen is 480 x 272 pixels in size. Because Misty does not adjust the scaling of images, for best results use an image with proportions similar to this._

First:
1. Choose the "SaveFileToRobot" block.
2. Add the "BrowseToImageFile" block. When you click on this block, you can select an image file on your computer to upload onto Misty. Valid image file types are .jpg, .jpeg, .gif, .png. and the maximum file size is 3 MB.
3. Click **Run**.

Then:
1. Choose the "ChangeDisplayImage" block.
2. Add the "ListFilesAvailable" block and select your file.
3. Click **Run**.


### Have Misty Play a Different Sound

Want Misty to say something new or make some noise other than her default sounds? It's another very simple, two-part process.

First:
1. Choose the "SaveFileToRobot" block.
2. Add the "BrowseToAudioFile" block. When you click on this block, you can browse for an audio file on your computer to upload onto Misty. All audio file types are valid, however Misty cannot currently play OGG files. The maximum file size is 3 MB.
3. Click **Run**.

Then:
1. Choose the "PlayAudioClip" block.
2. Add the "ListFilesAvailable" block and select your file.
3. Click **Run**.


## General Commands

These commands are mainly informational. To see results with some commands, you must have the JavaScript Console for the Blockly page open. For Chrome, select **View** > **Developer** > **JavaScript Console**. For Safari, go to **Preferences...**, click the checkbox for **Show Develop menu in menu bar**, then go to the **Develop** menu and select **Show JavaScript Console**.

![Misty Blockly - general commands](../../../assets/images/blockly_general_commands.png)


### SetNetworkConnection
Connects Misty to a specified Wi-Fi source.

Parameters
* NetworkName: The Wi-Fi network name (SSID).
* Password: The Wi-Fi network password.


### GetAvailableWifiNetworks
Displays a list of the Wi-Fi networks currently in range of Misty.

Parameters
* None

Returns
* A list of Wi-Fi networks currently in range of Misty. Open your browser's JavaScript console to view the results of this command.


### GetBatteryLevel
Obtains Misty's current battery level, along with other information about the battery.

Parameters
* None

Returns

* An object with information about Misty's current battery level. Includes the following properties:
  * capacitymAh (int)
  * chargePercent (double)
  * created (string)
  * currentmAh (int)
  * expiry (string)
  * isCharging (bool)
  * lastChargeCapacity (int)
  * maxMeasuredCapacity (int)
  * numberOfChargeCycles (int)
  * sensorId (string)
  * sensorName (string)
  * state (string)
  * temperature (int)
  * trained (bool)
  * voltage (double)

### GetDeviceInformation
Displays hardware and version information for your Misty robot.

Parameters
* None

Returns
* A set of data about your Misty robot. Open your browser's JavaScript console to view the results of this command. Information includes Windows OS version, Real Time Controller hardware version, Real Time Controller firmware version, IP address, and sensor capabilities.


### GetHelp
Displays information about Misty's available commands. Calling GetHelp with no parameters returns a list of all the commands that are available.

Parameters
* Command: Enter a specific command name or leave empty for a list of all commands.

Returns
* Information about a specific command or a list of all available commands. Open your browser's JavaScript console to view the results of this command.


### PauseForDuration
Inserts a pause between when Misty runs command blocks.

Parameters
* Duration: A value in milliseconds (ms) for the pause. Value range: 100ms - 10,000ms, in increments of 100ms.


### MoveHead (BETA)
Moves Misty's head to the left, right, up, or down.

Parameters
* Location: Left, Right, Up, or Down.
* Speed: The speed at which Misty's head moves. Value range: 0 to 10.


## Speaker Commands
These commands direct Misty to play different sounds and allow you to upload custom sounds to Misty.

![Misty Blockly - speaker commands](../../../assets/images/blockly_speaker_commands.png)


### SaveFileToRobot
Saves an audio file onto Misty. This block **must** connect with the "Browse for file" block, to select the audio file to be saved.

Parameters
* File: The audio file to save to Misty from the "Browse for file" block. This command accepts all audio format types, however Misty cannot currently play OGG files. The maximum file size is 3 MB.


### PlayAudioClip
Plays an audio file that has been previously uploaded to Misty. This block **must** connect with the "ListFilesAvailable" or "GetListOfAudioClips" block, to select the audio file to play.

Parameters
* File: The audio file to play. Connect the "ListFilesAvailable" or "GetListOfAudioClips" block to this block in order to select an audio file.

* Volume: A value between 0 (silent) and 100 (full volume) that determines how loudly Misty plays the audio clip.


### ListFilesAvailable
Lists the existing audio files on Misty. Connect this block to a "PlayAudioClip" block to select a sound to play. You can also connect this block to a "DeleteAudioAssetFromRobot" block to remove an audio file you've previously uploaded to Misty.

Parameters
* None


### BrowseToAudioFile
Allows you to browse for a file on your computer. Connect this with a "SaveFileToRobot" block to select a file to upload to Misty.

Parameters
* File: When you click on this block, a browse file dialog is displayed to allow for file selection. All audio file types are valid, however Misty cannot currently play OGG files. Maximum file size is 3 MB.


### GetListOfAudioClips
Lists the existing audio files on Misty. Connect this block to a "PlayAudioClip" block to select a sound to play.

Parameters
* None


### DeleteAudioAssetFromRobot
Enables you to remove an audio file from Misty that you have previously uploaded. Connect this with a "ListFilesAvailable" block to select a file to remove from Misty. **Note:** You can only delete audio files that you have previously uploaded to Misty. Blockly posts an error if you attempt to remove one of Misty's default system audio files.

Parameters
* The name of the audio file to remove, supplied by a connected "ListFilesAvailable" block.


## Display Commands
These commands direct Misty to display different images and allow you to upload custom images to Misty.

![Misty Blockly - display commands](../../../assets/images/blockly_display_commands.png)


### DeleteImageAssetFromRobot
Enables you to remove an image file from Misty that you have previously uploaded. Connect this with a "ListFilesAvailable" block to select a file to remove from Misty. **Note:** You can only delete image files that you have previously uploaded to Misty. Blockly posts an error if you attempt to remove one of Misty's default system image files.

Parameters
* The name of the image file to remove, supplied by a connected "ListFilesAvailable" block.


### SaveFileToRobot
Saves an image file to Misty. This block **must** connect with the "BrowseToImageFile" block, to select the image file to be saved.

Parameters
* File: The image file to save to Misty from the "BrowseToImageFile" block. Valid image file types are .jpg, .jpeg, .gif, .png. Maximum file size is 3 MB. Misty's screen is 480 x 272 pixels in size. Because Misty does not adjust the scaling of images, for best results use an image with proportions similar to this.


### ChangeDisplayImage
Displays an image on Misty's screen. This block **must** connect with the "ListFilesAvailable" block or the "BrowseToImageFile" block, to select the image file to display.

You can optionally use "ChangeDisplayImage" to display an image for a specific length of time and/or overlay an image on Misty's eyes.

Parameters
* Filename: The name of the file containing the image to display, selected from the "BrowseToImageFile" block or the "ListFilesAvailable" block. Valid image file types are .jpg, .jpeg, .gif, .png. Maximum file size is 3MB.

* Seconds: Optional. The length of time to display the specified image.

* Alpha: Optional. A decimal value for the transparency of the image. A value of 0 is completely transparent; 1 is completely opaque. When you specify a value greater than 0 and less than 1, the image appears but is transparent, and Misty's eyes appear behind the specified image.


### ChangeLEDColor
Changes the color of the LED behind the logo on Misty's torso.

Parameters
* Color: A color selected from the block's options.


### ListFilesAvailable
Obtains a list of the images currently stored on Misty. Connect this with a "ChangeDisplayImage" block to select a file to display on Misty's screen.

Parameters
* None


### BrowseToImageFile
Browse for a file on your computer. Connect this with a "SaveFileToRobot" block to select a file to upload to Misty.

Parameters
* File: When you click on this block, a browse file dialog is displayed to allow for file selection. Valid image file types are .jpg, .jpeg, .gif, .png.



## Locomotion Commands
Use these commands to drive Misty forward and backward, straight or in a curve, or stop.

**Note:** Before using any locomotion commands, have Misty on a flat surface with plenty of room to move. It's also a good idea to experiment with small velocity values before getting her going at full speed.

![Misty Blockly - locomotion commands](../../../assets/images/blockly_locomotion_commands2.png)


### Drive
Drives Misty forward or backward at a given speed. **Important!** The "Drive" block cannot be the final block in a project. "Drive" **must** be followed by "Stop" or some other block.

When using the "Drive" command, it helps to understand how linear velocity (speed in a straight line) and angular velocity (speed and direction of rotation) work together:
* Linear velocity (-100) and angular velocity (0) = driving straight backward at full speed.
* Linear velocity (100) and angular velocity (0) = driving straight forward at full speed.
* Linear velocity (0) and angular velocity (-100) = rotating clockwise at full speed.
* Linear velocity (0) and angular velocity (100) = rotating counter-clockwise at full speed.
* Linear velocity (non-zero) and angular velocity (non-zero) = Misty drives in a curve.

Parameters
* LinearVelocity: A percent value that sets the speed for Misty when she drives in a straight line. Default value range is from -100 (full speed backward) to 100 (full speed forward).
* AngularVelocity: A percent value that sets the speed and direction of Misty's rotation. Default value range is from -100 (full speed rotation clockwise) to 100 (full speed rotation counter-clockwise). **Note:** For best results when using angular velocity, first experiment with using small positive and negative values to observe the effect on Misty's movement.


### Move
Drives Misty forward or backward at a given speed for a duration specified in milliseconds.

Parameters
* Direction: Forward or backward.
* Speed: A value from 0 (stopped) to 100 (full speed).
* Duration: A value in milliseconds, using 100 ms increments, with a maximum value of 10,000 ms (10 seconds).

### LocomotionTrack
Drives Misty left, right, forward, or backward at a given speed.  **Important!** The "LocomotionTrack" block cannot be the final block in a project. "LocomotionTrack" **must** be followed by "Stop" or some other block.

Parameters
* LeftTrackSpeed: A value for the speed of the left track, ranging from -100 (full speed backward) to 100 (full speed forward).
* RightTrackSpeed: A value for the speed of the right track, ranging from -100 (full speed backward) to 100 (full speed forward).


### Stop
Stops Misty's movement.

Parameters
* None



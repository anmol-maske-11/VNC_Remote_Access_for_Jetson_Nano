# VNC Remote Access for Jetson Nano

Here we will connect jetson nano to VNC viewer application as the preinstalled Desktop Application crashes when we try to use it. To avoide this follow these steps:

## Step 1: Connect the board to wireless connection

This NVIDIA Jetson Nano L4T has poor support for USB Wi-Fi adapters and most adapters do not work with this distribution. Then purchase a compatible USB WiFi adapter to connect to your local network externally.

## Step 2: Start desktop sharing

1. First, open the terminal and paste this line.
<br>a. `sudo apt update`.
<br>b. `sudo apt-get upgrade`.

2. After both the command install nano editor.
<br>a. `sudo apt-get install nano`.

<img src="https://github.com/anmol-maske-11/IMG_Videos/blob/main/1.png">

4. Next paste this link in the terminal and press enter.
<br>a. `sudo nano /usr/share/glib-2.0/schemas/org.gnome.Vino.gschema.xml`.

<img src="https://github.com/anmol-maske-11/IMG_Videos/blob/main/1.png">

5. Open Key_for_XML_file present in this repo
<br>a. Paste the following key into opened XML file.
<br>b. Press `Ctrl + O` to Save than press Enter.
<br>c. To move back to the terminal press `Ctrl + Z`.

<img src="https://github.com/anmol-maske-11/IMG_Videos/blob/main/1.png">

7. Next compile the edited XML file.
<br>a. `sudo glib-compile-schemas /usr/share/glib-2.0/schemas`.

8. Now crashing of Desktop Sharing must have stopped. So Click on 'Search' icon and search for 'Desktop Sharing'. Open it and complete the following changes:
<br>a. Tick mark both the <b>Sharing</b> options. 
<br>b. Under <b>Security</b> Tick mark the 'Require the user to enter this password' and enter the password for VNC session.
<br>c. Close Desktop Sharing.

<img src="https://github.com/anmol-maske-11/IMG_Videos/blob/main/1.png">

## Step 3: Start the VNC server on each startup

Click on 'Search' icon and search for 'Startup Applications'. Open it. Now, click on `Add`, then type `Vino` in the name box. Paste `/usr/lib/vino/vino-server` in the command box. Click `Save` and then `Close`.

<img src="https://github.com/anmol-maske-11/IMG_Videos/blob/main/1.png">

<img src="https://github.com/anmol-maske-11/IMG_Videos/blob/main/1.png">

Now disable the default encryption of the VNC connection. To do this, paste these lines on 
terminal and press enter:
<br>a. `gsettings set org.gnome.Vino require-encryption false`.
<br>b. `gsettings set org.gnome.Vino prompt-enabled false`.

Now Reboot your Jetson Nano and VNC will be enabled on it.

## Step 4: Connect to your Nano via VNC

Login to your Jetson Nano board. Connect your Jetson Nano and your Personal Laptop to the same wifi network. Open terminal in Jetson Nano and type `ifconfig`. You will get the IP address which is assigned to your Jetson Nano. In my case assigned IP address is 192.168.137.222.

Now lets confirm VNC is working or not. Paste this in the terminal:
<br>a. `ps -ef|grep vnc`.

<img src="https://github.com/anmol-maske-11/IMG_Videos/blob/main/1.png">

Now once you know your IP and confirmed that VNC is running, lets move on to your personal laptop(Client Machine).

### Note: In my case I an using Ubantu Linux (ThinkServer Machine)

Open Remmina click the add button on the top left, then in Protocol option select 'Remmina VNC Plugin', then click the (…)button which is in the right end of the 'Server' IP address entering bar. This (…) button should automatically scan and show the name of your jetson Nano. Click on (in my case ipv4 bmek) and then 'Save and Connect'.
<img src="https://github.com/anmol-maske-11/IMG_Videos/blob/main/1.png">
<img src="https://github.com/anmol-maske-11/IMG_Videos/blob/main/2.png">
<img src="https://github.com/anmol-maske-11/IMG_Videos/blob/main/3.png">
<img src="https://github.com/anmol-maske-11/IMG_Videos/blob/main/4.png">
<img src="https://github.com/anmol-maske-11/IMG_Videos/blob/main/5.png">

<h3>Congralutations we have done it</h3>


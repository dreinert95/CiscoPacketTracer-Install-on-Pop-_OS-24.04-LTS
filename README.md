# CiscoPacketTracer-Install-on-Pop!_OS-24.04-LTS
This repository will serve as a guide on how to install CiscoPacketTracer on Pop!_OS 24.04 LTS

1. Navigate to https://www.netacad.com/ and create an account
2. Search for "Cisco Packet Tracer" and then click into "Getting Started with Cisco Packet Tracer" and then "Enroll in Course"
3. You can then watch and follow the outlined modules at your own pace
4. To download and install Cisco Packet Tracer, use the following link: https://www.netacad.com/resources/lab-downloads
5. Select the version of Packet Tracer you want to download
   - In this example we will download the Ubuntu 64bit version
6. Open and terminal and navigate to the Downloads folder.
7. Install the file using: sudo dpkg -i CiscoPacketTracer_*.deb
  - It is common to encounter dependency errors. Fix those errors using: sudo apt --fix-broken install
8. Run the program using: packettracer

# Pop!_OS 24.04 Wayland Issuess
Pop!_OS 24.04 uses newer libraries and since Cisco Packet Tracer was built using older Linux libraries, Pop!_OS 24.04 doesn't have all of the required libraries by default.

To ensure Pop!_OS 24.04 is fully updated, run the following command: sudo apt update
- If updates are available, run the following command to install them: sudo apt upgrade -y
- This will update and upgrade all available packages*** (the -y flag can be used to automatically allow the necessary storage and permissions required by the new update)

Install the additional libraries using the following command: sudo apt install fontconfig libfontconfig1 libxkbcommon-x11-0 libxcb-cursor0 libnss3
Install the additional Qt WebEngine dependencies using the following command: sudo apt install libgl1-mesa-glx libegl1 libxcomposite1 libxdamage1 libxrandr2 libgbm1 libasound2

Pop!_OS uses Wayland by default, therefore we must enforce the use of X11.
- This can be done using the following command: QT_QPA_PLATFORM=xcb packettracer

- Packet Tracer 9.x bundles an older Chromium engine and expects:

Older fontconfig layout
X11 display server
Older Qt libraries
Ubuntu 24.04 / Pop 24.04 changed several of those.

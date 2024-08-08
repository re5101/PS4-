# PS4-
Enhancing PS4 Jailbreaking: Simplifying the 11.00 Firmware Exploitation Process with Raspberry Pi:


I've developed a personal solution aimed at simplifying the PS4 jailbreaking process, particularly focusing on the 11.00 firmware. While TheFlow recently released an early version of the jailbreak, I'm working on refining it further. This solution, still in its trial phase, aims to automate the process, making it more accessible to users. While I'm in the beta stage, I take no responsibility for any potential issues that may arise. However, I'm committed to updating and improving the solution over time. Your feedback and contributions are welcome. It's important to note that this automation currently supports only the 11.00 PS4 firmware and requires a Raspberry Zero. Although it may also work with the 3,4,5, etc.. this compatibility remains untested at present.

#!/bin/bash

# Clone the repository
git clone --recursive https://github.com/TheOfficialFloW/PPPwn || { echo "Error: Cloning repository failed."; exit 1; }

# Navigate into the cloned directory
cd PPPwn || { echo "Error: Directory not found."; exit 1; }

# Install requirements
sudo pip install -r requirements.txt || { echo "Error: Installing requirements failed."; exit 1; }

# Compile the payloads for FW 11.00
make -C stage1 FW=1100 clean && make -C stage1 FW=1100 || { echo "Error: Compiling stage1 payload failed."; exit 1; }
make -C stage2 FW=1100 clean && make -C stage2 FW=1100 || { echo "Error: Compiling stage2 payload failed."; exit 1; }

# Run the exploit
sudo python3 http://pppwn.py --interface=enp0s3 --fw=1100 || { echo "Error: Exploit failed."; exit 1; }

echo "Exploit completed successfully."

Save this script with a .sh extension (e.g., automate_exploit.sh) and make it executable using the following command:

chmod +x automate_exploit.sh

Then, you can execute the script on your Raspberry Pi by running:

./automate_exploit.sh

This script handles cloning the repository, installing requirements, compiling payloads, and executing the exploit. In case of any failure during these steps, it will prompt an error message and terminate. Make sure to adjust the network interface name (enp0s3) according to your Raspberry Pi configuration.

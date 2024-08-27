If you are setting up a local installation on CodeReady Containers (CRC) for OpenShift and want to include some additional tools like Wireshark, here’s a more detailed step-by-step guide to help you install and configure everything:

### Step-by-Step Guide to Setting Up CRC with Additional Tools on a Local Machine

1. **Install CodeReady Containers (CRC):**

   First, you need to download and install CRC. Follow these steps based on your operating system:

   - **Windows:**
     - Download the CRC installer from the official [Red Hat Developer website](https://developers.redhat.com/products/codeready-containers/overview).
     - Install CRC by running the downloaded installer.

   - **macOS / Linux:**
     - Download the CRC binary and extract it.
     - Move the binary to a directory that is in your system’s PATH.

   ```bash
   # Example for Linux/macOS
   tar -xvf crc-linux-amd64.tar.xz
   sudo mv crc-linux-*-amd64/crc /usr/local/bin/
   ```

2. **Set Up CRC:**

   After installing CRC, set it up with the following steps:

   - **Run setup command:**

   ```bash
   crc setup
   ```

- **install bigger size apps to crc**
   ```bash
   crc config set disk-size 160
   ```

   - **Start CRC:**
   
   Make sure you have a valid pull secret from Red Hat. You can download it from your [Red Hat account](https://cloud.redhat.com/openshift/install/crc/installer-provisioned).

   ```bash
   crc start --pull-secret-file ~/Downloads/pull-secret.txt
   ```

3. **Install Wireshark on Windows using Chocolatey:**

   If you're on Windows and want to use Wireshark to capture network traffic, you can install it using Chocolatey, a package manager for Windows.

   - **Install Chocolatey** (if not already installed):

     Open a command prompt with administrative privileges and run the following command:

   ```powershell
   @"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"
   ```

   - **Install Wireshark** using Chocolatey:

   ```powershell
   choco install wireshark -y
   ```

   This command will install Wireshark without any additional prompts.

4. **Configure Network for CRC:**

   For Wireshark to capture network traffic properly, ensure your network interfaces are configured correctly. CRC typically sets up a virtual network adapter for the OpenShift environment.

5. **Capture Network Traffic with Wireshark:**

   Once Wireshark is installed:

   - Open Wireshark.
   - Select the network interface corresponding to the CRC virtual network.
   - Start capturing packets.

6. **Optional: Install Wireshark on macOS/Linux:**

   If you're using macOS or Linux, you can install Wireshark using a package manager.

   - **macOS:**

   ```bash
   brew install wireshark
   ```

   - **Linux:**

   ```bash
   sudo apt-get install wireshark -y  # Ubuntu/Debian
   sudo dnf install wireshark -y      # Fedora/RHEL
   ```

7. **Additional Configuration and Use:**

   - You may need to configure CRC or your local machine to ensure that the network packets of interest are captured. 
   - For advanced use cases, you can run commands within CRC (using `oc debug` or similar) to ensure the proper setup of packet capture on specific nodes or pods.

8. **Monitor CRC and OpenShift Resources:**

   You can use the `oc` CLI tool to manage and monitor resources within your OpenShift environment on CRC. Here are some useful commands:

   ```bash
   oc login -u developer -p developer https://api.crc.testing:6443
   oc get nodes
   oc get pods -A
   ```

This guide should help you set up CRC, install Wireshark on a Windows machine using Chocolatey, and start capturing network traffic effectively. Let me know if you need further assistance!

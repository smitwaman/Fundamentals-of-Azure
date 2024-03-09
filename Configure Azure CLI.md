To install Azure CLI, you can follow these steps:

**For Windows:**

1. **Download Installer:** Go to the [Azure CLI installation page](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli-windows?tabs=azure-cli) and download the installer for Windows.

2. **Run Installer:** Once the installer is downloaded, double-click on it to run. Follow the installation wizard instructions to complete the installation.

3. **Verify Installation:** After installation, open Command Prompt or PowerShell and type `az --version` to verify that Azure CLI is installed correctly. You should see the version number printed in the output.

**For macOS:**

1. **Install Homebrew (if not already installed):** If you don't have Homebrew installed, you can install it by running the following command in Terminal:
   ```
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```

2. **Install Azure CLI:** Once Homebrew is installed, you can install Azure CLI by running the following command in Terminal:
   ```
   brew update && brew install azure-cli
   ```

3. **Verify Installation:** After installation, type `az --version` in Terminal to verify that Azure CLI is installed correctly. You should see the version number printed in the output.

**For Linux (Ubuntu/Debian):**

1. **Install Dependencies:** Before installing Azure CLI, make sure to install the required dependencies by running the following commands in Terminal:
   ```
   sudo apt-get update
   sudo apt-get install ca-certificates curl apt-transport-https lsb-release gnupg
   ```

2. **Download and Install Azure CLI:** Run the following commands in Terminal:
   ```
   curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash
   ```

3. **Verify Installation:** After installation, type `az --version` in Terminal to verify that Azure CLI is installed correctly. You should see the version number printed in the output.

That's it! You have successfully installed Azure CLI on your system. You can now proceed with configuration and usage as needed.

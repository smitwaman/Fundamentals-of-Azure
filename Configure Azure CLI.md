To install Azure CLI, you can follow these steps:

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

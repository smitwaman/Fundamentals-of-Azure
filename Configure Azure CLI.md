To install Azure CLI on Ubuntu, you can follow these steps:

1. **Update Package Index:**
   ```
   sudo apt-get update
   ```

2. **Install Dependencies:**
   ```
   sudo apt-get install ca-certificates curl apt-transport-https lsb-release gnupg
   ```

3. **Download and Install the Microsoft Signing Key:**
   ```
   curl -sL https://packages.microsoft.com/keys/microsoft.asc | 
   gpg --dearmor | 
   sudo tee /etc/apt/trusted.gpg.d/microsoft.gpg > /dev/null
   ```

4. **Add Azure CLI Repository:**
   ```
   AZ_REPO=$(lsb_release -cs)
   echo "deb [arch=amd64] https://packages.microsoft.com/repos/azure-cli/ $AZ_REPO main" | 
   sudo tee /etc/apt/sources.list.d/azure-cli.list
   ```

5. **Update Package Index Again:**
   ```
   sudo apt-get update
   ```

6. **Install Azure CLI:**
   ```
   sudo apt-get install azure-cli
   ```

7. **Verify Installation:**
   ```
   az --version
   ```

This command should display the version of Azure CLI if the installation was successful.

Now, Azure CLI should be installed on your Ubuntu system. You can start using it by logging in to your Azure account and running various commands to manage your resources. Use `az login` to authenticate with Azure and begin using Azure CLI.

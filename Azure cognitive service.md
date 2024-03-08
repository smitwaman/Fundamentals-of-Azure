Explanation step by step creation of resource Azure Cognitive Services

●	LUIS (Language Understanding): Natural Language Processor. Some use-cases are:
○	Social Media Feedback monitoring and response

○	Bot Servicing product queries and feedback

○	Speech enabledIntelligent desktop app for order tracking

●	Bot service can be hosted inside an App Service plan

●	Bot channel is a connection between a bot and communication apps. The communication app can be a direct client, Skype, a web service chat etc.


To create a resource for Azure Cognitive Services, specifically for LUIS (Language Understanding), and integrate it with a bot service hosted in an App Service plan, follow these steps:

1. **Sign in to the Azure portal**: Log in to the Azure portal using your Azure account credentials.

2. **Create a new resource**: Click on the "Create a resource" button in the upper left corner of the Azure portal.

3. **Search for Cognitive Services**: In the search bar, type "Cognitive Services" and press Enter.

4. **Select Cognitive Services**: From the search results, select "Cognitive Services" and click on the "Create" button.

5. **Configure the Cognitive Services resource**:
   - Choose a subscription: Select the subscription you want to use for the Cognitive Services resource.
   - Resource group: Create a new resource group or select an existing one.
   - Region: Choose the region where you want to deploy the resource.
   - Name: Enter a unique name for your Cognitive Services resource.
   - Pricing tier: Select the pricing tier that fits your needs. LUIS is available under various pricing tiers, so choose according to your requirements.
   - Review the terms and conditions, then click on the "Review + create" button.

6. **Review and create**: Review the configuration settings for the Cognitive Services resource, and if everything looks good, click on the "Create" button to deploy the resource.

7. **Access the resource**: Once the deployment is complete, navigate to the resource from the Azure portal dashboard.

8. **Set up LUIS**: Within the Cognitive Services resource, look for the option to create a Language Understanding (LUIS) application. Click on it and follow the prompts to set up your LUIS application.

9. **Define intents and entities**: In your LUIS application, define intents (such as social media feedback monitoring, product queries, etc.) and entities (such as product names, feedback categories, etc.) that are relevant to your use cases.

10. **Train and test the LUIS model**: After defining intents and entities, train your LUIS model using sample utterances. Test the model to ensure that it accurately understands and extracts the intents and entities.

11. **Integrate with Bot Service**: Once your LUIS model is trained and tested, integrate it with your bot service hosted in an App Service plan.
    - Navigate to your bot service in the Azure portal.
    - Look for the option to configure channels or integrations.
    - Add the LUIS service as a channel or integration to your bot service.
    - Configure the endpoint URL of your LUIS application within the bot service settings.

12. **Connect bot to communication apps**: Finally, connect your bot to communication apps such as Skype, Microsoft Teams, web chat, etc., using the bot channels. This allows users to interact with your bot through these communication platforms.

By following these steps, you'll have successfully created a resource for Azure Cognitive Services, specifically for LUIS, and integrated it with a bot service hosted in an App Service plan, allowing your bot to understand natural language input from users and respond accordingly.

Here's a basic JSON template for creating an Azure Cognitive Services resource, specifically for Language Understanding (LUIS):

```json
{
  "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
  "contentVersion": "1.0.0.0",
  "parameters": {
    "cognitiveServiceName": {
      "type": "string",
      "metadata": {
        "description": "Name for the Cognitive Services resource"
      }
    },
    "location": {
      "type": "string",
      "defaultValue": "[resourceGroup().location]",
      "metadata": {
        "description": "Location for the Cognitive Services resource"
      }
    },
    "sku": {
      "type": "string",
      "defaultValue": "F0",
      "metadata": {
        "description": "Pricing tier for the Cognitive Services resource"
      }
    }
  },
  "resources": [
    {
      "type": "Microsoft.CognitiveServices/accounts",
      "apiVersion": "2017-04-18",
      "name": "[parameters('cognitiveServiceName')]",
      "location": "[parameters('location')]",
      "sku": {
        "name": "[parameters('sku')]"
      },
      "kind": "LUIS",
      "properties": {}
    }
  ]
}
```

This template defines parameters for the name, location, and pricing tier of the Cognitive Services resource. It then creates a Cognitive Services resource of type LUIS using the specified parameters.

You can customize this template further by adding additional properties or modifying existing ones based on your specific requirements and configurations.

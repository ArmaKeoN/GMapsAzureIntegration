# GMapsAzureIntegration
This repository hosts a GitHub Actions workflow for automatically rotating Google Maps API keys and securely storing them in Azure Key Vault. It ensures up-to-date key management and enhances security through automated processes

## Rotate and List Google Maps API Keys

This comprehensive documentation outlines the process for the automated rotation and listing of Google Maps API keys within the `GMapsAzureIntegration` GitHub project. This process is designed to be operational and maintainable by engineers, ensuring high security and compliance standards.

### Workflow Overview

This GitHub Actions workflow is scheduled to run daily at midnight UTC and can be triggered manually via workflow dispatch. It ensures that Google Maps API keys are rotated regularly for security reasons and updates Azure Key Vault with the new key.

### Workflow Steps

1. **Authentication**:
    - Authenticate with Google Cloud using the provided JSON credentials.

2. **Set up Cloud SDK**:
    - Set up a specific version of the Google Cloud SDK to ensure compatibility and stability.

3. **Retrieve Old API Key**:
    - List the current Google Maps API keys and identify the key to be rotated.

4. **Generate New API Key**:
    - Create a new Google Maps API key and store it temporarily.

5. **Store New API Key in Azure Key Vault**:
    - Authenticate with Azure and update the Azure Key Vault with the new API key.

6. **List All API Keys**:
    - List all Google Maps API keys post-rotation for verification.

7. **Delete Old API Key**:
    - Delete the old API key from Google Cloud to maintain security.

### Tools and Technologies Used

- **GitHub Actions**: Used for automating the workflow.
- **Google Cloud SDK**: Utilized for managing Google Maps API keys.
- **Azure Key Vault**: Stores the newly generated API key securely.
- **JQ**: Command-line JSON processor used for parsing command outputs.

### Key Resources
- **Repository Secrets**: `AZURE_CREDENTIALS`,`GOOGLE_APPLICATION_CREDENTIALS`
- **GitHub Repository**: [GMapsAzureIntegration](https://github.com/ArmaKeoN/GMapsAzureIntegration)
- **Google Cloud Project**: `GMapsAzureIntegration`
- **Google Cloud Service Principal**: `gmaps-apikey-manager`
- **Azure Resource Group**: `GMapsKeyVaultIntegrationRG`
- **Azure Service Principal**: `GMapsKeyVaultIntegrationSP`
- **Azure Key Vault**: `GMapsKeyVault`

### Schedule Execution Times Across Time Zones

This section provides the local times the task is scheduled to run across various time zones:

#### European Time Zones:
- **WET (UTC+0)**: 00:00 (midnight) - Portugal, UK (winter)
- **CET (UTC+1)**: 01:00 AM - Central Europe (winter)
- **EET (UTC+2)**: 02:00 AM - Eastern Europe (winter)
- **Summer Time Adjustments**: BST (UTC+1), CEST (UTC+2), EEST (UTC+3)

#### U.S. Time Zones:
- **EST (UTC-5)**: 19:00 (7 PM) previous day
- **CST (UTC-6)**: 18:00 (6 PM) previous day
- **MST (UTC-7)**: 17:00 (5 PM) previous day
- **PST (UTC-8)**: 16:00 (4 PM) previous day
- **Summer Time Adjustments**: EDT (UTC-4), CDT (UTC-5), MDT (UTC-6), PDT (UTC-7)

### Security and Compliance

Regular key rotation is enforced to minimize risks, and updates to the workflow should adhere to security best practices. Maintenance involves updating the documentation to reflect any procedural or tool changes.

### Benefits

- **Automation**: Fully automates the rotation of API keys, reducing manual errors and enhancing security.
- **Security**: Regular key rotation minimizes the risk of outdated or compromised keys.
- **Integration**: Seamless integration with cloud providers like Google Cloud and Azure enhances operational efficiency.

### Drawbacks

- **Complexity**: Requires initial setup and understanding of cloud services and GitHub Actions.
- **Dependency on External Services**: Relies on services remaining available and API compatibility.

### Drawbacks of Using ChatGPT

- **Verification Necessity**: There were occasions when I needed to verify the accuracy of information, as ChatGPT sometimes provided incorrect or illogical responses.
- **Efficiency Concerns**: While ChatGPT is instrumental in drafting initial versions, its lack of deep contextual understanding led to inefficiencies, notably when troubleshooting issues related to capturing outputs from GCP commands.
- **Knowledge Dependency**: Effective use of ChatGPT requires a solid foundational knowledge of the task at hand; otherwise, significant time might be spent directing the AI to achieve the desired outcome.

### Assumptions and Suggestions

- **Assumptions**: The process assumes the presence of only one Google Maps API key at any given time in both Google Cloud Platform and Azure.

### Action Items

- **API Key Management**: Assess whether the old API key should be deleted or merely disabled.
- **Environment Specific Keys**: Decide if different environments should have distinct API keys.
- **Single vs. Multiple Keys**: Determine if a single API key per environment suffices or if multiple keys are necessary.
- **Rotation Schedule**: Establish a rotation schedule for the API key—daily, weekly, monthly, or annually.
- **Workflow Timing**: Optimize the timing for this workflow's execution, considering whether multiple branches should run at different times to accommodate various time zones.

### Suggestions

- **Enhanced Script Flexibility**: Parameterize the script to toggle the output of information/data, particularly for debugging.
- **Secure Handling of API Keys**: Pass the old API key as a secret environment variable to identify and manage outdated keys, provided this is compliant with Azure’s security practices.
- **Warning Clean-Up**: Address and resolve any warnings that emerge during execution.
- **API Key Propagation**: Ensure new API keys are fully propagated and functional before retiring the old keys.
- **Disablement vs. Deletion**: Consider disabling instead of deleting API keys to avoid potential confusion and issues.
- **Notification System**: Implement a notification feature to inform stakeholders promptly upon successful API key rotation.
- **Robust Error Handling**: Expand error handling to manage most exceptions, minimizing the potential for unforeseen problems.
- **Sensitive Information Management**: Explore using GitHub’s native features to mask sensitive output instead of traditional methods like redirection to `/dev/null`.
- **Authentication Best Practices**: Investigate the use of Workload Identity Federation as recommended by GCP over Service Principal/Account.
- **Manual Trigger Considerations**: Evaluate the necessity of manually triggering the workflow, potentially limiting or removing this capability to enhance security.
- **Logging and Documentation**: Implement strategies to log output to files securely, possibly uploading these logs as artifacts to a designated repository area.
- **Infrastructure as Code**: Use Terraform or ARM templates to document the commands used to set up resources in Azure/GCP, serving as a reference for future environments.
- **Least Privilege Access**: Define custom roles with the least privilege necessary for Azure Key Vault and apply similar principles to GCP roles.

### Disclosure of AI Tools and External Resources

- **ChatGPT by OpenAI**: Utilized for generating documentation and code, as well as for troubleshooting and debugging code to enhance and streamline workflow processes.
- **Google GitHub Actions**: Provides direct integration for managing resources within GitHub workflows. Simplifies automation but relies on correct permissions and credentials setup.

This documentation should be reviewed and updated periodically to reflect any changes in the workflow or underlying technologies.
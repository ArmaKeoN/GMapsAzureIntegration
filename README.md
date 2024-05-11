# GMapsAzureIntegration
This repository hosts a GitHub Actions workflow for automatically rotating Google Maps API keys and securely storing them in Azure Key Vault. It ensures up-to-date key management and enhances security through automated processes

## Rotate and List Google Maps API Keys

This documentation details the automated process for rotating and listing Google Maps API keys. It's designed for engineers at Hyperproof to operate, maintain, and possibly enhance the workflow.

### Workflow Overview

This GitHub Actions workflow is scheduled to run daily at midnight UTC and can be triggered manually via workflow dispatch. It ensures that Google Maps API keys are rotated regularly for security reasons and updates Azure Key Vault with the new key.

### Tools and Technologies Used

- **GitHub Actions**: Used for automating the workflow.
- **Google Cloud SDK**: Utilized for managing Google Maps API keys.
- **Azure Key Vault**: Stores the newly generated API key securely.
- **JQ**: Command-line JSON processor used for parsing command outputs.

### Workflow Steps

1. **Authentication**:
    - Authenticate with Google Cloud using the provided JSON credentials.

2. **Set up Cloud SDK**:
    - Set up a specific version of the Google Cloud SDK to ensure compatibility and stability.

3. **Retrieve Old API Key**:
    - List the current Google Maps API keys and identify the key to be rotated.

4. **Generate New API Key**:
    - Create a new Google Maps API key and store it temporarily.

5. **Retrieve New API Key**:
    - Extract the path and key string for the newly generated API key.

6. **Store New API Key in Azure Key Vault**:
    - Authenticate with Azure and update the Azure Key Vault with the new API key.

7. **List All API Keys**:
    - List all Google Maps API keys post-rotation for verification.

8. **Delete Old API Key**:
    - Delete the old API key from Google Cloud to maintain security.

### Disclosure of AI Tools and External Resources

- **ChatGPT by OpenAI**: Used to generate this documentation. Provides natural language processing capabilities but might occasionally require manual adjustment for technical accuracy or clarity.
- **Google GitHub Actions**: Provides direct integration for managing resources within GitHub workflows. Simplifies automation but relies on correct permissions and credentials setup.

### Benefits

- **Automation**: Fully automates the rotation of API keys, reducing manual errors and enhancing security.
- **Security**: Regular key rotation minimizes the risk of outdated or compromised keys.
- **Integration**: Seamless integration with cloud providers like Google Cloud and Azure enhances operational efficiency.

### Drawbacks

- **Complexity**: Requires initial setup and understanding of cloud services and GitHub Actions.
- **Dependency on External Services**: Relies on services remaining available and API compatibility.

### Enhancements and Maintenance

Engineers can enhance this solution by incorporating additional security checks, automating more aspects of the cloud environment, or adapting the workflow to support other types of API keys or services. Regular updates to the action versions and dependency checks are recommended to keep up with new features and security practices.

This documentation should be reviewed and updated periodically to reflect any changes in the workflow or underlying technologies.
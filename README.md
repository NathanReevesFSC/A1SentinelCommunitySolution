# A1SentinelCommunitySolution
A community built Sentinel solution for the Action1 patch management platform.


# azuredeploy_Action1_CCF_complete_v1.0.2.json
This monolithic ARM template will deploy the following resources:

- DCE (Data collection endpoint). A DCE is mandatory for any CCF connector. While the content hub deployed connectors will all use a common DCE that's deployed with the first connector, this solution creates its own as an Azure resource.

- DCR (Cata collection rule). The DCR defines the incoming data stream, and in this case defines the ingestion time parsing that is done to extract the individual values from the JSON provided by the API. Those values are then mapped to specific table fields. The DCR processess on record at a time.

- Custom table. The custom table is of the V2 variety, making it Sentinel Data Lake compliant. The schema has been derived from a sample of 1,000 audit log events. It may not be perfect - if you see any issues please create a PR with updated assets.

- CCF data connector interface. This is the "Data Connectors" item in the Sentinel menu, used to visually monitor data 
connector status, and to perform initial configuration.

Deploy to Azure using the "Deploy a Custom Template" tile. During deployment you will be prompted for your Sentinel Log Analytics Workspace name, and the region name. After deployment, you are required to enter the API URL stub for your Action1 region, your API User and API Key.

# Installation instructions

1. Copy the JSON content
2. Navigate in Azure to "Deploy a custom template"
3. Click "Custom template from a file"
4. Paste the JSON data into the text box and accept
5. Enter the required variables (Sentinel LA Workspace name, and region)
6. After installation, navigate to Sentinel Data Connectors
7. Open the Action1 data connector, enter the stub URL for the region of your instance, and enter the Client ID and Client Secret of an API Credentials user who holds the Enterprise Viewer role.




# Future planned updates:

- Threat model, use cases, and detections.
- Additional data connector to ingest automation activity (audit logs appear to be human activity only)
- SOAR automations to isolate resources or users on high-confidence security detection
- MCP server and skills/agent definition for semi-autonomous patch and vulnerability management


# Disclaimer

This is an independent, community-developed project. I am not affiliated with, endorsed by, or representing Action1 or Microsoft.
The project is provided free of charge and “as is,” without warranty or guaranteed support. I built it as a self-directed security engineering project and have made it available for anyone who may find it useful.
If it works for you, that makes me happy. If it doesn’t, I’d genuinely appreciate hearing about the problem so I can learn from it and, where possible, work toward a fix.
# Azure-Sentinel-Workspace-Creation-Visualizing-Network-Activity

We are creating a workspace using all the logs generated within our environment—including those originating from potential malicious actors on the internet. This workspace will be used to develop world map visualization workbooks that display network activity based on the originating IP addresses. The goal is to provide a clear, geographic visualization of what is happening across the network for various security and monitoring scenarios, including:

Entra ID (Azure) Authentication Success – Monitor normal access patterns.

https://github.com/joshmadakor1/lognpacific-public/blob/main/cyber-range/sentinel/Directory-Login-Successes.json

Entra ID (Azure) Authentication Failures – Detect potential credential misuse.

https://github.com/joshmadakor1/lognpacific-public/blob/main/cyber-range/sentinel/Directory-Login-Failures.json

Azure Resource Creation – Track new resource provisioning and identify unauthorized changes.

https://github.com/joshmadakor1/lognpacific-public/blob/main/cyber-range/sentinel/Azure-Resource-Creation.json

VM Authentication Failures – Highlight failed virtual machine logins that may indicate compromise attempts.

https://github.com/joshmadakor1/lognpacific-public/blob/main/cyber-range/sentinel/VM-Authentication-Failures.json

Malicious Traffic Entering the Network – Visualize incoming traffic flagged as potentially malicious to identify attack sources.

https://github.com/joshmadakor1/lognpacific-public/blob/main/cyber-range/sentinel/Allowed-Inbound-Malicious-Flows.json


This approach ensures comprehensive visibility into both routine and suspicious network activity, supporting proactive security monitoring and enhanced situational awareness across the environment.

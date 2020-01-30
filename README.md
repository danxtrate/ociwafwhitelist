# OCI WAF CIDR whitelisting

To secure your WAF, you must configure your servers to accept traffic from the WAF servers. Configure your origin's ingress rules to only accept connections from cca 50 CIDR ranges. This can take a lot of time to do manually and cannot be reused. Using OCI CLI and the attached JSON file you can do that in seconds. 

## Prerequisites:

1. Install and configure OCI CLI as per [this guide] (https://docs.cloud.oracle.com/en-us/iaas/Content/API/SDKDocs/cliinstall.htm)

2. Create the VCN where the public facing endpoints will be connected (i.e. external LBaaS, web server). 

3. Make a note of the compartment and VCN OCIDs

4. Download the JSON file

5. Open the JSON file with a preferred editor (Atom, Notepad++, Visual Studio Code) and change the following:
 - "compartmentId": "compartment OCID you noted at step 3"
 - "vcnId": "VCN OCID you noted at step 3"
 - Take a look at the [OCI WAF CIDR whitelist page] (https://docs.cloud.oracle.com/en-us/iaas/Content/WAF/Concepts/gettingstarted.htm) and compare with the CIDR blocks in the JSON file and make adjustments if needed. 

6. Save the file 

7. start the OCI CLI in the same folder you stored your JSON file, deploy the changes by issuing the following command:
```
$ oci network security-list create --from-json file://<filename>.json
```

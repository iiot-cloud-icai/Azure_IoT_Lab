# Deploy a cloud to device messaging app


In this lab you will deploy a container to an Azure Container instance that allows for cloud to device messaging. 

# Get the Azure IoT Hub service key

You need to collect the Azure IoT Hub service keys, so you can provide it to the APP in the next step. This way, it can connect to your Azure IoT hub instance API securely. 

![Lab diagram](../images/cloud_to_device_1.jpg "Header Image")

# Deploy the Azure Container instance template 

Click in the blue icon below

[![Deploy To Azure](https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/1-CONTRIBUTION-GUIDE/images/deploytoazure.svg?sanitize=true)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FSeryioGonzalez%2FAzure_IoT_Lab%2Fmaster%2Fcloud-to-device-app%2Faci_template.json) 

During deployment, the next image will show up.
You need to provide a unique name to your container instance and paste the key you collected in the previous point in the parameter IOT_HUB_CONNECTION_STRING

![Lab diagram](../images/customDeployment.png "Header Image")

It may take a few minutes to deploy. Once deployed, go to resource and collect the hostname of YOUR resulting application, as shown as an example in the FQDN field in the following image:

![Lab diagram](../images/fqdn.png "Header Image")


# Configure the Azure Container instance template 

In the provided python script on `cloud-to-device-app/3_send_request.py`, you will need to update the parameters in the code where you define the hostname of your container application in the variable CONTAINER_HOSTNAME with the previously obtained FQDN, and the DEVICE_NAME with the name of the device you created in the IoT Hub, as shown in the following snippet.

![Lab diagram](../images/pythoncloudtodevice.png "Header Image")

To see the message sent by the `3_send_request.py` script, run the script you used in Module 6 to see the messages sent manually from Azure. 

You have a sample piece of logic you can now integrate in your application code for sending cloud to device messages

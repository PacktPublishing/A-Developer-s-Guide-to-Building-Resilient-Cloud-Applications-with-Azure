

# Create a Service Fabric cluster using Azure CLI
To create a new cluster:
``` shell
az sf cluster create -g packtrg -c hospitalmanagement -l estus --cluster-size 5 --vm-password Password#1234 --certificate-output-folder MyCertificates --certificate-subject-name hospitalmanagement
```
We can Use a keyvault certificate and custom template to deploy a cluster as below:
```shell
az sf cluster create -g packtrg  -c hospitalmanagement -l estus--template-file template.json \
    --parameter-file parameter.json --secret-identifier https://{KeyVault}.vault.azure.net:443/secrets/{MyCertificate}
```
And to create a new Azure Service Fabric cluster, we can use one or more properties mentioned below: 
```shell
az sf cluster create --resource-group
                     [--cert-out-folder]
                     [--cert-subject-name]
                     [--certificate-file]
                     [--certificate-password]
                     [--cluster-name]
                     [--cluster-size]
                     [--location]
                     [--os {UbuntuServer1604, WindowsServer1709, WindowsServer1709withContainers, WindowsServer1803withContainers, WindowsServer1809withContainers, WindowsServer2012R2Datacenter, WindowsServer2016Datacenter, WindowsServer2016DatacenterwithContainers, WindowsServer2019Datacenter, WindowsServer2019DatacenterwithContainers}]
                     [--parameter-file]
                     [--secret-identifier]
                     [--template-file]
                     [--vault-name]
                     [--vault-rg]
                     [--vm-password]
                     [--vm-sku]
                     [--vm-user-name]
```
Even created, you can list the list of cluster resources using this command Line or just check Azure Portal:
``` shell
az sf cluster list [--resource-group]
```
After cluster creation, sometimes we need to scale it, in the next section we will learn how to scale an Azure Service Fabric Cluster.

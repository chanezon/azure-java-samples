Docker support in Azure was announced a few days ago http://msopentech.com/blog/2014/06/09/docker-on-microsoft-azure/. Right now, in order to use it you need to install azure cli from dev tree https://github.com/Azure/azure-sdk-tools-xplat/tree/dev

Then as explained in https://github.com/MSOpenTech/azure-sdk-tools-xplat/issues/1 the cli new feature requires the Ubuntu image you use to have waagent 2.0.5 so you have to use http://jlmpublishing.blob.core.windows.net/vhd-store/umcemmew.zbl201406032125500609.vhd as a base image for your vm.

Here are the commands to create your first vm for docker in Azure. In a few days you won't need that hack, but I thought it may be useful for some of you, to make it easier to get started with Docker on Azure now. I added ssh option, and an endpoint, which makes it easier to debug.

```shell
azure vm disk upload --verbose http://jlmpublishing.blob.core.windows.net/vhd-store/umcemmew.zbl201406032125500609.vhd http://<yourstorage>.blob.core.windows.net/vhd-store/docker-vm.vhd <your-storage-key>
azure vm image create --os linux --blob-url http://<yourstorage>.blob.core.windows.net/vhd-store/docker-vm.vhd <your-docker-img-name> 
azure vm docker create -l "West US" --ssh --ssh-cert ~/<path-to-your-pem-file> <your-vm-name> <your-docker-img-name> user passwd
azure vm endpoint create <your-vm-name> 22 22
docker --tls -H tcp://<your-vm-name>.cloudapp.net:4243 run ubuntu echo hello world
```

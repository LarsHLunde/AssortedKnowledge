# OCI cheatsheet

## Install OCI cli
### Install OCI
```sudo pip3 install oci-cli```  
### Set up OCI cli
```oci setup config```  


## Managing buckets
### Upload to bucket
```oci os object put --file myfile.7z --namespace frrluwdwvspm --bucket-name vm-backup```
### Download from bucket
```oci os object get --file myfile.7z --name myfile.7z --namespace frrluwdwvspm --bucket-name vm-backup```
### Delete from bucket
```oci os object delete --file myfile.7z --namespace frrluwdwvspm --bucket-name vm-backup```

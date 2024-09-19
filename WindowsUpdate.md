# Windows Update and troubleshooting
## Intro
This article is based on an experience I had with a customer,  
where the AVD machines struggled with a windows update.  
These are the steps we ultimately had to take to get the updates installed.

## Warning, do not check for updates!  
Something we discovered while checking for updates was that this button:  
![image](https://github.com/user-attachments/assets/355cf283-5b60-41fd-a572-2f3840bcbac0)  
Will not just check for updates, but will also update, and later reboot the machine,  
if you do not want that to happen, do not push the button.  

## Checking for updates
On some environments, the computer does not have internet access by design,  
when you are ready to update click the button, if no updates are shown,  
you will have to do an offline update, which leads me to the next section:  

## Offline updates
Microsoft has kindly supplied us with a mirror for the updates called:  
[Microsoft Upgrade Catalog](https://www.catalog.update.microsoft.com/Home.aspx)  
![image](https://github.com/user-attachments/assets/2d862ad8-3857-49d9-ade5-4285f7f0a732)  
Where you will search for Windows Cumulative Update.  
You'll get a rather long list, so you may want to search for the operating system you need to update,  
like "Windows Server 2019 Cumulative Update".  
![image](https://github.com/user-attachments/assets/8f29b637-b538-4d99-b918-4f7c6e2c1fbd)  
Make sure it shows the right year, month and CPU architecture (x64).  
  
Of special note is the fact that the patches are cumulative,  
meaning they are **NOT** dependent on previous patches, and you could in theory patch a completely fresh system.  

## Checking that the update was successful
It is surprisingly common that updates through the update manager fail, hang or just don't complete without telling you.  
To check that an update actually went through, go to Settings -> Windows Update -> Update History.  

![image](https://github.com/user-attachments/assets/5b959f43-44f7-4d77-b7d0-6140eecb90ff)
If the update you installed is not listed, first try to manually update the inventory,  
by pausing updates for a week and then unpausing updates, then checking again:  
![image](https://github.com/user-attachments/assets/537ae498-5870-4090-b42c-f4a814319f39)
![image](https://github.com/user-attachments/assets/7f31bdf7-f39d-43ab-b0a6-bd5c1dc3953c)
If the update is still not installed, please install the offline version,  
then do the same procedure of pausing and unpausing updates to update the catalog.  

Once the update shows up in the history, you will know the update installed successfully.  
![image](https://github.com/user-attachments/assets/875fcf53-b43a-403d-8a50-8222210fa33b)







# How to reset the root password on Linux
## Intro
Sometimes you or a customer lose your root password for a machine,  
or in some cases, a machine can even be held hostage by an employee.  
  
What's important to note, is that you can't (without bruteforcing),  
and you can extract the password hash, and you can change the password,  
but it is impossible to recover the password.   
  
Although this has many nefarious uses it's also a very important tool  
to carry in your toolbelt as you become more skilled in IT.  

## The procedure
In this example, I will be using an Oracle Linux 8 VM,  
but the article it is based on uses Debian 10, and I've tested both.  
  
Once you've rebooted the machine, make sure to move the cursor  
when you get to the boot screen or it will start the machine automatically:  
  
![image](https://github.com/user-attachments/assets/d60208ce-eaa3-4da5-b2ec-52378de7790b)  
  
Once on this menu, mark the first option in the list and press the ```e``` button.  
  
The menu should look like this, and move your cursor to the end of the line that stats with ```linux```.  
  
![image](https://github.com/user-attachments/assets/8857eff0-16d9-4cc8-aaa4-34a642df4b9c)  
  
Then append ```init=/bin/bash``` to the end of the line.  
If you are on a Norwegian keyboard and working in some kind of hypervisor,  
the ```=``` is the button on the left of the backspace on your keyboard,  
and the ```/``` is the one to the left of the right shift key, where ```-``` would usually be.  
  
It should look like this:  
  
![image](https://github.com/user-attachments/assets/8541366f-f016-4217-bb8e-3b78d6cd4b21)  
  
Then press ```Ctrl+x``` to boot in to the system and look like this:  
  
![image](https://github.com/user-attachments/assets/3de7ac22-2f46-4669-bc28-63bee3c5b6b0)  
  
Due to logging in this odd manner, the operating system will be in read only mode,  
so we need to remount the root partition with read/write.  
  
In the prompt, enter ```mount -n -o remount,rw /``` and press enter:  
  
![image](https://github.com/user-attachments/assets/87dc17cc-3b2c-4960-879c-0ec6ca198c97)  

From here you just update the password with ```passwd``` like normal:  
  
![image](https://github.com/user-attachments/assets/84e9a94a-9872-4e35-8d1a-40704919ed1e)  
  
Last step is to reboot the computer, wether through menu or by sending a ```Ctrl+Alt+Del```,  
and you will have reset your password.  

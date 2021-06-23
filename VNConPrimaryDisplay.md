# How to get a VNC connection on your primary screen

Install tigervnc-scraping-server and screen  
```sudo apt-get install sceen tigervnc-scraping-server```  

Create a vnc config directory  
```mkdir -p /.vnc```  

Create a vncpasswd file  
```vncpasswd```  

Start the server in a screen  
```screen x0vncserver -passwordfile ~/.vnc/passwd -display :0```

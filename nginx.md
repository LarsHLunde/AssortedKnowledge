# Some general notes and cheatsheet for nginx

## General knowledge

Main config file:  
```/etc/nginx/nginx.conf```
  
Main site config file:  
```/etc/nginx/sites-enabled/default```  

After any change in config, restart the service:  
```sudo service nginx restart```

  
## Reverse proxy configuration
```  
        location / {
                proxy_pass http://127.0.0.1:3000;
        }
```  
  
or you can do one that's not in the root  
  
```  
        location /files/ {
                rewrite ^/files(.*) $1 break;
                proxy_pass http://127.0.0.1:3000;
        }
```

## Password protection
Setting up very basic file-based password protection is very easy.
Replace MyUser with an apropriate username:  
```sudo sh -c "echo -n 'MyUser:' >> /etc/nginx/.htpasswd"```  
  
Then add a password for the user:  
```sudo sh -c "openssl passwd -apr1 >> /etc/nginx/.htpasswd"```
  
Repeat procedure for as many users as you want, they will all be valid,  
to remove a user, just remove their line from the file.  
  
Then add it to your site configuration:  
```  
        location / {
                try_files $uri $uri/ =404;
                auth_basic "Restricted Content";
                auth_basic_user_file /etc/nginx/.htpasswd;
        }
```  

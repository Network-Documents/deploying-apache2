# deploying-apache2
ابتدا apache2 رو نصب میکنیم   
```
apt update && apt install apache2 
```   
برای بررسی عملکرد کار وب سرور باید ابزار curl رو نصب کرد   
```
apt install curl 
```   
 سپس دایرکتوری به اسم 
   
 domain    
  
  مورد نظر میسازیم   
  
  ``` 
	 mkdir /var/www/skill
  ```

سپس فایل html مورد نظر رو   میسازیم   
      
```
nano /var/www/your_domain/index.html  
```

```
‫<html>
    <head>
        <title>Welcome to skill</title>
    </head>
    <body>
        <h1> The WELCOME‬‬ TO‬‬ SKILLS ‬‬‫‪WORLD‬‬ 
</h1>
</body>
</html>
```
برای
domain
مورد نظر فایل کانفیگ ست میکنیم 
``` 
nano /etc/apache2/sites-available/skill.conf
```

سپس موارد زیر را در آن مینویسیم (کیس سنستیو است)
```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName skill
    ServerAlias www.skill
    DocumentRoot /var/www/skill
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```
سپس فایل کانفیگ رو فعال میکنیم 
``` 
 a2ensite skill.conf
```
و بعد از ان سرویس 
apache2 
رو ری استارت میکنیم 
```
systemctl reload apache2   

```

 سپس در فایل زی
 domain
 را وارد میکنیم  
 
 ``` 
 nano /etc/hosts
 ```
 
 >127.0.0.1 localhost   skill
 
سپس با استفاده از کامند زیر میتوان محتوای بالا امده روی وب سرور رو دریافت کرد 
```  
 curl skill
```

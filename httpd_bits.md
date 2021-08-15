## HTTPD Config Snippets

### Redirecting to https
The easiest method to redirect to https would be to use the Redirect directive from mod_alias like in the following example:

Redirect permanent / https://sandbox.com

### If you want you can do https redirection from .htaccess files
>RewriteEngine On  
RewriteCond %{HTTPS} on  
RewriteCond %{HTTP:X-Forwarded-Proto} !https  
RewriteRule ^ https://%{HTTP_HOST}%{REQUEST_URI} [NE,L,R]


### With wordpress you will find there is a .htaccess with the following config

><IfModule mod_rewrite.c>  
RewriteEngine On  
RewriteBase /  
RewriteRule ^index\.php$ - [L]  
RewriteCond %{REQUEST_FILENAME} !-f  
RewriteCond %{REQUEST_FILENAME} !-d  
RewriteRule . /index.php [L]  
</IfModule>  




# NGINX configuration on Ubuntu
- First install NGINX

      apt install nginx
- Now install ssl certs

      apt install ssl-cert
- Go to folder where the configuration is

      cd /etc/nginx/snippets/
- Copy the file `snakeoil.conf` and change to another name

      cp snakeoil.conf NAME.conf
- Edit the configuration and inside change your `certificates`

      nano NAME.conf
- Go to folder `sites-available`
      
      cd ../sites-available/
- Copy the file to another name

      cp default SAFE
- Edit SAFE

      nano SAFE
- Inside	
  
      delete this lines :80
	    uncomment this lines :443
	    uncomment include snippets/snakeoil.conf;
	    change snakeoil.conf to NAME.conf
	    change root to htmls
- Go to folder where its your WEB page

      cd /var/www/
- Duplicate the folder

      cp -r html/ htmls
- Enter in one folder `insecure` first

      cd html/
- Use `>` to remove everything that is inside

      > index.nginx-debian.html
- Edit the file to what you want

      nano index.nginx-debian.html (you are changing :80)
- Now go to htmls `secure`
      
      cd htmls/
- Do the same to remove everything

      > index.nginx-debian.html
- Edit

      nano index.nginx-debian.html (You are changing :443)
- Go to `sites-enable`

      cd /etc/nginx/sites-enabled/
- Create a save launch

      ln -s /etc/nginx/sites-available/SAFE SAFE
- Restart and see status form NGINX
      
      systemctl restart nginx
      systemctl status nginx
Now just open your browser and add `http://your.public.ip` to see insecure and `https://your.public.ip` to see secure     

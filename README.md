# node-ufw-certbot-pm2-nginx
Despliegue de aplicacion backend
Hilo de comandos:

#Instalar nvm 
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.4/install.sh | bash
source ~/.bashrc
```
#Instalar node
```
nvm install node
cd books-express
```
#Iniciando el servidor
```
npm install
npm start
```

#Configurando pm2
npm install pm2 -g
pm2 start src/app.js --name myapp
pm2 startup
pm2 save

#Configurando el firewall
sudo ufw enable
sudo ufw allow ssh
sudo ufw allow http
sudo ufw allow https
sudo ufw reload

#Configurando NGINX
sudo cp nginxconf /etc/nginx/sites-available/nginxconf
nginx -t
sudo ln -s /etc/nginx/sites-available/nginxconf /etc/nginx/sites-enabled/nginxconf
nginx -t
sudo service nginx restart

#SSL con lets encrypt
sudo snap install --classic certbot
sudo ln -s /snap/bin/certbot /usr/bin/certbot
sudo certbot --nginx -d tu.dominio -d www.tu.dominio
certobot renew --dry-run


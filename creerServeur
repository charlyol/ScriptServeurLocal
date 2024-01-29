echo "server { \n listen 80; \n server_name $1.local;\n index public/index.php;\n root /var/www/$1;\n location ~\.php$ { \n include snippets/fastcgi-php.conf;\n fastcgi_pass unix:/var/run/php/php8.3-fpm.sock;\n}}" >> /etc/nginx/sites-available/$1.local;
mkdir /var/www/$1;
mkdir /var/www/$1/public;
echo "<?php \n echo 'serveur mis en place' \n ?> \n <h1>Test</h1>" >> /var/www/$1/public/index.php;

echo "127.0.0.1		$1.local" >> /etc/hosts;

ln -s /etc/nginx/sites-available/$1.local /etc/nginx/sites-enabled/;
service apache2 stop;
service nginx reload;

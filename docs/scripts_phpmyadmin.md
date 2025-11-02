Scripts Bash (automatización)

- .env (NO subir a repo) DOMAIN=mi-dominio.local MYSQL\_ROOT\_PASS=TU\_PASS\_ROOT PMA\_DB\_USER=pma\_user PMA\_DB\_PASS=PMA\_PASS\_SEGURA PHP\_VERSION=8.1
- install\_lemp.sh #!/usr/bin/env bash set -euo pipefail
- Cargar variables source ./scripts/.env

  echo "Instalando LEMP básico..." sudo apt update

  sudo apt upgrade -y

  sudo apt install -y nginx mysql-server php${PHP\_VERSION}-fpm \

  `    `php${PHP\_VERSION}-mbstring php${PHP\_VERSION}-zip php${PHP\_VERSION}-gd php$ {PHP\_VERSION}-json php${PHP\_VERSION}-curl unzip wget git apache2-utils

- Asegurar MySQL root (no interactivo: usar expect sería otra opción).
- Aquí sólo mostramos cómo hacerlo vía mysql -e

sudo mysql -e "ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql\_native\_password BY '${MYSQL\_ROOT\_PASS}'; FLUSH PRIVILEGES;"

sudo systemctl enable --now nginx

sudo systemctl enable --now mysql

sudo systemctl enable --now php${PHP\_VERSION}-fpm

echo "LEMP instalado."

Una vez hecho le damos permisos.

- install\_phpmyadmin.sh

#!/usr/bin/env bash set -euo pipefail

source ./scripts/.env PHP\_VERSION=${PHP\_VERSION:-8.1}

echo "Descargando phpMyAdmin..."

- Version estable (ajustar si quieres versión específica)

PMA\_VER="5.2.1"  # ejemplo; para producción verifica la última versión oficial

wget https://www.phpmyadmin.net/downloads/phpMyAdmin-${PMA\_VER}-all-languages.zip -O /tmp/phpmyadmin.zip

unzip /tmp/phpmyadmin.zip -d /tmp

sudo mv /tmp/phpMyAdmin-${PMA\_VER}-all-languages /usr/share/phpmyadmin

sudo mkdir -p /usr/share/phpmyadmin/tmp

sudo chown -R www-data:www-data /usr/share/phpmyadmin

sudo chmod 750 /usr/share/phpmyadmin

- Crear configuración mínima

sudo cp /usr/share/phpmyadmin/config.sample.inc.php /usr/share/phpmyadmin/config.inc.php

- Generar blowfish secret

BLOWFISH\_SECRET=$(openssl rand -hex 32)

sudo sed -i "s|\$cfg\['blowfish\_secret'\] = ''|\$cfg['blowfish\_secret'] = '$ {BLOWFISH\_SECRET}';|" /usr/share/phpmyadmin/config.inc.php

- Crear usuario pma\_user en MySQL

sudo mysql -e "CREATE USER IF NOT EXISTS '${PMA\_DB\_USER}'@'localhost' IDENTIFIED BY '${PMA\_DB\_PASS}'; GRANT ALL PRIVILEGES ON \*.\* TO '$ {PMA\_DB\_USER}'@'localhost' WITH GRANT OPTION; FLUSH PRIVILEGES;"

- Configurar nginx site (archivo /etc/nginx/sites-available/phpmyadmin). Reemplaza DOMAIN por variable o IP

  sudo tee /etc/nginx/sites-available/phpmyadmin > /dev/null <<EOF

  server {

  `    `listen 80;

  `    `server\_name ${DOMAIN};

  `    `root /usr/share/phpmyadmin;     index index.php index.html;

  `    `location / {

  `        `try\_files \$uri \$uri/ =404;     }

  `    `location ~ \.php$ {

  `        `include snippets/fastcgi-php.conf;

  `        `fastcgi\_pass unix:/run/php/php${PHP\_VERSION}-fpm.sock;     }

  `    `location /phpmyadmin {

  `        `alias /usr/share/phpmyadmin/;

  `        `index index.php index.html;

  `        `auth\_basic "Restricted - phpMyAdmin";

  `        `auth\_basic\_user\_file /etc/nginx/.htpasswd\_phpmyadmin;     }

  }

  EOF

  sudo ln -sf /etc/nginx/sites-available/phpmyadmin /etc/nginx/sites-enabled/phpmyadmin sudo nginx -t

  sudo systemctl reload nginx

  echo "phpMyAdmin instalado y configurado en /usr/share/phpmyadmin"

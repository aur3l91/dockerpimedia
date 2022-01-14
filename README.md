# Installation Docker Compose pour Pi-Média

### Pré-requis :

    apt-get update && apt-get dist-upgrade
    apt-get install git-core

### Installations :
    cd /home/aurelien
    git clone https://github.com/aur3l91/dockerpimedia.git
    cd dockerpimedia
    docker-compose up -d`

### Création Proxy pour ruTorrent

    docker run -it --name web -p 1802:80 -p 1305:443 --link vpn:rutorrent --network aurelien_default \
    -d dperson/nginx -w "http://home.aur3lex.fr:1401;/"

# Installation Docker Compose pour Pi-Média

### Pré-requis :

    apt-get update && apt-get dist-upgrade
    apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release \
    sudo \
    git-core \
    wget
    
### Installer Docker :    

    sudo mkdir -p /etc/apt/keyrings
    curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
    
    echo \
    "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
    $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
   
### Installer Docker-Compose : 

    curl -s https://api.github.com/repos/docker/compose/releases/latest | grep browser_download_url  | grep docker-compose-linux-x86_64 | cut -d '"' -f 4 | wget -qi -
    chmod +x docker-compose-linux-x86_64
    sudo mv docker-compose-linux-x86_64 /usr/local/bin/docker-compose

### Installations :
    cd /home/aurelien
    git clone https://github.com/aur3l91/dockerpimedia.git
    cd dockerpimedia
    docker-compose up -d`

### Création Proxy pour ruTorrent

    docker run -it --name web -p 1802:80 -p 1305:443 --link vpn:rutorrent --network aurelien_default \
    -d dperson/nginx -w "http://home.aur3lex.fr:1401;/"

# VPN_Serveur
Déploiement d’un serveur VPN sécurisé avec OpenVPN sur Debian 12, incluant la génération de certificats et la configuration client.
## Serveur VPN avec OpenVPN sur Debian 12
📋 Description
## Ce projet présente la mise en place d’un serveur VPN sécurisé sous Debian 12 à l’aide d’OpenVPN. Il comprend :

La configuration du serveur VPN.

La génération des certificats avec Easy-RSA.

La création des profils clients.

La connexion d’un client à distance au réseau privé.

Ce système permet d'assurer un accès distant sécurisé et chiffré à une infrastructure interne.

## ⚙️ Technologies utilisées
Debian 12

OpenVPN 2.6.x

Easy-RSA 3

Net-tools / IP utils

## 🚀 Installation
1. Installation des paquets nécessaires
bash
sudo apt update
sudo apt install openvpn easy-rsa net-tools -y
## 2. Initialisation de la PKI
bash
make-cadir ~/easy-rsa
cd ~/easy-rsa
./easyrsa init-pki
./easyrsa build-ca
./easyrsa gen-req server nopass
./easyrsa sign-req server server
./easyrsa gen-dh
openvpn --genkey --secret ta.key
## 3. Initialisation de la PKI
bash
make-cadir ~/easy-rsa
cd ~/easy-rsa
./easyrsa init-pki
./easyrsa build-ca
./easyrsa gen-req server nopass
./easyrsa sign-req server server
./easyrsa gen-dh
openvpn --genkey --secret ta.key

## 4. Configuration du serveur
Le fichier de configuration server.conf se trouve dans le répertoire config/server/. Il doit être copié dans /etc/openvpn/.

## 5. Création des clients
bash
./easyrsa gen-req client1 nopass
./easyrsa sign-req client client1
Les fichiers .ovpn sont générés dans client-configs/files/.

## 🔐 Sécurité
Utilisation de TLS pour la sécurisation du canal.

Clé statique ta.key pour éviter les attaques DoS.

Certificats valides générés localement.

📦 Structure du projet
vpn-project/
├── server.conf
├── easy-rsa/
│   └── pki/
├── client-configs/
│   └── files/
└── README.md

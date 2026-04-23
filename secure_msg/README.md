
•Installation

1. Assurez-vous d'avoir Python 3.10+ installé.
2. Installez la bibliothèque de cryptographie :
   bash
   pip install cryptography
   

* Exemples CLI

1. Génération des clés
Génère les fichiers private.pem et public.pem :
bash
python3 main.py --action keygen


2. Chiffrement et Envoi
Chiffre un message et l'enregistre dans un paquet JSON :
bash
python3 main.py --action send --msg "Mon message secret" > msg.json


3. Déchiffrement et Réception
Vérifie la signature et déchiffre le message :
bash
python3 main.py --action receive --packet msg.json


 -Justifications

-AES-256-GCM: Choisi pour sa rapidité et son mode "Authentifié" qui détecte toute modification du texte chiffré sans avoir besoin d'un HMAC supplémentaire.
-RSA-2048 (OAEP) : Utilisé pour chiffrer la clé AES. Le padding OAEP est utilisé car il protège contre les attaques par répétition et les vulnérabilités du padding PKCS#1 v1.5.
-RSA-PSS : Utilisé pour la signature numérique. C'est le standard le plus robuste pour garantir l'authenticité et l'intégrité du message.
-Approche Hybride : Permet de combiner la sécurité de l'asymétrique (pas de partage de secret préalable) avec la performance du symétrique (chiffrement rapide de gros volumes de données).
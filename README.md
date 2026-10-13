Git & Portfolio
Ici on a créée un portfolio en HTML & CSS et on l'a push sur Github.

Comment push un projet en local sur Github ?
Etape 1 : Installer Git sur sa machine
sudo apt-get update
sudo apt install git
Avec ces 2 commandes, on installe git sur notre machine. On le fait une fois pour toutes.

Etape 2 : Initialiser le projet git
On se localise sur le projet qu'on veut envoyer sur github, puis

git init
Cette commande va initialiser un projet git

Etape 3 : On commit (sauvegarde) notre projet
git add . # Ca va selectionner l'entiereté du dossier où on est
git commit -m "Premier commit !" # Ca va commit (sauvegarder) tout les éléments qu'on a add (séléctionner)
Etape 4 : On créer le repository distant sur Github
Dans Github, on va dans -> Repository -> New Repository -> On met le nom du repository et on le créer Ensuite, on recopie le lien ssh du repository

Etape 5 : On génère une clé SSH sur notre machine local
Une clé ssh sert à prouver son identité. On va s'en servir pour s'authentifier à Github car c'est un serveur distant.

Generating public/private rsa key pair.
Enter file in which to save the key (/home/imed/.ssh/id_rsa): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/imed/.ssh/id_rsa
Your public key has been saved in /home/imed/.ssh/id_rsa.pub
The key fingerprint is:
SHA256:... imed@imed-virtual-machine
The key's randomart image is:
+---[RSA 3072]----+
|          ..
...
+----[SHA256]-----+
La clé a été enregistré dans /home/imed/.ssh. Ensuite on va récupérer le contenu de notre clé publique :

cd ~
cd .ssh
cat id_rsa.pub
On recopie le contenu de la clé publique. Une fois recopié on va la définir dans notre compte Github sur github.com. Sur github : Tout en haut à droite on clique sur notre photo de profil -> Settings -> SSH and GPG keys -> New SSH keys alt text Pour le titre on nomme notre clé comme on veut genre "clé machine ubuntu" et dans Key on colle le contenu de notre clé publique (ca commence par ssh-rsa ... et ca se termine par le nom de votre machine). Puis on clique sur Add SSH key. alt text

Etape 6 : On met en lien notre projet git local avec notre serveur distant git via le lien ssh
Sur github, on va sur notre repository qu'on a créée à l'étape 4, puis on recopie le lien ssh alt text

Puis sur notre terminal on fait :

git remote add origin le_lien_ssh_de_votre_repo_github
Etape 7 : On push
La premiere fois que vous pushez sur ce repository github il faut faire :

git push --set-upstream origin master
Sinon le reste du temps :

git push
git config --global user.email "you@example.com" git config --global user.name "Your Name"

# Chrome OS // Initialisation du conteneur 'penguin'

## Auteur

### Kevin Doolaeghe

## Configuration initiale du conteneur

* Mettre à jour le conteneur :
```
sudo apt update
sudo apt upgrade
```

* Trouver l'utilisateur non-root créé pour le conteneur :
```
grep 1000:1000 /etc/passwd|cut -d':' -f1
```

* Donner à l'utilisateur un mot de passe et les permissions super-utilisateur :
```
passwd <username>
usermod -aG sudo <username>
```

* Se connecter avec le compte de l'utilisateur non-root :
```
su - <username>
```

## Configuration de base du conteneur `penguin`

* Mettre à jour le conteneur :
```
sudo apt update
sudo apt upgrade
```

* Modifier le fichier `/etc/apt/sources.list` :
```
sudo apt install software-properties-common
sudo add-apt-repository contrib
sudo add-apt-repository non-free
sudo apt update
```

* Installer les paquets de base :
```
sudo apt install nano build-essential net-tools git make
```

* Créer un lien symbolique vers `/` dans le dossier utilisateur :
```
sudo ln -s / ~/root
```

* Modifier le mot de passe `root` :
```
sudo passwd root
```

* Modifier les paramètres du shell :
```
nano ~/.bashrc
```

* Installer `vscode` :
```
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > packages.microsoft.gpg
sudo install -o root -g root -m 644 packages.microsoft.gpg /etc/apt/trusted.gpg.d/
sudo sh -c 'echo "deb [arch=amd64,arm64,armhf signed-by=/etc/apt/trusted.gpg.d/packages.microsoft.gpg] https://packages.microsoft.com/repos/code stable main" > /etc/apt/sources.list.d/vscode.list'
rm -f packages.microsoft.gpg
```

```
sudo apt install apt-transport-https
sudo apt update
sudo apt install code
```

* Ouvrir les fichiers avec Visual Studio Code par défaut :
```
sudo update-alternatives --set editor /usr/bin/code
```

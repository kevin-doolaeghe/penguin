# Chrome OS | Initialisation du conteneur `penguin`

## Auteur

### Kevin Doolaeghe

## Configuration de base du conteneur `penguin`

* Mettre à jour le conteneur :
```
sudo apt update
sudo apt upgrade
```

* Ajouter les sources `contrib` et `non-free` pour les dépôts :
```
sudo apt install software-properties-common
sudo add-apt-repository contrib
sudo add-apt-repository non-free
sudo apt update
```
Il est également possible de modifier le fichier `/etc/apt/sources.list` puis d'ajouter manuellement les paramètres `contrib` et `non-free`.

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

## Installer Visual Studio Code :

* Ajouter les dépendences suffisantes pour l'installation :
```
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > packages.microsoft.gpg
sudo install -o root -g root -m 644 packages.microsoft.gpg /etc/apt/trusted.gpg.d/
sudo sh -c 'echo "deb [arch=amd64,arm64,armhf signed-by=/etc/apt/trusted.gpg.d/packages.microsoft.gpg] https://packages.microsoft.com/repos/code stable main" > /etc/apt/sources.list.d/vscode.list'
rm -f packages.microsoft.gpg
```

* Installer `vscode` :
```
sudo apt install apt-transport-https
sudo apt update
sudo apt install code
```

* Ouvrir les fichiers avec Visual Studio Code par défaut :
```
sudo update-alternatives --set editor /usr/bin/code
```

# Installer Oracle VM VirtualBox :

* Ajouter les dépendances nécessaires à l'installation :
```
deb [arch=amd64] https://download.virtualbox.org/virtualbox/debian <distribution> contrib
```

```
wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -
wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add -
```

* Installer `virtualbox` :
```
sudo apt-get update
sudo apt-get install virtualbox-6.1
```

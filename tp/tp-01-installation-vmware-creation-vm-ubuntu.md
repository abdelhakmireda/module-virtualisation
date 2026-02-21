
---

# 🧪 tp/tp-01-installation-vmware-creation-vm-ubuntu.md

# 🎓 TP 01 — Installation de VMware & Création d’une VM Ubuntu 24

👨‍🏫 Responsable : Reda Abdelhakmi
📚 Module : Virtualisation de Base

---

# 🎯 Objectifs du TP

À la fin de ce TP, l’étudiant sera capable de :

✔ Installer VMware Workstation Pro 17
✔ Comprendre chaque option d’installation
✔ Créer une machine virtuelle Ubuntu 24
✔ Configurer CPU, RAM, Disque et Réseau
✔ Installer complètement Ubuntu dans une VM

---

# 📦 Partie 1 — Préparation des Fichiers

Dans le dossier partagé (Drive), vous trouverez :
https://drive.google.com/drive/folders/1i3EldakRNwHfPqLsQyKngrem1QImjonE?usp=drive_link

* VMware Workstation Pro 17
* Ubuntu 24.xx Desktop (ISO)
* WinRAR

---

## 🔎 Vérification importante

1. Le fichier Ubuntu doit être au format :

   ```
   ubuntu-24.xx-desktop-amd64.iso
   ```
2. ❌ Ne pas extraire le fichier ISO
3. WinRAR sert uniquement si le fichier est compressé (.zip ou .rar)

---

# 🛠️ Partie 2 — Installation de VMware Workstation Pro 17

## Étape 1 : Lancer l’installation

Double-cliquer sur :

```
VMware-workstation-full-17.x.x.exe
```

---

## Étape 2 : Choisir le type d’installation

Deux options apparaissent :

* Typical (Recommandé)
* Custom (Avancé)

👉 Choisir : **Typical**

### ❓ Question TP :

Pourquoi choisit-on Typical dans un environnement académique ?

---

## Étape 3 : Accepter la licence

✔ I accept the terms

---

## Étape 4 : Installation

Cliquer sur Install
Attendre la fin
Redémarrer si demandé

---

# 🐧 Partie 3 — Création d’une Machine Virtuelle Ubuntu 24

---

## Étape 1 : Create a New Virtual Machine

Ouvrir VMware
Cliquer sur :

```
Create a New Virtual Machine
```

Choisir : **Typical**

---

## Étape 2 : Choisir la source d’installation

Sélectionner :

```
Installer disc image file (ISO)
```

Puis parcourir et choisir :

```
ubuntu-24.xx-desktop-amd64.iso
```

VMware détecte automatiquement : Linux → Ubuntu 64-bit

---

## Étape 3 : Informations système invité

Remplir :

* Full Name
* Username
* Password

⚠️ Bien noter le mot de passe.

---

# ⚙️ Partie 4 — Configuration des Ressources

Cette partie est essentielle pour comprendre la virtualisation.

---

## 🧠 1. Configuration CPU

Cliquer sur "Customize Hardware"

Paramètres :

* Number of Processors
* Number of Cores per Processor

👉 Recommandation :

* 1 Processor
* 2 ou 4 Cores

### ❓ Questions TP :

1. Pourquoi ne doit-on pas allouer tous les cœurs ?
2. Quelle est la différence entre Processor et Core ?

---

## 🧮 2. Configuration RAM

Recommandation Ubuntu 24 :

* Minimum : 2 GB
* Recommandé : 4 GB

Si votre machine possède 16 GB :

👉 Allouer 4 GB

### ❓ Question TP :

Que se passe-t-il si vous allouez 14 GB sur une machine de 16 GB ?

---

## 💾 3. Configuration Disque

Taille recommandée :

40 GB

Choisir :

✔ Store virtual disk as a single file

### ❓ Question TP :

Pourquoi un SSD améliore-t-il les performances des VM ?

---

## 🌐 4. Configuration Réseau

Choisir :

✔ NAT

### ❓ Question TP :

Quelle différence entre NAT et Bridged ?

---

## 🎮 5. Graphique

✔ Cocher : Accelerate 3D Graphics

---

# 🔄 Partie 5 — Installation Ubuntu 24

Démarrer la VM

Étapes :

1. Try or Install Ubuntu
2. Installation normale
3. Effacer le disque (virtuel uniquement)
4. Créer utilisateur
5. Redémarrage

---

# 🧠 Partie 6 — Analyse Post-Installation

Après installation :

1. Vérifier la RAM :

   ```
   free -h
   ```
2. Vérifier le CPU :

   ```
   lscpu
   ```
3. Vérifier l’adresse IP :

   ```
   ip a
   ```

---

# 📋 Livrables Demandés

Chaque étudiant doit fournir :

✔ Capture écran VMware installé
✔ Capture écran configuration CPU/RAM
✔ Capture écran Ubuntu installé
✔ Réponses aux questions TP

# 🏁 Conclusion du TP

Ce TP permet de comprendre :

* Comment un hyperviseur partage les ressources
* Comment une VM est configurée
* Comment un OS invité s’installe

C’est la base fondamentale avant :

🔐 Snapshots
📦 Clonage
🌐 Réseau avancé
☁️ Infrastructure virtualisée

---


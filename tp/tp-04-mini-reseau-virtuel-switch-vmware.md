-

# 🧪 TP 04 — Mini Réseau Virtuel avec Switch Virtuel VMware

👨‍🏫 Responsable : **Reda Abdelhakmi**
📚 Module : **Virtualisation de Base**
🖥️ Hyperviseur : **VMware Workstation Pro 17**
🐧 OS invité : **Ubuntu 24.xx**

---

# 🎯 Objectifs

À la fin de ce TP, l’étudiant sera capable de :

✔ Comprendre le fonctionnement d’un **switch virtuel**
✔ Créer un **réseau isolé entre plusieurs machines virtuelles**
✔ Configurer les adresses **IP manuellement**
✔ Tester la communication réseau avec **ping**
✔ Simuler un **petit laboratoire réseau**

---

# 📌 Prérequis

Avant de commencer :

✔ VMware Workstation Pro installé
✔ Une VM Ubuntu fonctionnelle
✔ Connaissance des commandes Linux de base
✔ Terminal accessible (**Ctrl + Alt + T**)

---

# 🖧 PARTIE 1 — Comprendre le Switch Virtuel

Dans VMware, un **switch virtuel** permet de connecter plusieurs machines virtuelles.

Il fonctionne **comme un switch réseau physique**.

### Schéma simplifié

```
           Switch Virtuel VMware
                (VMnet1)

        VM1 -----------|
                       |
        VM2 -----------|------ Réseau virtuel
                       |
        VM3 -----------|
```

Les machines virtuelles peuvent communiquer **sans connexion internet**.

---

# 🔧 PARTIE 2 — Création du Réseau Virtuel

Dans VMware :

Menu :

```
Edit → Virtual Network Editor
```

Identifier :

```
VMnet1 → Host-Only
```

Ce réseau sera notre **switch virtuel de laboratoire**.

---

# 🖥️ PARTIE 3 — Création des Machines Virtuelles

Nous allons utiliser **3 machines virtuelles** :

| Machine | Rôle          |
| ------- | ------------- |
| VM1     | Client Linux  |
| VM2     | Client Linux  |
| VM3     | Serveur Linux |

Vous pouvez :

✔ cloner la VM existante
✔ créer plusieurs clones

Nom des VMs :

```
Ubuntu_Client1
Ubuntu_Client2
Ubuntu_Server
```

---

# 🔌 PARTIE 4 — Connecter les VMs au Switch Virtuel

Pour chaque VM :

VM → Settings → Network Adapter

Choisir :

```
Host-Only (VMnet1)
```

Toutes les VMs doivent être sur **le même réseau virtuel**.

---

# 🌐 PARTIE 5 — Configuration IP Manuelle

Dans chaque VM ouvrir le terminal :

```
Ctrl + Alt + T
```

Vérifier interface réseau :

```bash
ip a
```

Interface exemple :

```
ens33
```

---

## Configuration VM1

```bash
sudo ip addr add 192.168.50.10/24 dev ens33
```

---

## Configuration VM2

```bash
sudo ip addr add 192.168.50.11/24 dev ens33
```

---

## Configuration VM3 (Serveur)

```bash
sudo ip addr add 192.168.50.100/24 dev ens33
```

---

# 🧪 PARTIE 6 — Test de Connectivité

Dans **VM1** :

```bash
ping 192.168.50.11
```

Tester le serveur :

```bash
ping 192.168.50.100
```

Résultat attendu :

```
64 bytes from 192.168.50.100
```

---

# 🖧 PARTIE 7 — Visualisation du Réseau

Architecture finale :

```
            Switch Virtuel VMware
                (VMnet1)

     192.168.50.10
      Ubuntu_Client1
            |
            |
     192.168.50.11
      Ubuntu_Client2
            |
            |
     192.168.50.100
       Ubuntu_Server
```

Toutes les machines communiquent **via le switch virtuel**.

---

# 🔐 PARTIE 8 — Introduction au protocole SSH
## 📜 Définition

SSH (Secure Shell) est un protocole réseau qui permet de :

✔ se connecter à distance à une machine
✔ exécuter des commandes à distance
✔ administrer un serveur de manière sécurisée

---

## 🔐 Pourquoi SSH est sécurisé ?

Contrairement à des protocoles anciens (comme Telnet) :

❌ Telnet → données non chiffrées
✔ SSH → données chiffrées

👉 Les informations (mot de passe, commandes) sont protégées contre l’interception.

---

## 🖥️ Fonctionnement de SSH

SSH fonctionne selon le modèle **Client / Serveur** :

* Le **client** (VM1) envoie une demande de connexion
* Le **serveur** (VM3) écoute sur le port 22
* Une connexion sécurisée est établie

---

## ⚙️ Étapes d’une connexion SSH

1️⃣ Le client contacte le serveur
2️⃣ Le serveur envoie sa clé
3️⃣ Le client valide la connexion
4️⃣ L’utilisateur s’authentifie (mot de passe)
5️⃣ Une session distante est ouverte

---

## 🎯 Objectif dans ce TP

Dans ce TP, SSH permet de :

✔ simuler un accès à un serveur distant
✔ comprendre le fonctionnement d’un service réseau
✔ manipuler une architecture client / serveur

---

## 🌍 Importance dans le monde réel

SSH est utilisé dans :

✔ Cloud Computing
✔ Administration système
✔ Cybersécurité
✔ DevOps

👉 Exemple : un administrateur peut gérer un serveur à distance sans accès physique.

---

# 🔐 PARTIE 9 — Simulation d’un Serveur (SSH)

Dans **VM3 (Serveur)** installer SSH :

```bash
sudo apt update
```

```bash
sudo apt install openssh-server
```

Vérifier :

```bash
sudo systemctl status ssh
```

---

# 🧪 Test SSH depuis VM1

Dans **VM1** :

```bash
ssh user@192.168.50.100
```

Si la connexion fonctionne :

```
Welcome to Ubuntu
```

Vous venez de créer **un réseau virtuel avec un serveur**.

---

# ⚖️ Analyse du Laboratoire

Compléter :

| Élément        | Description                      |
| -------------- | -------------------------------- |
| Switch virtuel | Connecte les machines virtuelles |
| Host-Only      | Réseau isolé                     |
| Adresse IP     | Identifie chaque machine         |
| Ping           | Test de connectivité             |

---

# ❓ Questions

1️⃣ Qu’est-ce qu’un **switch virtuel** ?

2️⃣ Pourquoi toutes les VMs doivent être sur **le même VMnet** ?

3️⃣ Quelle commande permet de **tester la connectivité réseau** ?

4️⃣ Pourquoi le mode **Host-Only est utilisé dans les laboratoires** ?

5️⃣ Quel avantage offre un **réseau virtuel pour l’apprentissage** ?

---

# 📋 Livrables

Chaque étudiant doit fournir :

✔ Capture écran **Virtual Network Editor**
✔ Capture écran **configuration IP VM1**
✔ Capture écran **ping entre machines**
✔ Capture écran **architecture réseau**
✔ Capture écran **connexion SSH**

---

# 🎓 Conclusion du TP

Dans ce TP vous avez créé :

✔ un **switch virtuel VMware**
✔ un **réseau isolé entre plusieurs VMs**
✔ un **serveur accessible en SSH**

Ce type de laboratoire est utilisé dans :

☁️ Cloud Computing
🔐 Cybersécurité
🧪 Laboratoires réseaux
🏢 Data Centers

---


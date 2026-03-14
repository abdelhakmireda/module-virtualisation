

# 📘 Séance 05 — Virtualisation du Stockage & du Réseau

👨‍🏫 Responsable : **Reda Abdelhakmi**
📚 Module : **Virtualisation de Base**

---

# 🎯 Objectifs de la séance

À la fin de cette séance, l’étudiant sera capable de :

✔ Comprendre **la virtualisation du stockage**
✔ Comprendre **la virtualisation du réseau**
✔ Différencier **NAT, Bridge et Host-Only**
✔ Comprendre le fonctionnement d’un **switch virtuel**
✔ Savoir comment les **machines virtuelles communiquent**

---

# 🎬 Introduction

Dans les séances précédentes nous avons appris :

✔ Créer une machine virtuelle
✔ Configurer CPU et RAM
✔ Utiliser les snapshots et le clonage

Mais une machine virtuelle doit aussi :

💾 **stocker des données**
🌐 **communiquer avec le réseau**

Pour cela, l’hyperviseur crée :

* un **disque virtuel**
* une **carte réseau virtuelle**

Ces deux éléments permettent à la VM de fonctionner **comme un vrai ordinateur**.

---

# 💾 1️⃣ La Virtualisation du Stockage

## 📜 Définition

La virtualisation du stockage consiste à créer un **disque dur virtuel** pour la machine virtuelle.

En réalité, ce disque est simplement **un fichier sur l’ordinateur hôte**.

Exemple de fichier disque :

```
Ubuntu.vmdk
```

Ce fichier contient :

* le système Linux
* les fichiers utilisateurs
* les logiciels installés

---

# 🔬 Fonctionnement simplifié

Architecture :

```
Machine Physique
      ↓
Hyperviseur (VMware)
      ↓
Fichier disque virtuel (.vmdk)
      ↓
Machine virtuelle
```

Pour la VM :

➡ ce fichier est vu comme **un vrai disque dur**

---

# 🍕 Exemple simple — La Pizza

Imaginez une pizza entière 🍕

La pizza = **disque physique**

Chaque part = **machine virtuelle**

Chaque VM reçoit **sa part du disque**.

---

# 📂 2️⃣ Types de Disques Virtuels

## 📉 Disque Dynamique (Thin Provisioning)

Le disque grandit **selon l'utilisation**.

Exemple :

Disque configuré : **50 GB**

Espace utilisé réel : **10 GB**

Avantages :

✔ économise l’espace disque
✔ flexible

Inconvénient :

⚠ performances légèrement inférieures

---

## 📈 Disque Pré-alloué (Thick Provisioning)

Tout l’espace est réservé **dès la création**.

Exemple :

Disque configuré : **50 GB**

Espace utilisé : **50 GB**

Avantages :

✔ meilleures performances
✔ stabilité

Inconvénient :

❌ consomme beaucoup d’espace disque

---

# 📊 Formats des Disques Virtuels

| Hyperviseur | Format |
| ----------- | ------ |
| VMware      | VMDK   |
| VirtualBox  | VDI    |
| KVM         | QCOW2  |

---

# 🌐 3️⃣ Virtualisation du Réseau

## 📜 Définition

Chaque machine virtuelle possède :

📡 une **carte réseau virtuelle**
🆔 une **adresse MAC virtuelle**
🌍 une **adresse IP**

L’hyperviseur crée un **switch virtuel** pour connecter les machines.

---

# 🔌 Schéma Simplifié

```
VM1
   \
    → Switch virtuel → Internet
   /
VM2
```

Le switch virtuel agit **comme un vrai switch réseau**.

---

# 🌍 4️⃣ Les Modes Réseau

Les hyperviseurs offrent plusieurs modes réseau.

---

# 🌐 Mode NAT

La VM utilise **la connexion internet de l’ordinateur hôte**.

Architecture :

```
VM → Hyperviseur → PC hôte → Internet
```

Avantages :

✔ configuration simple
✔ accès internet immédiat

Inconvénient :

❌ difficile d'accéder à la VM depuis le réseau local

---

# 🏢 Mode Bridge

La VM est connectée **directement au réseau local**.

Architecture :

```
VM → Réseau local → Internet
```

La VM reçoit **une vraie adresse IP du réseau**.

Exemple :

```
192.168.1.25
```

Avantages :

✔ accès direct depuis le réseau
✔ simulation réseau réelle

Inconvénient :

⚠ dépend de la sécurité du réseau

---

# 🔒 Mode Host-Only

La VM communique uniquement avec :

* le PC hôte
* les autres VMs

Architecture :

```
VM1 ↔ VM2 ↔ PC Hôte
```

❌ Pas d’accès internet.

---

# 🎮 Exemple simple — Le Jeu en Ligne

Imaginez trois types de connexion :

🎮 NAT → jouer via **le routeur de la maison**

🏢 Bridge → jouer **directement sur le réseau**

🔒 Host-Only → jouer **uniquement avec des amis dans la même pièce**

---

# 🖧 5️⃣ Le Switch Virtuel

Un **switch virtuel** fonctionne comme un switch physique.

Il permet :

✔ connecter les VMs
✔ connecter les VMs au réseau externe
✔ isoler des réseaux virtuels

---

# 🧪 Exemple en laboratoire

Dans un laboratoire réseau on peut créer :

* 10 machines Linux
* 5 machines Windows
* 1 serveur

Toutes connectées via **un switch virtuel**.

Sans acheter **aucun matériel physique**.

---

# ☁️ Importance en Cloud Computing

Les datacenters utilisent massivement :

✔ virtualisation réseau
✔ virtualisation stockage

C’est la base des plateformes :

* cloud
* data center
* cybersécurité
* laboratoires virtuels

---

# 🎯 Synthèse de la Séance

Aujourd’hui vous avez appris :

✔ ce qu’est **la virtualisation du stockage**
✔ la différence **disque dynamique vs pré-alloué**
✔ la virtualisation du réseau
✔ les modes **NAT / Bridge / Host-Only**
✔ le rôle d’un **switch virtuel**

Ces concepts sont essentiels pour comprendre :

☁️ **Cloud Computing**
🏢 **Data Centers**
🔐 **Cybersécurité**

---

# ❓ Questions Académiques

1️⃣ Qu’est-ce qu’un disque virtuel ?

2️⃣ Quelle est la différence entre **Disque Dynamique (Thin Provisioning)** et **Disque Pré-alloué (Thick Provisioning)** ?

3️⃣ Quelle différence entre **NAT et Bridge** ?

4️⃣ Dans quel cas utilise-t-on **Host-Only** ?

5️⃣ Quel est le rôle d’un **switch virtuel** ?

---

# 📘 Réponses — Séance 05

**1️⃣ Qu’est-ce qu’un disque virtuel ?**

Un disque virtuel est un fichier (ex : VMDK) qui représente le disque dur d’une machine virtuelle et qui contient son système d’exploitation et ses données.

---

**2️⃣ Différence entre Disque Dynamique (Thin Provisioning) et Disque Pré-alloué (Thick Provisioning)**

Thin :
le disque utilise seulement l’espace nécessaire et grandit progressivement.

Thick :
tout l’espace disque est réservé dès la création.

---

**3️⃣ Différence entre NAT et Bridge**

NAT :
la VM passe par la connexion internet de la machine hôte.

Bridge :
la VM est directement connectée au réseau local et possède sa propre adresse IP.

---

**4️⃣ Quand utiliser Host-Only ?**

Host-Only est utilisé pour :

* les laboratoires
* les tests réseau
* les environnements isolés

---

**5️⃣ Quel est le rôle du switch virtuel ?**

Le switch virtuel permet de connecter les machines virtuelles entre elles et avec le réseau externe, comme un switch physique.

---


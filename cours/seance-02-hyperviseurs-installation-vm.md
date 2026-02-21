
# 📘 cours/seance-02-hyperviseurs-installation-vm.md

# 🎓 Séance 02 — Hyperviseurs & Création d’une Machine Virtuelle

👨‍🏫 Responsable : Reda Abdelhakmi
📚 Module : Virtualisation de Base

---

# 🎬 Introduction

Lors de la séance 01, nous avons étudié :

* 🧠 L’architecture matérielle
* 🧮 Le fonctionnement CPU / RAM
* 💾 Le stockage
* 🏛️ L’origine de la virtualisation (Mainframes IBM)

Aujourd’hui, nous entrons dans la **mise en œuvre concrète**.

Nous allons comprendre :

✔ Les solutions de virtualisation du marché
✔ Les différents types d’hyperviseurs
✔ Les versions de VMware
✔ Les modes d’installation
✔ La création et configuration détaillée d’une VM Ubuntu

---

# 📗 1️⃣ Les Hyperviseurs

## 📜 Définition

Un **hyperviseur** est un logiciel (ou firmware) qui permet de créer et gérer des machines virtuelles en partageant les ressources d’une machine physique.

Il agit comme une couche d’abstraction entre :

* 🖥️ Le matériel
* 💻 Les systèmes d’exploitation invités

---

# 🏗️ 2️⃣ Type 1 vs Type 2

## 🔵 Hyperviseur Type 1 (Bare Metal)

Installé directement sur le matériel.

### Schématisation :

```
+-------------------------+
|     Machines Virtuelles |
+-------------------------+
|        Hyperviseur      |
+-------------------------+
|      Matériel Physique  |
+-------------------------+
```

Exemples :

* VMware ESXi
* Microsoft Hyper-V Server

📌 Utilisé en Data Center

---

## 🟢 Hyperviseur Type 2

Installé sur un système d’exploitation existant.

### Schématisation :

```
+-------------------------+
|     Machines Virtuelles |
+-------------------------+
|     Hyperviseur         |
+-------------------------+
|  OS Hôte (Windows/Linux)|
+-------------------------+
|   Matériel Physique     |
+-------------------------+
```

Exemples :

* VMware Workstation
* Oracle VirtualBox

📌 Utilisé en laboratoire et environnement académique

---

# 🌍 3️⃣ Solutions du Marché

## 🔵 VMware

Leader historique de la virtualisation.

Produits principaux :

| Produit            | Usage                    |
| ------------------ | ------------------------ |
| Workstation Player | Gratuit, usage personnel |
| Workstation Pro    | Labo avancé / entreprise |
| ESXi               | Serveurs                 |
| vSphere            | Data Center              |

---

## 🟢 Oracle VirtualBox

* Gratuit
* Open Source
* Simple à utiliser
* Moins performant sur forte charge

---

# ⚖️ VMware vs VirtualBox

| Critère            | VMware Workstation Pro | VirtualBox   |
| ------------------ | ---------------------- | ------------ |
| Performance CPU    | 🔥 Optimisée           | Bonne        |
| Gestion RAM        | Avancée                | Standard     |
| Snapshots          | Multiples              | Limités      |
| Réseau virtuel     | Avancé                 | Basique      |
| Support entreprise | Oui                    | Non officiel |
| Prix               | Payant                 | Gratuit      |

📌 Conclusion académique :

VirtualBox → environnement pédagogique
VMware Pro → environnement professionnel

---

# 🏷️ 4️⃣ Versions VMware Workstation

## 🔹 VMware Workstation Player

* Gratuit
* Une VM active
* Pas de snapshots avancés

## 🔹 VMware Workstation Pro 17

* Snapshots multiples
* Clonage complet
* Gestion réseau avancée
* Support TPM virtuel
* Support Windows 11
* Optimisation GPU

---

# 🛠️ 5️⃣ Installation : Typical vs Custom

Lors de l’installation de VMware :

## 🔹 Typical Installation

* Paramètres par défaut
* Installation rapide
* Convient pour 90% des usages académiques

## 🔹 Custom Installation

Permet :

* Choix du chemin d’installation
* Configuration modules réseau
* Compatibilité matérielle
* Paramétrage avancé

📌 En environnement pédagogique → Typical recommandé

---

# 📦 6️⃣ Préparation des Outils

Dans le repository Drive :

* Ubuntu ISO 🐧
* VMware Workstation Pro 17
* WinRAR

⚠️ Important :

Un fichier `.iso` ne doit pas être extrait.
Il doit être monté comme disque virtuel.

---

# 🐧 7️⃣ Création d’une Machine Virtuelle Ubuntu

## Étape 1 : Create New Virtual Machine

Choisir : Typical

---

## Étape 2 : Source d’installation

Sélectionner :

```
ubuntu-xx.xx-desktop-amd64.iso
```

VMware détecte automatiquement Linux Ubuntu.

---

# ⚙️ 8️⃣ Configuration Détaillée des Ressources

Cette partie est essentielle pédagogiquement.

---

## 🧠 A. Configuration CPU

Paramètres :

* Number of Processors
* Number of Cores per Processor

Exemple machine hôte :

8 cœurs / 16 threads

Recommandation VM Ubuntu :

2 à 4 cœurs

### Schéma conceptuel :

```
Machine Physique : 8 Cœurs
         ↓
Hyperviseur
         ↓
VM Ubuntu : 4 Cœurs
```

⚠️ Ne jamais allouer 100% des ressources CPU.

---

## 🧮 B. Configuration RAM

Exemple machine hôte :

16 GB RAM

Recommandation :

| Usage    | RAM  |
| -------- | ---- |
| Minimum  | 2 GB |
| Standard | 4 GB |
| Confort  | 6 GB |

### Schéma mémoire :

```
16 GB RAM Totale
│
├── 4 GB → VM Ubuntu
└── 12 GB → OS Hôte
```

Principe :
Toujours conserver minimum 50% pour l’OS hôte.

---

## 💾 C. Disque Virtuel

Choix :

1️⃣ Store as a single file
2️⃣ Split into multiple files

Recommandation labo :

Single file + SSD

Taille recommandée :

40 GB

---

## 🌐 D. Configuration Réseau

Modes disponibles :

| Mode      | Description               |
| --------- | ------------------------- |
| NAT       | VM partage connexion hôte |
| Bridged   | VM reçoit IP locale       |
| Host-Only | Isolation complète        |

Recommandation pédagogique : NAT

---

## 🎮 E. Carte Graphique Virtuelle

Activer :

✔ Accelerate 3D Graphics

Pourquoi ?

Ubuntu Desktop utilise interface graphique.

---

# 🔄 9️⃣ Installation Ubuntu

Étapes :

1. Try or Install Ubuntu
2. Installation normale
3. Partition automatique
4. Création utilisateur
5. Redémarrage

---

# 🧠 1️⃣0️⃣ Analyse : Machine Physique vs Machine Virtuelle

### Schéma global :

```
+----------------------------------+
|        VM Ubuntu                 |
| CPU virtuel | RAM virtuelle      |
| Disque virtuel | GPU virtuel     |
+----------------------------------+
              ↓
+----------------------------------+
| Hyperviseur VMware Workstation   |
+----------------------------------+
              ↓
+----------------------------------+
| Windows / Linux (OS Hôte)        |
+----------------------------------+
              ↓
+----------------------------------+
| Matériel Physique                |
+----------------------------------+
```

---

# 🎯 Synthèse de la Séance

Aujourd’hui vous avez appris :

✔ Le rôle d’un hyperviseur
✔ Type 1 vs Type 2
✔ Différences VMware / VirtualBox
✔ Différences Player / Pro
✔ Installation Typical vs Custom
✔ Configuration CPU / RAM / Disque / Réseau
✔ Création complète d’une VM Ubuntu

---

# ❓ Questions Académiques

1. Pourquoi VMware est-il plus performant que VirtualBox ?
2. Pourquoi ne doit-on pas allouer toute la RAM à une VM ?
3. Quelle différence entre NAT et Bridged ?
4. Quelle différence entre Player et Pro ?
5. Pourquoi l’hyperviseur Type 1 est utilisé en Data Center ?

---

# 📌 Message du Responsable du Module

La virtualisation ne consiste pas seulement à installer une VM.

Elle consiste à comprendre :

* Le partage des ressources
* L’abstraction matérielle
* L’optimisation des performances

Celui qui comprend l’hyperviseur… comprend le Cloud ☁️🚀

---


Dis-moi la prochaine étape 🔥

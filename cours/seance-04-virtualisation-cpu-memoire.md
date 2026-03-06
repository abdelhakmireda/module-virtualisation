

# 📘 Séance 04 — Virtualisation du CPU et de la Mémoire

👨‍🏫 Responsable : **Reda Abdelhakmi**
📚 Module : **Virtualisation de Base**

---

# 🎬 Introduction

Lors des séances précédentes, nous avons appris à :

✔ installer **VMware Workstation Pro**
✔ créer des **machines virtuelles**
✔ utiliser **snapshots et clonage**

Mais une question essentielle se pose :

❓ **Comment plusieurs machines virtuelles peuvent-elles utiliser le même matériel en même temps ?**

Un ordinateur possède :

* un **CPU**
* de la **RAM**
* un **disque**
* un **réseau**

Pourtant, une seule machine physique peut exécuter **plusieurs VM simultanément**.

Cela est possible grâce à la **virtualisation des ressources matérielles**.

Aujourd’hui nous allons comprendre :

🧠 la virtualisation du **CPU**
🧮 la virtualisation de la **mémoire (RAM)**
⚙️ le rôle de l’**hyperviseur**
🚀 les technologies **Intel VT-x et AMD-V**

---

# 🧠 1️⃣ Virtualisation du CPU

## 📜 Définition

La **virtualisation du CPU** permet à plusieurs machines virtuelles de partager un même processeur physique.

Chaque machine virtuelle possède :

👉 un **CPU virtuel (vCPU)**

Mais ce CPU virtuel n’est pas réel.
Il est **géré par l’hyperviseur**.

---

# 🏗️ Schéma du partage CPU

```
CPU Physique
     │
Hyperviseur
     │
 ├── VM 1 (vCPU)
 ├── VM 2 (vCPU)
 └── VM 3 (vCPU)
```

Le processeur est partagé **dans le temps**.

---

# ⏱️ 2️⃣ Le CPU Scheduler

Un CPU ne peut exécuter qu’une instruction à la fois par cœur.

L’hyperviseur utilise donc un système appelé :

👉 **CPU Scheduler**

Son rôle :

* répartir le temps CPU entre les VM
* garantir l’équité entre les machines virtuelles
* optimiser les performances

---

# 🎓 Exemple simple — Salle d’examen

Imaginez :

* 1 professeur
* 3 étudiants qui veulent poser une question

Le professeur écoute :

* Étudiant 1 → quelques secondes
* Étudiant 2 → quelques secondes
* Étudiant 3 → quelques secondes

Puis il recommence.

Chaque étudiant pense avoir l’attention complète.

👉 C’est exactement ce que fait le **CPU scheduler**.

---

# ⚙️ 3️⃣ Les vCPU

Chaque VM peut avoir un ou plusieurs **vCPU**.

Exemple :

Machine physique :

* 8 cœurs CPU

VM :

* 2 vCPU

La VM croit posséder **2 processeurs**.

Mais en réalité, ils sont **partagés avec les autres VM**.

---

# ⚠️ Surallocation CPU

Exemple :

Machine physique :

8 cœurs

VM créées :

* VM1 → 4 vCPU
* VM2 → 4 vCPU
* VM3 → 4 vCPU

Total :

👉 **12 vCPU**

Mais la machine physique n’a que **8 cœurs**.

L’hyperviseur devra partager les ressources.

---

# 🧮 4️⃣ Virtualisation de la Mémoire

Chaque VM croit posséder sa propre RAM.

Exemple :

Machine physique :

16 GB RAM

Machines virtuelles :

* VM1 → 4 GB
* VM2 → 4 GB
* VM3 → 4 GB

La RAM est **allouée et contrôlée par l’hyperviseur**.

---

# 🏗️ Schéma mémoire

```
RAM Physique (16 GB)

 ├── VM1 → 4 GB
 ├── VM2 → 4 GB
 ├── VM3 → 4 GB
 └── OS hôte
```

---

# ⚙️ 5️⃣ Optimisation de la Mémoire

Les hyperviseurs utilisent plusieurs techniques pour optimiser la RAM.

---

# 📌 Memory Overcommitment

Permet d’allouer **plus de RAM virtuelle que la RAM physique**.

Exemple :

RAM physique : 16 GB

VM totale : 24 GB

L’hyperviseur optimise l’utilisation réelle.

---

# 📌 Memory Ballooning

Technique permettant de récupérer de la RAM inutilisée.

Exemple :

VM possède 4 GB mais utilise seulement 2 GB.

L’hyperviseur peut récupérer la RAM inutilisée.

---

# 📌 Memory Swapping

Si la RAM est insuffisante :

l’hyperviseur utilise le disque comme mémoire temporaire.

Mais cela ralentit les performances.

---

# 🚀 6️⃣ Virtualisation Matérielle

Les processeurs modernes possèdent des technologies dédiées.

---

# 🔵 Intel VT-x

Technologie Intel permettant :

✔ virtualisation CPU plus rapide
✔ meilleure isolation
✔ meilleure performance

---

# 🔴 AMD-V

Technologie équivalente chez AMD.

Elle permet également :

✔ virtualisation matérielle
✔ meilleure gestion des VM

---

# 🔍 Vérifier dans Ubuntu

Pour vérifier si la virtualisation est activée :

```bash
lscpu | grep Virtualization
```

Résultat possible :

```
Virtualization: VT-x
```

---

# 🧠 7️⃣ Exemple réel — Data Center

Un serveur moderne peut avoir :

* 64 cœurs CPU
* 512 GB RAM

Sur ce serveur on peut exécuter :

👉 **des dizaines ou centaines de VM**.

Chaque VM utilise une partie des ressources.

C’est le principe du **Cloud Computing**.

---

# ☁️ Lien avec le Cloud

Les grandes plateformes cloud fonctionnent avec la virtualisation :

* Amazon AWS
* Microsoft Azure
* Google Cloud

Les utilisateurs louent des **machines virtuelles sur des serveurs physiques partagés**.

---

# 🎯 Synthèse de la Séance

Aujourd’hui vous avez appris :

✔ comment le CPU est partagé entre les VM
✔ ce qu’est un **vCPU**
✔ comment la RAM est virtualisée
✔ les techniques d’optimisation mémoire
✔ les technologies **Intel VT-x et AMD-V**

Ces concepts sont fondamentaux pour comprendre :

* les **data centers**
* les **cloud providers**
* les **infrastructures virtualisées modernes**

---

# ❓ Questions Académiques

1️⃣ Qu’est-ce qu’un **vCPU** ?
2️⃣ Pourquoi le **CPU scheduler** est-il nécessaire ?
3️⃣ Quelle est la différence entre **RAM physique et RAM virtuelle** ?
4️⃣ Qu’est-ce que le **memory ballooning** ?
5️⃣ Pourquoi les technologies **Intel VT-x / AMD-V** améliorent la virtualisation ?

---

# 📌 Message du Responsable du Module

La virtualisation ne consiste pas seulement à créer des machines virtuelles.

Elle consiste à comprendre **comment les ressources matérielles sont partagées intelligemment**.

Celui qui comprend la virtualisation du **CPU et de la mémoire** comprend le fonctionnement des **data centers et du cloud moderne**. ☁️🚀

---


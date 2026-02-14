
# 📦 `virtualisation-de-base`

## 📘 `cours/seance-01-fondamentaux-architecture.md`

---

# 🎓 Séance 01 — Fondamentaux de l’Architecture Informatique & Origine de la Virtualisation

---

## 🎬 Introduction

Chers étudiants 👨‍🎓👩‍🎓,

Avant de parler de virtualisation, de machines virtuelles ou de Cloud ☁️, nous devons comprendre **la machine physique** 🖥️.

La virtualisation ne peut exister que si l’on comprend :

* 🧠 Le processeur (CPU)
* 🧮 La mémoire (RAM)
* 💾 Le stockage
* 🎮 La carte graphique
* 🔌 La communication entre ces composants

Aujourd’hui, nous allons démonter un ordinateur… mais de manière académique 🔬✨

---

# 🏢 1️⃣ Les Mainframes
Parfait Prof Reda 👨‍🏫, je te donne une version complète et claire uniquement pour la partie **🏢 1️⃣ Les Mainframes**, avec explication de ce qu’est un **mainframe** et son rôle historique :

---

# 🏢 1️⃣ Les Mainframes

### 📜 Définition

Un **mainframe** est un **ordinateur central de grande puissance** utilisé principalement par les grandes entreprises, institutions financières et administrations.

C’est une machine **très robuste et fiable**, capable de :

* Traiter simultanément des milliers de transactions 💳
* Gérer de très grandes quantités de données 🗃️
* Exécuter plusieurs systèmes ou applications isolés en même temps 🔄

### 🕰️ Historique

* Apparition : **années 1960**
* Fabricant emblématique : **IBM** (ex : IBM System/360)
* Usage : banques, compagnies d’assurance, universités, administrations
* Prix : **100 000 à 10 000 000 $** 💰 selon le modèle

> À l’époque, posséder un mainframe signifiait un **investissement colossal**, mais c’était indispensable pour les tâches critiques et le traitement en masse.

### ⚠️ Problématique

* Chaque utilisateur ou application avait besoin d’une machine dédiée → **coût énorme** 💸
* Machines souvent sous-utilisées
* Difficulté pour les tests et développement d’applications

### 💡 Solution apportée par la virtualisation

La virtualisation a permis de **partager un mainframe** entre plusieurs systèmes et utilisateurs, créant des **machines virtuelles isolées**, chacune pensant disposer de son propre ordinateur physique.

### 🖼️ Schéma simplifié d’un Mainframe

```
+----------------------------------------+
|           Mainframe IBM 360            |
|----------------------------------------|
| CPU central 🧠                          |
| Mémoire centrale 🧮                     |
| Stockage massif 💾                       |
| Console utilisateur 👤                   |
+----------------------------------------+
```
---

# 🧠 2️⃣ Le Processeur (CPU)

Le CPU est le **cerveau de la machine**.

Il exécute les instructions du système d’exploitation et des applications.

### 📌 Structure interne

Un CPU moderne contient :

* 🧮 **Cœurs (Cores)**
* 🧵 **Threads**
* 🗃️ Cache (L1, L2, L3)
* 🔄 Unité de contrôle
* ➕ Unité arithmétique et logique (ALU)

---

## 🔎 Cœur vs Thread

* **Cœur** = unité physique réelle de calcul
* **Thread** = unité logique d’exécution

Exemple : Un processeur 8 cœurs / 16 threads signifie :

* 8 unités physiques
* 16 flux d’exécution simultanés (Hyper-Threading)

---

## 🏆 Processeurs puissants (2026)

* AMD Ryzen 9 7950X
* Intel Core i9-14900K
* AMD EPYC 9654
* Intel Xeon Platinum 8490H

---

## 📊 Idée de Benchmark

Les benchmarks mesurent la performance :

* Cinebench (rendu 3D)
* Geekbench (calcul général)
* PassMark (score global)

Exemple : un processeur serveur comme EPYC peut dépasser **100 000 points PassMark**, contre ~35 000 pour un CPU grand public.

---

## 🚀 L’idée du processeur ultra-puissant

Évolution :

1960 → CPU mono-cœur
2005 → multi-cœurs
2015 → +20 cœurs
2025 → +96 cœurs en serveur

Aujourd’hui, la puissance vient :

* du parallélisme massif
* de l’optimisation énergétique
* de l’IA embarquée 🤖

---

# 🧮 3️⃣ La Mémoire RAM

La RAM est la **mémoire volatile**.

Elle stocke temporairement les données utilisées par le CPU.

### 📚 Évolution des générations

* DDR1 (2000)
* DDR2 (2003)
* DDR3 (2007)
* DDR4 (2014)
* DDR5 (2020)

| Génération | Vitesse       | Consommation     |
| ---------- | ------------- | ---------------- |
| DDR3       | ~1600 MHz     | + élevée         |
| DDR4       | ~3200 MHz     | ↓                |
| DDR5       | 4800–7200 MHz | plus optimisée ⚡ |

---

# 💾 4️⃣ Le Stockage

### 🔵 HDD (Hard Disk Drive)

* Disque mécanique
* Plateaux rotatifs
* Lent (100–200 MB/s)
* Bruyant
* Bon marché

### 🟢 SSD (Solid State Drive)

* Mémoire flash
* Aucun mouvement mécanique
* Très rapide (500 MB/s SATA, 7000 MB/s NVMe)
* Silencieux
* Plus cher

### 🟡 SSHD (Hybrid)

* Combinaison HDD + petite mémoire flash
* Compromis vitesse/prix

### 📊 Comparaison simple

| Type | Vitesse   | Fiabilité | Prix |
| ---- | --------- | --------- | ---- |
| HDD  | ❌ Lent    | Moyen     | 💰   |
| SSD  | 🚀 Rapide | Élevée    | 💰💰 |
| SSHD | ⚖️ Moyen  | Moyen     | 💰💰 |

---

# 🎮 5️⃣ Carte Graphique (GPU)

Le GPU traite :

* Graphismes
* Calcul parallèle massif
* Intelligence artificielle 🤖

## 🧠 VRAM

VRAM = mémoire dédiée du GPU.

Plus il y a de VRAM :

* Meilleur rendu 3D
* Meilleur traitement IA
* Capacité à gérer de grandes données

---

## 🔥 GPU puissants

* NVIDIA GeForce RTX 4090
* NVIDIA H100

Le GPU H100 est conçu pour l’IA et peut coûter plusieurs dizaines de milliers d’euros.

---

# 🏗️ 6️⃣ Machine Physique vs Machine Virtuelle

### Schéma explicatif

```
Machine Physique
+-------------------------+
| CPU 🧠                   |
| RAM 🧮                   |
| Stockage 💾              |
| GPU 🎮                   |
| OS physique              |
+-------------------------+

Machine Virtuelle (VM)
+-------------------------+
| CPU virtuel 🧠           |
| RAM virtuelle 🧮          |
| Disque virtuel 💾         |
| OS invité                |
+-------------------------+

        ↕ Virtualisation (Hyperviseur)
+-------------------------+
| OS physique ou Hyperviseur |
+-------------------------+
```

* La VM croit avoir son propre matériel
* En réalité, l’hyperviseur partage les ressources de la machine physique

---

# 🏛️ 7️⃣ Naissance de la Virtualisation

* Années 1960 : IBM → partage des mainframes
* Années 2000 : VMware, Microsoft Hyper-V, Oracle VirtualBox

**Problématique résolue :**

* Optimisation du coût des ressources 💰
* Possibilité de faire tourner plusieurs systèmes isolés 🔄
* Base pour Cloud, DevOps et laboratoires modernes 🌐

---

# 🎯 Conclusion

Avant de virtualiser, il faut comprendre le réel.

La virtualisation est :

> Une abstraction intelligente du matériel 🧠
> Une optimisation des ressources 💰
> Une révolution pour le Cloud ☁️

---

# ❓ Questions de réflexion

1. Pourquoi un CPU avec plus de cœurs est-il utile en virtualisation ?
2. Pourquoi un SSD est recommandé pour les VM ?
3. Quelle est la différence entre VRAM et RAM ?
4. Pourquoi la virtualisation est née dans les environnements mainframe ?
5. Un CPU 8 cœurs / 16 threads peut-il exécuter 16 VM simultanément ?

---

# 📌 Message du Professeur

La virtualisation n’est pas magique.

Elle repose sur une compréhension profonde du matériel.

Celui qui maîtrise l’architecture… maîtrise le Cloud ☁️🚀

---


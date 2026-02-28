
# 📘 Séance 03 — Snapshots, Clonage & Gestion Avancée des Machines Virtuelles

👨‍🏫 Responsable : Reda Abdelhakmi
📚 Module : Virtualisation de Base

---

# 🎬 Introduction

Après avoir :

✔ Installé VMware Workstation Pro 17
✔ Créé une VM Ubuntu
✔ Configuré CPU, RAM et Réseau

Nous allons maintenant apprendre à :

* 📸 Sauvegarder un état système (Snapshot)
* 📦 Copier une machine virtuelle (Clone)
* 🔄 Restaurer un environnement
* 🏢 Comprendre l’avantage professionnel de VMware Pro

Cette séance est essentielle en :

* 🔐 Cybersécurité
* 🧪 Laboratoires
* 🏢 Entreprise
* ☁️ Infrastructure Cloud

---

# 📸 1️⃣ Les Snapshots

## 📜 Définition

Un snapshot est une capture instantanée de l’état d’une machine virtuelle à un moment précis.

Il enregistre :

* L’état du disque
* La configuration matérielle
* Optionnellement la RAM

---

## 🔬 Fonctionnement technique simplifié

Lorsqu’un snapshot est créé :

1. Le disque principal devient lecture seule
2. VMware crée un disque différentiel (delta)
3. Les nouvelles modifications sont stockées dans ce delta

Schéma :

```
Disque principal.vmdk
        ↓
Créer Snapshot
        ↓
Disque-delta.vmdk
```

Si on restaure :

→ Le delta est annulé
→ Retour à l’état exact du snapshot

---

## 🎓 Exemple simple — Le Match ⚽

Vous regardez un match.
Vous mettez pause à la 30e minute.

Le snapshot = bouton pause.

Si vous revenez → vous reprenez à la 30e minute.

Mais :

❌ Ce n’est pas une copie du match
❌ Si le match disparaît → la pause ne sert plus

---

## 🍽️ Exemple simple — Le Plat au Restaurant

Avant d’ajouter du piment 🌶️
Vous prenez une photo du plat.

Si le goût devient mauvais →
Vous revenez à la version initiale.

Le snapshot = photo temporaire.

---

## ⚠️ Important

Un snapshot :

❌ N’est pas une sauvegarde complète
❌ Dépend du disque original
❌ Ne doit pas être conservé trop longtemps

---

# 📦 2️⃣ Le Clonage

## 📜 Définition

Le clonage crée une copie d’une machine virtuelle.

Contrairement au snapshot, le clone est une nouvelle VM.

---

## 🔹 Full Clone (Clone complet)

✔ Copie totale
✔ Indépendant
✔ Utilisable ailleurs

---

## 🔹 Linked Clone (Clone lié)

✔ Création rapide
✔ Moins d’espace disque
❌ Dépend de la VM parent

---

## 📚 Exemple simple — Photocopie d’un Livre

Vous avez un livre original.

Vous faites une photocopie complète.

Vous avez maintenant deux livres indépendants.

Le clone = photocopie complète.

Même si l’original disparaît → la copie reste.

---

## 👨‍🏫 Exemple pédagogique

Le professeur crée :

1 VM modèle Ubuntu.

Il génère 20 clones pour les étudiants.

Tous ont le même environnement.

Gain de temps énorme 🚀

---

# ⚖️ Snapshot vs Clone

| Snapshot                   | Clone                 |
| -------------------------- | --------------------- |
| Pause / point restauration | Copie complète        |
| Usage temporaire           | Usage durable         |
| Dépend du disque principal | Peut être indépendant |

---

# 🏆 3️⃣ VMware Pro vs Player vs VirtualBox

## 📸 Snapshots

| Fonction            | VMware Pro | VMware Player | VirtualBox |
| ------------------- | ---------- | ------------- | ---------- |
| Snapshots multiples | ✔          | ❌             | ✔          |
| Arborescence        | ✔          | ❌             | Limité     |
| Snapshot RAM        | ✔          | ❌             | ✔          |
| Usage professionnel | ✔          | ❌             | ❌          |

VMware Pro permet une gestion avancée en arbre, idéale pour laboratoire complexe.

---

## 📦 Clonage

| Fonction              | VMware Pro | VMware Player | VirtualBox |
| --------------------- | ---------- | ------------- | ---------- |
| Full Clone            | ✔          | ❌             | ✔          |
| Linked Clone          | ✔          | ❌             | ✔          |
| Clone depuis snapshot | ✔          | ❌             | Limité     |
| Optimisation disque   | 🔥 Élevée  | ❌             | Moyenne    |

VMware Player est très limité.
VirtualBox permet le clonage, mais avec moins d’optimisation.
VMware Pro est conçu pour usage professionnel.

---

# 🚀 Pourquoi VMware Pro est supérieur ?

Parce qu’il offre :

✔ Snapshots arborescents
✔ Linked Clone performant
✔ Clone depuis snapshot
✔ Meilleure gestion disque delta
✔ Stabilité élevée
✔ Usage entreprise

Il est adapté à :

* Tests de patch
* Simulations cybersécurité
* Déploiement multi-VM
* Environnements professionnels

---

# 🛠️ 4️⃣ Gestion Avancée

Dans VMware Pro, on peut :

* Modifier CPU / RAM
* Étendre disque
* Gérer réseau avancé
* Naviguer entre snapshots

Toujours éteindre la VM avant modification matérielle.

---

# 🎯 Synthèse de la Séance

Aujourd’hui vous avez appris :

✔ Fonctionnement technique d’un snapshot
✔ Différence snapshot vs clone
✔ Full Clone vs Linked Clone
✔ Exemples simples pour comprendre
✔ Supériorité de VMware Workstation Pro

La virtualisation devient maintenant un outil stratégique.

---

# ❓ Questions Académiques

1. Pourquoi un snapshot n’est-il pas une sauvegarde ?
2. Quelle différence entre Full Clone et Linked Clone ?
3. Pourquoi VMware Pro est plus adapté en entreprise ?
4. Quel est le risque d’un Linked Clone ?
5. Quand utiliser un snapshot plutôt qu’un clone ?

---

# 📌 Message du Responsable du Module

Un bon administrateur système :

* Ne teste jamais sans snapshot
* Déploie toujours avec des clones
* Choisit un outil professionnel adapté

Celui qui maîtrise snapshots et clones…
maîtrise l’infrastructure virtuelle. 🚀

---

# 📘 Réponses — Séance 03

---

## 1️⃣ Pourquoi un snapshot n’est-il pas une sauvegarde ?

Parce qu’il dépend du disque original de la VM.
Si le fichier principal est supprimé ou corrompu, le snapshot devient inutilisable.
Il est destiné aux tests temporaires, pas au stockage long terme.

---

## 2️⃣ Quelle différence entre Full Clone et Linked Clone ?

* **Full Clone** : copie complète et indépendante de la VM.
* **Linked Clone** : dépend de la VM parent et utilise un disque différentiel.

Le Full Clone est plus sûr, le Linked Clone est plus rapide et léger.

---

## 3️⃣ Pourquoi VMware Pro est plus adapté en entreprise ?

Parce qu’il permet :

* Snapshots multiples en arborescence
* Linked Clone performant
* Clonage depuis snapshot
* Meilleure gestion des ressources
* Stabilité professionnelle

Il est conçu pour les environnements complexes.

---

## 4️⃣ Quel est le risque d’un Linked Clone ?

Il dépend de la VM parent.
Si la VM parent est supprimée ou endommagée, le Linked Clone peut ne plus fonctionner.

---

## 5️⃣ Quand utiliser un snapshot plutôt qu’un clone ?

On utilise un snapshot :

* Pour tester temporairement
* Avant une mise à jour
* Avant une manipulation risquée

On utilise un clone :

* Pour créer un nouvel environnement
* Pour déployer plusieurs machines
* Pour un usage durable

---


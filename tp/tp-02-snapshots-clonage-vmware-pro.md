
# 🧪 TP 02 — Snapshots & Clonage (Version Terminal)

👨‍🏫 Responsable : Reda Abdelhakmi
📚 Module : Virtualisation de Base
🖥️ Hyperviseur : VMware Workstation Pro 17
🐧 OS invité : Ubuntu 24.xx

---

# 🎯 Objectifs

À la fin du TP, l’étudiant sera capable de :

✔ Manipuler fichiers/dossiers en ligne de commande
✔ Créer et restaurer un Snapshot
✔ Créer un Full Clone
✔ Créer un Linked Clone
✔ Analyser la différence pratique

---

# 📌 Prérequis

* VMware Pro installé
* VM Ubuntu fonctionnelle
* Terminal accessible (`Ctrl + Alt + T`)

---

# 🔹 PARTIE 1 — Préparation (Terminal Ubuntu)

---

## 1️⃣ Ouvrir le Terminal

```bash
Ctrl + Alt + T
```

---

## 2️⃣ Vérifier informations système

### Vérifier RAM :

```bash
free -h
```

### Vérifier CPU :

```bash
lscpu
```

### Vérifier IP :

```bash
ip a
```

---

# 📁 PARTIE 2 — Création Environnement Test

---

## 1️⃣ Créer un dossier TEST_SNAPSHOT

```bash
mkdir ~/TEST_SNAPSHOT
```

Vérification :

```bash
ls ~
```

---

## 2️⃣ Entrer dans le dossier

```bash
cd ~/TEST_SNAPSHOT
```

---

## 3️⃣ Créer plusieurs fichiers

```bash
touch fichier1.txt fichier2.txt fichier3.txt
```

---

## 4️⃣ Ajouter du contenu

```bash
echo "Test Snapshot 1" > fichier1.txt
echo "Test Snapshot 2" > fichier2.txt
echo "Test Snapshot 3" > fichier3.txt
```

---

## 5️⃣ Vérifier contenu

```bash
cat fichier1.txt
```

---

# 📸 PARTIE 3 — Création Snapshot

---

## Étape VMware

Dans VMware :

```
VM → Snapshot → Take Snapshot
```

Nom :

```
Avant_Suppression
```

Description :

```
Etat avant suppression dossier TEST_SNAPSHOT
```

---

# 🗑️ PARTIE 4 — Modification Après Snapshot

---

## 1️⃣ Supprimer dossier

Revenir au home :

```bash
cd ~
```

Supprimer :

```bash
rm -r TEST_SNAPSHOT
```

Vérifier :

```bash
ls
```

Le dossier doit disparaître.

---

# 🔄 PARTIE 5 — Restauration Snapshot

Dans VMware :

```
VM → Snapshot → Revert to Snapshot
```

Redémarrer la VM si nécessaire.

---

## Vérification Terminal

```bash
ls ~
```

Le dossier TEST_SNAPSHOT doit réapparaître.

---

# ❓ Questions Snapshot

1. Pourquoi le dossier est revenu ?
2. Le snapshot est-il indépendant ?
3. Que se passe-t-il si on supprime la VM principale ?

---

# 📦 PARTIE 6 — Full Clone

---

## 1️⃣ Éteindre la VM

Dans Ubuntu :

```bash
sudo poweroff
```

---

## 2️⃣ Dans VMware

Clic droit → Manage → Clone
Choisir :

```
Full Clone
```

Nom :

```
Ubuntu_Full_Clone
```

---

## 3️⃣ Démarrer le Clone

Dans le clone, vérifier :

```bash
hostname
```

Modifier le hostname (test) :

```bash
sudo hostnamectl set-hostname FULLCLONE
```

Redémarrer :

```bash
sudo reboot
```

---

## Vérifier que la VM originale n’a pas changé

Démarrer la VM originale :

```bash
hostname
```

---

# ❓ Questions Full Clone

1. Pourquoi les modifications n’affectent pas l’original ?
2. Le Full Clone dépend-il de la VM parent ?

---

# 🔗 PARTIE 7 — Linked Clone

---

## 1️⃣ Créer Snapshot obligatoire

Avant Linked Clone :

```
VM → Snapshot → Take Snapshot
```

Nom :

```
Base_Model
```

---

## 2️⃣ Créer Linked Clone

Clic droit → Manage → Clone
Choisir :

```
Linked Clone
```

Nom :

```
Ubuntu_Linked_Clone
```

---

## 3️⃣ Test dans Linked Clone

Créer fichier :

```bash
touch ~/linked_test.txt
```

Vérifier :

```bash
ls ~
```

---

# ❓ Question Linked Clone

Que risque-t-il d’arriver si la VM parent est supprimée ?

---

# ⚖️ PARTIE 8 — Analyse Comparative

Compléter :

| Critère            | Snapshot | Full Clone | Linked Clone |
| ------------------ | -------- | ---------- | ------------ |
| Usage temporaire   | ✔        | ❌          | ❌            |
| Indépendant        | ❌        | ✔          | ❌            |
| Gain espace disque | ✔        | ❌          | ✔            |
| Usage entreprise   | ✔        | ✔          | ✔            |

---

# 📋 Livrables

Chaque étudiant doit fournir :

✔ Capture écran commandes création fichiers
✔ Capture écran snapshot
✔ Capture écran restauration
✔ Capture écran Full Clone
✔ Capture écran Linked Clone

---

# 🎓 Conclusion du TP

Ce TP démontre :

✔ La puissance des snapshots
✔ La différence réelle clone vs snapshot
✔ L’avantage professionnel de VMware Pro
✔ L’importance des commandes Linux

---

On passe à la partie technique avancée ? 🚀

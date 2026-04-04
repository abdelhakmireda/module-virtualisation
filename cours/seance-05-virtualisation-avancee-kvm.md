
# 📘 🎓 Séance 06 — Virtualisation Réseau Avancée & Transition vers l’Infrastructure Professionnelle

👨‍🏫 Responsable : Reda Abdelhakmi
📚 Module : Virtualisation de Base

---

## 🎬 Introduction (prise de parole)

Chers étudiants 👨‍🎓👩‍🎓,

Jusqu’à maintenant, vous avez appris à :

✔ créer des machines virtuelles
✔ installer un système Linux
✔ configurer CPU, RAM
✔ manipuler le réseau (NAT, Bridge, Host-Only)
✔ créer un mini réseau avec plusieurs machines

👉 Vous avez donc construit un **petit laboratoire virtuel**

Mais maintenant, je vais vous poser une question :

❓ *Est-ce que ce que vous avez fait jusqu’à présent est utilisé tel quel dans une entreprise ?*

👉 La réponse est : **pas exactement**

Aujourd’hui, nous allons comprendre :

➡️ les limites de ce que vous avez fait
➡️ comment les professionnels travaillent réellement
➡️ pourquoi on va bientôt changer d’outil

---

## 🧠 1️⃣ Limites de VMware Workstation (explication + exemple)

👉 Ce que vous utilisez depuis le début :

VM → VMware → Windows → Matériel

💬 Prof :

> Imaginez que vous voulez courir…
> mais vous portez un sac de 20 kg 🎒
>
> Ce sac… c’est Windows + VMware.

👉 Résultat :

✔ ça fonctionne
❌ mais ce n’est pas optimal

### ❌ Problèmes

✔ consommation mémoire
✔ dépendance au système hôte
✔ performances limitées

---

## 🏗️ 2️⃣ C’est quoi une vraie infrastructure ?

💬 Prof :

> Jusqu’ici, vous avez créé UNE VM… puis DEUX… puis TROIS
>
> Mais dans la vraie vie ?

👉 On parle de :

✔ dizaines de machines
✔ serveurs spécialisés
✔ réseaux complets

---

### 🎓 Exemple réel

Une entreprise peut avoir :

✔ 1 serveur Web
✔ 1 serveur base de données
✔ 1 serveur SSH
✔ 10 machines clients

👉 Tout ça… en virtualisé

---

## 🌐 3️⃣ Réseau : ce que vous avez fait vs réalité

💬 Prof :

> Vous avez utilisé NAT, Bridge, Host-Only
>
> Très bien 👍
> Mais ce n’est que la base.

---

### 🧪 Exemple TP 04

Vous avez fait :

✔ VM1 → client
✔ VM2 → client
✔ VM3 → serveur SSH

👉 C’est un mini réseau.

---

### 🌍 En entreprise

On ajoute :

✔ plusieurs réseaux
✔ segmentation
✔ sécurité
✔ routage

---

💬 Prof :

> Imaginez une université 🎓
>
> Il y a :
>
> * réseau étudiants
> * réseau professeurs
> * réseau administration
>
> 👉 On ne mélange pas tout !

---

## 🖧 4️⃣ Architecture multi-machines

💬 Prof :

> Une VM seule… ne sert presque à rien en production.

👉 Ce qui compte :

➡️ la communication entre machines

---

### 🎓 Exemple concret

```id="infra1"
Client → Serveur Web → Base de données
```

---

💬 Prof :

> Quand vous ouvrez un site web 🌐
>
> Vous parlez à plusieurs machines… sans le savoir.

---

## 🔐 5️⃣ Notion de service (SSH comme exemple)

💬 Prof :

> Dans votre TP, vous avez installé SSH.
> Ce n’est pas un hasard.

---

### 📌 SSH sert à :

✔ accéder à une machine à distance
✔ administrer un serveur
✔ travailler sans interface graphique

---

### 🎓 Exemple réel

💬 Prof :

> Un administrateur à Casablanca peut gérer un serveur en France 🇫🇷
>
> 👉 sans jamais le voir physiquement

---

## ⚙️ 6️⃣ Pourquoi VMware devient limité

💬 Prof :

> Maintenant imaginez…
> 100 machines virtuelles sur votre PC 😅

👉 Impossible !

---

### ❌ Limites

✔ pas scalable
✔ pas adapté production
✔ réseau limité
✔ dépend du système hôte

---

## ☁️ 7️⃣ Ce que font les entreprises

💬 Prof :

> Les entreprises ne travaillent pas comme vous actuellement.

Elles utilisent :

✔ hyperviseur Type 1
✔ virtualisation native
✔ infrastructure complète

---

### 🎓 Exemple

✔ Data Center
✔ Cloud (AWS, Azure)
✔ serveurs physiques puissants

---

## 🧠 8️⃣ Transition vers la virtualisation professionnelle

💬 Prof :

> Jusqu’ici, vous avez appris à conduire une voiture 🚗
>
> Maintenant… on va passer au camion 🚛

👉 VMware = apprentissage
👉 prochaine étape = professionnel

---

## 🔄 9️⃣ Ce qui arrive dans la prochaine séance

💬 Prof :

> Dans la prochaine séance, vous allez découvrir :

🚀 KVM (virtualisation native Linux)

👉 Là… vous allez changer de niveau.

---

## 🎯 Synthèse (prise de parole)

💬 Prof :

Aujourd’hui, vous devez retenir :

✔ VMware est un outil pédagogique
✔ une VM seule ne suffit pas
✔ le réseau est essentiel
✔ une infrastructure = plusieurs machines + services
✔ le monde professionnel est plus complexe

---

## ❓ Questions à poser aux étudiants

💬 Prof :

1️⃣ Pourquoi VMware Workstation n’est pas utilisé en Data Center ?
2️⃣ Quelle est la différence entre une VM et une infrastructure ?
3️⃣ Pourquoi isoler les réseaux ?
4️⃣ À quoi sert SSH dans un réseau réel ?
5️⃣ Pourquoi passer à une autre technologie ?

---

## 🎓 Conclusion (forte)

💬 Prof :

> Ce que vous avez appris jusqu’ici…
> c’est la base.
>
> Mais maintenant…
>
> 👉 vous êtes prêts à entrer dans le monde réel de la virtualisation.

---

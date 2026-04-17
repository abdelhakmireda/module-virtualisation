
---

# 📘 🎓 Séance 07 — Introduction à KVM & Virtualisation Native Linux

👨‍🏫 Responsable : Reda Abdelhakmi
📚 Module : Virtualisation de Base

---

# 🎬 Introduction (prise de parole)

Chers étudiants 👨‍🎓👩‍🎓,

Lors de la séance précédente, nous avons compris :

✔ les limites de VMware
✔ la différence entre labo et production
✔ la notion d’infrastructure virtuelle

👉 Aujourd’hui… on change de niveau.

💬 Prof :

> Jusqu’ici vous utilisiez un simulateur…
> 👉 Aujourd’hui, vous allez utiliser une vraie technologie de production.

---

# 🧠 1️⃣ C’est quoi KVM ?

## 📜 Définition

KVM (Kernel-based Virtual Machine) est une technologie de virtualisation intégrée dans le noyau Linux.

👉 Cela signifie :

✔ Linux devient un hyperviseur
✔ pas besoin d’un logiciel lourd comme VMware

---

💬 Prof :

> Imaginez que votre système Linux… devient lui-même VMware 😄

---

# 🏗️ 2️⃣ Architecture KVM (vision simple)

```
Machines virtuelles
        ↓
KVM (dans le noyau Linux)
        ↓
Matériel physique
```

---

💬 Prof :

> Ici… il n’y a plus d’intermédiaire inutile
> 👉 accès direct au matériel = performance 🚀

---

# ⚖️ 3️⃣ VMware vs KVM

| Critère     | VMware Workstation | KVM         |
| ----------- | ------------------ | ----------- |
| Type        | Type 2             | Type 1      |
| Performance | Moyenne            | Élevée      |
| OS requis   | Windows/Linux      | Linux       |
| Usage       | Labo               | Data Center |

---

💬 Prof :

> VMware = apprendre
> 👉 KVM = travailler

---

# ⚙️ 4️⃣ Prérequis KVM

✔ CPU support virtualisation (VT-x / AMD-V)
✔ virtualisation activée BIOS
✔ Linux installé

---

## 🔍 Vérification

```bash
lscpu | grep Virtualization
```

---

💬 Prof :

> Si vous ne voyez rien…
> 👉 KVM ne fonctionnera pas !

---

# 🧩 5️⃣ Les composants de KVM (PARTIE CLÉ)

💬 Prof :

> ⚠️ Très important :
> KVM seul… ne suffit pas
> 👉 c’est un écosystème complet

---

## 🖧 Schéma global

```
👨‍💻 Utilisateur
        │
        ▼
🖥️ virt-manager (interface)
        │
        ▼
🎼 libvirt (gestion)
        │
        ▼
⚙️ QEMU (exécution VM)
        │
        ▼
🔥 KVM (noyau Linux)
        │
        ▼
💻 Matériel réel (CPU / RAM)
```

---

💬 Prof :

> Ce schéma… vous devez le comprendre
> 👉 c’est le fonctionnement réel d’une VM

---

# 🔍 6️⃣ Rôle de chaque composant

---

## 🔥 KVM (le cœur)

* intégré au noyau Linux
* utilise le CPU réel
* gère mémoire

💬 Prof :

> KVM = celui qui fait le vrai travail

---

## ⚙️ QEMU (le moteur)

👉 QEMU simule une machine complète

```
VM
 │
 ▼
QEMU simule :
 ├── disque dur
 ├── carte réseau
 ├── CPU virtuel
```

💬 Prof :

> QEMU crée l’illusion d’un ordinateur

---

## 🎼 libvirt (le chef d’orchestre)

```
libvirt
 ├── créer VM
 ├── démarrer VM
 ├── arrêter VM
 ├── gérer réseau
 └── gérer stockage
```

💬 Prof :

> libvirt organise tout…
> 👉 sans lui, c’est très compliqué

---

## 🖥️ virt-manager (interface)

👉 Interface graphique

💬 Prof :

> C’est ce que vous utilisez…
> 👉 mais ce n’est que la surface

---

# 🎭 7️⃣ Analogie simple (très importante)

💬 Prof :

> Imaginez un restaurant 🍽️

| Élément          | Rôle      |
| ---------------- | --------- |
| 👨‍🍳 KVM        | cuisinier |
| 🔥 QEMU          | outils    |
| 🎼 libvirt       | manager   |
| 🖥️ virt-manager | serveur   |

---

👉 Le client ne voit que le serveur
👉 mais le travail est derrière

---

# 🔄 8️⃣ Fonctionnement réel (cycle complet)

💬 Prof :

> Quand vous cliquez “Start VM”… voilà ce qui se passe :

```
1. Vous cliquez
        │
        ▼
2. virt-manager envoie la demande
        │
        ▼
3. libvirt traite
        │
        ▼
4. QEMU exécute
        │
        ▼
5. KVM utilise CPU réel
        │
        ▼
🚀 VM démarre
```

---

💬 Prof :

> Un simple clic…
> 👉 déclenche toute une architecture

---

# 🧪 9️⃣ Exemple concret (niveau étudiant)

👉 Créer une VM Ubuntu

```
virt-manager → libvirt → QEMU → KVM → CPU
```

---

👉 Résultat :

✔ VM Linux
✔ disque virtuel
✔ réseau

---

# 🏢 🔟 Exemple réel (entreprise)

💬 Prof :

> En entreprise, ce n’est pas UNE VM…

---

```
          🌐 Réseau virtuel
                │
 ┌──────────────┼──────────────┐
 │              │              │
 ▼              ▼              ▼
Client1       Client2       Serveur Web
                                │
                                ▼
                         Base de données
```

---

💬 Prof :

> Tout ça… peut tourner sur une seule machine physique 😄

---

# 🧠 1️⃣1️⃣ Pourquoi KVM est utilisé en entreprise ?

✔ open source
✔ performant
✔ stable
✔ scalable

---

🎓 Exemple réel :

✔ Proxmox
✔ OpenStack
✔ Cloud privé

---

💬 Prof :

> Quand vous utilisez le cloud…
> 👉 il y a souvent KVM derrière

---

# 🔄 1️⃣2️⃣ Transition pédagogique

💬 Prof :

> Avant : vous cliquiez dans VMware
> Maintenant : vous comprenez ce qu’il y a derrière

---

# 🎯 Synthèse finale

✔ KVM = virtualisation native
✔ QEMU = moteur
✔ libvirt = gestion
✔ virt-manager = interface

---

👉 Une VM =

```
virt-manager → libvirt → QEMU → KVM
```

---

# ❓ Questions

1️⃣ Pourquoi KVM est plus performant ?
2️⃣ Différence Type 1 / Type 2 ?
3️⃣ Rôle de QEMU ?
4️⃣ Pourquoi Linux est obligatoire ?
5️⃣ Où utilise-t-on KVM ?

---

# 🎓 Conclusion

💬 Prof :

> Aujourd’hui… vous venez de franchir un cap.

👉 Vous ne créez plus seulement des VMs
👉 Vous comprenez comment elles fonctionnent

---

# 🚀 Transition vers TP 05

💬 Prof :

> Maintenant que vous avez compris l’architecture…

👉 il est temps de passer à la pratique

👉 **TP 05 — Installation et utilisation de KVM**

---


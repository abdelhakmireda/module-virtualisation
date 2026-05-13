# 🧪 🎓 TP 06 — Création d’une Machine Virtuelle KVM avec CLI

👨‍🏫 Responsable : Reda Abdelhakmi
📚 Module : Virtualisation de Base

---

# 🎯 Objectif

Dans ce TP, nous allons apprendre à créer une machine virtuelle KVM en ligne de commande avec :

✔ KVM
✔ QEMU
✔ libvirt
✔ virt-install

👉 Sans utiliser l’interface graphique.

---

# 🧠 Contexte

💬 Prof :

> En entreprise, les administrateurs système travaillent souvent sans interface graphique.
>
> Aujourd’hui, nous allons créer une VM uniquement avec le terminal Linux 😎

---

# 🖥️ Informations de la VM

| Paramètre | Valeur                           |
| --------- | -------------------------------- |
| Nom VM    | kvmmv                            |
| OS        | Ubuntu 16.04                     |
| RAM       | 2 GB                             |
| CPU       | 1 vCPU                           |
| Disque    | 10 GB                            |
| Réseau    | NAT par défaut                   |
| ISO       | ubuntu-16.04.7-desktop-amd64.iso |

---

# 📁 Étape 1 — Vérifier l’ISO Ubuntu

Dans votre dossier Téléchargements :

```bash
cd ~/Téléchargements
```

Vérifier le fichier ISO :

```bash
ls
```

Vous devez voir :

```text
ubuntu-16.04.7-desktop-amd64.iso
```

---

# 💾 Étape 2 — Vérifier l’espace disque disponible

Avant de créer une VM, il faut vérifier que le système possède assez d’espace disque.

Commande :

```bash
df -h
```

Exemple :

```text
Sys. de fichiers Taille Utilisé Dispo Uti% Monté sur
/dev/sda2           20G     16G  3,1G  84% /
```

⚠️ Important :

Si l’espace libre est inférieur à la taille du disque virtuel demandée, `virt-install` affichera une erreur.

Exemple :

```text
allocation requiert 10240 M > 4212 M sont disponibles
```

👉 Solution :

* réduire la taille du disque virtuel
* supprimer des fichiers inutiles
* ou agrandir le disque VMware/VirtualBox

---

# 🔍 Étape 3 — Vérifier KVM

Vérifier la virtualisation CPU :

```bash
lscpu | grep Virtualization
```

Exemple :

```text
Virtualization: VT-x
```

---

# 🔍 Étape 4 — Vérifier réseau KVM

Afficher les réseaux libvirt :

```bash
virsh net-list --all
```

Vous devez voir :

```text
default
```

---

# 🚀 Étape 5 — Créer la VM avec CLI

Commande complète :

```bash
virt-install \
--name kvmmv \
--ram 2048 \
--vcpus 1 \
--disk path=$HOME/kvmmv.qcow2,size=3 \
--cdrom ~/Téléchargements/ubuntu-16.04.7-desktop-amd64.iso \
--os-variant ubuntu16.04 \
--network network=default \
--graphics spice
```

---

# 🧠 Explication des paramètres

| Paramètre        | Rôle                |
| ---------------- | ------------------- |
| --name           | nom VM              |
| --ram 2048       | 2 GB RAM            |
| --vcpus 1        | 1 processeur        |
| --disk           | disque virtuel      |
| --cdrom          | ISO Ubuntu          |
| --network        | réseau NAT          |
| --graphics spice | interface graphique |

---

# 🔄 Étape 6 — Partage d’une image ISO entre plusieurs VMs

Par défaut, libvirt peut détecter qu’une image ISO est déjà utilisée par une autre VM.

Exemple d’erreur :

```text
Le disque ISO est déjà utilisé par d’autres invités
```

👉 Pour autoriser le partage de la même image ISO :

```bash
virt-install \
--name kvmmv \
--ram 2048 \
--vcpus 1 \
--disk path=$HOME/kvmmv.qcow2,size=3 \
--cdrom ~/Téléchargements/ubuntu-16.04.7-desktop-amd64.iso \
--os-variant ubuntu16.04 \
--network network=default \
--graphics spice \
--check path_in_use=off
```

🧠 Explication :

| Paramètre               | Rôle                                                |
| ----------------------- | --------------------------------------------------- |
| --check path_in_use=off | autorise plusieurs VMs à utiliser la même image ISO |

👉 Très utile dans les laboratoires de virtualisation.

---

# 📂 Étape 7 — Vérifier création du disque

Si le disque est stocké dans `/var/lib/libvirt/images/` :

```bash
ls /var/lib/libvirt/images/
```

Sinon si le disque est dans le dossier personnel :

```bash
ls $HOME/
```

Vous devez voir :

```text
kvmmv.qcow2
```

---

# 🖥️ Étape 8 — Vérifier les VMs

```bash
virsh list --all
```

Résultat attendu :

```text
 Id   Name    State
------------------------
 1    kvmmv   running
```

---

# ⚙️ Étape 9 — Démarrer et arrêter VM

## ▶ Démarrer

```bash
virsh start kvmmv
```

## ⏹ Arrêter

```bash
virsh shutdown kvmmv
```

---

# 🔍 Étape 10 — Informations VM

```bash
virsh dominfo kvmmv
```

---

# 🌐 Étape 11 — Vérifier IP de la VM

```bash
virsh net-dhcp-leases default
```

---

# 📋 Livrables

✔ Création VM `kvmmv`
✔ Capture `virsh list --all`
✔ Capture installation Ubuntu
✔ Vérification disque `.qcow2`
✔ Vérification espace disque avec `df -h`
✔ Vérification partage ISO entre plusieurs VMs

---

# ❓ Questions

### 1️⃣ Pourquoi utilise-t-on `virt-install` ?

👉 Pour créer et gérer des machines virtuelles directement en ligne de commande.

---

### 2️⃣ Quel est le rôle de `libvirt` ?

👉 `libvirt` permet de gérer les machines virtuelles, réseaux et stockages KVM/QEMU.

---

### 3️⃣ Pourquoi le disque est en `.qcow2` ?

👉 Parce que `qcow2` supporte :

* snapshots
* compression
* allocation dynamique
* clonage

---

### 4️⃣ Quelle différence entre GUI et CLI ?

| GUI                      | CLI                    |
| ------------------------ | ---------------------- |
| interface graphique      | terminal               |
| plus simple              | plus rapide            |
| consomme plus ressources | léger                  |
| adapté débutants         | adapté administrateurs |

---

### 5️⃣ Pourquoi KVM est performant ?

👉 Parce qu’il utilise directement les extensions matérielles du processeur :

* Intel VT-x
* AMD-V

et fonctionne dans le noyau Linux.

---

# 🎓 Conclusion

💬 Prof :

> Aujourd’hui…
>
> 👉 vous avez créé votre première machine virtuelle KVM en ligne de commande.
>
> 👉 vous avez vérifié l’espace disque disponible.
>
> 👉 vous avez appris à partager une image ISO entre plusieurs VMs.
>
> Et cela représente exactement la manière dont travaillent les administrateurs système dans les infrastructures professionnelles 🚀

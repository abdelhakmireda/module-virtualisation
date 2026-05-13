# 🧪 🎓 TP 06 — Création d’une Machine Virtuelle KVM avec CLI

👨‍🏫 **Responsable : Reda Abdelhakmi**
📚 **Module : Virtualisation de Base**

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

💬 **Prof :**

En entreprise, les administrateurs système travaillent souvent sans interface graphique.

Aujourd’hui, nous allons créer une VM uniquement avec le terminal Linux 😎

---

# 🖥️ Informations de la VM

| Paramètre | Valeur                           |
| --------- | -------------------------------- |
| Nom VM    | `kvmmv`                          |
| OS        | Ubuntu 16.04                     |
| RAM       | 2 GB                             |
| CPU       | 1 vCPU                           |
| Disque    | 10 GB                            |
| Réseau    | NAT par défaut                   |
| ISO       | ubuntu-16.04.7-desktop-amd64.iso |

---

# 📁 Étape 1 — Vérifier l’ISO Ubuntu

Dans votre dossier Téléchargements :

```bash id="k0g2yk"
cd ~/Téléchargements
```

Vérifier le fichier ISO :

```bash id="6gzjlwm"
ls
```

Vous devez voir :

```bash id="8lwwxv"
ubuntu-16.04.7-desktop-amd64.iso
```

---

# 🔍 Étape 2 — Vérifier KVM

Vérifier virtualisation :

```bash id="5bmqta"
lscpu | grep Virtualization
```

---

# 🔍 Étape 3 — Vérifier réseau KVM

Afficher réseaux libvirt :

```bash id="szvnl3"
virsh net-list --all
```

Vous devez voir :

```bash id="31eq1z"
default
```

---

# 🚀 Étape 4 — Créer la VM avec CLI

Commande complète :

```bash id="rx3zrs"
virt-install \
--name kvmmv \
--ram 2048 \
--vcpus 1 \
--disk path=/var/lib/libvirt/images/kvmmv.qcow2,size=10 \
--cdrom ~/Téléchargements/ubuntu-16.04.7-desktop-amd64.iso \
--os-type linux \
--network network=default \
--graphics spice
```

---

# 🧠 Explication des paramètres

| Paramètre          | Rôle                |
| ------------------ | ------------------- |
| `--name`           | nom VM              |
| `--ram 2048`       | 2 GB RAM            |
| `--vcpus 1`        | 1 processeur        |
| `--disk`           | disque virtuel      |
| `--cdrom`          | ISO Ubuntu          |
| `--network`        | réseau NAT          |
| `--graphics spice` | interface graphique |

---

# 📂 Étape 5 — Vérifier création du disque

```bash id="5fk2pc"
ls /var/lib/libvirt/images/
```

Vous devez voir :

```bash id="z7g0r9"
kvmmv.qcow2
```

---

# 🖥️ Étape 6 — Vérifier les VMs

```bash id="jlwmfh"
virsh list --all
```

Résultat attendu :

```bash id="jlwmfh"
 Id   Name    State
------------------------
 1    kvmmv   running
```

---

# ⚙️ Étape 7 — Démarrer et arrêter VM

## Démarrer

```bash id="bgk7na"
virsh start kvmmv
```

## Arrêter

```bash id="m7j5z9"
virsh shutdown kvmmv
```

---

# 🔍 Étape 8 — Informations VM

```bash id="4t7v5y"
virsh dominfo kvmmv
```

---

# 🌐 Étape 9 — Vérifier IP de la VM

```bash id="gk3mtt"
virsh net-dhcp-leases default
```

---

# 📋 Livrables

✔ Création VM `kvmmv`
✔ Capture `virsh list --all`
✔ Capture installation Ubuntu
✔ Vérification disque `.qcow2`

---

# ❓ Questions

1️⃣ Pourquoi utilise-t-on `virt-install` ?
2️⃣ Quel est le rôle de libvirt ?
3️⃣ Pourquoi le disque est en `.qcow2` ?
4️⃣ Quelle différence entre GUI et CLI ?
5️⃣ Pourquoi KVM est performant ?

---

# 🎓 Conclusion

💬 **Prof :**

Aujourd’hui…

👉 vous avez créé votre première machine virtuelle KVM en ligne de commande.

Et cela représente exactement la manière dont travaillent les administrateurs système dans les infrastructures professionnelles 🚀

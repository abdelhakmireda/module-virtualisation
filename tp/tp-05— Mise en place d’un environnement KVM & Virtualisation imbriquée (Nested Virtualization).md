
---

# 🧪 📘 🎓 TP 05 — Mise en place d’un environnement KVM sous VMware & Création de Mini VMs Linux

👨‍🏫 Responsable : Reda Abdelhakmi
📚 Module : Virtualisation de Base
🖥️ Environnement : VMware Workstation Pro + Ubuntu (Nested Virtualization)

---

# 🎯 Objectifs

À la fin de ce TP, l’étudiant sera capable de :

✔ Comprendre la virtualisation imbriquée (Nested Virtualization)
✔ Installer KVM dans une machine virtuelle Ubuntu
✔ Configurer un environnement de virtualisation professionnel
✔ Créer des machines virtuelles Linux légères (mini VMs)
✔ Organiser un mini laboratoire virtualisé

---

# 🧠 Contexte du TP

💬 Prof :

> Jusqu’ici vous utilisiez VMware pour créer des VMs…
> 👉 aujourd’hui, vous allez créer un hyperviseur **dans une VM**

👉 C’est ce qu’on appelle :

➡️ **Nested Virtualization**

---

## 🖧 Architecture du TP

```bash
💻 Machine Physique
    ↓
🖥️ VMware Workstation
    ↓
🐧 VM Ubuntu (6GB RAM / 30GB Disk)
    ↓
🔥 KVM + QEMU + libvirt
    ↓
📦 Mini VMs Linux
```

---

💬 Prof :

> Vous allez créer un mini Data Center… dans une VM 😄

---

# 📌 PARTIE 1 — Création de la VM Ubuntu (VMware)

Créer une VM avec :

| Ressource | Valeur |
| --------- | ------ |
| RAM       | 6 GB   |
| CPU       | 2–4    |
| Disk      | 30 GB  |
| Network   | NAT    |

---

## ⚠️ Activation de la virtualisation imbriquée

Dans VMware :

👉 VM Settings → Processor

✔ Activer :

```bash
Virtualize Intel VT-x/EPT or AMD-V/RVI
```

---

💬 Prof :

> Sans cette option… KVM ne fonctionnera pas ❌

---

# 🧠 PARTIE 2 — Vérification dans Ubuntu

Dans la VM Ubuntu :

```bash
lscpu | grep Virtualization
```

👉 Résultat attendu :

✔ VT-x ou AMD-V

---

# ⚙️ PARTIE 3 — Installation de KVM

```bash
sudo apt update
sudo apt install qemu-kvm libvirt-daemon-system libvirt-clients bridge-utils virt-manager -y
```

---

## 🔍 Vérification

```bash
sudo systemctl status libvirtd
```

✔ active (running)

---

## 👤 Configuration utilisateur

```bash
sudo usermod -aG libvirt $USER
```

👉 redémarrer session

---

## 🔍 Vérifier modules KVM

```bash
lsmod | grep kvm
```

✔ kvm_intel ou kvm_amd

---

# 🖥️ PARTIE 4 — Lancer KVM

```bash
virt-manager
```

---

💬 Prof :

> Vous êtes maintenant dans un hyperviseur…
> 👉 à l’intérieur d’une VM 😎

---

# 🧪 PARTIE 5 — Création des mini VMs Linux

---

## 🎯 Objectif

Créer des machines légères pour simulation réseau / serveur.

---

## 📥 Choix des OS (au choix)

✔ Ubuntu Server (recommandé)
✔ Debian minimal
✔ Alpine Linux (léger)

---

## ⚙️ Configuration des mini VMs

| Ressource | Valeur        |
| --------- | ------------- |
| RAM       | 512 MB – 1 GB |
| CPU       | 1             |
| Disk      | 5 – 10 GB     |

---

💬 Prof :

> Optimisez vos ressources…
> 👉 comme un vrai administrateur système

---

## 🖥️ Étapes

1️⃣ Create new VM
2️⃣ Choisir ISO
3️⃣ Configurer ressources
4️⃣ Installer OS

---

# 🧠 PARTIE 6 — Organisation du laboratoire

Créer plusieurs VMs :

```bash
KVM Host (Ubuntu)
 ├── VM1 : client-linux
 ├── VM2 : client-linux
 ├── VM3 : serveur-ssh
```

---

💬 Prof :

> Une VM seule ne sert à rien…
> 👉 ce qui compte, c’est l’interconnexion

---

# 🌐 PARTIE 7 — Tests

Dans les VMs :

```bash
ip a
```

```bash
ping <IP_VM>
```

---

## 🔐 Test SSH (optionnel)

Dans serveur :

```bash
sudo apt install openssh-server
```

Depuis client :

```bash
ssh user@IP_SERVEUR
```

---

# ⚠️ PARTIE 8 — Limites du lab

| Limite      | Explication           |
| ----------- | --------------------- |
| Performance | double virtualisation |
| RAM         | limitée à 6GB         |
| CPU         | partagé               |
| réseau      | simulation            |

---

💬 Prof :

> Ce n’est pas un vrai Data Center…
> 👉 mais c’est une excellente simulation

---

# ❓ Questions

1️⃣ Qu’est-ce que la virtualisation imbriquée ?
2️⃣ Pourquoi activer VT-x dans VMware ?
3️⃣ Quel rôle de KVM dans ce TP ?
4️⃣ Pourquoi utiliser des VMs légères ?
5️⃣ Quelle différence entre VMware et KVM ?

---

# 📋 Livrables

✔ Capture configuration VMware (6GB RAM)
✔ Capture activation VT-x
✔ Capture installation KVM
✔ Capture virt-manager
✔ Capture mini VMs créées
✔ Capture test ping
✔ (optionnel) Capture SSH

---

---

# ⚠️ 🛠️ PARTIE 9 — Résolution des problèmes (Virtualisation VMware / KVM)

---

## 🎯 Objectif

Aider l’étudiant à résoudre les problèmes liés à :

❌ impossibilité d’activer VT-x dans VMware
❌ erreur “Virtualized Intel VT-x/EPT is not supported”
❌ KVM qui ne fonctionne pas

---

# 🧪 1️⃣ Vérification sous Windows (CMD)

👉 Ouvrir **Invite de commandes (CMD) en administrateur**

```bash
systeminfo
```

---

## 🔍 Vérifier cette partie :

👉 Si vous voyez :

```text
Un hyperviseur a été détecté
```

❌ PROBLÈME → Hyper-V actif (bloque VMware)

---

## ✅ Résultat attendu :

✔ PAS de ligne “hyperviseur détecté”
✔ Virtualisation activée : Oui

---

# ⚠️ 2️⃣ Problème principal

💬 Prof :

> Si un hyperviseur est détecté…
> 👉 VMware ne peut pas utiliser la virtualisation matérielle

👉 Donc :

❌ KVM ne fonctionnera pas
❌ virt-manager échouera

---

# 🔧 3️⃣ Solution — Désactiver Hyper-V (OBLIGATOIRE)

---

## 🧪 Étape 1 — CMD (Admin)

```bash
bcdedit /set hypervisorlaunchtype off
```

---

## 🧪 Étape 2 — Désactiver fonctionnalités Windows

```bash
dism.exe /Online /Disable-Feature:Microsoft-Hyper-V-All
```

```bash
dism.exe /Online /Disable-Feature:VirtualMachinePlatform
```

```bash
dism.exe /Online /Disable-Feature:HypervisorPlatform
```

```bash
dism.exe /Online /Disable-Feature:Containers-DisposableClientVM
```

---

## 🧪 Étape 3 — Désactiver sécurité VBS

```bash
reg add "HKLM\System\CurrentControlSet\Control\DeviceGuard" /v EnableVirtualizationBasedSecurity /t REG_DWORD /d 0 /f
```

```bash
reg add "HKLM\System\CurrentControlSet\Control\Lsa" /v LsaCfgFlags /t REG_DWORD /d 0 /f
```

---

## 🔁 Étape 4 — Redémarrage

```bash
shutdown /r /t 0
```

---

# 🧪 4️⃣ Vérification après correction

```bash
systeminfo
```

---

## ✅ Résultat attendu :

✔ Plus de ligne “hyperviseur détecté”
✔ Virtualisation activée

---

# ⚙️ 5️⃣ Configuration VMware

👉 Dans VMware :

✔ Activer :

```
Virtualize Intel VT-x/EPT or AMD-V/RVI
```

✔ Activer :

```
Virtualize IOMMU
```

❌ Désactiver :

```
Virtualize CPU performance counters
```

---

# 🧠 6️⃣ Vérification dans Ubuntu (KVM)

```bash
lscpu | grep Virtualization
```

```bash
lsmod | grep kvm
```

---

## ✅ Résultat attendu :

✔ VT-x ou AMD-V
✔ kvm_intel ou kvm_amd

---

# 🎓 Conclusion

💬 Prof :

> Aujourd’hui… vous avez fait quelque chose de très avancé.

👉 Vous avez créé un hyperviseur… dans une machine virtuelle

👉 Vous avez simulé une infrastructure complète

---

### ✅ Image recommandée

**Alpine Linux Virt x86_64 ISO**
Lien officiel : ([alpinelinux.org][1])
Téléchargement direct dossier : ([dl-cdn.alpinelinux.org][2])

Prends ce fichier :

```text
alpine-virt-3.23.0-x86_64.iso
```

Ou la version la plus récente affichée dans le dossier officiel.

### Commande dans Ubuntu

```bash
cd ~/Downloads
wget https://dl-cdn.alpinelinux.org/alpine/latest-stable/releases/x86_64/alpine-virt-3.23.0-x86_64.iso
```

### Configuration conseillée dans virt-manager

```text
OS : Alpine Linux
RAM : 512 MB
CPU : 1
Disque : 5 GB
Réseau : NAT
Image : alpine-virt-3.23.0-x86_64.iso
```

### Alternative plus simple pour étudiants

**Ubuntu Server Cloud Image 24.04** existe aussi officiellement, mais elle est moins directe pour débutants car elle demande souvent cloud-init/login SSH. ([cloud-images.ubuntu.com][3])

Donc pour ton TP : **Alpine Virt ISO est le meilleur choix**.





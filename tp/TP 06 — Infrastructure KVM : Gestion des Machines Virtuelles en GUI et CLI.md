
---

# 🧪 🎓 TP 06 — Infrastructure KVM (GUI + CLI)

## 🎯 Objectif

👉 Construire une infrastructure KVM complète avec :

* Création de VMs
* Réseau
* SSH
* Serveur Web

👉 En utilisant :

* 🖥️ **virt-manager (interface graphique)**
* ⚙️ **virsh / ligne de commande**

---

# 🧠 Contexte

💬 Prof :

> En entreprise, vous avez deux profils :
>
> 👉 Administrateur junior → utilise interface graphique
> 👉 Administrateur système → travaille en ligne de commande
>
> Aujourd’hui… vous allez faire les deux 😎

---

# 🖥️ PARTIE 1 — VERSION GUI (virt-manager)

## 1️⃣ Lancer interface

```bash
virt-manager
```

---

## 2️⃣ Créer VM (client-linux)

👉 Create new VM
👉 Local install media (ISO)

### Configuration :

| Paramètre | Valeur |
| --------- | ------ |
| RAM       | 512 MB |
| CPU       | 1      |
| Disk      | 5 GB   |
| Network   | NAT    |

👉 Installer Alpine ou Ubuntu Server

---

## 3️⃣ Créer autres VMs

👉 Faire la même chose pour :

* serveur-ssh
* serveur-web

---

## 4️⃣ Vérifier réseau

Dans chaque VM :

```bash
ip a
```

---

## 5️⃣ Tester communication

```bash
ping IP_VM
```

---

## 6️⃣ Installer services

### SSH :

```bash
sudo apt install openssh-server -y
```

### WEB :

```bash
sudo apt install apache2 -y
```

---

## 7️⃣ Test depuis client

```bash
ssh user@IP
curl http://IP
```

---

# ⚙️ PARTIE 2 — VERSION CLI (niveau PRO 🔥)

💬 Prof :

> Là… on quitte l’interface graphique
> 👉 Bienvenue dans le monde des administrateurs système

---

## 1️⃣ Voir les VMs

```bash
virsh list --all
```

---

## 2️⃣ Démarrer une VM

```bash
virsh start nom-vm
```

---

## 3️⃣ Arrêter VM

```bash
virsh shutdown nom-vm
```

---

## 4️⃣ Accéder console VM

```bash
virsh console nom-vm
```

👉 quitter avec :

```
CTRL + ]
```

---

## 5️⃣ Voir réseau KVM

```bash
virsh net-list --all
```

---

## 6️⃣ Infos VM

```bash
virsh dominfo nom-vm
```

---

## 7️⃣ Créer VM en ligne de commande (niveau avancé)

```bash
virt-install \
--name client-cli \
--ram 512 \
--vcpus 1 \
--disk size=5 \
--cdrom alpine.iso \
--os-type linux \
--network network=default \
--graphics none
```

💬 Prof :

> Ici… vous créez une VM sans interface graphique
> 👉 comme dans un Data Center réel

---

# 🔥 BONUS — Automatisation

Créer plusieurs VMs rapidement :

```bash
for i in 1 2 3
do
virt-install \
--name vm$i \
--ram 512 \
--vcpus 1 \
--disk size=5 \
--cdrom alpine.iso \
--network network=default \
--graphics none
done
```

---

# 📋 Livrables

✔ VM créée avec GUI
✔ VM créée avec CLI
✔ Test ping
✔ Test SSH
✔ Test serveur web
✔ Capture virsh list

---

# ❓ Questions

1. Quelle différence entre GUI et CLI ?
2. Pourquoi CLI est utilisée en entreprise ?
3. Quel avantage de virsh ?
4. Pourquoi automatiser avec script ?

---

# 🎓 Conclusion (style prof)

💬 Prof :

> Aujourd’hui vous avez franchi un cap.
>
> 👉 Vous savez créer une VM avec interface
> 👉 Mais surtout… vous savez le faire en ligne de commande
>
> 👉 Et ça… c’est ce qui fait la différence entre un étudiant… et un administrateur système 🔥

---



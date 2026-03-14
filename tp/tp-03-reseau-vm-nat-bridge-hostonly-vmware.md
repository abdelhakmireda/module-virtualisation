

# 🧪 TP 03 — Réseau des Machines Virtuelles (NAT / Bridge / Host-Only)

👨‍🏫 Responsable : **Reda Abdelhakmi**
📚 Module : **Virtualisation de Base**
🖥️ Hyperviseur : **VMware Workstation Pro 17**
🐧 OS invité : **Ubuntu 24.xx**

---

# 🎯 Objectifs

À la fin du TP, l’étudiant sera capable de :

✔ Identifier l’adresse IP d’une machine virtuelle
✔ Tester la connectivité réseau
✔ Comprendre les modes **NAT / Bridge / Host-Only**
✔ Configurer l’adaptateur réseau dans **VMware Pro**
✔ Tester la communication entre machines virtuelles

---

# 📌 Prérequis

Avant de commencer :

✔ VMware Workstation Pro installé
✔ Une VM Ubuntu fonctionnelle
✔ Terminal Linux accessible
✔ Connexion internet

---

# 🔹 PARTIE 1 — Vérification réseau de base (Terminal Ubuntu)

## 1️⃣ Ouvrir le Terminal

```bash
Ctrl + Alt + T
```

---

## 2️⃣ Vérifier l’adresse IP

Commande :

```bash
ip a
```

Chercher l’interface réseau :

```
ens33
```

Exemple d’IP :

```
192.168.159.128
```

---

## 3️⃣ Tester la connexion internet

Commande :

```bash
ping google.com
```

Résultat attendu :

```
64 bytes from ...
```

Pour arrêter :

```
Ctrl + C
```

---

# 🌐 PARTIE 2 — Comprendre le Mode NAT

Par défaut VMware utilise **NAT**.

Architecture :

```
VM → VMware NAT → PC Hôte → Internet
```

Avantages :

✔ simple
✔ internet immédiat

Inconvénient :

❌ VM difficile à atteindre depuis le réseau local.

---

## Test NAT

Commande :

```bash
ip route
```

Résultat exemple :

```
default via 192.168.159.2
```

Cela signifie que **VMware agit comme routeur**.

---

# 🏢 PARTIE 3 — Passage en Mode Bridge

## 1️⃣ Éteindre la VM

Commande :

```bash
sudo poweroff
```

---

## 2️⃣ Modifier le réseau dans VMware

Dans VMware :

```
VM → Settings → Network Adapter
```

Choisir :

```
Bridged
```

Valider puis **démarrer la VM**.

---

## 3️⃣ Vérifier la nouvelle IP

Dans Ubuntu :

```bash
ip a
```

Nouvelle IP attendue :

```
192.168.1.xx
```

Cela signifie que la VM est **directement sur le réseau local**.

---

# 🌍 PARTIE 4 — Test de Connectivité Réseau

Tester communication avec le routeur :

```bash
ping 192.168.1.1
```

Tester internet :

```bash
ping google.com
```

---

# 🔒 PARTIE 5 — Mode Host-Only

Ce mode crée un réseau **isolé**.

Les machines peuvent communiquer :

✔ entre elles
✔ avec le PC hôte

❌ pas d’internet

---

## 1️⃣ Éteindre la VM

```bash
sudo poweroff
```

---

## 2️⃣ Modifier réseau

Dans VMware :

```
VM → Settings → Network Adapter
```

Choisir :

```
Host-Only
```

---

## 3️⃣ Redémarrer VM

Dans Ubuntu :

```bash
ip a
```

Exemple IP :

```
192.168.56.xx
```

---

## 4️⃣ Tester Internet

```bash
ping google.com
```

Résultat attendu :

```
Network unreachable
```

Cela prouve que **Host-Only est isolé**.

---

# 🖧 PARTIE 6 — Communication entre deux VMs

Créer **une deuxième VM Ubuntu** (clone possible).

Dans **VM1** :

```bash
ip a
```

Exemple :

```
192.168.56.101
```

Dans **VM2** :

```bash
ping 192.168.56.101
```

Si la communication fonctionne :

```
64 bytes from 192.168.56.101
```

Les deux machines communiquent **via le switch virtuel VMware**.

---

# ⚖️ PARTIE 7 — Analyse Comparative

Compléter le tableau :

| Mode réseau | Internet | Visible réseau local | Usage             |
| ----------- | -------- | -------------------- | ----------------- |
| NAT         | ✔        | ❌                    | usage simple      |
| Bridge      | ✔        | ✔                    | simulation réseau |
| Host-Only   | ❌        | ❌                    | laboratoire       |

---

# ❓ Questions

1️⃣ Quelle commande permet de connaître l’adresse IP ?

2️⃣ Quelle différence entre **NAT et Bridge** ?

3️⃣ Pourquoi le mode **Host-Only n’a pas internet** ?

4️⃣ Dans quel cas utiliser le mode **Bridge** ?

5️⃣ Quel est le rôle du **switch virtuel VMware** ?

---

# 📋 Livrables

Chaque étudiant doit fournir :

✔ Capture écran **commande ip a**
✔ Capture écran **test ping google.com**
✔ Capture écran **configuration NAT**
✔ Capture écran **configuration Bridge**
✔ Capture écran **test communication entre VMs**

---

# 🎓 Conclusion du TP

Ce TP démontre :

✔ comment fonctionne **le réseau des machines virtuelles**
✔ la différence entre **NAT / Bridge / Host-Only**
✔ l’importance du **switch virtuel**
✔ comment les VMs communiquent dans un laboratoire

Ces compétences sont essentielles pour :

☁️ Cloud Computing
🔐 Cybersécurité
🧪 Laboratoires réseaux
🏢 Infrastructure virtualisée

---



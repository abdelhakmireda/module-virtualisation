

# 📘 🎓 Séance 07 — Introduction à KVM & Virtualisation Native Linux

👨‍🏫 Responsable : Reda Abdelhakmi
📚 Module : Virtualisation de Base

---

## 🎬 Introduction (prise de parole)

Chers étudiants 👨‍🎓👩‍🎓,

Lors de la séance précédente, nous avons compris :

✔ les limites de VMware
✔ la différence entre labo et production
✔ la notion d’infrastructure virtuelle

👉 Aujourd’hui… on change de niveau.

💬 Prof :

> Jusqu’ici vous utilisiez un simulateur…
>
> Aujourd’hui, vous allez utiliser une vraie technologie de production.

---

## 🧠 1️⃣ C’est quoi KVM ?

📜 Définition :

KVM (Kernel-based Virtual Machine) est une technologie de virtualisation intégrée dans le noyau Linux.

👉 Cela signifie :

✔ Linux devient un hyperviseur
✔ pas besoin d’un logiciel lourd comme VMware

---

💬 Prof :

> Imaginez que votre système Linux… devient lui-même VMware 😄

---

## 🏗️ 2️⃣ Architecture KVM

```
Machines virtuelles
        ↓
KVM (dans le noyau Linux)
        ↓
Matériel physique
```

---

💬 Prof :

> Ici… il n’y a plus d’intermédiaire inutile.
>
> 👉 accès direct au matériel = performance 🚀

---

## ⚖️ 3️⃣ VMware vs KVM

| Critère     | VMware Workstation | KVM         |
| ----------- | ------------------ | ----------- |
| Type        | Type 2             | Type 1      |
| Performance | Moyenne            | Élevée      |
| OS requis   | Windows/Linux      | Linux       |
| Usage       | Labo               | Data Center |

---

💬 Prof :

> VMware = apprendre
> KVM = travailler

---

## ⚙️ 4️⃣ Prérequis KVM

Pour utiliser KVM :

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

## 🧩 5️⃣ Les composants de KVM

KVM fonctionne avec :

✔ QEMU → moteur de virtualisation
✔ libvirt → gestion
✔ virt-manager → interface graphique

---

💬 Prof :

> KVM seul ne suffit pas…
> c’est un écosystème.

---

## 🧠 6️⃣ Pourquoi KVM est utilisé en entreprise ?

✔ open source
✔ performant
✔ stable
✔ scalable

---

### 🎓 Exemple réel

✔ Proxmox
✔ OpenStack
✔ Cloud privé

---

💬 Prof :

> Quand vous utilisez le cloud…
> il y a souvent KVM derrière.

---

## 🔄 7️⃣ Transition pédagogique

💬 Prof :

> Avant : vous cliquiez dans VMware
>
> Maintenant : vous allez comprendre ce qu’il y a derrière.

---

## 🎯 Synthèse

✔ KVM = virtualisation native
✔ meilleures performances
✔ utilisé en production
✔ base du cloud

---

## ❓ Questions

1️⃣ Pourquoi KVM est plus performant ?
2️⃣ Quelle différence Type 1 / Type 2 ?
3️⃣ Quel rôle de QEMU ?
4️⃣ Pourquoi Linux est obligatoire ?
5️⃣ Où utilise-t-on KVM ?

---

## 🎓 Conclusion

💬 Prof :

> Aujourd’hui… vous venez de franchir un cap.
>
> 👉 Vous entrez dans la virtualisation professionnelle.


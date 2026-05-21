# LAB1-Security / Préparation d’un environnement Android Security 
<img width="681" height="382" alt="image" src="https://github.com/user-attachments/assets/750f04c5-7b1e-4fbd-bd4a-47861f6452d3" />


## Objectif du TP

Ce TP consiste à préparer un environnement de cybersécurité Android permettant :

* l’analyse d’applications Android,
* l’utilisation d’ADB,
* la communication entre une VM Linux et une cible Android,
* la création d’un environnement reproductible grâce aux snapshots.

---

# Environnement utilisé

| Élément             | Description                         |
| ------------------- | ----------------------------------- |
| VirtualBox / VMware | Virtualisation                      |
| Mobexler            | VM Linux dédiée à l’analyse Android |
| Android Device      | Smartphone ou émulateur             |
| ADB                 | Communication Android Debug Bridge  |

---

# Étape 1 — Téléchargement de Mobexler

Téléchargement du fichier OVA :

```text id="cbrcif"
Mobexler.ova
```

Lien officiel :

```text id="6mb6ju"
https://drive.google.com/file/d/1rd8g3bmK_XMTtb6PlcfIwjyoJ-mEhAk5/view
```

## Vérification SHA256

### Windows

```powershell id="zk4ol4"
Get-FileHash .\Mobexler.ova -Algorithm SHA256
```

### Linux/macOS

```bash id="ccjlwm"
sha256sum Mobexler.ova
```

---

# Étape 2 — Importation dans VirtualBox

## Import de l’OVA

```text id="l8y4cm"
File → Import Appliance
```

Sélection :

```text id="myk3cp"
Mobexler.ova
```

---

# Configuration réseau

## Adapter 1

```text id="r4phkx"
NAT
```

Permet :

* accès Internet,
* mises à jour,
* téléchargement d’outils.

---

## Adapter 2

```text id="g0kj9z"
Host-Only Adapter
```

Permet :

* communication privée avec Android,
* réseau de laboratoire isolé.

---

# Étape 3 — Premier démarrage

## Connexion

### Username

```text id="c2m0ig"
mobexler
```

### Password

```text id="th7j8g"
mobexler
```

---

# Étape 4 — Vérification réseau

## Vérifier les interfaces

```bash id="sl6d5q"
ip a
```

---

## Vérifier la route

```bash id="53vgh7"
ip route
```

---

## Tester Internet

```bash id="k0n5v8"
ping -c 2 8.8.8.8
ping -c 2 google.com
```

---

# Étape 5 — Création du snapshot

Nom du snapshot :

```text id="j5cshz"
CLEAN_BASELINE_TP1
```

Description :

```text id="jlwmh8"
Import OK, NAT+HostOnly OK, boot OK, prêt ADB
```

---

# Étape 6 — Préparation Android

## Activation USB Debugging

Chemin :

```text id="6uwj7w"
Settings → Developer Options → USB Debugging
```

---

# Vérification ADB

## Vérifier version

```bash id="m2sr4m"
adb version
```

## Vérifier appareils

```bash id="1ldzui"
adb devices
```

---

# Résultat attendu

Le téléphone Android doit apparaître :

```text id="h8rx2m"
device
```

---

# Conclusion

Ce TP permet de préparer un laboratoire Android destiné :

* au pentest mobile,
* au reverse engineering,
* à l’analyse réseau Android,
* à l’utilisation d’ADB et des outils de cybersécurité mobile.

# Auteur
ASSEKNOUR Sana
ENSA Marrakech - Cybersecurity

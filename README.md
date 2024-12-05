# **LabConnect : Simulation d'Attaque Réseau avec GNS3**

## **Description**
LabConnect est un projet collaboratif visant à créer un laboratoire réseau pédagogique. Ce laboratoire permet aux étudiants d'explorer, configurer et tester des concepts avancés en réseau et cybersécurité à l'aide de simulations réalistes dans GNS3.

Les étudiants pourront apprendre à :
- Concevoir des topologies réseau.
- Configurer des équipements et des protocoles réseau.
- Simuler des attaques et des défenses réseau.
- Analyser le trafic réseau et rédiger des rapports professionnels.

---

## **Objectifs Pédagogiques**
1. Renforcer les compétences techniques en réseau et cybersécurité.
2. Comprendre les mécanismes des attaques et des défenses réseau.
3. Acquérir des compétences pratiques en configuration et en simulation réseau.
4. Apprendre à documenter et présenter des résultats techniques.

---

## **Topologie Réseau**
La topologie de base inclut :
- **1 PC attaquant** : Simule les attaques réseau.
- **2 PC victimes** : Représentent les cibles des attaques.
- **1 switch** : Interconnecte les appareils.
- **1 routeur** : Gère le routage entre les réseaux.

![Diagramme de topologie réseau](path/to/topology-diagram.png)

---

## **Étapes du Projet**

### **1. Création de la Topologie**
- Installer un switch dans GNS3.
- Ajouter un routeur dans GNS3.
- Configurer un PC attaquant et deux PC victimes.
- Connecter tous les appareils et vérifier la connectivité.

### **2. Configuration Réseau**
- Attribuer des adresses IP statiques aux appareils.
- Configurer la table de routage sur le routeur.
- Tester la connectivité avec des commandes ping.

### **3. Simulation des Scénarios d’Attaque**
- Scénario 1 : Scan réseau (avec Nmap).
- Scénario 2 : Attaque par déni de service (DoS).
- Scénario 3 : Man-in-the-Middle (avec ARP Spoofing).

### **4. Défense et Sécurité**
- Configurer des VLAN pour isoler les segments réseau.
- Mettre en place un pare-feu sur les victimes.
- Observer les attaques en temps réel avec Wireshark.

### **5. Documentation et Rapport**
- Générer des rapports techniques détaillés :
  - Analyse des attaques et de leurs impacts.
  - Efficacité des mécanismes de défense.
  - Recommandations pour renforcer la sécurité.
- Intégrer des captures d’écran et des logs pour illustrer les résultats.

---



## **Prérequis Techniques**
- **GNS3** : Version 2.2 ou supérieure.
- **Wireshark** : Pour analyser le trafic réseau.
- **Nmap** : Pour les scans réseau.
- **Kali Linux** (ou équivalent) : Pour simuler les attaques.
- **Outils de virtualisation** : VMware, VirtualBox ou QEMU (pour héberger les machines virtuelles).

---

## **Installation**

1. **Cloner le Référentiel**
   ```bash
   git clone https://github.com/ton-nom-utilisateur/LabConnect.git
   cd LabConnect



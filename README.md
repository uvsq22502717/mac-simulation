# mac-simulation
DES simulation of Mac protocol

# Simulation du protocole MAC : Exponential Backoff (2025-2026)

Ce dépôt contient le projet de simulation d'un protocole de contrôle d'accès au support (MAC) réalisé dans le cadre du cours de réseaux.

## 📋 Présentation du projet
L'objectif de ce projet est d'analyser les performances d'un réseau décentralisé composé de $N$ stations partageant un canal de communication unique. [cite_start]Nous étudions spécifiquement l'algorithme **Exponential Backoff**, utilisé pour gérer les collisions de manière autonome par chaque station.

### Principes du modèle
- **Arrivées** : Les paquets arrivent selon une loi exponentielle de paramètre $\lambda$.
- **Files d'attente** : Chaque station possède une file de capacité bornée $K$.
- **Transmission** : La durée d'émission est fixe (1 unité de temps).
- **Gestion des collisions** : En cas de collision dans l'état $i$, la station passe à l'état $i+1$ et attend un temps aléatoire de moyenne $2^i \tau$ avant de ré-émettre.

## 🛠 Structure du programmeLe simulateur est basé sur une architecture à **événements discrets (DES)** codée en Python. La structure est modulaire et orientée objet :

- `Station` : Gère l'état local, la file d'attente et la logique de backoff.
- `Canal` : Gère l'état du support et la détection des conflits temporels.
- `Event` : Définit les événements de simulation (ARRIVAL, START_TX, END_TX).
- `Statistics` : Module dédié à la collecte des métriques et à l'intégration temporelle des données.
- `run_simulation` : Fonction principale permettant d'exécuter un cycle complet de simulation.

##  Utilisation

### Prérequis
Le projet nécessite Python 3.x et les bibliothèques suivantes :
```bash
pip install numpy pandas matplotlib seaborn 

Exécution
Pour lancer une simulation et obtenir les indicateurs de performance :

# Exemple de paramètres
results = run_simulation(N=20, K=5, Lambda=0.1, Tau=0.5, T_max=10000)
print(f"Débit (Throughput) : {results['throughput']}")

Binôme
Volodymyr Grynenko
Flora Sambieni
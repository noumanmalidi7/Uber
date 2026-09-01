# 🚗 Analyse des courses Uber – Détection des zones chaudes à New York

## 📌 Contexte du projet
Uber souhaite réduire le temps d'attente des utilisateurs en recommandant aux chauffeurs les **zones chaudes (hot zones)** où la demande est la plus forte. L'enjeu est de passer d'une logique réactive à une logique proactive : anticiper les pics de demande pour positionner les véhicules au bon endroit et au bon moment.

Ce projet se concentre sur **New York** et utilise les données de courses d'avril à septembre 2014. L'objectif est double :
1. **Détecter** des zones géographiques cohérentes (clusters) où les pickups sont concentrés.
2. **Visualiser** ces zones sur des cartes interactives, par jour de semaine et par heure.

## 🎯 Objectifs principaux
- Créer un algorithme pour identifier les zones chaudes (hot zones).
- Visualiser les résultats sur un tableau de bord interactif (cartes Plotly).
- Décrire les hot zones par jour de la semaine.
- Comparer au moins deux algorithmes de clustering non supervisé : **KMeans** et **DBSCAN**.

## 📂 Structure du projet
Uber_HotZones/
│
├── uber_ds3.ipynb # Notebook principal (analyse complète)
├── requirements.txt # Dépendances Python
├── README.md # Ce fichier
│
├── uber-trip-data/ # Dossier contenant les données brutes
│ ├── uber-raw-data-apr14.csv
│ ├── uber-raw-data-may14.csv
│ ├── uber-raw-data-jun14.csv
│ ├── uber-raw-data-jul14.csv
│ ├── uber-raw-data-aug14.csv
│ ├── uber-raw-data-sep14.csv
│ └── uber-raw-data-janjune-15.csv # (Ignoré, car sans coordonnées GPS)
│
└── models/ # Dossier créé automatiquement pour le cache
├── kmeans_model.pkl # Modèle KMeans entraîné (sauvegardé)
└── dbscan_labels.npy # Labels DBSCAN (sauvegardés)

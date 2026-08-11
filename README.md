# 🎨 Raytracer Python

Un moteur de **ray tracing 3D développé en Python**, capable de générer des scènes composées de sphères et de surfaces planes avec gestion des **ombres, réflexions et différentes sources lumineuses**.

Le moteur effectue les calculs d'intersection, d'éclairage et de réflexion nécessaires au rendu de la scène et permet également de générer des **animations GIF** à partir de plusieurs images calculées successivement.

<p align="center">
  <img src="animation.gif" alt="Animation générée avec le raytracer" width="650">
</p>

## ✨ Fonctionnalités

- 🔵 Rendu de **sphères**
- 🧱 Rendu de **parallélogrammes** utilisés comme murs et surfaces
- 💡 Plusieurs types d'éclairage :
  - Lumière ambiante
  - Lumière ponctuelle
  - Lumière directionnelle
- 🌑 Gestion des **ombres portées**
- 🪞 Gestion des **réflexions récursives**
- 📷 Export du rendu au format **BMP**
- 🎞️ Génération d'**animations GIF**
- 📄 Chargement des scènes depuis un fichier texte

## 🧠 Principe du ray tracing

Le raytracer simule le trajet de rayons depuis la caméra vers chaque pixel de l'image.

Pour chaque rayon, le moteur recherche une intersection avec les objets présents dans la scène.

```text
Camera
   │
   │ Rayon
   ▼
   ●────────────► Objet
  Pixel             │
                    ├── Couleur
                    ├── Éclairage
                    ├── Ombre
                    │
                    └── Réflexion
                           │
                           └──► Nouveau rayon
```

La couleur finale d'un pixel dépend notamment :

- de l'objet intersecté ;
- de sa couleur ;
- des différentes sources lumineuses ;
- de la présence éventuelle d'un objet entre la lumière et le point calculé ;
- de la réflexion de la surface.

Les surfaces réfléchissantes peuvent générer de nouveaux rayons, permettant d'obtenir des **réflexions récursives**.

## 🛠️ Technologies

- **Python**
- Calcul vectoriel 3D
- Géométrie analytique
- Programmation orientée objet
- Génération d'images BMP
- Génération d'animations GIF

## 🚀 Installation

Cloner le repository puis installer les dépendances :

```bash
pip install -r requirements.txt
```

## ▶️ Utilisation

### Rendu d'une image

Lancer :

```bash
python3 main.py
```

Le programme charge la scène définie dans :

```text
scene.txt
```

puis génère :

```text
output.bmp
```

### Génération d'une animation

Lancer :

```bash
python3 animation.py
```

Le programme génère les différentes frames dans :

```text
frames/
```

puis crée l'animation finale :

```text
animation.gif
```

## 🌐 Définition d'une scène

Les objets et les sources lumineuses sont définis dans le fichier `scene.txt`.

### Sphère

```text
sphere x y z radius r g b specular reflective
```

avec :

- `x y z` : position du centre
- `radius` : rayon de la sphère
- `r g b` : couleur RGB
- `specular` : intensité de la réflexion spéculaire
- `reflective` : coefficient de réflexion

### Parallélogramme

```text
parallelogram Ax Ay Az Ux Uy Uz Vx Vy Vz r g b specular reflective
```

Le parallélogramme est défini à partir d'un point `A` et de deux vecteurs `U` et `V`.

### Lumière ambiante

```text
light ambient intensity
```

### Lumière ponctuelle

```text
light point intensity x y z
```

### Lumière directionnelle

```text
light directional intensity dx dy dz
```

## 📝 Exemple de scène

```text
sphere 0 -1 3 1 255 0 0 500 0.2

light ambient 0.2
light point 0.6 2 1 0
```

Cet exemple crée une sphère rouge et ajoute deux sources lumineuses : une lumière ambiante et une lumière ponctuelle.

## 📂 Structure du projet

```text
Raytracer/
│
├── main.py              # Point d'entrée principal
├── animation.py         # Génération des animations GIF
│
├── Canvas.py            # Gestion du canvas 2D
├── Camera.py            # Position et configuration de la caméra
├── Viewport.py          # Gestion du viewport
├── Scene.py             # Gestion de la scène
│
├── Sphere.py            # Objet sphère
├── parallelogramme.py   # Objet parallélogramme / mur
├── Light.py             # Sources lumineuses
│
├── vec3.py              # Calculs et opérations vectorielles
├── fonctions_utils.py   # Algorithmes de ray tracing et utilitaires
│
├── scene.txt            # Description de la scène
└── animation.gif        # Exemple d'animation générée
```

## 👥 Auteurs

Projet réalisé en équipe par :

- **Kadir Ersoy**
- **Mohamed**

## 🎓 Contexte académique

Projet réalisé à **ESIEE Paris** dans le cadre de notre formation d'ingénieur.

L'objectif du projet était de mettre en pratique la **programmation Python, la programmation orientée objet, le calcul vectoriel et les principes fondamentaux de l'infographie 3D** à travers l'implémentation d'un moteur de ray tracing.

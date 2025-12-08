+++
title = "Projet"
weight = 30
[params]
  author = 'Samy, Umar et Ashank'
+++

# Énoncé – Mini-Projet Love2D : "SURVIVE!"

---

## Objectif
Créer un mini-jeu en Lua avec Love2D dans lequel un joueur doit survivre le plus longtemps possible en évitant des ennemis qui se déplacent de manière aleatoire.

## Description du jeu
- Le joueur contrôle un personnage qui peut se déplacer avec les touches W, A, S, D.
- Plusieurs ennemis apparaissent progressivement à l’écran et se déplacent dans des directions aléatoires.
- Les ennemis rebondissent sur les bords de la fenêtre.
- Si le joueur touche un ennemi, le jeu passe en mode **Game Over**.
- Le jeu inclut un **score**, un **timer**, et un **high score**.
- Le jeu possède trois états :
  1. **Menu** (appuyer sur ENTER pour jouer)
  2. **Game**
  3. **Game Over** (appuyer sur R pour recommencer)

## Exigences techniques

---

### 1. Système de jeu
- Implémenter trois états : *menu*, *game*, *gameover*.
- Gérer la transition avec les touches :
  - `ENTER` = démarrer
  - `R` = recommencer

### 2. Joueur
- Image du joueur affichée en utilisant `love.graphics.draw`.
- Redimensionnement via une variable globale `SCALE`.
- Hitbox réduite avec un multiplicateur.
- Déplacements fluides avec W/A/S/D.
- Empêcher le joueur de sortir de l’écran.


### 3. Ennemis
- Au moins 3 ennemis au début.
- Apparition progressive pendant la partie.
- Position initiale sécuritaire (pas trop près du joueur).
- Mouvement avec vitesse aléatoire.
- Rebonds sur les murs.
- Hitbox réduite comme le joueur.

> [!warning] Attention
> Il est nécessaire de ajouter une reduction au hitbox ET a l'image avec `SCALE`, parce que sinon le jeu ne va **PAS** run!!

### 4. Collisions
- Collision rectangle-rectangle (AABB) entre le joueur et chaque ennemi.
- Si collision : passage en mode **Game Over** + mise à jour du high score.

### 5. Interface visuelle
- Afficher :
  - Temps survécu
  - Score
  - High score
- Optionnel (BONUS):
    - Ajouter un effet de **fade noir** pour transitions (début/fin de partie).
    - Fond sombre constant (#0D0D12 environ).

### 6. Gameplay
- Score basé sur le temps de survie.
- Difficulté progressive : plus le joueur survit longtemps, plus il y a d'ennemis.

---

## Résultat attendu
Un mini-jeu fonctionnel, stable, fluide, où :
- Le joueur peut se déplacer.
- Les ennemis se déplacent et rebondissent.
- La difficulté augmente avec le temps.
- Les collisions fonctionnent.
- Le score, le high score et le fade sont affichés correctement.
- Le jeu peut être recommencé sans bug.


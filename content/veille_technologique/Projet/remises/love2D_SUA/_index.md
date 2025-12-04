+++
title = "Love2D"
weight = 1
[params]
  author = 'Samy, Umar et Ashank'
+++
# 1.Introduction à LOVE2D
LÖVE2D, souvent appelé Love2D, est un framework open-source destiné à la création de jeux vidéo en 2D. Il utilise le langage de programmation Lua, reconnu pour sa simplicité, sa rapidité et sa facilité de prise en main. Love2D rend le développement très accessible grâce à sa structure claire et à son fonctionnement basé sur une boucle de jeu déjà intégrée, ce qui évite au développeur de devoir gérer lui-même les rafraîchissements de l’écran ou le timing des images.

Lua étant un langage interprété, l'exécution est rapide et les tests sont quasi immédiats, ce qui favorise l’expérimentation. Love2D est aussi extrêmement léger : un projet peut être constitué d’un seul fichier main.lua, ce qui permet aux débutants de se concentrer sur la logique du jeu plutôt que sur la configuration d’un environnement complexe.

Love2D repose sur trois fonctions fondamentales qui définissent la structure d’un projet :

```Lua
function love.load() end     -- exécuté une seule fois au début
function love.update(dt) end -- logique du jeu (environ 60fps)
function love.draw() end     --  partie visuelle du jeu
```

love.load() sert à initialiser les variables, charger les ressources et configurer le jeu. love.update(dt) traite les déplacements, animations, collisions ou IA. Le paramètre dt (delta time) représente le temps écoulé entre deux frames, ce qui permet d’avoir des mouvements constants quel que soit le FPS. Enfin, love.draw() se charge de tout l’affichage : texte, images, formes, sprites animés, etc.
## Installation

Télécharger LOVE2D ici :
https://love2d.org/



## Un exemple minimal 
Créer un fichier `main.lua` :

```txt
Projet-1-Hello/
    main.lua
```
Commande pour afficher un texte:
```Lua
function love.draw()
    love.graphics.print("Hello Love2D!", 100, 100)
end

```
![alt text](hello.png)

## Demarrer un jeu avec Love2D (Drag and Drop)

1. Ouvrir `C:\Program Files\LOVE`
2. Trouver `love.exe`
3. Ouvrir l’explorateur Windows dans ton projet
4. Glisser ton dossier ENTIER sur `love.exe`

Comme ceci :

![alt text](drag.png)

Projet-1-Hello → glisser sur love.exe  
Le jeu démarre automatiquement 🎮

---

# 2.Graphismes : formes, couleurs & images

Cette section couvre tout ce qu’un débutant doit savoir pour **afficher du texte**, **dessiner des formes**, **changer les couleurs**, et **afficher des images** dans Love2D.  
L’objectif est de comprendre comment Love2D dessine à l’écran : chaque élément visuel, qu’il s’agisse d’un rectangle, d’un cercle ou d’un sprite complet, passe par les fonctions du module `love.graphics`.  
Cette base est essentielle pour tous les jeux 2D, qu’ils soient simples ou avancés.

---

## Exemple complet : formes + couleurs

Dans cet exemple, on montre comment changer la couleur actuelle du pinceau de dessin, puis comment afficher un rectangle, un cercle et enfin du texte.  
Love2D redessine l’écran **à chaque frame**, donc tout ce qui doit apparaître visuellement doit être dans `love.draw()`.

```lua
function love.load()
    -- rien à charger ici
end

function love.update(dt)
    -- logique du jeu (vide pour ce chapitre)
end

function love.draw()
    -- carré rouge
    love.graphics.setColor(1, 0, 0, 1)
    love.graphics.rectangle("fill", 50, 50, 120, 80)

    -- cercle bleu
    love.graphics.setColor(0, 0, 1, 1)
    love.graphics.circle("fill", 300, 150, 40)

    -- texte en blanc
    love.graphics.setColor(1, 1, 1, 1)
    love.graphics.print("Hello Love2D!", 50, 200)
end
```
![alt text](formes.png)
---
Cet exemple montre trois choses essentielles :

1. Comment modifier la couleur courante (setColor)

2. Comment dessiner des formes simples (rectangle, circle)

3. Comment afficher du texte (print)

##  Afficher une image
Pour afficher une image, elle doit être placée dans un dossier accessible au jeu.
Voici une structure recommandée pour éviter les erreurs de chemin :
```txt
afficherimage/
    main.lua
    assets/
        images/
            player.png
```
Voici le code complet pour charger et afficher une image :
```lua
local playerImg
local playerX = 200
local playerY = 200

function love.load()
    playerImg = love.graphics.newImage("assets/images/player.png")
end

function love.update(dt)
    -- rien pour l'instant
end

function love.draw()
    love.graphics.setColor(1, 1, 1, 1) -- reset couleur
    love.graphics.draw(playerImg, playerX, playerY)
end

```
![alt text](perso.png)
---
Ce code démontre :

1. Comment charger une image avec newImage()

2. Comment stocker la position du sprite

3. Comment afficher l’image dans love.draw()

## Déplacer une image avec une variable
Dans cet exemple, l'image se déplace automatiquement en modifiant sa position à chaque frame.
dt permet d’assurer un déplacement fluide et stable même si le nombre de FPS change.

```lua
local img
local x = 100
local y = 100
local speed = 200 -- pixels/sec

function love.load()
    img = love.graphics.newImage("assets/images/player.png")
end

function love.update(dt)
    x = x + speed * dt      -- mouvement automatique horizontal
end

function love.draw()
    love.graphics.draw(img, x, y)
end
```

Ici, l’image se déplace vers la droite grâce à l’ajout progressif de speed * dt.
C’est le principe fondamental du mouvement dans presque tous les jeux 2D.


---
## Quelques exercises pour mettre en pratique cette section

Les exercices suivants  permettent de pratiquer immédiatement les concepts vus ci-dessus.
Chaque exercice correspond à une action simple mais essentielle pour se familiariser avec les bases de l’affichage.

---
### 1. Dessiner un rectangle rouge
Le Resultat: 

![alt text](rect.png)

Cet exercice vérifie que tu sais utiliser setColor et rectangle.

---
### 2. Dessiner un cercle bleu
Resultat: 

![alt text](cercleB.png)

Cet exercice valide la manipulation de formes simples et les couleurs.

---
### 3. Afficher une image player.png

Resultat:

![alt text](perso.png)
Cela confirme que tu maîtrises la structure des dossiers et le chargement d’images avec newImage.

---
### 4. Déplacer une image avec une variable

Resultat:

![alt text](vid.gif)
Cet exercice t’aide à comprendre la logique de mouvement, la mise à jour d’une position, et l’importance du delta time.

---

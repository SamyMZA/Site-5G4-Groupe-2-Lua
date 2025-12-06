+++
title = "Notes de cours - LUA"
weight = 2
+++

Notes de cours sur votre sujet.

## Ques ce que LUA ?

Lua est un langage de programmation polyvalent, créé par Bjarne Stroustrup pour etndare le language c a de la programmation orienté objet tout en gardant les performance du C.

Lua est un langage de programmation léger, rapide et flexible, pensé pour être intégré à d’autres logiciels plutôt que d’être utilisé comme un langage autonome. Créé en 1993 au sein de l’Université Pontificale Catholique de Rio de Janeiro, Lua a gagné une popularité mondiale en raison de son efficacité, de sa simplicité et de sa capacité unique à s’intégrer dans des projets écrits en C et C++.

Contrairement à des langages comme Python, Java ou C++, Lua n’a pas été conçu pour devenir un langage généraliste destiné à remplacer les autres. Sa philosophie repose sur une idée simple : fournir un petit noyau extrêmement performant et minimaliste que les développeurs peuvent étendre selon leurs besoins. C’est un langage pensé comme un couteau suisse du scripting, capable d’être embarqué dans des moteurs de jeux, des systèmes embarqués, des logiciels métiers, ou des environnements nécessitant un langage de configuration.

Lua est apprécié pour sa petite taille, vitesse, facilité d'ntegration et sa syntaxe simple.

Lua se retrouve aujourd’hui dans des domaines aussi variés que l’industrie du jeu vidéo (Roblox, World of Warcraft, Angry Birds), les systèmes embarqués, la robotique, la cybersécurité, l’automatisation, et même les outils de configuration de Linux.

---

## Installation et dépendance

Pour un premier programme

On crée un premier fichier qui va s'appeler main.lua

dedans on ajoute la ligne suivante pour afficher du texte :

```lua
print("Bonjour, Lua fonctionne !")
```
puis dans le teminal

```bash
lua main.lua
```

voici un mini-programme pour verfifier l'age d'une personne


```lua
print("Quel est ton âge ?")
local age = tonumber(io.read())

if age >= 18 then
    print("Tu es majeur.")
else
    print("Tu es mineur.")
end
```


---

## Variables

Lua possède un nombre limité de types de données, ce qui le rend à la fois simple et flexible. Les types les plus utilisés sont le nombre, la chaîne de caractères, le booléen, et la table. Les nombres sont toujours stockés en double précision, et depuis Lua 5.3, on distingue entiers et flottants, mais les opérations restent simples à manipuler. Les chaînes de caractères sont immuables et peuvent être écrites avec des guillemets simples, doubles, ou même en utilisant la syntaxe de chaînes multilignes [[ ... ]].

Les tables sont le cœur du langage. Elles permettent de représenter à la fois des tableaux, des dictionnaires, et même des objets ou modules simulés. Chaque table peut contenir des clés et des valeurs de n’importe quel type, et on peut utiliser des métatables pour modifier leur comportement, par exemple pour surcharger des opérateurs ou créer des comportements personnalisés.


## Types


![alt.text](luatypes.jpg)

Le type `nil` représente « aucune valeur ».  
Il est utilisé pour indiquer l’absence de données ou pour supprimer une clé d’une table.
Un peu comme le NULL habituel.

```lua
x = nil
```
pour le type boolean, seul false et nil sont considéer comme faux. tout le rest est vrai

Lua utilise un type unique pour les nombres (double précision IEEE 754).
Depuis Lua 5.3, les entiers et flottants sont différenciés, mais la manipulation reste simple.


Les chaînes de caractères sont immuables.
Lua permet les guillemets simples, doubles et même les chaînes multilignes [[ ... ]].


```lua
s = "Hello"
s2 = [[Texte
sur plusieurs lignes]]
```

Les tables, metatables
Le type le plus important du langage.
Tout comme le PHP, Lua va stocker les valeurs a l'aide de clés.
Il remplace :

les tableaux, les dictionnaires, les objets (via metatables), les modules, les classes simulées

```lua
t = { name = "John", age = 20 }
```

Metatables

Les metatables permettent de modifier le comportement des objets.

Exemple : surcharge de l’opérateur +.

```lua
mt = {
    __add = function(a, b)
        return { x = a.x + b.x }
    end
}

v1 = { x = 10 }
v2 = { x = 5 }

setmetatable(v1, mt)
setmetatable(v2, mt)

result = v1 + v2
print(result.x) -- 15
```

userdata :
Permet d’intégrer des objets C depuis le langage hôte.
C’est l’outil principal pour intégrer Lua dans une application externe.


thread:
Utilisé pour les coroutines, un mécanisme puissant permettant une forme de multitâche coopératif.

## Opérateurs

Les opérateur en lua sont assez classique.

Opérateurs arithmétiques:

+   addition
-   soustraction
*   multiplication
/   division
%   modulo
^   puissance
//  division entière


Opérateurs relationnels

==  égal
~=  différent
>   supérieur
<   inférieur
>=  supérieur ou égal
<=  inférieur ou égal


Opérateurs logiques

and
or
not


BONUS : pour concatener (..  concaténation)

```lua
s = "Hello " .. "World"
```

## Fonction

Les fonctions sont des valeurs : elles peuvent être stockées dans des variables, passées en paramètres, retournées par d'autres fonctions.

Appeler une fionction:

```lua
res1, res2 = mafonction(var)
```

Définition simple
```lua
function mafonction(arg1, arg2, ...)
 -- code
 return résultat1, résultat2
end
```

Fontion anonyme
```lua
function add(a, b)
    return a + b
end
```

Retour multiple
```lua
function stats()
    return 10, 20
end

x, y = stats()
```

Fermetures lexicales

Lua prend en charge les closures :

```lua
function counter()
    local n = 0
    return function()
        n = n + 1
        return n
    end
end

c = counter()
print(c())
print(c()) 
```

Constructeur:

```lua
function Constructeur:new(x, y, z)    -- Constructeur
  -- Le ":" passe "self" en premier, qui référence "Vector"
  return setmetatable({x = x, y = y, z = z}, self)
end
```


Les conditon en Lua sont semblables a plein d'autre language
On change pas une queipe gagngante XD:

```lua
if condition1 then

elseif condition2 then

else

end
```

Leas bloucles :


Do While

```lua
repeat
 -- code
until condition
```

While Do

```lua
while condition do
 -- code
end
```

For

```lua
for var = start, valend, step do
 -- code
end
```



Coté mathematique / logique :
Comme en JavaScript et plein d'autre language, il y a, en Lua, un module math pour fair certain calculs directement.
Par exemple, afficher le pi: 
```lua
print(math.pi) 
```

## Comparaison avec le python

Le python est considéré comme le plus facile, puissant et universel language de prog.
Le Lua serait comparable dans la forme.
Voici leut comparaison :


## Tableau de comparaison avec d’autres langages

| Critère           | Lua            | Python               |
|------------------|----------------|--------------------|
| Taille du runtime | ~300 KB        | ~25 MB             |
| Vitesse           | très rapide    | moyenne            |
| Paradigme         | flexible       | orienté objet      |
| Extensions        | C/C++ faciles  | C plus complexe    |
| Usage             | embarqué       | scripting généraliste |
 

## utilisation domaine

Lua est le langage numéro 1 du scripting dans l’industrie du jeu :
Roblox (100+ millions d’utilisateurs), CryEngine, WoW Addons, Angry Birds, Baldur’s Gate

Il permet de séparer :
le moteur (C++), le script du gameplay (Lua), Automatisation / DevOps

Utilisé dans :
Neovim,OpenResty (Nginx + Lua),AwesomeWM,Redis (scripts Lua dans le serveur),Réseau et cybersécurité,

Lua est intégré dans :
Wireshark, Nmap (NSE scripts), Suricata, Systèmes embarqués

Grâce à sa taille minuscule, on le retrouve dans :
microcontrôleurs,robots éducatifs, objets connectés

## Conclusion

Lua est un langage unique, minimaliste, mais extrêmement puissant. Sa philosophie est simple : fournir un cœur léger, extensible, qui permet aux développeurs de créer exactement ce dont ils ont besoin. Sa vitesse, sa simplicité, sa portabilité et sa capacité d’intégration dans des applications C/C++ en font l’un des langages les plus utilisés dans l’embarqué, le jeu vidéo, l’automatisation et les environnements nécessitant un langage flexible.

Bien qu’il soit peu médiatisé comparé à Python ou JavaScript, Lua reste un outil crucial dans de nombreuses industries grâce à sa stabilité et à son efficacité.
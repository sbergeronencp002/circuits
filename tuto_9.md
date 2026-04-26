# Circuits électriques — Tutoriel 9

## @showdialog

🎯 **Objectif** : crée un spectacle lumineux avec les **fonctions** !

Dans ce tutoriel, tu vas découvrir les **fonctions** — des blocs que tu programmes une seule fois et que tu peux appeler autant de fois que tu veux, où tu veux dans ton programme !

C'est parti ! 🚀

## Étape 1 — Préparer l'espace de travail

🧹 Fais le ménage !

➡️ Supprime les blocs ``||basic:au démarrage||`` et ``||basic:toujours||``.

> 💡 On va travailler avec les **boutons** et les **fonctions** — pas besoin de ces deux blocs pour l'instant !

## Étape 2 — Créer la fonction « clignoter »

✨ Nouvelle notion : la **fonction** !

➡️ Clique sur **Fonctions** dans le menu, puis sur **Créer une fonction**.

➡️ Nomme-la `clignoter`.

➡️ À l'intérieur, glisse un bloc ``||loops:répéter 3 fois||``.

➡️ Dans la boucle, glisse ``||pins:écrire sur la broche P0 la valeur numérique 1||``, puis ``||basic:pause (ms) 100||``, puis ``||pins:écrire sur la broche P0 la valeur numérique 0||``, puis ``||basic:pause (ms) 100||``.

> 💡 Une **fonction**, c'est comme une recette — tu l'écris une seule fois, et tu peux l'utiliser autant de fois que tu veux en l'**appelant** !

```blocks
function clignoter() {
    for (let index = 0; index < 3; index++) {
        pins.digitalWritePin(DigitalPin.P0, 1)
        basic.pause(100)
        pins.digitalWritePin(DigitalPin.P0, 0)
        basic.pause(100)
    }
}
```

## Étape 3 — Créer la fonction « ondulation »

✨ Une deuxième fonction !

➡️ Crée une nouvelle fonction et nomme-la `ondulation`.

➡️ À l'intérieur : allume P0, attends `200` ms, éteins P0. Puis allume P1, attends `200` ms, éteins P1. Puis allume P2, attends `200` ms, éteins P2.

> 💡 L'ondulation allume les DEL **une par une dans l'ordre** — comme une vague qui traverse ton circuit de gauche à droite !

```blocks
function ondulation() {
    pins.digitalWritePin(DigitalPin.P0, 1)
    basic.pause(200)
    pins.digitalWritePin(DigitalPin.P0, 0)
    pins.digitalWritePin(DigitalPin.P1, 1)
    basic.pause(200)
    pins.digitalWritePin(DigitalPin.P1, 0)
    pins.digitalWritePin(DigitalPin.P2, 1)
    basic.pause(200)
    pins.digitalWritePin(DigitalPin.P2, 0)
}
```

## Étape 4 — Créer la fonction « gyrophare »

✨ Une troisième fonction !

➡️ Crée une nouvelle fonction et nomme-la `gyrophare`.

➡️ À l'intérieur, glisse un bloc ``||loops:répéter 4 fois||``.

➡️ Dans la boucle : allume P0 et P2, attends `100` ms, éteins P0 et P2, allume P1, attends `100` ms, éteins P1.

> 💡 `gyrophare` alterne rapidement entre les DEL des côtés et celle du centre — comme les lumières d'une voiture de police ! 🚨

```blocks
function gyrophare() {
    for (let index = 0; index < 4; index++) {
        pins.digitalWritePin(DigitalPin.P0, 1)
        pins.digitalWritePin(DigitalPin.P2, 1)
        basic.pause(100)
        pins.digitalWritePin(DigitalPin.P0, 0)
        pins.digitalWritePin(DigitalPin.P2, 0)
        pins.digitalWritePin(DigitalPin.P1, 1)
        basic.pause(100)
        pins.digitalWritePin(DigitalPin.P1, 0)
    }
}
```

## Étape 5 — Bouton A : appeler clignoter

✨ Appelle ta première fonction !

➡️ Glisse le bloc ``||input:lorsque le bouton A est pressé||`` dans l'espace de travail.

➡️ À l'intérieur, glisse le bloc ``||functions:appeler clignoter||``.

> 💡 **Appeler** une fonction, c'est lui dire : « Lance-toi maintenant ! » — tout le code de la fonction s'exécute d'un seul coup, avec un seul bloc !

```blocks
input.onButtonPressed(Button.A, function () {
    clignoter()
})
```

## Étape 6 — Bouton B : appeler ondulation

➡️ Glisse le bloc ``||input:lorsque le bouton B est pressé||`` dans l'espace de travail.

➡️ À l'intérieur, glisse le bloc ``||functions:appeler ondulation||``.

```blocks
input.onButtonPressed(Button.B, function () {
    ondulation()
})
```

## Étape 7 — Bouton A+B : appeler gyrophare

➡️ Glisse le bloc ``||input:lorsque le bouton A+B est pressé||`` dans l'espace de travail.

➡️ À l'intérieur, glisse le bloc ``||functions:appeler gyrophare||``.

```blocks
input.onButtonPressed(Button.AB, function () {
    gyrophare()
})
```

## Étape 8 — La fonction chef d'orchestre 🎼

✨ Une fonction qui appelle d'autres fonctions !

➡️ Crée une nouvelle fonction et nomme-la `spectacle`.

➡️ À l'intérieur, glisse successivement ``||functions:appeler clignoter||``, ``||functions:appeler ondulation||``, ``||functions:appeler gyrophare||``.

➡️ Glisse le bloc ``||input:lorsque secouer||`` dans l'espace de travail et appelle `spectacle` à l'intérieur.

> 💡 Une fonction peut **appeler d'autres fonctions** — c'est la vraie puissance ! Le bloc « secousse » ne contient qu'une ligne, mais il déclenche tout le spectacle !

```blocks
function spectacle() {
    clignoter()
    ondulation()
    gyrophare()
}
input.onGesture(Gesture.Shake, function () {
    spectacle()
})
```

## Étape 9 — Télécharger le programme

💾 Envoie ton programme sur le micro:bit !

➡️ Clique sur le bouton **Télécharger** pour transférer ton programme.

> 💡 Le programme doit être dans le micro:bit avant de réaliser le circuit !

## Étape 10 — Réaliser le circuit 🔌

🔌 Réalise le branchement du circuit !

➡️ Rappelle-toi que la couleur des fils n'a aucune importance ! 🎨

> 💡 Trois DEL branchées sur **P0**, **P1** et **P2** — comme aux tutoriels 7 et 8 !

## Étape 11 — Question réflexive 🤔

❓ **Que se passerait-il si tu voulais changer le clignotement pour qu'il se répète 5 fois au lieu de 3 — sans les fonctions ?**

❓ **Quel est l'avantage de la fonction `spectacle` par rapport à copier-coller tous les blocs dans le bloc secousse ?**

> 💡 Sans fonctions, tu devrais modifier le code à plusieurs endroits ! Avec une fonction, tu changes une seule chose et tout le programme suit. C'est ce qu'on appelle la **réutilisabilité** — programmer moins pour faire plus !

## Étape 12 — Défi de base 🧠

➡️ Ajoute une fonction `éteindre` qui éteint les trois DEL d'un seul coup.

➡️ Appelle-la au début de chaque autre fonction pour t'assurer que toutes les DEL sont éteintes avant de démarrer.

> ❓ Est-ce que les DEL s'éteignent bien proprement entre chaque effet ?

## Étape 13 — Défi avancé 🧠

➡️ Modifie la fonction `spectacle` pour qu'elle enchaîne le spectacle **2 fois** en utilisant un bloc ``||loops:répéter||``.

➡️ Ajoute ensuite la fonction `éteindre` à la fin du spectacle pour terminer proprement.

```blocks
function spectacle() {
    for (let index = 0; index < 2; index++) {
        clignoter()
        ondulation()
        gyrophare()
    }
    éteindre()
}
```

> ❓ Combien de lignes de code faudrait-il sans les fonctions pour obtenir le même résultat ?

🚀 Bravo ! Tu sais maintenant créer des fonctions et les combiner pour programmer des spectacles lumineux réutilisables !

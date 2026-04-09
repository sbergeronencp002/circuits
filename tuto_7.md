# Circuits électriques — Tutoriel 7

## @showdialog

🎯 **Objectif** : programme un feu de circulation 🚦 avec trois DEL !

Dans ce tutoriel, tu vas programmer une séquence automatique — rouge, jaune, vert — comme un vrai feu de circulation !

## Étape 1 — Préparer l'espace de travail

🧹 Fais le ménage !

➡️ Supprime le bloc ``||basic:au démarrage||``.

> 💡 On garde le bloc ``||basic:toujours||`` — la séquence va se répéter en boucle indéfiniment !

## Étape 2 — DEL rouge : allumer

✨ Commence la séquence !

➡️ Glisse le bloc ``||pins:écrire sur la broche P0 la valeur 0||`` à l'intérieur du bloc ``||basic:toujours||``.

➡️ Remplace la valeur `0` par `1`.

> 💡 La DEL **rouge** est branchée sur la broche **P0** — elle s'allume en premier !

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P0, 1)
})
```

## Étape 3 — DEL rouge : pause

⏱️ Ajoute une pause !

➡️ Glisse le bloc ``||basic:pause (ms) 100||`` sous le bloc ``||pins:écrire sur la broche P0||``.

➡️ Remplace la valeur par `3000`.

> 💡 Le feu rouge dure **3 secondes** — comme un vrai feu de circulation !

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P0, 1)
    basic.pause(3000)
})
```

## Étape 4 — DEL rouge : éteindre

➡️ Glisse un deuxième bloc ``||pins:écrire sur la broche P0 la valeur 0||`` sous la pause.

➡️ Laisse la valeur à `0`.

> 💡 On éteint la DEL rouge avant d'allumer la suivante !

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P0, 1)
    basic.pause(3000)
    pins.digitalWritePin(DigitalPin.P0, 0)
})
```

## Étape 5 — DEL jaune : allumer

✨ Deuxième couleur !

➡️ Glisse le bloc ``||pins:écrire sur la broche P1 la valeur 0||`` sous le bloc précédent.

➡️ Remplace la valeur `0` par `1`.

> 💡 La DEL **jaune** est branchée sur la broche **P1** — attention, le feu va changer ! 🟡

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P0, 1)
    basic.pause(3000)
    pins.digitalWritePin(DigitalPin.P0, 0)
    pins.digitalWritePin(DigitalPin.P1, 1)
})
```

## Étape 6 — DEL jaune : pause

⏱️ Ajoute une pause !

➡️ Glisse le bloc ``||basic:pause (ms) 100||`` sous le bloc ``||pins:écrire sur la broche P1||``.

➡️ Remplace la valeur par `1000`.

> 💡 Le feu jaune dure **1 seconde** — juste assez pour avertir les conducteurs !

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P0, 1)
    basic.pause(3000)
    pins.digitalWritePin(DigitalPin.P0, 0)
    pins.digitalWritePin(DigitalPin.P1, 1)
    basic.pause(1000)
})
```

## Étape 7 — DEL jaune : éteindre

➡️ Glisse un deuxième bloc ``||pins:écrire sur la broche P1 la valeur 0||`` sous la pause.

➡️ Laisse la valeur à `0`.

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P0, 1)
    basic.pause(3000)
    pins.digitalWritePin(DigitalPin.P0, 0)
    pins.digitalWritePin(DigitalPin.P1, 1)
    basic.pause(1000)
    pins.digitalWritePin(DigitalPin.P1, 0)
})
```

## Étape 8 — DEL verte : allumer

✨ Troisième couleur !

➡️ Glisse le bloc ``||pins:écrire sur la broche P2 la valeur 0||`` sous le bloc précédent.

➡️ Remplace la valeur `0` par `1`.

> 💡 La DEL **verte** est branchée sur la broche **P2** — c'est parti, on peut traverser ! 🟢

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P0, 1)
    basic.pause(3000)
    pins.digitalWritePin(DigitalPin.P0, 0)
    pins.digitalWritePin(DigitalPin.P1, 1)
    basic.pause(1000)
    pins.digitalWritePin(DigitalPin.P1, 0)
    pins.digitalWritePin(DigitalPin.P2, 1)
})
```

## Étape 9 — DEL verte : pause

⏱️ Ajoute une pause !

➡️ Glisse le bloc ``||basic:pause (ms) 100||`` sous le bloc ``||pins:écrire sur la broche P2||``.

➡️ Remplace la valeur par `3000`.

> 💡 Le feu vert dure **3 secondes** — comme le feu rouge !

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P0, 1)
    basic.pause(3000)
    pins.digitalWritePin(DigitalPin.P0, 0)
    pins.digitalWritePin(DigitalPin.P1, 1)
    basic.pause(1000)
    pins.digitalWritePin(DigitalPin.P1, 0)
    pins.digitalWritePin(DigitalPin.P2, 1)
    basic.pause(3000)
})
```

## Étape 10 — DEL verte : éteindre

➡️ Glisse un deuxième bloc ``||pins:écrire sur la broche P2 la valeur 0||`` sous la pause.

➡️ Laisse la valeur à `0`.

> 💡 On éteint la DEL verte — la séquence recommence depuis le début avec le feu rouge !

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P0, 1)
    basic.pause(3000)
    pins.digitalWritePin(DigitalPin.P0, 0)
    pins.digitalWritePin(DigitalPin.P1, 1)
    basic.pause(1000)
    pins.digitalWritePin(DigitalPin.P1, 0)
    pins.digitalWritePin(DigitalPin.P2, 1)
    basic.pause(3000)
    pins.digitalWritePin(DigitalPin.P2, 0)
})
```

## Étape 11 — Télécharger le programme

💾 Envoie ton programme sur le micro:bit !

➡️ Clique sur le bouton **Télécharger** pour transférer ton programme.

> 💡 Le programme doit être dans le micro:bit avant de réaliser le circuit !

## @showdialog

🔌 Réalise le branchement du circuit !

➡️ Rappelle-toi que la couleur des fils n'a aucune importance ! 🎨

> 💡 Cette fois, tu vas brancher **trois DEL** — rouge sur **P0**, jaune sur **P1** et verte sur **P2** !

❓ **Quelle est la différence entre le branchement de ce tutoriel et celui des tutoriels précédents ?**

## Étape 12 — Question réflexive 🤔

❓ **Pourquoi est-il important d'éteindre une DEL avant d'allumer la suivante ?**

❓ **Que se passerait-il si on oubliait d'éteindre une DEL ?**

> 💡 Sans éteindre les DEL précédentes, toutes les couleurs seraient allumées en même temps — ce ne serait plus un vrai feu de circulation ! La séquence précise est essentielle pour que le programme fonctionne correctement 🚦

## Étape 13 — Défi supplémentaire 🧠

**Défi de base :**

➡️ Modifie les valeurs des pauses pour changer la durée de chaque feu.

> ❓ Quelle combinaison de durées donne le feu de circulation le plus réaliste ?

**Défi avancé :**

➡️ Ajoute une icône sur l'écran du micro:bit pour chaque couleur — un X ❌ pour le rouge, un triangle ⚠️ pour le jaune et un crochet ✅ pour le vert.

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P0, 1)
    basic.showIcon(IconNames.No)
    basic.pause(3000)
    pins.digitalWritePin(DigitalPin.P0, 0)
    pins.digitalWritePin(DigitalPin.P1, 1)
    basic.showIcon(IconNames.Triangle)
    basic.pause(1000)
    pins.digitalWritePin(DigitalPin.P1, 0)
    pins.digitalWritePin(DigitalPin.P2, 1)
    basic.showIcon(IconNames.Yes)
    basic.pause(3000)
    pins.digitalWritePin(DigitalPin.P2, 0)
    basic.clearScreen()
})
```

> ❓ Est-ce que les icônes correspondent bien aux couleurs du feu de circulation ?

🚀 Bravo ! Tu viens de programmer un vrai feu de circulation avec le micro:bit ! 🚦
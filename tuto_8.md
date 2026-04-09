# Circuits électriques — Tutoriel 8

## @showdialog

🎯 **Objectif** : programme un sapin de Noël 🎄 avec trois DEL qui clignotent !

Dans ce tutoriel, tu vas combiner les **boutons**, les **boucles** et les **broches** pour créer une belle décoration lumineuse !

## Étape 1 — Préparer l'espace de travail

🧹 Fais le ménage !

➡️ Supprime les blocs ``||basic:au démarrage||`` et ``||basic:toujours||``.

> 💡 Le micro:bit va **attendre** que tu appuies sur un bouton avant de réagir !

## Étape 2 — Afficher le sapin au démarrage

✨ Ajoute un dessin de démarrage !

➡️ Glisse le bloc ``||basic:au démarrage||`` dans l'espace de travail.

➡️ Glisse le bloc ``||basic:montrer LEDs||`` à l'intérieur et reproduis le dessin du sapin ci-dessous.

> 💡 Au démarrage, le micro:bit affiche un sapin sur son écran ! 🎄

```blocks
basic.showLeds(`
    . . # . .
    . # # # .
    # # # # #
    . . # . .
    . # # # .
    `)
```

## Étape 3 — Bouton A : ajouter une boucle

✨ Ajoute une première séquence !

➡️ Glisse le bloc ``||loops:répéter 4 fois||`` à l'intérieur du bloc ``||input:lorsque le bouton A est pressé||``.

➡️ Remplace la valeur `4` par `10`.

> 💡 La boucle va répéter la cascade **10 fois** à chaque appui sur **A** !

```blocks
input.onButtonPressed(Button.A, function () {
    for (let index = 0; index < 10; index++) {
    }
})
```

## Étape 4 — Bouton A : allumer P0

➡️ À l'intérieur de la boucle, glisse trois blocs ``||pins:écrire sur la broche||`` :

➡️ **P0** → valeur `1` 🔆

➡️ **P1** → valeur `0` 💤

➡️ **P2** → valeur `0` 💤

> 💡 Seulement la DEL sur **P0** est allumée — les deux autres sont éteintes !

```blocks
input.onButtonPressed(Button.A, function () {
    for (let index = 0; index < 10; index++) {
        pins.digitalWritePin(DigitalPin.P0, 1)
        pins.digitalWritePin(DigitalPin.P1, 0)
        pins.digitalWritePin(DigitalPin.P2, 0)
    }
})
```

## Étape 5 — Bouton A : pause après P0

➡️ Glisse le bloc ``||basic:pause (ms) 100||`` sous les trois blocs ``||pins:écrire sur la broche||``.

➡️ Remplace la valeur par `300`.

```blocks
input.onButtonPressed(Button.A, function () {
    for (let index = 0; index < 10; index++) {
        pins.digitalWritePin(DigitalPin.P0, 1)
        pins.digitalWritePin(DigitalPin.P1, 0)
        pins.digitalWritePin(DigitalPin.P2, 0)
        basic.pause(300)
    }
})
```

## Étape 6 — Bouton A : allumer P1

➡️ Sous la pause, glisse trois autres blocs ``||pins:écrire sur la broche||`` :

➡️ **P0** → valeur `0` 💤

➡️ **P1** → valeur `1` 🔆

➡️ **P2** → valeur `0` 💤

> 💡 Maintenant c'est la DEL sur **P1** qui s'allume — les deux autres s'éteignent !

```blocks
input.onButtonPressed(Button.A, function () {
    for (let index = 0; index < 10; index++) {
        pins.digitalWritePin(DigitalPin.P0, 1)
        pins.digitalWritePin(DigitalPin.P1, 0)
        pins.digitalWritePin(DigitalPin.P2, 0)
        basic.pause(300)
        pins.digitalWritePin(DigitalPin.P0, 0)
        pins.digitalWritePin(DigitalPin.P1, 1)
        pins.digitalWritePin(DigitalPin.P2, 0)
    }
})
```

## Étape 7 — Bouton A : pause après P1

➡️ Glisse un deuxième bloc ``||basic:pause (ms) 100||`` sous les trois blocs.

➡️ Remplace la valeur par `300`.

```blocks
input.onButtonPressed(Button.A, function () {
    for (let index = 0; index < 10; index++) {
        pins.digitalWritePin(DigitalPin.P0, 1)
        pins.digitalWritePin(DigitalPin.P1, 0)
        pins.digitalWritePin(DigitalPin.P2, 0)
        basic.pause(300)
        pins.digitalWritePin(DigitalPin.P0, 0)
        pins.digitalWritePin(DigitalPin.P1, 1)
        pins.digitalWritePin(DigitalPin.P2, 0)
        basic.pause(300)
    }
})
```

## Étape 8 — Bouton A : allumer P2

➡️ Sous la pause, glisse trois autres blocs ``||pins:écrire sur la broche||`` :

➡️ **P0** → valeur `0` 💤

➡️ **P1** → valeur `0` 💤

➡️ **P2** → valeur `1` 🔆

> 💡 C'est maintenant au tour de la DEL sur **P2** — la cascade est complète ! À chaque tour de boucle, les DEL s'allument une par une. 🌟

```blocks
input.onButtonPressed(Button.A, function () {
    for (let index = 0; index < 10; index++) {
        pins.digitalWritePin(DigitalPin.P0, 1)
        pins.digitalWritePin(DigitalPin.P1, 0)
        pins.digitalWritePin(DigitalPin.P2, 0)
        basic.pause(300)
        pins.digitalWritePin(DigitalPin.P0, 0)
        pins.digitalWritePin(DigitalPin.P1, 1)
        pins.digitalWritePin(DigitalPin.P2, 0)
        basic.pause(300)
        pins.digitalWritePin(DigitalPin.P0, 0)
        pins.digitalWritePin(DigitalPin.P1, 0)
        pins.digitalWritePin(DigitalPin.P2, 1)
    }
})
```

## Étape 9 — Bouton A : pause après P2

➡️ Glisse un troisième bloc ``||basic:pause (ms) 100||`` sous les trois blocs.

➡️ Remplace la valeur par `300`.

```blocks
input.onButtonPressed(Button.A, function () {
    for (let index = 0; index < 10; index++) {
        pins.digitalWritePin(DigitalPin.P0, 1)
        pins.digitalWritePin(DigitalPin.P1, 0)
        pins.digitalWritePin(DigitalPin.P2, 0)
        basic.pause(300)
        pins.digitalWritePin(DigitalPin.P0, 0)
        pins.digitalWritePin(DigitalPin.P1, 1)
        pins.digitalWritePin(DigitalPin.P2, 0)
        basic.pause(300)
        pins.digitalWritePin(DigitalPin.P0, 0)
        pins.digitalWritePin(DigitalPin.P1, 0)
        pins.digitalWritePin(DigitalPin.P2, 1)
        basic.pause(300)
    }
})
```

## Étape 10 — Bouton B : ajouter une boucle

✨ Ajoute une deuxième séquence !

➡️ Glisse le bloc ``||loops:répéter 4 fois||`` à l'intérieur du bloc ``||input:lorsque le bouton B est pressé||``.

➡️ Remplace la valeur `4` par `10`.

```blocks
input.onButtonPressed(Button.B, function () {
    for (let index = 0; index < 10; index++) {
    }
})
```

## Étape 11 — Bouton B : allumer toutes les DEL

➡️ À l'intérieur de la boucle, glisse trois blocs ``||pins:écrire sur la broche||`` :

➡️ **P0** → valeur `1` 🔆

➡️ **P1** → valeur `1` 🔆

➡️ **P2** → valeur `1` 🔆

> 💡 Toutes les DEL s'allument en même temps !

```blocks
input.onButtonPressed(Button.B, function () {
    for (let index = 0; index < 10; index++) {
        pins.digitalWritePin(DigitalPin.P0, 1)
        pins.digitalWritePin(DigitalPin.P1, 1)
        pins.digitalWritePin(DigitalPin.P2, 1)
    }
})
```

## Étape 12 — Bouton B : pause

➡️ Glisse le bloc ``||basic:pause (ms) 100||`` sous les trois blocs.

➡️ Remplace la valeur par `300`.

```blocks
input.onButtonPressed(Button.B, function () {
    for (let index = 0; index < 10; index++) {
        pins.digitalWritePin(DigitalPin.P0, 1)
        pins.digitalWritePin(DigitalPin.P1, 1)
        pins.digitalWritePin(DigitalPin.P2, 1)
        basic.pause(300)
    }
})
```

## Étape 13 — Bouton B : éteindre toutes les DEL

➡️ Sous la pause, glisse trois autres blocs ``||pins:écrire sur la broche||`` :

➡️ **P0** → valeur `0` 💤

➡️ **P1** → valeur `0` 💤

➡️ **P2** → valeur `0` 💤

```blocks
input.onButtonPressed(Button.B, function () {
    for (let index = 0; index < 10; index++) {
        pins.digitalWritePin(DigitalPin.P0, 1)
        pins.digitalWritePin(DigitalPin.P1, 1)
        pins.digitalWritePin(DigitalPin.P2, 1)
        basic.pause(300)
        pins.digitalWritePin(DigitalPin.P0, 0)
        pins.digitalWritePin(DigitalPin.P1, 0)
        pins.digitalWritePin(DigitalPin.P2, 0)
    }
})
```

## Étape 14 — Bouton B : pause finale

➡️ Glisse un deuxième bloc ``||basic:pause (ms) 100||`` sous les trois blocs.

➡️ Remplace la valeur par `300`.

> 💡 Toutes les DEL s'allument et s'éteignent en même temps — comme des guirlandes qui clignotent ! 🎄

```blocks
input.onButtonPressed(Button.B, function () {
    for (let index = 0; index < 10; index++) {
        pins.digitalWritePin(DigitalPin.P0, 1)
        pins.digitalWritePin(DigitalPin.P1, 1)
        pins.digitalWritePin(DigitalPin.P2, 1)
        basic.pause(300)
        pins.digitalWritePin(DigitalPin.P0, 0)
        pins.digitalWritePin(DigitalPin.P1, 0)
        pins.digitalWritePin(DigitalPin.P2, 0)
        basic.pause(300)
    }
})
```

## Étape 15 — Bouton A+B : ajouter une boucle

✨ Ajoute une troisième séquence !

➡️ Glisse le bloc ``||loops:répéter 4 fois||`` à l'intérieur du bloc ``||input:lorsque le bouton A+B est pressé||``.

➡️ Remplace la valeur `4` par `10`.

```blocks
input.onButtonPressed(Button.AB, function () {
    for (let index = 0; index < 10; index++) {
    }
})
```

## Étape 16 — Bouton A+B : paquet 1

➡️ À l'intérieur de la boucle, glisse trois blocs ``||pins:écrire sur la broche||`` :

➡️ **P0** → valeur `1` 🔆

➡️ **P1** → valeur `1` 🔆

➡️ **P2** → valeur `0` 💤

➡️ Glisse ensuite un bloc ``||basic:pause (ms) 100||`` en dessous et remplace la valeur par `300`.

> 💡 Le premier paquet allume P0 et P1 ensemble !

```blocks
input.onButtonPressed(Button.AB, function () {
    for (let index = 0; index < 10; index++) {
        pins.digitalWritePin(DigitalPin.P0, 1)
        pins.digitalWritePin(DigitalPin.P1, 1)
        pins.digitalWritePin(DigitalPin.P2, 0)
        basic.pause(300)
    }
})
```

## Étape 17 — Bouton A+B : paquet 2

➡️ Sous la pause, glisse trois autres blocs ``||pins:écrire sur la broche||`` :

➡️ **P0** → valeur `0` 💤

➡️ **P1** → valeur `1` 🔆

➡️ **P2** → valeur `1` 🔆

➡️ Glisse ensuite un bloc ``||basic:pause (ms) 100||`` en dessous et remplace la valeur par `300`.

> 💡 Le deuxième paquet allume P1 et P2 ensemble !

```blocks
input.onButtonPressed(Button.AB, function () {
    for (let index = 0; index < 10; index++) {
        pins.digitalWritePin(DigitalPin.P0, 1)
        pins.digitalWritePin(DigitalPin.P1, 1)
        pins.digitalWritePin(DigitalPin.P2, 0)
        basic.pause(300)
        pins.digitalWritePin(DigitalPin.P0, 0)
        pins.digitalWritePin(DigitalPin.P1, 1)
        pins.digitalWritePin(DigitalPin.P2, 1)
        basic.pause(300)
    }
})
```

## Étape 18 — Bouton A+B : paquet 3

➡️ Sous la pause, glisse trois autres blocs ``||pins:écrire sur la broche||`` :

➡️ **P0** → valeur `1` 🔆

➡️ **P1** → valeur `0` 💤

➡️ **P2** → valeur `1` 🔆

➡️ Glisse ensuite un bloc ``||basic:pause (ms) 100||`` en dessous et remplace la valeur par `300`.

> 💡 Le troisième paquet allume P0 et P2 ensemble — la rotation est complète ! 🌟

```blocks
input.onButtonPressed(Button.AB, function () {
    for (let index = 0; index < 10; index++) {
        pins.digitalWritePin(DigitalPin.P0, 1)
        pins.digitalWritePin(DigitalPin.P1, 1)
        pins.digitalWritePin(DigitalPin.P2, 0)
        basic.pause(300)
        pins.digitalWritePin(DigitalPin.P0, 0)
        pins.digitalWritePin(DigitalPin.P1, 1)
        pins.digitalWritePin(DigitalPin.P2, 1)
        basic.pause(300)
        pins.digitalWritePin(DigitalPin.P0, 1)
        pins.digitalWritePin(DigitalPin.P1, 0)
        pins.digitalWritePin(DigitalPin.P2, 1)
        basic.pause(300)
    }
})
```

## Étape 19 — Secousse : éteindre P0

✨ Ajoute une quatrième séquence !

➡️ Glisse le bloc ``||pins:écrire sur la broche P0 la valeur 0||`` à l'intérieur du bloc ``||input:lorsque secouer||``.

➡️ Laisse la valeur à `0`.

```blocks
input.onGesture(Gesture.Shake, function () {
    pins.digitalWritePin(DigitalPin.P0, 0)
})
```

## Étape 20 — Secousse : éteindre P1 et P2

➡️ Glisse deux autres blocs ``||pins:écrire sur la broche||`` sous le premier :

➡️ **P1** → valeur `0` 💤

➡️ **P2** → valeur `0` 💤

```blocks
input.onGesture(Gesture.Shake, function () {
    pins.digitalWritePin(DigitalPin.P0, 0)
    pins.digitalWritePin(DigitalPin.P1, 0)
    pins.digitalWritePin(DigitalPin.P2, 0)
})
```

## Étape 21 — Secousse : afficher le sapin

➡️ Glisse le bloc ``||basic:montrer LEDs||`` sous les trois blocs et reproduis le dessin du sapin.

> 💡 En secouant le micro:bit, toutes les DEL s'éteignent et le sapin réapparaît — prêt pour une nouvelle animation ! 🎄

```blocks
input.onGesture(Gesture.Shake, function () {
    pins.digitalWritePin(DigitalPin.P0, 0)
    pins.digitalWritePin(DigitalPin.P1, 0)
    pins.digitalWritePin(DigitalPin.P2, 0)
    basic.showLeds(`
        . . # . .
        . # # # .
        # # # # #
        . . # . .
        . # # # .
        `)
})
```

## Étape 22 — Télécharger le programme

💾 Envoie ton programme sur le micro:bit !

➡️ Clique sur le bouton **Télécharger** pour transférer ton programme.

> 💡 Le programme doit être dans le micro:bit avant de réaliser le circuit !

## @showdialog

🔌 Réalise le branchement du circuit !

➡️ Rappelle-toi que la couleur des fils n'a aucune importance ! 🎨

> 💡 Trois DEL branchées sur **P0**, **P1** et **P2** — comme au tutoriel précédent !

❓ **Quelle est la différence entre les trois modes de clignotement ?**

## Étape 23 — Question réflexive 🤔

❓ **Quelle est la différence entre la cascade simple et la cascade en paquets de 2 ?**

❓ **Que se passe-t-il si tu appuies sur un bouton pendant qu'une animation est en cours ?**

> 💡 Avec les boucles ``||loops:répéter||``, le micro:bit doit terminer l'animation en cours avant de réagir à un nouveau bouton — c'est pourquoi la secousse n'arrête pas immédiatement l'animation !

## Étape 24 — Défi supplémentaire 🧠

**Défi de base :**

➡️ Modifie les valeurs des pauses pour accélérer ou ralentir les animations.

> ❓ Quelle combinaison de pauses donne l'effet le plus festif ? 🎄

**Défi avancé :**

➡️ Modifie la cascade simple pour qu'elle aille dans les deux sens — P0 → P1 → P2 → P2 → P1 → P0 — pour un effet de va-et-vient ! 🌊

```blocks
input.onButtonPressed(Button.A, function () {
    for (let index = 0; index < 5; index++) {
        pins.digitalWritePin(DigitalPin.P0, 1)
        pins.digitalWritePin(DigitalPin.P1, 0)
        pins.digitalWritePin(DigitalPin.P2, 0)
        basic.pause(300)
        pins.digitalWritePin(DigitalPin.P0, 0)
        pins.digitalWritePin(DigitalPin.P1, 1)
        pins.digitalWritePin(DigitalPin.P2, 0)
        basic.pause(300)
        pins.digitalWritePin(DigitalPin.P0, 0)
        pins.digitalWritePin(DigitalPin.P1, 0)
        pins.digitalWritePin(DigitalPin.P2, 1)
        basic.pause(300)
        pins.digitalWritePin(DigitalPin.P0, 0)
        pins.digitalWritePin(DigitalPin.P1, 1)
        pins.digitalWritePin(DigitalPin.P2, 0)
        basic.pause(300)
        pins.digitalWritePin(DigitalPin.P0, 1)
        pins.digitalWritePin(DigitalPin.P1, 0)
        pins.digitalWritePin(DigitalPin.P2, 0)
        basic.pause(300)
    }
})
```

> ❓ Est-ce que tu peux voir la différence entre la cascade simple et la cascade en va-et-vient ?

🚀 Bravo ! Tu viens de programmer un sapin de Noël lumineux avec le micro:bit ! 🎄🌟
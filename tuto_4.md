# Circuits électriques — Tutoriel 4

## @showdialog

🎯 **Objectif** : contrôle deux DEL 💡💡 indépendamment avec les boutons du micro:bit 💻 !

Dans ce tutoriel, tu vas apprendre à contrôler **deux broches** pour allumer et éteindre deux DEL séparément.

## Étape 1 — Préparer l'espace de travail

🧹 Fais le ménage !

➡️ Supprime les blocs ``||basic:au démarrage||`` et ``||basic:toujours||``.

> 💡 Le micro:bit va **attendre** que tu appuies sur un bouton avant de réagir !

## Étape 2 — Bouton A : allumer la DEL 1, éteindre la DEL 2 🔆💤

✨ Ajoute une première séquence !

➡️ Glisse le bloc ``||pins:écrire sur la broche P1 la valeur 0||`` à l'intérieur du bloc ``||input:lorsque le bouton A est pressé||``.

➡️ Remplace la valeur `0` par `1`.

➡️ Glisse ensuite le bloc ``||pins:écrire sur la broche P2 la valeur 0||`` en dessous.

➡️ Laisse la valeur à `0`.

> 💡 En appuyant sur **A**, la DEL 1 s'allume et la DEL 2 s'éteint !

```blocks
input.onButtonPressed(Button.A, function () {
    pins.digitalWritePin(DigitalPin.P1, 1)
    pins.digitalWritePin(DigitalPin.P2, 0)
})
```

## Étape 3 — Bouton B : allumer la DEL 2, éteindre la DEL 1 💤🔆

✨ Ajoute une deuxième séquence !

➡️ Glisse le bloc ``||pins:écrire sur la broche P1 la valeur 0||`` à l'intérieur du bloc ``||input:lorsque le bouton B est pressé||``.

➡️ Laisse la valeur à `0`.

➡️ Glisse ensuite le bloc ``||pins:écrire sur la broche P2 la valeur 0||`` en dessous.

➡️ Remplace la valeur `0` par `1`.

> 💡 En appuyant sur **B**, la DEL 2 s'allume et la DEL 1 s'éteint !

```blocks
input.onButtonPressed(Button.B, function () {
    pins.digitalWritePin(DigitalPin.P1, 0)
    pins.digitalWritePin(DigitalPin.P2, 1)
})
```

## Étape 4 — Bouton A+B : allumer les deux DEL 🔆🔆

✨ Ajoute une troisième séquence !

➡️ Glisse le bloc ``||pins:écrire sur la broche P1 la valeur 0||`` à l'intérieur du bloc ``||input:lorsque le bouton A+B est pressé||``.

➡️ Remplace la valeur `0` par `1`.

➡️ Glisse ensuite le bloc ``||pins:écrire sur la broche P2 la valeur 0||`` en dessous.

➡️ Remplace la valeur `0` par `1`.

> 💡 En appuyant sur **A+B**, les deux DEL s'allument en même temps !

```blocks
input.onButtonPressed(Button.AB, function () {
    pins.digitalWritePin(DigitalPin.P1, 1)
    pins.digitalWritePin(DigitalPin.P2, 1)
})
```

## Étape 5 — Secousse : éteindre les deux DEL 💤💤

✨ Ajoute une quatrième séquence !

➡️ Glisse le bloc ``||pins:écrire sur la broche P1 la valeur 0||`` à l'intérieur du bloc ``||input:lorsque secouer||``.

➡️ Laisse la valeur à `0`.

➡️ Glisse ensuite le bloc ``||pins:écrire sur la broche P2 la valeur 0||`` en dessous.

➡️ Laisse la valeur à `0`.

> 💡 En secouant le micro:bit, les deux DEL s'éteignent — comme un interrupteur général !

```blocks
input.onGesture(Gesture.Shake, function () {
    pins.digitalWritePin(DigitalPin.P1, 0)
    pins.digitalWritePin(DigitalPin.P2, 0)
})
```

## Étape 6 — Télécharger le programme

💾 Envoie ton programme sur le micro:bit !

➡️ Clique sur le bouton **Télécharger** pour transférer ton programme.

> 💡 Le programme doit être dans le micro:bit avant de réaliser le circuit !

## Étape 7 — Réaliser le circuit 🔌

🔌 Réalise le branchement du circuit !

➡️ Rappelle-toi que la couleur des fils n'a aucune importance ! 🎨

> 💡 Cette fois, tu vas brancher **deux DEL** — une sur la broche **P1** et une sur la broche **P2** !

❓ **Quelle est la différence entre le branchement de ce tutoriel et celui des tutoriels précédents ?**

## Étape 8 — Question réflexive 🤔

❓ **Pourquoi éteint-on une DEL en même temps qu'on allume l'autre ?**

❓ **À quoi pourrait ressembler ce circuit dans la vraie vie ?**

> 💡 En éteignant toujours l'autre DEL, on s'assure qu'une seule DEL est allumée à la fois — sauf avec **A+B** ! C'est le même principe qu'un interrupteur va-et-vient dans une maison 💡

## Étape 9 — Défi de base 🧠

➡️ Ajoute un bloc ``||basic:afficher texte||`` pour afficher le nom de la DEL allumée sur l'écran du micro:bit.

```blocks
input.onButtonPressed(Button.A, function () {
    pins.digitalWritePin(DigitalPin.P1, 1)
    pins.digitalWritePin(DigitalPin.P2, 0)
    basic.showString("DEL 1")
})
input.onButtonPressed(Button.B, function () {
    pins.digitalWritePin(DigitalPin.P1, 0)
    pins.digitalWritePin(DigitalPin.P2, 1)
    basic.showString("DEL 2")
})
input.onButtonPressed(Button.AB, function () {
    pins.digitalWritePin(DigitalPin.P1, 1)
    pins.digitalWritePin(DigitalPin.P2, 1)
    basic.showString("DEL 1+2")
})
input.onGesture(Gesture.Shake, function () {
    pins.digitalWritePin(DigitalPin.P1, 0)
    pins.digitalWritePin(DigitalPin.P2, 0)
    basic.clearScreen()
})
```

> ❓ Est-ce que l'écran du micro:bit affiche toujours le bon état ?

## Étape 10 — Défi avancé 🧠

➡️ Ajoute une icône différente pour chaque situation — un soleil ☀️ pour la DEL 1, une lune 🌙 pour la DEL 2, un cœur ❤️ pour les deux, et un écran vide pour la secousse.

```blocks
input.onButtonPressed(Button.A, function () {
    pins.digitalWritePin(DigitalPin.P1, 1)
    pins.digitalWritePin(DigitalPin.P2, 0)
    basic.showLeds(`
        . . # . .
        . # # # .
        # # # # #
        . # # # .
        . . # . .
        `)
})
input.onButtonPressed(Button.B, function () {
    pins.digitalWritePin(DigitalPin.P1, 0)
    pins.digitalWritePin(DigitalPin.P2, 1)
    basic.showLeds(`
        . . # # .
        . # . . .
        # . . . .
        . # . . .
        . . # # .
        `)
})
input.onButtonPressed(Button.AB, function () {
    pins.digitalWritePin(DigitalPin.P1, 1)
    pins.digitalWritePin(DigitalPin.P2, 1)
    basic.showIcon(IconNames.Heart)
})
input.onGesture(Gesture.Shake, function () {
    pins.digitalWritePin(DigitalPin.P1, 0)
    pins.digitalWritePin(DigitalPin.P2, 0)
    basic.clearScreen()
})
```

> ❓ Est-ce que les icônes correspondent bien à l'état des DEL ?

🚀 Bravo ! Tu sais maintenant contrôler deux DEL indépendamment avec le micro:bit !
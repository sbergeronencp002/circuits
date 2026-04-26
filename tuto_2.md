# Circuits électriques — Tutoriel 2

## @showdialog

🎯 **Objectif** : contrôle une DEL 💡 avec les boutons du micro:bit 💻 !

Dans ce tutoriel, tu vas apprendre à utiliser les **boutons A et B** du micro:bit pour allumer et éteindre ta DEL.

## Étape 1 — Préparer l'espace de travail

🧹 Fais le ménage !

➡️ Supprime les blocs ``||basic:au démarrage||`` et ``||basic:toujours||``.

> 💡 Cette fois, le micro:bit va **attendre** que tu appuies sur un bouton avant de réagir !

## Étape 2 — Bouton A : allumer la DEL 🔆

✨ Ajoute une première séquence !

➡️ Glisse le bloc ``||pins:écrire sur la broche P1 la valeur 0||`` à l'intérieur du bloc ``||input:lorsque le bouton A est pressé||``.

➡️ Remplace la valeur `0` par `1`.

> 💡 En appuyant sur **A**, le micro:bit envoie un signal **allumé** sur la broche P1 — la DEL s'allume !

```blocks
input.onButtonPressed(Button.A, function () {
    pins.digitalWritePin(DigitalPin.P1, 1)
})
```

## Étape 3 — Bouton B : éteindre la DEL 💤

✨ Ajoute une deuxième séquence !

➡️ Glisse le bloc ``||pins:écrire sur la broche P1 la valeur 0||`` à l'intérieur du bloc ``||input:lorsque le bouton B est pressé||``.

➡️ Laisse la valeur à `0`.

> 💡 En appuyant sur **B**, le micro:bit envoie un signal **éteint** sur la broche P1 — la DEL s'éteint !

```blocks
input.onButtonPressed(Button.B, function () {
    pins.digitalWritePin(DigitalPin.P1, 0)
})
```

## Étape 4 — Télécharger le programme

💾 Envoie ton programme sur le micro:bit !

➡️ Clique sur le bouton **Télécharger** pour transférer ton programme.

> 💡 Le programme doit être dans le micro:bit avant de réaliser le circuit !

## Étape 5 — Réaliser le circuit 🔌

🔌 Réalise le branchement du circuit. !

➡️ Rappelle-toi que la couleur des fils n'a aucune importance ! 🎨

> 💡 C'est sensiblement le même branchement qu'au tutoriel précédent — mais cette fois, c'est **toi** qui décides quand la DEL s'allume !

❓ **Quelle est la différence entre le branchement de ce tutoriel et celui du tutoriel précédent ?**

## Étape 6 — Question réflexive 🤔

❓ **Quelle est la différence entre ce programme et celui du tutoriel précédent ?**

❓ **Que se passe-t-il si tu appuies sur A et B en même temps ?**

> 💡 Au tutoriel 1, la DEL s'allumait **automatiquement** dès le démarrage. Ici, c'est **toi** qui contrôles — le micro:bit attend tes instructions avant d'agir. C'est la puissance des **événements** !

## Étape 7 — Défi de base 🧠

➡️ Ajoute un bloc ``||basic:afficher texte||`` pour afficher `"ON"` quand tu appuies sur **A** et `"OFF"` quand tu appuies sur **B**.

```blocks
input.onButtonPressed(Button.A, function () {
    pins.digitalWritePin(DigitalPin.P1, 1)
    basic.showString("ON")
})
input.onButtonPressed(Button.B, function () {
    pins.digitalWritePin(DigitalPin.P1, 0)
    basic.showString("OFF")
})
```

> ❓ Est-ce que l'écran du micro:bit affiche toujours le bon état ?

## Étape 8 — Défi avancé 🧠

➡️ Remplace les textes `"ON"` et `"OFF"` par des icônes — affiche le soleil ☀️ quand la DEL est allumée et la lune 🌙 quand elle est éteinte.

➡️ Ajoute également une séquence pour le bouton **A+B** — affiche une icône de ton choix et éteins la DEL.

```blocks
input.onButtonPressed(Button.A, function () {
    pins.digitalWritePin(DigitalPin.P1, 1)
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
    basic.showLeds(`
        . . # # .
        . # . . .
        # . . . .
        . # . . .
        . . # # .
        `)
})
input.onButtonPressed(Button.AB, function () {
    pins.digitalWritePin(DigitalPin.P1, 0)
    basic.clearScreen()
})
```

> ❓ Que se passe-t-il sur l'écran du micro:bit après avoir appuyé sur A+B ?

🚀 Bravo ! Tu sais maintenant contrôler une DEL avec les boutons du micro:bit !
# Circuits électriques — Tutoriel 3

## @showdialog

🎯 **Objectif** : programme une DEL 💡 pour qu'elle clignote avec le micro:bit 💻 !

Dans ce tutoriel, tu vas apprendre à utiliser une **boucle** et des **pauses** pour faire clignoter ta DEL automatiquement.

## Étape 1 — Préparer l'espace de travail

🧹 Fais le ménage !

➡️ Supprime les blocs ``||basic:au démarrage||`` et ``||basic:toujours||``.

> 💡 Cette fois, le micro:bit va **attendre** que tu appuies sur le bouton **A** avant de faire clignoter la DEL !

## Étape 2 — Ajouter une boucle

✨ Ajoute une boucle !

➡️ Glisse le bloc ``||loops:répéter 4 fois||`` à l'intérieur du bloc ``||input:lorsque le bouton A est pressé||``.

➡️ Remplace la valeur `4` par `10`.

> 💡 La boucle va répéter les actions à l'intérieur **10 fois** — la DEL clignotera 10 fois à chaque appui sur **A** !

```blocks
input.onButtonPressed(Button.A, function () {
    for (let index = 0; index < 10; index++) {
    }
})
```

## Étape 3 — Allumer la DEL

✨ Remplis la boucle !

➡️ Glisse le bloc ``||pins:écrire sur la broche P2 la valeur 0||`` à l'intérieur de la boucle.

➡️ Remplace la valeur `0` par `1`.

> 💡 Ce bloc allume la DEL en envoyant un signal **allumé** sur la broche P2 !

```blocks
input.onButtonPressed(Button.A, function () {
    for (let index = 0; index < 10; index++) {
        pins.digitalWritePin(DigitalPin.P2, 1)
    }
})
```

## Étape 4 — Ajouter une pause

⏱️ Ajoute une première pause !

➡️ Glisse le bloc ``||basic:pause (ms) 100||`` sous le bloc ``||pins:écrire sur la broche||``.

➡️ Remplace la valeur `100` par `500`.

> 💡 La pause de `500 ms` correspond à **une demi-seconde** — la DEL restera allumée pendant ce temps !

```blocks
input.onButtonPressed(Button.A, function () {
    for (let index = 0; index < 10; index++) {
        pins.digitalWritePin(DigitalPin.P2, 1)
        basic.pause(500)
    }
})
```

## Étape 5 — Éteindre la DEL

✨ Ajoute un deuxième bloc !

➡️ Glisse un deuxième bloc ``||pins:écrire sur la broche P2 la valeur 0||`` sous la pause.

➡️ Laisse la valeur à `0`.

> 💡 Ce bloc éteint la DEL en envoyant un signal **éteint** sur la broche P2 !

```blocks
input.onButtonPressed(Button.A, function () {
    for (let index = 0; index < 10; index++) {
        pins.digitalWritePin(DigitalPin.P2, 1)
        basic.pause(500)
        pins.digitalWritePin(DigitalPin.P2, 0)
    }
})
```

## Étape 6 — Ajouter une deuxième pause

⏱️ Ajoute une deuxième pause !

➡️ Glisse un deuxième bloc ``||basic:pause (ms) 100||`` sous le bloc ``||pins:écrire sur la broche||``.

➡️ Remplace la valeur `100` par `500`.

> 💡 À chaque tour de boucle : la DEL s'allume, attend **500 ms**, s'éteint, attend **500 ms** — et recommence ! La DEL clignotera **10 fois** au total.

```blocks
input.onButtonPressed(Button.A, function () {
    for (let index = 0; index < 10; index++) {
        pins.digitalWritePin(DigitalPin.P2, 1)
        basic.pause(500)
        pins.digitalWritePin(DigitalPin.P2, 0)
        basic.pause(500)
    }
})
```

## Étape 7 — Télécharger le programme

💾 Envoie ton programme sur le micro:bit !

➡️ Clique sur le bouton **Télécharger** pour transférer ton programme.

> 💡 Le programme doit être dans le micro:bit avant de réaliser le circuit !

## @showdialog

🔌 Réalise le branchement du circuit !

➡️ Rappelle-toi que la couleur des fils n'a aucune importance ! 🎨

> 💡 C'est sensiblement le même branchement qu'aux tutoriels précédents !

❓ **Quelle est la différence entre le branchement de ce tutoriel et celui du tutoriel précédent ?**

## Étape 8 — Question réflexive 🤔

❓ **Quelle est la différence entre le bloc ``||basic:toujours||`` et le bloc ``||loops:répéter||`` ?**

❓ **Que se passe-t-il si tu changes la valeur de la boucle à `3` ? Et à `20` ?**

> 💡 Le bloc ``||basic:toujours||`` répète indéfiniment — il ne s'arrête jamais. Le bloc ``||loops:répéter||`` s'arrête après un nombre précis de répétitions — c'est toi qui décides combien de fois la DEL clignote !

## Étape 9 — Défi supplémentaire 🧠

**Défi de base :**

➡️ Remplace le bouton **A** par l'événement ``||input:lorsque secouer||`` pour déclencher le clignotement en secouant le micro:bit !

```blocks
input.onGesture(Gesture.Shake, function () {
    for (let index = 0; index < 10; index++) {
        pins.digitalWritePin(DigitalPin.P2, 1)
        basic.pause(500)
        pins.digitalWritePin(DigitalPin.P2, 0)
        basic.pause(500)
    }
})
```

> ❓ Que se passe-t-il si tu secoues le micro:bit pendant que la DEL clignote déjà ?

**Défi avancé :**

➡️ Combine les deux événements — utilise le bouton **A** pour un clignotement lent (`500 ms`) et la secousse pour un clignotement rapide (`100 ms`).

➡️ Ajoute un bloc ``||basic:afficher texte||`` pour afficher `"Lent"` ou `"Rapide"` sur l'écran du micro:bit selon l'événement déclenché.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.showString("Lent")
    for (let index = 0; index < 10; index++) {
        pins.digitalWritePin(DigitalPin.P2, 1)
        basic.pause(500)
        pins.digitalWritePin(DigitalPin.P2, 0)
        basic.pause(500)
    }
})
input.onGesture(Gesture.Shake, function () {
    basic.showString("Rapide")
    for (let index = 0; index < 10; index++) {
        pins.digitalWritePin(DigitalPin.P2, 1)
        basic.pause(100)
        pins.digitalWritePin(DigitalPin.P2, 0)
        basic.pause(100)
    }
})
```

> ❓ Est-ce que l'écran du micro:bit affiche toujours le bon message ?
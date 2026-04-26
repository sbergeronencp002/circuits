# Circuits électriques — Tutoriel 1

## @showdialog

🎯 **Objectif** : programme un micro:bit 💻 et réalise un petit circuit électrique 🔌 pour allumer une DEL 💡 !

Dans ce tutoriel, tu vas découvrir comment utiliser les **broches** du micro:bit pour envoyer un signal électrique à une DEL.

## Étape 1 — Préparer l'espace de travail

🧹 Fais le ménage !

➡️ Supprime le bloc ``||basic:au démarrage||``.

> 💡 On garde le bloc ``||basic:toujours||`` — on va s'en servir à l'étape suivante !

## Étape 2 — Éteindre la DEL

✨ Ajoute un premier bloc !

➡️ Glisse le bloc ``||pins:écrire sur la broche P0 la valeur 0||`` à l'intérieur du bloc ``||basic:toujours||``.

> 💡 La valeur `0` envoie un signal 💤 **éteint** sur la broche P0 — la DEL ne s'allumera pas encore !

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P0, 0)
})
```

## Étape 3 — Allumer la DEL

✏️ Modifie la valeur !

➡️ Remplace la valeur `0` par `1` dans le bloc ``||pins:écrire sur la broche||``.

> 💡 La valeur `1` envoie un signal 🔆 **allumé** sur la broche P0 — la DEL va s'allumer !

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P0, 1)
})
```

## Étape 4 — Télécharger le programme

💾 Envoie ton programme sur le micro:bit !

➡️ Clique sur le bouton **Télécharger** pour transférer ton programme.

> 💡 Le programme doit être dans le micro:bit avant de réaliser le circuit — comme ça, la DEL s'allumera dès que tu brancheras les fils !

## Étape 5 — Réaliser le circuit 🔌

🔌 Réalise le branchement ci-dessous !

➡️ La couleur des fils n'a aucune importance ! 🎨

![Circuit DEL](https://github.com/sbergeroncp/micro-seb/blob/master/1.png?raw=true)

> 💡 Le micro:bit agit comme un **interrupteur numérique** — c'est ton programme qui décide si la DEL est allumée ou éteinte !

## Étape 6 — Question réflexive 🤔

❓ **Que se passerait-il si tu remettais la valeur `0` dans ton programme ?**

❓ **Quelle est la différence entre allumer une DEL avec un interrupteur ordinaire et avec un micro:bit ?**

> 💡 Avec un interrupteur ordinaire, c'est toi qui allumes manuellement. Avec le micro:bit, c'est ton **programme** qui contrôle la lumière — tu pourrais l'allumer automatiquement, à distance, ou selon des conditions !

## Étape 7 — Défi de base 🧠

➡️ Modifie ton programme pour que la DEL clignote — alterne entre `0` et `1` avec une pause de `500 ms` entre les deux.

```blocks
basic.forever(function () {
    pins.digitalWritePin(DigitalPin.P0, 1)
    basic.pause(500)
    pins.digitalWritePin(DigitalPin.P0, 0)
    basic.pause(500)
})
```

> ❓ Que se passe-t-il si tu changes la valeur de la pause à `100` ? Et à `1000` ?

## Étape 8 — Défi avancé 🧠

➡️ Utilise une boucle ``||loops:répéter 4 fois||`` pour faire clignoter la DEL un nombre précis de fois, puis l'éteindre définitivement.

➡️ Remplace la valeur `4` par `10`.

➡️ Remplace le bloc ``||basic:toujours||`` par le bloc ``||input:lorsque le bouton A est pressé||`` pour déclencher l'animation sur demande.

```blocks
input.onButtonPressed(Button.A, function () {
    for (let index = 0; index < 10; index++) {
        pins.digitalWritePin(DigitalPin.P0, 1)
        basic.pause(200)
        pins.digitalWritePin(DigitalPin.P0, 0)
        basic.pause(200)
    }
})
```

🚀 Bravo ! Tu sais maintenant contrôler une DEL avec le micro:bit !
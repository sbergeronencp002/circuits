# Circuits électriques — Tutoriel 5

## @showdialog

🎯 **Objectif** : allume une DEL 💡 automatiquement quand il fait sombre et affiche le pourcentage de luminosité sur demande !

Dans ce tutoriel, tu vas combiner le **capteur de luminosité**, une **variable**, une **condition** et les **boutons** pour créer une vraie veilleuse intelligente !

## Étape 1 — Préparer l'espace de travail

🧹 Fais le ménage !

➡️ Supprime le bloc ``||basic:au démarrage||``.

> 💡 On garde le bloc ``||basic:toujours||`` — le micro:bit va lire la luminosité en continu !

## Étape 2 — Créer une variable

✨ Crée une variable !

➡️ Clique sur **Variables** dans le menu, puis sur **Créer une variable**.

➡️ Nomme-la `luminosite`.

➡️ Glisse le bloc ``||variables:définir luminosite à 0||`` à l'intérieur du bloc ``||basic:toujours||``.

> 💡 La variable `luminosite` va mémoriser le pourcentage de luminosité calculé à chaque instant !

```blocks
basic.forever(function () {
    let luminosite = 0
})
```

## Étape 3 — Insérer le capteur de luminosité

➡️ Remplace le `0` du bloc ``||variables:définir luminosite à 0||`` par le bloc ``||input:niveau d'intensité lumineuse||``.

> 💡 Le capteur retourne une valeur entre `0` (noir total) et `255` (très lumineux) !

```blocks
basic.forever(function () {
    let luminosite = input.lightLevel()
})
```

## Étape 4 — Multiplier par 100

➡️ Entoure le bloc ``||input:niveau d'intensité lumineuse||`` avec le bloc ``||math:0 × 0||`` depuis l'onglet **Maths**.

➡️ Dans la partie gauche, garde le bloc ``||input:niveau d'intensité lumineuse||``.

➡️ Dans la partie droite, écris `100`.

```blocks
basic.forever(function () {
    let luminosite = input.lightLevel() * 100
})
```

## Étape 5 — Diviser par 255

➡️ Entoure le calcul précédent avec le bloc ``||math:0 ÷ 0||``.

➡️ Dans la partie droite, écris `255`.

> 💡 La formule `luminosité × 100 ÷ 255` convertit la valeur brute en pourcentage — `0%` pour le noir total et `100%` pour le maximum de lumière !

```blocks
basic.forever(function () {
    let luminosite = input.lightLevel() * 100 / 255
})
```

## Étape 6 — Ajouter la première condition

✨ Ajoute une première condition !

➡️ Glisse un bloc ``||logic:si vrai alors||`` sous le bloc ``||variables:définir luminosite||``.

➡️ Dans la case de la condition, glisse le bloc de comparaison ``||logic:0 < 0||``.

➡️ Dans la partie gauche, insère la variable `luminosite`. Dans la partie droite, écris `40`.

> 💡 Si la luminosité est **inférieure à `40%`**, il fait sombre !

```blocks
basic.forever(function () {
    let luminosite = input.lightLevel() * 100 / 255
    if (luminosite < 40) {
    }
})
```

## Étape 7 — Allumer la DEL si sombre

➡️ À l'intérieur de la première condition, glisse le bloc ``||pins:écrire sur la broche P0 la valeur 0||``.

➡️ Remplace la valeur `0` par `1`.

> 💡 Quand il fait sombre, le micro:bit envoie un signal **allumé** sur la broche P0 — la DEL s'allume automatiquement !

```blocks
basic.forever(function () {
    let luminosite = input.lightLevel() * 100 / 255
    if (luminosite < 40) {
        pins.digitalWritePin(DigitalPin.P0, 1)
    }
})
```

## Étape 8 — Ajouter la deuxième condition

✨ Ajoute une deuxième condition !

➡️ Glisse un deuxième bloc ``||logic:si vrai alors||`` sous le premier.

➡️ Dans la case de la condition, glisse le bloc de comparaison ``||logic:0 ≥ 0||``.

➡️ Dans la partie gauche, insère la variable `luminosite`. Dans la partie droite, écris `40`.

> 💡 Si la luminosité est **supérieure ou égale à `40%`**, il fait clair !

```blocks
basic.forever(function () {
    let luminosite = input.lightLevel() * 100 / 255
    if (luminosite < 40) {
        pins.digitalWritePin(DigitalPin.P0, 1)
    }
    if (luminosite >= 40) {
    }
})
```

## Étape 9 — Éteindre la DEL si clair

➡️ À l'intérieur de la deuxième condition, glisse le bloc ``||pins:écrire sur la broche P0 la valeur 0||``.

➡️ Laisse la valeur à `0`.

> 💡 Quand il fait clair, le micro:bit envoie un signal **éteint** sur la broche P0 — la DEL s'éteint automatiquement !

```blocks
basic.forever(function () {
    let luminosite = input.lightLevel() * 100 / 255
    if (luminosite < 40) {
        pins.digitalWritePin(DigitalPin.P0, 1)
    }
    if (luminosite >= 40) {
        pins.digitalWritePin(DigitalPin.P0, 0)
    }
})
```

## Étape 10 — Bouton A : afficher le pourcentage

✨ Ajoute une séquence pour le bouton A !

➡️ Glisse le bloc ``||basic:afficher nombre||`` à l'intérieur du bloc ``||input:lorsque le bouton A est pressé||``.

➡️ Dans le bloc ``||basic:afficher nombre||``, insère la variable `luminosite`.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.showNumber(luminosite)
})
```

## Étape 11 — Bouton A : pause et effacement

➡️ Glisse le bloc ``||basic:pause (ms) 100||`` sous le bloc ``||basic:afficher nombre||``.

➡️ Remplace la valeur par `2000`.

➡️ Glisse ensuite le bloc ``||basic:effacer l'écran||`` en dessous.

> 💡 Le micro:bit affiche le pourcentage de luminosité pendant **2 secondes**, puis efface l'écran — prêt pour la prochaine lecture !

```blocks
input.onButtonPressed(Button.A, function () {
    basic.showNumber(luminosite)
    basic.pause(2000)
    basic.clearScreen()
})
```

## Étape 12 — Télécharger le programme

💾 Envoie ton programme sur le micro:bit !

➡️ Clique sur le bouton **Télécharger** pour transférer ton programme.

> 💡 Le programme doit être dans le micro:bit avant de réaliser le circuit !

## Étape 13 — Réaliser le circuit 🔌

🔌 Réalise le branchement du circuit !

➡️ Rappelle-toi que la couleur des fils n'a aucune importance ! 🎨

> 💡 Une seule DEL branchée sur la broche **P0** — comme au tutoriel 1 !

❓ **Quelle est la différence entre le branchement de ce tutoriel et celui des tutoriels précédents ?**

## Étape 14 — Question réflexive 🤔

❓ **Pourquoi utilise-t-on une variable plutôt que d'insérer directement le capteur dans les conditions ?**

❓ **À quoi pourrait ressembler ce circuit dans la vraie vie ?**

> 💡 La variable `luminosite` permet de calculer le pourcentage **une seule fois** et de le réutiliser partout — dans les conditions ET dans l'affichage. Sans variable, il faudrait recalculer à chaque fois ! Ce principe est utilisé dans les lampadaires intelligents et les veilleuses automatiques 🌙

## Étape 15 — Défi de base 🧠

➡️ Modifie le seuil de `40` pour qu'il corresponde mieux à la luminosité de ta classe.

➡️ Appuie sur **A** pour vérifier le pourcentage et ajuster au besoin.

> ❓ Quelle valeur donne le meilleur résultat dans ton environnement ?

## Étape 16 — Défi avancé 🧠

➡️ Ajoute une icône sur l'écran du micro:bit — la lune 🌙 quand la DEL est allumée et le soleil ☀️ quand elle est éteinte.

➡️ Ajoute aussi le bouton **B** pour afficher un message `"Sombre"` ou `"Clair"` selon la luminosité actuelle.

```blocks
let luminosite = 0
basic.forever(function () {
    luminosite = input.lightLevel() * 100 / 255
    if (luminosite < 40) {
        pins.digitalWritePin(DigitalPin.P0, 1)
        basic.showLeds(`
            . . # # .
            . # . . .
            # . . . .
            . # . . .
            . . # # .
            `)
    }
    if (luminosite >= 40) {
        pins.digitalWritePin(DigitalPin.P0, 0)
        basic.showLeds(`
            . . # . .
            . # # # .
            # # # # #
            . # # # .
            . . # . .
            `)
    }
})
input.onButtonPressed(Button.A, function () {
    basic.showNumber(luminosite)
    basic.pause(2000)
    basic.clearScreen()
})
input.onButtonPressed(Button.B, function () {
    if (luminosite < 40) {
        basic.showString("Sombre")
        basic.pause(2000)
        basic.clearScreen()
    }
    if (luminosite >= 40) {
        basic.showString("Clair")
        basic.pause(2000)
        basic.clearScreen()
    }
})
```

> ❓ Est-ce que l'icône et le message correspondent bien à l'état de la DEL ?

🚀 Bravo ! Tu sais maintenant utiliser le capteur de luminosité pour contrôler une DEL automatiquement et afficher le pourcentage de luminosité !
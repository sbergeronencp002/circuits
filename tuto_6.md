# Circuits électriques — Tutoriel 6

## @showdialog

🎯 **Objectif** : allume une DEL 💡 automatiquement selon la température et affiche la température sur demande !

Dans ce tutoriel, tu vas combiner le **capteur de température**, une **variable**, une **condition** et les **boutons** pour créer un vrai thermomètre intelligent !

## Étape 1 — Préparer l'espace de travail

🧹 Fais le ménage !

➡️ Supprime le bloc ``||basic:au démarrage||``.

> 💡 On garde le bloc ``||basic:toujours||`` — le micro:bit va lire la température en continu !

## Étape 2 — Créer une variable

✨ Crée une variable !

➡️ Clique sur **Variables** dans le menu, puis sur **Créer une variable**.

➡️ Nomme-la `temperature`.

➡️ Glisse le bloc ``||variables:définir temperature à 0||`` à l'intérieur du bloc ``||basic:toujours||``.

> 💡 La variable `temperature` va mémoriser la valeur lue par le capteur à chaque instant !

```blocks
let temperature = 0
basic.forever(function () {
    temperature = 0
})
```

## Étape 3 — Insérer le capteur de température

➡️ Remplace le `0` du bloc ``||variables:définir temperature à 0||`` par le bloc ``||input:température (°C)||``.

> 💡 Le capteur retourne la température en degrés Celsius — généralement entre `0°C` et `40°C` en classe !

```blocks
basic.forever(function () {
    let temperature = input.temperature()
})
```

## Étape 4 — Ajouter la première condition

✨ Ajoute une première condition !

➡️ Glisse un bloc ``||logic:si vrai alors||`` sous le bloc ``||variables:définir temperature||``.

➡️ Dans la case de la condition, glisse le bloc de comparaison ``||logic:0 > 0||``.

➡️ Dans la partie gauche, insère la variable `temperature`. Dans la partie droite, écris `25`.

> 💡 Si la température est **supérieure à `25°C`**, il fait chaud !

```blocks
basic.forever(function () {
    let temperature = input.temperature()
    if (temperature > 25) {
    }
})
```

## Étape 5 — Allumer la DEL si chaud

➡️ À l'intérieur de la première condition, glisse le bloc ``||pins:écrire sur la broche P2 la valeur 0||``.

➡️ Remplace la valeur `0` par `1`.

> 💡 Quand il fait chaud, le micro:bit envoie un signal **allumé** sur la broche P2 — la DEL s'allume automatiquement !

```blocks
basic.forever(function () {
    let temperature = input.temperature()
    if (temperature > 25) {
        pins.digitalWritePin(DigitalPin.P2, 1)
    }
})
```

## Étape 6 — Ajouter la deuxième condition

✨ Ajoute une deuxième condition !

➡️ Glisse un deuxième bloc ``||logic:si vrai alors||`` sous le premier.

➡️ Dans la case de la condition, glisse le bloc de comparaison ``||logic:0 ≤ 0||``.

➡️ Dans la partie gauche, insère la variable `temperature`. Dans la partie droite, écris `25`.

> 💡 Si la température est **inférieure ou égale à `25°C`**, il fait frais !

```blocks
basic.forever(function () {
    let temperature = input.temperature()
    if (temperature > 25) {
        pins.digitalWritePin(DigitalPin.P2, 1)
    }
    if (temperature <= 25) {
    }
})
```

## Étape 7 — Éteindre la DEL si frais

➡️ À l'intérieur de la deuxième condition, glisse le bloc ``||pins:écrire sur la broche P2 la valeur 0||``.

➡️ Laisse la valeur à `0`.

> 💡 Quand il fait frais, le micro:bit envoie un signal **éteint** sur la broche P2 — la DEL s'éteint automatiquement !

```blocks
basic.forever(function () {
    let temperature = input.temperature()
    if (temperature > 25) {
        pins.digitalWritePin(DigitalPin.P2, 1)
    }
    if (temperature <= 25) {
        pins.digitalWritePin(DigitalPin.P2, 0)
    }
})
```

## Étape 8 — Bouton A : afficher la température

✨ Ajoute une séquence pour le bouton A !

➡️ Glisse le bloc ``||basic:afficher nombre||`` à l'intérieur du bloc ``||input:lorsque le bouton A est pressé||``.

➡️ Dans le bloc ``||basic:afficher nombre||``, insère la variable `temperature`.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.showNumber(temperature)
})
```

## Étape 9 — Bouton A : pause et effacement

➡️ Glisse le bloc ``||basic:pause (ms) 100||`` sous le bloc ``||basic:afficher nombre||``.

➡️ Remplace la valeur par `2000`.

➡️ Glisse ensuite le bloc ``||basic:effacer l'écran||`` en dessous.

> 💡 Le micro:bit affiche la température pendant **2 secondes**, puis efface l'écran — prêt pour la prochaine lecture !

```blocks
input.onButtonPressed(Button.A, function () {
    basic.showNumber(temperature)
    basic.pause(2000)
    basic.clearScreen()
})
```

## Étape 10 — Télécharger le programme

💾 Envoie ton programme sur le micro:bit !

➡️ Clique sur le bouton **Télécharger** pour transférer ton programme.

> 💡 Le programme doit être dans le micro:bit avant de réaliser le circuit !

## @showdialog

🔌 Réalise le branchement du circuit !

➡️ Rappelle-toi que la couleur des fils n'a aucune importance ! 🎨

> 💡 Une seule DEL branchée sur la broche **P2** !

❓ **Quelle est la différence entre ce tutoriel et le tutoriel précédent sur la luminosité ?**

## Étape 11 — Question réflexive 🤔

❓ **Pourquoi la DEL s'allume-t-elle quand il fait chaud plutôt que quand il fait froid ?**

❓ **À quoi pourrait ressembler ce circuit dans la vraie vie ?**

> 💡 Ce principe est utilisé dans les thermostats, les climatiseurs intelligents et les serres agricoles — quand la température dépasse un seuil, un système se déclenche automatiquement ! 🌡️

## Étape 12 — Défi supplémentaire 🧠

**Défi de base :**

➡️ Modifie le seuil de `25` pour qu'il corresponde mieux à la température de ta classe.

➡️ Appuie sur **A** pour vérifier la température et ajuster au besoin.

> ❓ Quelle valeur donne le meilleur résultat dans ton environnement ?

**Défi avancé :**

➡️ Ajoute une icône sur l'écran du micro:bit — le soleil ☀️ quand la DEL est allumée et le flocon ❄️ quand elle est éteinte.

➡️ Ajoute aussi le bouton **B** pour afficher un message `"Chaud !"` ou `"Frais !"` selon la température actuelle.

```blocks
let temperature = 0
basic.forever(function () {
    temperature = input.temperature()
    if (temperature > 25) {
        pins.digitalWritePin(DigitalPin.P2, 1)
        basic.showLeds(`
            . . # . .
            . # # # .
            # # # # #
            . # # # .
            . . # . .
            `)
    }
    if (temperature <= 25) {
        pins.digitalWritePin(DigitalPin.P2, 0)
        basic.showLeds(`
            # . # . #
            . # # # .
            # # # # #
            . # # # .
            # . # . #
            `)
    }
})
input.onButtonPressed(Button.A, function () {
    basic.showNumber(temperature)
    basic.pause(2000)
    basic.clearScreen()
})
input.onButtonPressed(Button.B, function () {
    if (temperature > 25) {
        basic.showString("Chaud !")
        basic.pause(2000)
        basic.clearScreen()
    }
    if (temperature <= 25) {
        basic.showString("Frais !")
        basic.pause(2000)
        basic.clearScreen()
    }
})
```

> ❓ Est-ce que l'icône et le message correspondent bien à l'état de la DEL ?

🚀 Bravo ! Tu sais maintenant utiliser le capteur de température pour contrôler une DEL automatiquement !
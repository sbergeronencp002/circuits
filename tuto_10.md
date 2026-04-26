# Circuits électriques — Tutoriel 10

## @showdialog

🎯 **Objectif** : envoie des messages secrets en code Morse avec une seule DEL ! ✉️

Dans ce tutoriel, tu vas utiliser les **fonctions** pour créer les deux briques de base du morse — le **point** et le **tiret** — et les assembler pour transmettre un vrai message !

C'est parti ! 🚀

## Étape 1 — Préparer l'espace de travail

🧹 Fais le ménage !

➡️ Supprime les blocs ``||basic:au démarrage||`` et ``||basic:toujours||``.

> 💡 On va construire notre programme entièrement avec des **fonctions** — deux briques suffisent pour tout le morse !

## Étape 2 — Créer la fonction « point »

✨ La première brique du morse !

➡️ Clique sur **Fonctions** dans le menu, puis sur **Créer une fonction**.

➡️ Nomme-la `point`.

➡️ À l'intérieur : allume P0, attends `200` ms, éteins P0, attends `200` ms.

> 💡 En morse, un **point** est un signal **court** — une petite lumière rapide !

```blocks
function point() {
    pins.digitalWritePin(DigitalPin.P0, 1)
    basic.pause(200)
    pins.digitalWritePin(DigitalPin.P0, 0)
    basic.pause(200)
}
```

## Étape 3 — Créer la fonction « tiret »

✨ La deuxième brique du morse !

➡️ Crée une nouvelle fonction et nomme-la `tiret`.

➡️ À l'intérieur : allume P0, attends `600` ms, éteins P0, attends `200` ms.

> 💡 En morse, un **tiret** dure **3 fois plus longtemps** qu'un point — une lumière longue !

```blocks
function tiret() {
    pins.digitalWritePin(DigitalPin.P0, 1)
    basic.pause(600)
    pins.digitalWritePin(DigitalPin.P0, 0)
    basic.pause(200)
}
```

## Étape 4 — Créer la fonction « pause_lettre »

✨ Une pause entre les lettres !

➡️ Crée une nouvelle fonction et nomme-la `pause_lettre`.

➡️ À l'intérieur, glisse simplement un bloc ``||basic:pause (ms) 100||`` et remplace la valeur par `400`.

> 💡 En morse, on marque une **pause** entre chaque lettre pour que le destinataire sache quand une lettre se termine et quand la suivante commence !

```blocks
function pause_lettre() {
    basic.pause(400)
}
```

## Étape 5 — Coder la lettre S

✨ Assemblons les briques !

➡️ Crée une nouvelle fonction et nomme-la `lettre_S`.

➡️ La lettre S en morse, c'est **trois points** : `· · ·`

➡️ À l'intérieur, appelle `point` trois fois, puis `pause_lettre`.

> 💡 La lettre **S** est l'une des plus simples en morse — trois points, et c'est tout !

```blocks
function lettre_S() {
    point()
    point()
    point()
    pause_lettre()
}
```

## Étape 6 — Coder la lettre O

✨ La deuxième lettre !

➡️ Crée une nouvelle fonction et nomme-la `lettre_O`.

➡️ La lettre O en morse, c'est **trois tirets** : `— — —`

➡️ À l'intérieur, appelle `tiret` trois fois, puis `pause_lettre`.

> 💡 La lettre **O** est tout aussi simple — mais avec des tirets. S + O + S = le signal de détresse universel !

```blocks
function lettre_O() {
    tiret()
    tiret()
    tiret()
    pause_lettre()
}
```

## Étape 7 — Envoyer SOS 🆘

✨ Assemble le message !

➡️ Crée une nouvelle fonction et nomme-la `SOS`.

➡️ À l'intérieur, appelle `lettre_S`, `lettre_O`, `lettre_S`.

➡️ Glisse le bloc ``||input:lorsque le bouton A est pressé||`` dans l'espace de travail.

➡️ À l'intérieur, appelle `SOS`.

> 💡 Regarde ton code : le bloc bouton A contient **un seul appel** — et pourtant il envoie 9 signaux lumineux précis. C'est la puissance des fonctions empilées !

```blocks
function SOS() {
    lettre_S()
    lettre_O()
    lettre_S()
}
input.onButtonPressed(Button.A, function () {
    SOS()
})
```

## Étape 8 — Afficher la progression sur l'écran

✨ Un retour visuel !

➡️ Dans chaque fonction de lettre, ajoute ``||basic:afficher texte||`` **avant** d'appeler les points/tirets.

➡️ Dans `lettre_S`, affiche `"S"`. Dans `lettre_O`, affiche `"O"`.

> 💡 L'écran du micro:bit affiche la lettre en cours d'envoi — le destinataire voit à la fois la lumière et le texte !

```blocks
function lettre_S() {
    basic.showString("S")
    point()
    point()
    point()
    pause_lettre()
}
function lettre_O() {
    basic.showString("O")
    tiret()
    tiret()
    tiret()
    pause_lettre()
}
```

## Étape 9 — Télécharger le programme

💾 Envoie ton programme sur le micro:bit !

➡️ Clique sur le bouton **Télécharger** pour transférer ton programme.

> 💡 Le programme doit être dans le micro:bit avant de réaliser le circuit !

## Étape 10 — Réaliser le circuit 🔌

🔌 Réalise le branchement du circuit !

➡️ Rappelle-toi que la couleur des fils n'a aucune importance ! 🎨

> 💡 Une seule DEL branchée sur **P0** suffit — le morse n'a besoin que d'un seul signal !

## Étape 11 — Question réflexive 🤔

❓ **Combien de blocs ``||pins:écrire sur la broche||`` seraient nécessaires pour coder SOS sans les fonctions `point` et `tiret` ?**

❓ **Pourquoi est-il plus facile de modifier la durée d'un point ou d'un tiret avec des fonctions que sans ?**

> 💡 Sans fonctions, SOS nécessiterait **18 blocs** d'écriture sur broche + 18 pauses ! Avec les fonctions, tu changes **une seule valeur** dans `point` ou `tiret` et tout le message s'adapte automatiquement. Les fonctions rendent le code court, lisible et facile à modifier !

## Étape 12 — Défi de base 🧠

➡️ Ajoute une fonction `lettre_M` (deux tirets : `— —`) et une fonction `lettre_I` (deux points : `· ·`).

➡️ Crée une fonction `MOI` qui envoie M, O, I et appelle-la avec le bouton B.

> ❓ La DEL clignote-t-elle correctement pour chaque lettre ?

## Étape 13 — Défi avancé 🧠

➡️ Consulte le tableau du code Morse ci-dessous et code **ton prénom** en créant une fonction par lettre.

➡️ Crée une fonction `prenom` qui appelle toutes tes lettres dans l'ordre.

```
A · —     B — · · ·   C — · — ·   D — · ·
E ·       F · · — ·   G — — ·     H · · · ·
I · ·     J · — — —   K — · —     L · — · ·
M — —     N — ·       O — — —     P · — — ·
R · — ·   S · · ·     T —         U · · —
```

> ❓ Combien de fonctions as-tu créées pour ton prénom ? Est-ce que le message est lisible à la lumière ?

🚀 Bravo ! Tu sais maintenant utiliser les fonctions comme des briques de base pour construire des programmes complexes à partir d'éléments simples !

# AI Development Method

Méthode de conduite de projets logiciels réalisés avec un agent de développement IA.

## Prompt ultra-court pour lancer une nouvelle idée

Copier-coller simplement ceci dans une nouvelle conversation avec le chef de projet IA :

> **J'ai une nouvelle idée de projet. Connecte-toi à `https://github.com/Cowprod/aiDevMethod`, lis la méthode et applique-la. Voici mon idée : [décrire l'idée, même très vaguement]. Nous devons d'abord en discuter et cadrer le projet avant tout développement. Quand tu estimeras que le moment est venu, demande-moi de créer le dépôt Git du nouveau projet.**

Le chef de projet doit alors :
- lire la méthode ;
- commencer la phase d'interrogation/conception ;
- ne pas coder ;
- ne pas demander au porteur du produit de créer immédiatement un dépôt par réflexe ;
- **demander explicitement la création du dépôt projet au moment où il devient utile pour commencer à documenter durablement la conception** ;
- une fois le dépôt créé, y verser progressivement la conception, les décisions et les questions ouvertes.

Le principe central est simple :

> **Git est la mémoire durable du projet. Les conversations avec les agents sont des contextes de travail jetables.**

La méthode sépare clairement trois rôles :

- **Porteur du produit** : décide du besoin, des comportements et des arbitrages produit.
- **Chef de projet / architecte IA** : mène l'interrogation, formalise les décisions, organise les POC, prépare les jalons, rédige les missions des exécutants et contrôle les preuves.
- **Agent exécutant** : OpenCode, Codex ou autre agent capable de modifier le dépôt. Il exécute une mission bornée ; il ne prend pas silencieusement de décision produit ou structurante.

## Cycle

```text
Idée parfois très vague
        ↓
Phase 0 — conception / interrogation
        ↓
Décisions produit + questions ouvertes
        ↓
Maquettes / parcours si nécessaires
        ↓
Inconnues techniques
        ↓
POC ciblés
        ↓
Décisions techniques / architecture
        ↓
Gate de préparation
        ↓
Plan en jalons
        ↓
Mission autonome dans un contexte d'exécution neuf
        ↓
Implémentation + tests + preuves
        ↓
PASS technique
        ↓
Revue chef de projet
        ↓
Validation humaine si nécessaire
        ↓
ACCEPTÉ
        ↓
Merge
```

Un **PASS technique n'est jamais une acceptation humaine**.

## Démarrer un projet

Lire [00-PROMPT-DEMARRAGE.md](00-PROMPT-DEMARRAGE.md), puis utiliser les modèles du dossier [templates/](templates/).

La méthode complète est dans [METHODE-PROJET-IA.md](METHODE-PROJET-IA.md).

## Référentiels externes

Cette méthode ne duplique pas les normes techniques d'une organisation. Elles restent dans leur source canonique et sont rattachées au projet avec une version précise.

Pour les projets Cowprod, le référentiel technique est actuellement :

- `Cowprod/referenciel`

Le projet doit indiquer quelles parties du référentiel sont applicables et à quel commit. Voir [REFERENTIELS.md](REFERENTIELS.md).

## Héritage

Cette version reprend les principes du kit projet IA V2 et les renforce avec les enseignements tirés de projets réels : interrogation amont plus stricte, mémoire Git, POC mesurables, maquettes fonctionnelles, jalons autonomes, critères de STOP, preuves reproductibles et validation en plusieurs niveaux.

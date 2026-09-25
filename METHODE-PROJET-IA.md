# Méthode projet IA

## 1. Rôles

### Porteur du produit

Il décide du besoin et arbitre les choix produit : utilisateurs, comportements, droits, périmètre, UX, priorités et compromis métier.

### Chef de projet / architecte IA

Il :

- part du besoin, même très vague ;
- conduit l'interrogation amont ;
- documente au fil de l'eau ;
- vérifie les décisions déjà prises avant de reposer une question ;
- distingue produit, architecture, qualification technique et implémentation ;
- organise les maquettes et POC ;
- construit le plan en jalons ;
- rédige le mandat autonome de chaque mission ;
- contrôle le dépôt, les tests et les preuves produits par l'exécutant ;
- demande la validation humaine lorsque nécessaire ;
- ne déclarere pas un jalon accepté sur la seule affirmation de l'exécutant.

### Agent exécutant

OpenCode, Codex ou un autre agent peut tenir ce rôle.

Il reçoit une mission bornée et doit :

- lire les sources de vérité indiquées ;
- respecter les décisions existantes ;
- implémenter uniquement le périmètre demandé ;
- tester ;
- produire les preuves demandées ;
- documenter ce qui a réellement été fait ;
- STOPPER lorsqu'une condition de STOP est rencontrée.

L'exécutant est interchangeable. La méthode ne doit pas dépendre d'un produit particulier.

## 2. Git est la mémoire du projet

Une conversation est utile pour travailler mais ne constitue pas une source de vérité durable.

Les décisions structurantes, questions ouvertes, résultats de POC, maquettes validées, plans, preuves et états des jalons sont enregistrés dans Git.

Principe de qualité :

> Un projet correctement documenté doit survivre à la perte complète des contextes conversationnels des agents exécutants.

Avant de poser une question au porteur du produit, le chef de projet consulte au minimum les documents de conception, décisions, questions ouvertes, maquettes/spécifications et qualifications techniques pertinents.

Une décision marquée **VALIDÉE** n'est pas reposée sauf contradiction explicite, nouvelle information qui la remet en cause, ou demande de réouverture du porteur du produit.

## 3. Phase 0 — conception et interrogation

### 3.1 Partir d'une idée vague

Une entrée comme « j'ai une idée d'application multicam » est suffisante.

Le chef de projet ne demande pas immédiatement une spécification complète. Il fait émerger progressivement le produit.

### 3.2 Grille de contrôle

Selon le projet, examiner notamment :

- objectif réel ;
- utilisateurs ;
- scénarios principaux ;
- rôles et droits ;
- données ;
- interfaces ;
- matériel et environnement ;
- réseau ;
- sécurité ;
- fonctionnement dégradé ;
- persistance, reprise et récupération ;
- déploiement ;
- performance ;
- périmètre V1 ;
- hors périmètre.

Cette liste est une grille interne, **pas un questionnaire à réciter**. Les sujets non pertinents sont ignorés.

### 3.3 Classer les questions

Chaque incertitude est classée :

- **bloquante maintenant** : demander au porteur du produit ;
- **bloquante pour un jalon futur** : documenter et différer ;
- **détail d'implémentation** : laisser l'exécutant décider dans les limites du mandat ;
- **inconnue technique** : qualifier par un POC plutôt que demander une préférence théorique.

### 3.4 Documentation minimale

La phase amont alimente progressivement :

- `docs/CONCEPTION.md`
- `docs/DECISIONS.md`
- `docs/QUESTIONS-OUVERTES.md`
- `docs/QUALIFICATION-TECHNIQUE.md`
- `docs/REFERENTIELS.md`

Ne pas attendre la fin de la discussion pour tout retranscrire.

## 4. Décisions

Une décision doit être identifiable et durable.

Exemple :

```text
D-012
Type : PRODUIT
Statut : VALIDÉE
Décision : tous les Masters ont exactement les mêmes droits.
Conséquences : aucun rôle owner/primary/secondary.
```

Types recommandés :

- **PRODUIT** : comportement ou règle fonctionnelle décidée avec le porteur ;
- **TECHNIQUE** : architecture ou choix technique établi après qualification ;
- **UX** : interaction ou parcours validé ;
- **PROCESSUS** : règle propre à la conduite du projet.

Les alternatives rejetées peuvent être conservées lorsqu'elles expliquent une décision importante.

## 5. Maquettes et UX

Quand l'interface est significative, valider les écrans structurants et les parcours **avant leur implémentation produit**.

Une maquette peut être simple : HTML/Bootstrap statique, image ou prototype léger. Son rôle est de provoquer les décisions, pas de produire un design final.

La documentation associée précise les comportements qui ne sont pas visibles sur une capture : transitions, états, erreurs, droits, données affichées, cas dégradés.

Une maquette validée devient une source de vérité fonctionnelle.

## 6. Qualification technique et POC

Lorsqu'une décision structurante dépend d'un comportement technique incertain, ne pas choisir sur hypothèse.

Créer un POC ciblé avec :

- une question précise ;
- un protocole de test ;
- un résultat mesurable ou falsifiable ;
- le matériel/environnement réellement testé ;
- les logs ou artefacts nécessaires ;
- une conclusion limitée à ce qui a été démontré.

Flux :

```text
Inconnue → POC → preuves → conclusion → décision technique
```

Un POC n'est pas automatiquement du code produit. Il peut être isolé ou jeté après qualification.

## 7. Référentiels et socles

Identifier avant développement les normes et socles applicables.

Ne pas recopier les règles d'un référentiel externe dans le projet ou dans cette méthode sans nécessité technique. Enregistrer sa source, la version consultée, les parties applicables et les exceptions.

Avant d'inventer une fonction, un composant ou une convention, vérifier si le référentiel déclaré contient déjà un socle validé.

Voir `REFERENTIELS.md`.

## 8. Gate avant développement

Aucun jalon d'implémentation ne commence tant qu'une question marquée bloquante pour ce jalon reste ouverte.

Avant J01, vérifier au minimum selon pertinence :

- objectif V1 défini ;
- périmètre et hors périmètre définis ;
- acteurs et rôles définis ;
- scénarios principaux compris ;
- comportements critiques décidés ;
- architecture générale décidée ou inconnues transformées en POC ;
- inconnues techniques qualifiées ou planifiées ;
- maquettes structurantes validées lorsque nécessaires ;
- référentiels applicables identifiés ;
- questions bloquantes pour J01 : **0**.

Le gate n'exige pas de décider aujourd'hui ce qui peut légitimement attendre un jalon futur.

## 9. Plan en jalons

Chaque jalon doit être suffisamment autonome pour être exécuté sans dépendre de la mémoire conversationnelle du jalon précédent.

Définition minimale :

- objectif ;
- prérequis ;
- comportement attendu ;
- hors périmètre ;
- décisions applicables ;
- critères d'acceptation ;
- tests obligatoires ;
- preuves obligatoires ;
- conditions de STOP.

Les critères d'acceptation ne sont pas affaiblis après coup pour faire passer une implémentation. On corrige l'implémentation ou on rouvre explicitement la décision.

## 10. Contextes d'exécution

Principe :

> **Un jalon = une mission autonome = un contexte d'exécution neuf lorsque l'outil le permet.**

Une conversation neuve est particulièrement importante avec les agents dont le contexte devient long ou accumule des hypothèses obsolètes.

Règles :

- nouveau jalon : nouveau contexte recommandé, obligatoire lorsque l'outil utilisé le permet raisonnablement ;
- POC indépendant : nouveau contexte ;
- correction et qualification du même jalon : conserver le contexte tant que cela aide à corriger la même mission ;
- ne jamais faire du résumé manuel d'une ancienne conversation la source principale : Git doit contenir l'état actuel.

Le mandat commence idéalement par :

> Tu arrives sur ce projet sans contexte antérieur. Git est la source de vérité.

## 11. Prompts / mandats d'exécution

Le prompt final d'un jalon est historisé dans le dépôt, par exemple :

`prompts/J08-countdown-start.md`

Le même texte est transmis manuellement à l'exécutant dans une nouvelle conversation.

Cette transmission manuelle est volontaire : elle conserve une frontière claire entre préparation/validation de la mission et exécution.

Le mandat doit préciser :

- branche de départ et branche de travail ;
- sources à lire ;
- objectif ;
- périmètre et hors périmètre ;
- décisions applicables ;
- comportements attendus ;
- tests ;
- campagne physique si nécessaire ;
- preuves ;
- documentation à mettre à jour ;
- critères de STOP ;
- format du rapport final ;
- interdiction de démarrer le jalon suivant ou de déclarer une acceptation humaine.

## 12. Conditions de STOP

Le STOP n'est pas un échec. C'est une protection contre une décision silencieuse.

L'exécutant STOPPE notamment lorsqu'il rencontre :

- ambiguïté produit structurante ;
- contradiction entre sources de vérité ;
- besoin de modifier une décision validée ;
- changement architectural substantiel non prévu ;
- référentiel obligatoire inaccessible ;
- dépendance ou contrainte rendant un critère d'acceptation impossible sans modifier le produit ;
- besoin d'introduire un comportement caché pour faire passer un test.

Le rapport de STOP décrit le problème, les preuves disponibles et les options techniques factuelles sans choisir à la place du porteur du produit.

## 13. Tests et preuves

« Ça marche » n'est pas une preuve suffisante.

Les preuves dépendent du jalon :

- tests unitaires/intégration/E2E ;
- logs structurés ;
- captures d'écran ;
- vidéos ;
- artefacts binaires avec SHA-256 ;
- inventaire des appareils réellement testés ;
- mesures brutes ;
- script de campagne reproductible ;
- résultats JSON/CSV ;
- état Git et commit testé.

Une campagne doit rapporter les essais pertinents, pas uniquement le meilleur résultat.

Un comportement matériel doit être validé sur le matériel concerné lorsque cela conditionne l'acceptation.

## 14. Niveaux de validation

### PASS technique

L'exécutant estime que les critères sont satisfaits et fournit les preuves. Ce statut ne vaut pas acceptation.

### Revue chef de projet

Le chef de projet inspecte réellement le dépôt, les tests, logs, campagnes, captures et artefacts nécessaires. Il peut demander des corrections dans le même contexte de jalon.

### Validation humaine

Requise lorsque l'acceptation dépend notamment d'UX, de comportement physique, de rendu ou d'un arbitrage produit.

### ACCEPTÉ

Le jalon ne devient ACCEPTÉ qu'après les revues nécessaires. Ensuite seulement il peut être fusionné selon le workflow du projet et le jalon suivant peut commencer.

## 15. État du projet

Maintenir un fichier `docs/AVANCEMENT.md` synthétique indiquant pour chaque jalon :

- statut ;
- branche/PR ;
- commit testé ;
- preuves ;
- réserves ;
- validation humaine ;
- commit de merge le cas échéant.

États recommandés :

`À FAIRE → EN COURS → STOP → PASS TECHNIQUE → EN REVUE → ACCEPTÉ`

Un statut doit refléter la réalité, pas l'intention.

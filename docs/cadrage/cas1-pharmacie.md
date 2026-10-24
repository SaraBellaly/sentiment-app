# Fiche de cadrage : Ordonnances incomplètes en pharmacie

> Remplir chaque rubrique en une à trois phrases. Les rubriques marquées (obligatoire) sont vérifiées par `pytest`.

## Besoin en une phrase (obligatoire)

Signaler au comptoir toute ordonnance à laquelle il manque une mention obligatoire.

## Utilisateur final (obligatoire)

Le pharmacien et les préparateurs au comptoir, qui reçoivent une alerte listant les champs manquants avant de délivrer.

## Approche retenue (obligatoire)

Cocher une seule case :

- [x] Règles métier
- [ ] Machine learning
- [ ] RAG
- [ ] Modèle génératif seul

## Justification (obligatoire, citer au moins deux critères de la grille : (a) données étiquetées, (b) vérifiabilité, (c) coût par requête, (d) conséquence d'une erreur)

Les mentions obligatoires d'une ordonnance sont fixées par la réglementation : la logique est connue et stable, une liste de contrôles suffit. (b) Chaque alerte s'explique par la règle qui a échoué (« signature absente »), ce que le pharmacien peut vérifier immédiatement. (d) Une ordonnance incomplète validée à tort peut mener à une délivrance dangereuse : on veut un comportement déterministe, pas probabiliste. (a) Aucun historique d'ordonnances étiquetées « complète / incomplète » n'existe, et le constituer exposerait des données de santé.

## Données nécessaires et leur origine (obligatoire)

La liste des mentions obligatoires issue de la réglementation et de l'ordre des pharmaciens, et les champs de l'ordonnance saisis dans le logiciel de la pharmacie (ou lus par OCR sur l'ordonnance scannée, puis confirmés par le préparateur).

## Métrique de succès et seuil d'acceptation (obligatoire)

Rappel sur les ordonnances incomplètes mesuré sur un échantillon de 200 ordonnances (hypothèse) contrôlées à la main : 100 % exigé ; taux de fausses alertes inférieur à 5 % (hypothèse) pour ne pas ralentir le comptoir.

## Conséquence d'une erreur et validation humaine prévue (obligatoire)

Une ordonnance incomplète non signalée peut entraîner une erreur de traitement ; une fausse alerte fait perdre quelques secondes. Le pharmacien garde la décision finale : l'outil alerte, il ne bloque ni ne valide jamais seul.

## Risques éthiques ou de confidentialité (obligatoire)

Les ordonnances sont des données de santé sensibles : traitement local dans le logiciel de la pharmacie, aucun envoi à un service tiers, conservation limitée à la durée légale.

## Approche écartée et pourquoi (facultatif)

Machine learning : pas de données étiquetées et des erreurs difficiles à expliquer, alors que les règles sont déjà écrites dans la réglementation.

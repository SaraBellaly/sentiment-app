# Fiche de cadrage : Priorisation des avis négatifs

> Remplir chaque rubrique en une à trois phrases. Les rubriques marquées (obligatoire) sont vérifiées par `pytest`.

## Besoin en une phrase (obligatoire)

Classer chaque avis client publié sur le site (négatif, neutre, positif) pour faire remonter en tête de file les avis négatifs à traiter en priorité.

## Utilisateur final (obligatoire)

L'équipe du service client, qui traite d'abord les avis négatifs au lieu de parcourir des milliers d'avis dans l'ordre d'arrivée.

## Approche retenue (obligatoire)

Cocher une seule case :

- [ ] Règles métier
- [x] Machine learning
- [ ] RAG
- [ ] Modèle génératif seul

## Justification (obligatoire, citer au moins deux critères de la grille : (a) données étiquetées, (b) vérifiabilité, (c) coût par requête, (d) conséquence d'une erreur)

(a) Chaque avis est accompagné d'une note en étoiles : l'historique fournit des milliers d'exemples étiquetés presque gratuitement (1-2 étoiles négatif, 3 neutre, 4-5 positif). (c) Des milliers d'avis par jour : un classifieur de sentiment coûte presque rien par requête, un LLM coûterait à chaque avis. (d) Les faux négatifs coûtent cher : un avis négatif classé positif reste sans réponse et le client mécontent peut partir, d'où l'exigence d'un rappel élevé sur la classe « négatif » ; à l'inverse, un avis remonté à tort ne coûte que quelques secondes à l'agent, qui le reclasse.

## Données nécessaires et leur origine (obligatoire)

Export de la base des avis du site (texte, note, date, produit), sans nom ni adresse électronique du client ; `data/sample_reviews.csv` sert de premier échantillon.

## Métrique de succès et seuil d'acceptation (obligatoire)

Rappel sur la classe « négatif » mesuré sur un jeu de test tenu à l'écart : au moins 0,90, avec un F1 macro d'au moins 0,80 sur les trois classes.

## Conséquence d'une erreur et validation humaine prévue (obligatoire)

Un avis négatif classé positif reste sans réponse plus longtemps et peut faire perdre un client ; un faux positif coûte quelques secondes à l'agent. L'agent peut reclasser un avis en un clic, et ces corrections alimentent le réentraînement. Les avis critiques (fraude, abus) doivent être escaladés dans les 2 heures.

## Risques éthiques ou de confidentialité (obligatoire)

Les avis peuvent contenir des données personnelles (nom, téléphone, numéro de commande) : anonymisation avant entraînement. Vérifier aussi que le modèle ne classe pas systématiquement plus mal les avis rédigés en darija ou avec des fautes.

## Approche écartée et pourquoi (facultatif)

Règles par mots-clés : elles ratent l'ironie et les négations (« pas mal du tout »), trop de formulations imprévues sur des milliers d'avis.

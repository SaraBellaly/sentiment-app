# Fiche de cadrage : Questions sur le règlement intérieur

> Remplir chaque rubrique en une à trois phrases. Les rubriques marquées (obligatoire) sont vérifiées par `pytest`.

## Besoin en une phrase (obligatoire)

Répondre aux questions des élèves et des parents sur le règlement intérieur (absences, retards, sanctions, tenue, examens) en citant l'article concerné.

## Utilisateur final (obligatoire)

Les élèves et leurs parents, qui obtiennent une réponse immédiate, ainsi que le secrétariat, qui reçoit moins de questions répétitives.

## Approche retenue (obligatoire)

Cocher une seule case :

- [ ] Règles métier
- [ ] Machine learning
- [x] RAG
- [ ] Modèle génératif seul

## Justification (obligatoire, citer au moins deux critères de la grille : (a) données étiquetées, (b) vérifiabilité, (c) coût par requête, (d) conséquence d'une erreur)

La réponse doit être tirée de documents qui existent déjà (règlement intérieur, notes de service). Un modèle qui répond seul ne connaît pas le règlement propre à l'école et ne peut pas citer sa source : le RAG retrouve d'abord les articles pertinents, puis rédige la réponse uniquement à partir d'eux. (b) Chaque réponse cite l'article et le passage retrouvés, ce que l'utilisateur peut vérifier lui-même. (a) Nous n'avons pas de questions étiquetées avec leur réponse : un classifieur supervisé est exclu. (d) Un modèle génératif seul pourrait inventer une règle ou une sanction ; ancrer la réponse dans le texte limite ce risque. (c) Quelques dizaines de questions par jour : le coût d'un appel au LLM reste acceptable.

## Données nécessaires et leur origine (obligatoire)

Le règlement intérieur en vigueur et les notes de service fournis par la direction, découpés par article et indexés ; une cinquantaine (hypothèse) de questions réelles collectées auprès du secrétariat pour constituer un jeu de test.

## Métrique de succès et seuil d'acceptation (obligatoire)

Sur 50 questions de test relues par le secrétariat : au moins 90 % (hypothèse) de réponses correctes avec le bon article cité, et 100 % de refus (« je ne sais pas, contactez le secrétariat ») quand le règlement ne répond pas.

## Conséquence d'une erreur et validation humaine prévue (obligatoire)

Une mauvaise réponse peut faire croire à un élève qu'une absence est justifiée ou qu'une sanction n'existe pas. Chaque réponse affiche le lien vers l'article source, et l'assistant renvoie vers le secrétariat pour tout cas disciplinaire ou individuel.

## Risques éthiques ou de confidentialité (obligatoire)

Les questions peuvent contenir des noms ou des situations personnelles d'élèves mineurs : pas de conservation nominative des questions, avertissement de ne pas saisir de données personnelles, LLM hébergé sans réutilisation des données.

## Approche écartée et pourquoi (facultatif)

Modèle génératif seul : il ne connaît pas le règlement de l'école et répondrait de façon plausible mais invérifiable.

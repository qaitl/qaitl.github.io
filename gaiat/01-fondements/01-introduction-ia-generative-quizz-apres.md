# Quizz de validation des acquis — Après l'atelier
## Introduction à l'IA générative

> **Objectif :** Valider la compréhension des concepts clés abordés dans ce module.
>
> **Interprétation du score :**
> - **0–9 points** : Des lacunes subsistent — relire les sections concernées est recommandé.
> - **10–14 points** : Bonne compréhension générale, quelques points à consolider.
> - **15–18 points** : Maîtrise solide du module.

---

## Partie A — Histoire et fondements de l'IA

### Question 1
**Dans quelle période et avec quelle approche l'IA symbolique a-t-elle dominé ?**

- A. Années 2010, avec des réseaux de neurones profonds
- B. Années 1950–1980, avec des règles écrites explicitement par des experts
- C. Années 1990–2010, avec des algorithmes apprenant à partir de données
- D. Depuis 2020, avec la génération de contenu

<details><summary>Réponse</summary>

**B. Années 1950–1980, avec des règles écrites explicitement par des experts**

L'IA symbolique repose sur le principe "si X alors Y". Elle est efficace dans un périmètre précis mais fragile hors du cadre prévu.

</details>

---

### Question 2
**Quel exemple illustre le mieux le machine learning classique ?**

- A. Un système expert de diagnostic médical avec des règles codées à la main
- B. Un filtre anti-spam qui apprend à partir de milliers d'exemples d'emails
- C. Un modèle qui génère des images à partir d'une description textuelle
- D. Un agent qui navigue sur le web de manière autonome

<details><summary>Réponse</summary>

**B. Un filtre anti-spam qui apprend à partir de milliers d'exemples d'emails**

Le machine learning classique apprend des patterns à partir d'exemples, sans que les règles soient programmées manuellement.

</details>

---

### Question 3
**Quelle capacité distingue l'IA générative des générations précédentes d'IA ?**

- A. Elle classe et reconnaît des données mieux que tout système précédent
- B. Elle crée du contenu nouveau : texte, images, code, musique
- C. Elle fonctionne sans données d'entraînement
- D. Elle est la première à utiliser des réseaux de neurones

<details><summary>Réponse</summary>

**B. Elle crée du contenu nouveau : texte, images, code, musique**

Les générations précédentes reconnaissaient et classifiaient. L'IA générative produit du contenu original — c'est le changement de paradigme central.

</details>

---

## Partie B — Fonctionnement des LLMs

### Question 4
**Sur quel principe repose fondamentalement un LLM ?**

- A. La recherche dans une base de connaissances structurée
- B. La prédiction du token suivant le plus probable
- C. L'exécution de règles logiques formelles
- D. La compression de texte pour en extraire le sens

<details><summary>Réponse</summary>

**B. La prédiction du token suivant le plus probable**

Un LLM prédit itérativement le prochain fragment de texte (token). À grande échelle, cela donne l'illusion de compréhension et de raisonnement.

</details>

---

### Question 5
**Pourquoi un LLM échoue-t-il sur le comptage exact de lettres dans un mot ?**

- A. Il n'a pas été entraîné sur des données alphabétiques
- B. Il découpe le texte en tokens, pas en caractères individuels
- C. Il refuse les questions trop simples par conception
- D. Sa mémoire de travail est trop courte pour lire un mot entier

<details><summary>Réponse</summary>

**B. Il découpe le texte en tokens, pas en caractères individuels**

Le mot "tester" peut être tokenisé en `test` + `er`. Le LLM n'a pas de vision caractère par caractère, ce qui le rend peu fiable pour les tâches de manipulation littérale.

</details>

---

### Question 6
**Laquelle de ces affirmations sur les LLMs est correcte ?**

- A. Un LLM comprend et raisonne de la même façon qu'un humain
- B. Un LLM a une mémoire persistante entre toutes les conversations par défaut
- C. Un LLM est probabiliste : ses sorties peuvent varier pour une même entrée
- D. Un LLM peut uniquement traiter du texte en anglais

<details><summary>Réponse</summary>

**C. Un LLM est probabiliste : ses sorties peuvent varier pour une même entrée**

Les LLMs ne comprennent pas au sens humain, n'ont pas de mémoire persistante par défaut (sauf configuration), et supportent de nombreuses langues.

</details>

---

## Partie C — Acteurs et types d'outils

### Question 7
**Quelle startup française propose des modèles LLM compétitifs au niveau mondial ?**

- A. Mistral AI
- B. Anthropic
- C. DeepMind
- D. xAI

<details><summary>Réponse</summary>

**A. Mistral AI**

Mistral AI est une startup française qui propose des modèles open source (Mistral, Mixtral) et une offre cloud (Le Chat), l'une des rares en dehors des États-Unis à ce niveau de performance.

</details>

---

### Question 8
**Dans quel contexte est-il préférable d'utiliser un modèle open source auto-hébergé plutôt qu'un chatbot cloud ?**

- A. Quand on veut accéder aux modèles les plus puissants du marché
- B. Quand les données sont sensibles et ne doivent pas quitter l'infrastructure interne
- C. Quand on n'a pas de compétences techniques
- D. Quand on veut bénéficier des mises à jour les plus récentes automatiquement

<details><summary>Réponse</summary>

**B. Quand les données sont sensibles et ne doivent pas quitter l'infrastructure interne**

L'auto-hébergement est le choix des contextes bancaires, médicaux ou de défense. En contrepartie, les modèles open source sont souvent moins puissants et nécessitent une configuration technique.

</details>

---

### Question 9
**Qu'apporte un outil intégrant un LLM (comme GitHub Copilot ou Xray AI) par rapport à un chatbot grand public ?**

- A. Une interface plus colorée et plus moderne
- B. L'injection automatique du contexte métier (code, tickets, exigences) dans le prompt
- C. Un accès illimité sans abonnement
- D. La garantie que les résultats sont exempts d'hallucinations

<details><summary>Réponse</summary>

**B. L'injection automatique du contexte métier dans le prompt**

C'est la différence clé : l'outil intégré connaît votre environnement (votre code, vos tickets) sans que vous ayez à le fournir manuellement à chaque interaction.

</details>

---

## Partie D — Usages et limites dans les tests logiciels

### Question 10
**Quelle capacité d'un LLM est la plus utile pour reformuler une exigence ambiguë en critère testable ?**

- A. La classification
- B. La complétion de code
- C. La transformation de format et la détection d'anomalies textuelles
- D. La synthèse vocale

<details><summary>Réponse</summary>

**C. La transformation de format et la détection d'anomalies textuelles**

Les LLMs excellent à identifier les termes vagues ("rapidement", "souvent") et à reformuler en critères mesurables. La décision sur le seuil acceptable reste humaine.

</details>

---

### Question 11
**Un LLM génère une suite de cas de test à partir d'une user story. Que doit impérativement faire le testeur ensuite ?**

- A. Rien — le LLM est certifié ISTQB
- B. Valider la pertinence métier des cas et identifier les cas manquants (cas négatifs, cas limites métier)
- C. Soumettre les cas à un deuxième LLM pour validation croisée
- D. Convertir les cas en un format XML avant utilisation

<details><summary>Réponse</summary>

**B. Valider la pertinence métier et identifier les cas manquants**

Le LLM produit rapidement une base de cas nominaux. Les cas négatifs (cas négatif / negative test case) et les cas limites spécifiques au contexte métier restent la valeur ajoutée du testeur expérimenté.

</details>

---

### Question 12
**Parmi les tâches suivantes, lesquelles sont des points FORTS des LLMs en test logiciel ? (2 bonnes réponses)**

- A. Compter précisément les lignes de code d'un fichier
- B. Générer une première version de cas de test à partir d'une spécification
- C. Garantir l'exactitude arithmétique de tous les calculs
- D. Reformuler un rapport de défaut dans un style adapté à une équipe non technique

<details><summary>Réponse</summary>

**B et D**

Les LLMs sont excellents pour les tâches sémantiques et textuelles (génération, reformulation, résumé). Ils sont peu fiables pour les calculs exacts et le comptage.

</details>

---

## Partie E — Modèles multimodaux et IA agentique

### Question 13
**Quel est l'usage des modèles de vision (vision models) dans les tests logiciels ?**

- A. Générer de la musique de fond pendant les sessions de test exploratoire
- B. Analyser une capture d'écran pour lister les éléments d'interface ou détecter des différences visuelles
- C. Remplacer entièrement les outils de test automatisé comme Selenium
- D. Traduire les spécifications en plusieurs langues

<details><summary>Réponse</summary>

**B. Analyser une capture d'écran pour lister les éléments d'interface ou détecter des différences visuelles**

Les modèles de vision permettent l'analyse d'interfaces, la comparaison de maquettes, la détection de problèmes d'accessibilité visuelle, et la transcription de tableaux blancs photographiés.

</details>

---

### Question 14
**Quelle est la différence entre un modèle de raisonnement (reasoning model) et un LLM standard ?**

- A. Le modèle de raisonnement est exclusivement open source
- B. Avant de répondre, le modèle de raisonnement effectue une phase de réflexion interne visible (chaîne de pensée)
- C. Le modèle de raisonnement fonctionne sans données d'entraînement
- D. Le modèle de raisonnement peut uniquement répondre à des questions de mathématiques

<details><summary>Réponse</summary>

**B. Avant de répondre, le modèle de raisonnement effectue une phase de réflexion interne visible**

Des modèles comme o1/o3 (OpenAI) ou Claude avec extended thinking effectuent une phase de réflexion avant de répondre, ce qui réduit les erreurs sur les tâches complexes, au prix d'une latence et d'un coût plus élevés.

</details>

---

### Question 15
**Qu'est-ce qui caractérise l'IA agentique par rapport à un LLM conversationnel classique ?**

- A. L'agent répond plus vite aux questions
- B. L'agent peut enchaîner des actions, utiliser des outils externes et adapter son plan selon les résultats intermédiaires
- C. L'agent ne peut traiter que du texte, pas des images
- D. L'agent mémorise toutes les conversations précédentes automatiquement

<details><summary>Réponse</summary>

**B. L'agent peut enchaîner des actions, utiliser des outils externes et adapter son plan**

L'IA agentique reçoit une mission, pas une question. Elle peut lire des fichiers, appeler des APIs, exécuter du code, et ajuster sa stratégie — avec les risques (actions irréversibles, hallucinations en cascade) que cela implique.

</details>

---

### Question 16
**Pourquoi la supervision humaine reste-t-elle essentielle dans un pipeline agentique ?**

- A. Parce que les agents IA ne peuvent pas lire les spécifications
- B. Parce que les agents peuvent prendre des actions irréversibles et que les hallucinations peuvent se propager en cascade
- C. Parce que les agents ne supportent pas le langage naturel
- D. Parce que la supervision est obligatoire uniquement pour les agents open source

<details><summary>Réponse</summary>

**B. Actions irréversibles possibles et hallucinations en cascade**

Un agent qui agit (écriture de fichiers, appels API, exécution de code) peut causer des dommages difficiles à corriger. Les erreurs d'un LLM peuvent se propager et s'amplifier à chaque étape d'un pipeline agentique.

</details>

---

## Partie F — Synthèse

### Question 17
**Complétez : "L'IA générative est un ___, pas un remplaçant du testeur."**

- A. Concurrent
- B. Accélérateur
- C. Superviseur
- D. Auditeur

<details><summary>Réponse</summary>

**B. Accélérateur**

L'IA déplace l'effort humain vers la validation, le jugement et la créativité — là où la valeur ajoutée du testeur est la plus forte.

</details>

---

### Question 18
**Parmi ces affirmations, laquelle résume le mieux la limite fondamentale d'un LLM dans un contexte de test ?**

- A. Un LLM ne peut pas lire les fichiers PDF
- B. Un LLM produit des sorties probabilistes qui nécessitent une validation humaine, car il peut halluciner ou omettre des cas métier critiques
- C. Un LLM est trop lent pour être utile en pratique
- D. Un LLM ne supporte que l'anglais et quelques langues européennes

<details><summary>Réponse</summary>

**B. Sorties probabilistes nécessitant une validation humaine**

C'est la limite transversale à tous les usages : la vérification humaine des sorties du LLM est une étape obligatoire dans tout processus de test sérieux.

</details>

---

*Score : comptez 1 point par bonne réponse (Q12 compte pour 1 point si les 2 bonnes réponses sont cochées). Résultat sur 18.*

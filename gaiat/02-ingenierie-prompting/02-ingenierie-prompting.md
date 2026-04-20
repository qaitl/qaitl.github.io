# Ingénierie du prompting pour des tests logiciels efficaces

> **À qui s'adresse ce chapitre ?** Aux testeurs qui souhaitent exploiter efficacement l'IA générative dans leurs activités de test en maîtrisant la conception de prompts (prompt) structurés et les principales techniques de prompting.

---

## 1. Développement efficace des prompts

Une conception efficace des prompts facilite la réalisation précise et efficace des tâches de test logiciel par les outils d'IA générative. Un prompt bien structuré aide les testeurs à obtenir des résultats utiles des grands modèles de langage (LLM / large language model).

### 1.1 Structure des prompts pour l'IA générative dans les tests logiciels

Un prompt structuré (prompt structuré / structured prompt) pour le test logiciel comprend généralement six composants :

| Composant | Définition | Exemple dans un contexte de test |
|---|---|---|
| **Rôle** | La perspective ou le persona que le modèle doit adopter | *"Tu es un testeur logiciel senior certifié ISTQB"* |
| **Contexte** | Les informations de fond sur l'objet de test | *"L'application est un e-commerce. La fonctionnalité à tester est le panier d'achat."* |
| **Instructions** | Les directives claires et impératives décrivant la tâche | *"Génère une liste de conditions de test (conditions de test / test conditions) pour la fonctionnalité d'ajout au panier."* |
| **Données d'entrée** | Les informations nécessaires à l'exécution de la tâche | *User story, critères d'acceptation, captures d'écran, cas de test existants* |
| **Contraintes** | Les restrictions à respecter | *"Limite-toi aux tests fonctionnels. Ne génère pas de tests de performance."* |
| **Format de sortie** | La structure attendue de la réponse | *"Utilise un tableau Markdown avec les colonnes : ID, Description, Priorité"* |

> **Pourquoi structurer ses prompts ?** Un prompt non structuré donne des résultats génériques. Un prompt structuré guide le LLM vers une réponse précise, pertinente et directement exploitable dans votre contexte de test.

**Exemple complet de prompt structuré :**

```
[Rôle] Tu es un testeur logiciel senior spécialisé dans les tests fonctionnels.

[Contexte] On teste une application de gestion de congés. La règle métier : un congé ne peut
être posé moins de 5 jours ouvrés avant sa date de début.

[Instruction] Génère des conditions de test pour la règle de délai de préavis.

[Données d'entrée] User story : "En tant qu'employé, je veux poser un congé afin de planifier
mon temps de repos."

[Contraintes] Focus uniquement sur la règle des 5 jours. Couvre les cas nominaux, alternatifs
et négatifs.

[Format de sortie] Tableau Markdown : ID | Condition | Type (nominal/alternatif/négatif) | Priorité
```

---

### 1.2 Principales techniques de prompting pour les tests logiciels

Trois techniques de prompting (ingénierie du prompting / prompt engineering) sont particulièrement adaptées aux tâches de test logiciel, en complément de la structure à six composants.

#### L'enchaînement de prompts (prompt chaining)

L'enchaînement de prompts (enchaînement de prompts / prompt chaining) consiste à **diviser une tâche complexe en une série d'étapes intermédiaires**. Le résultat de chaque étape est vérifié — manuellement ou automatiquement — avant de passer à l'étape suivante.

**Quand l'utiliser :** tâches complexes nécessitant une décomposition en sous-tâches et une vérification systématique des résultats intermédiaires.

**Exemple appliqué à une User Story :**
1. Prompt 1 → *"Identifie les ambiguïtés dans cette User Story"*
2. Vérification humaine → validation ou correction des ambiguïtés identifiées
3. Prompt 2 → *"Sur la base des ambiguïtés corrigées, génère les critères d'acceptation (critères d'acceptation / acceptance criteria)"*
4. Vérification humaine → validation des critères
5. Prompt 3 → *"Génère les cas de test (cas de test / test case) correspondant à ces critères"*

**Avantage :** chaque réponse informe le prompt suivant, ce qui améliore la précision globale et permet des interactions dynamiques dans le processus de test.

---

#### Le few-shot prompting

Le few-shot prompting consiste à **fournir des exemples dans le prompt** pour guider le modèle vers le format et le contenu attendus.

| Variante | Nombre d'exemples | Usage |
|---|---|---|
| **Zero-shot** | 0 — s'appuie sur les connaissances du modèle | Tâches génériques |
| **One-shot** | 1 — illustre le résultat souhaité | Tâches simples avec format précis |
| **Few-shot** | Plusieurs — consolide le comportement attendu | Tâches répétitives avec format contraint |

**Quand l'utiliser :** génération répétitive avec un format de sortie spécifique (scénarios Gherkin, tests dirigés par les mots-clés / keyword-driven test, rapports de test standardisés).

**Exemple :**
```
Voici deux exemples de scénarios Gherkin pour une fonctionnalité de connexion :

Exemple 1 :
Étant donné que l'utilisateur est sur la page de connexion
Lorsqu'il saisit un email valide et un mot de passe correct
Alors il est redirigé vers son tableau de bord

Exemple 2 :
Étant donné que l'utilisateur est sur la page de connexion
Lorsqu'il saisit un mot de passe incorrect
Alors un message d'erreur "Identifiants invalides" s'affiche

Génère maintenant des scénarios Gherkin pour la fonctionnalité de réinitialisation de mot de passe.
```

---

#### Le méta-prompting

Le méta-prompting (méta-prompting / meta-prompting) **exploite la capacité de l'IA à générer ou améliorer ses propres prompts**. Dans un cycle itératif, le LLM peut générer des prompts que le testeur évalue et affine.

**Quand l'utiliser :** lorsque vous ne savez pas comment formuler un prompt efficace, ou lorsque vous souhaitez optimiser un prompt existant.

**Exemple :**
```
Je dois générer des cas de test de performance pour une API REST.
Je n'ai pas encore de prompt efficace pour cette tâche.
Génère un prompt structuré (rôle, contexte, instruction, contraintes, format de sortie)
que je pourrais utiliser pour cette tâche de test de performance.
```

**Avantage :** réduit l'effort manuel de conception de prompts et favorise une forme de **binômage avec l'IA** (AI pair testing), où testeur et IA collaborent de manière interactive.

> **Combinaison des techniques :** Il est possible d'utiliser plusieurs techniques pour un même cas d'utilisation. Par exemple : le méta-prompting crée le prompt initial → le few-shot prompting l'enrichit d'exemples → l'enchaînement de prompts décompose l'exécution en étapes validées.

---

> **Actualisation par rapport au syllabus (CT-GenAI v1.0, juillet 2025)**
>
> Deux évolutions récentes modifient la façon d'appliquer ces techniques en pratique.
>
> **Les modèles de raisonnement (reasoning models)** — tels que o1/o3 (OpenAI), Claude 3.7 Sonnet avec *extended thinking* (Anthropic) ou Gemini 2.0 Flash Thinking (Google) — effectuent un enchaînement de pensée **en interne** avant de répondre. Avec ces modèles, l'enchaînement manuel de prompts est moins nécessaire pour les tâches complexes : le modèle décompose lui-même le problème en sous-étapes. La vérification humaine des résultats intermédiaires reste cependant indispensable. Voir aussi le chapitre 1, section 9.1.
>
> **Le few-shot prompting est moins critique avec les modèles récents.** Les grands modèles actuels (GPT-4o, Claude 3.5+, Gemini 1.5+) obtiennent de très bons résultats en zero-shot sur la plupart des tâches de test courantes. Le few-shot reste utile principalement lorsque le format de sortie est très contraint et spécifique à votre organisation (templates internes, conventions de nommage propres à votre projet), ou pour les tâches où la cohérence entre plusieurs générations est critique.

---

### 1.3 Prompt système et prompt utilisateur

Les LLMs reçoivent deux types de prompts distincts, chacun jouant un rôle différent dans la conversation.

| | Prompt système (system prompt) | Prompt utilisateur (user prompt) |
|---|---|---|
| **Qui le définit ?** | Le développeur ou le testeur qui configure l'outil | L'utilisateur final du chatbot |
| **Visibilité** | Généralement invisible pour l'utilisateur | Directement visible dans l'interface |
| **Quand est-il envoyé ?** | Une seule fois, au début de la session | À chaque interaction |
| **Contenu typique** | Rôle, contraintes, ton, règles générales | Instructions, questions, données spécifiques |
| **Persistance** | Constant tout au long de la session | Change à chaque échange |

**Exemple de prompt système :**
> *"Vous êtes un assistant spécialisé dans les tests logiciels. Répondez toujours clairement, utilisez un langage formel et concentrez-vous sur les pratiques recommandées par l'ISTQB. Évitez les spéculations et citez les principes de test lorsque cela est pertinent."*

**Exemple de prompt utilisateur correspondant :**
> *"Énumère les principales différences entre les tests boîte noire (black-box testing) et les tests boîte blanche (white-box testing), avec des exemples."*

**Pour une implémentation efficace :**
- Le prompt système doit être clair sur le rôle du LLM et ses contraintes ; il peut contenir des informations contextuelles et des instructions générales.
- Le prompt utilisateur doit être ciblé et bien structuré, avec des instructions explicites et des informations contextuelles pertinentes.

---

## 2. Application des techniques d'ingénierie du prompting aux tâches de test logiciel

### 2.1 Analyse de test (test analysis) avec l'IA générative

L'IA générative peut prendre en charge les tâches d'analyse de test (analyse de test / test analysis) en générant et en hiérarchisant les conditions de test (conditions de test / test conditions), en identifiant les défauts dans la base de test (base de test / test basis) et en fournissant une analyse de couverture (analyse de couverture / coverage analysis).

**Tâches typiques supportées par l'IA générative :**

- **Identifier les défauts potentiels dans la base de test** : L'IA analyse les exigences pour détecter incohérences, ambiguïtés ou informations incomplètes.
- **Générer des conditions de test** à partir des User Stories et exigences : grâce au traitement du langage naturel (traitement du langage naturel / natural language processing, NLP), le LLM décompose les exigences en instructions mesurables et testables.
- **Hiérarchiser les conditions de test** par niveau de risque : en tenant compte de la probabilité de défaillance, de l'impact, des contraintes réglementaires et des données historiques sur les défauts.
- **Aider à l'analyse de couverture** : en cartographiant les exigences aux conditions de test pour identifier les lacunes.
- **Suggérer des techniques de test** : analyse des valeurs limites (analyse des valeurs limites / boundary value analysis), partition d'équivalence (partition d'équivalence / equivalence partitioning), etc.

> **Règle d'or :** La qualité et la pertinence des données d'entrée fournies au LLM déterminent directement l'exactitude et la précision des résultats. *Garbage in, garbage out* s'applique au prompting comme à tout traitement automatisé.

---

### 2.2 Conception et implémentation des tests avec l'IA générative

La conception des tests (conception des tests / test design) implique l'élaboration des conditions de test, qui sont ensuite traduites en cas de test (cas de test / test case) et autres testware (testware / testware). L'implémentation des tests (implémentation des tests / test implementation) implique la création du testware nécessaire pour exécuter les tests.

**Tâches typiques :**

- **Génération de cas de test** : à partir d'exigences fonctionnelles et non fonctionnelles — préconditions, données d'entrée, résultats attendus, critères de couverture.
- **Synthèse des données de test (données de test / test data)** : création de données synthétiques représentatives et respectueuses de la confidentialité, couvrant cas nominaux et cas limites (cas limite / boundary value case).
- **Génération de scripts de test automatisés (script de test automatisé / automated test script)** : traduction des étapes de test en code compatible avec les frameworks d'automatisation.
- **Planification et hiérarchisation de l'exécution des tests** : optimisation des calendriers d'exécution en fonction des priorités, risques et dépendances.

**Tableau de sélection des techniques selon la tâche :**

| Technique | Cas d'utilisation recommandé | Caractéristiques |
|---|---|---|
| **Enchaînement de prompts** | Tâches complexes nécessitant une vérification à chaque étape | Analyse des tests, conception, automatisation avec validation intermédiaire |
| **Few-shot prompting** | Tâches répétitives ou contraintes en format de sortie | Scénarios Gherkin, tests par mots-clés, reporting standardisé |
| **Méta-prompting** | Tâches flexibles, création de prompts pour de nouvelles tâches | Analyse de rapports de test, détection d'anomalies |

---

### 2.3 Tests de régression automatisés (automated regression testing) avec l'IA générative

À mesure que les itérations se multiplient, le nombre de cas de test de régression (cas de test de régression / regression test case) augmente. L'IA générative peut rationaliser la création, la maintenance et l'optimisation des suites de tests de régression automatisés.

**Activités supportées :**

- **Implémentation de scripts de test basés sur des mots-clés** (keyword-driven test script) : les LLMs cartographient les mots-clés prédéfinis vers des cas de test spécifiques et génèrent les scripts correspondants.
- **Analyse d'impact et optimisation des tests** : identification des zones à haut risque suite aux modifications du code.
- **Tests auto-réparateurs et adaptatifs (self-healing tests)** : ajustement automatique des scripts pour gérer les modifications mineures de l'interface utilisateur ou de l'API.
- **Reporting automatisé des tests** : génération de rapports détaillés avec métriques de réussite, défaillances et informations clés.
- **Amélioration des rapports de défauts (rapport de défaut / defect report)** : compilation automatique avec logs de test, captures d'écran et données sur l'environnement.

> **Vigilance :** L'IA générative peut faire des erreurs. Toute sortie générée doit être soigneusement vérifiée, en fonction du risque associé.

---

### 2.4 Suivi des tests (test monitoring) et contrôle des tests (test control) avec l'IA générative

Les tâches de suivi des tests nécessitent l'analyse de grandes quantités de données, souvent disponibles dans des outils de gestion des tests.

**Activités supportées :**

- **Suivi des tests et analyse des métriques** : automatisation du suivi, analyse des tendances, alertes en cas d'écart par rapport au plan.
- **Contrôle des activités de test** : redéfinition des priorités, ajustement du calendrier, réaffectation des ressources.
- **Informations sur la clôture des tests (clôture des tests / test closure)** : génération de rapports de clôture, réussites et leçons apprises.
- **Visualisation et reporting améliorés** : tableaux de bord dynamiques et résumés en langage naturel pour toutes les parties prenantes.

---

### 2.5 Choisir les techniques de prompting adaptées

Le tableau suivant synthétise les recommandations pour choisir la technique de prompting en fonction des caractéristiques de la tâche de test.

| Technique de prompting | Cas d'utilisation recommandé | Principales caractéristiques et applications |
|---|---|---|
| **Enchaînement de prompts** | Tâches complexes nécessitant une vérification humaine à chaque étape | Divise les tâches en étapes plus petites ; utile pour l'analyse des tests, la conception des tests et l'automatisation des tests |
| **Few-shot prompting** | Tâches répétitives ou contraintes en format de sortie | Fournit des exemples à l'IA pour la génération répétitive : Gherkin, tests dirigés par les mots-clés, reporting avec format imposé |
| **Méta-prompting** | Tâches flexibles et dynamiques, création de prompts pour de nouvelles tâches | Description générale de l'objectif qui guide le LLM ; utile pour l'analyse de rapports de test et la détection d'anomalies |

---

## 3. Évaluer les résultats de l'IA générative et affiner les prompts

### 3.1 Métriques pour évaluer les résultats de l'IA générative sur des tâches de test

Plusieurs métriques (métrique / metric) permettent d'évaluer la qualité et l'efficience des résultats de l'IA générative sur une tâche de test :

| Métrique | Description | Exemple |
|---|---|---|
| **Exactitude** | Exactitude globale par rapport à une référence (cas de test experts, exigences) | Degré de couverture de toutes les exigences spécifiées par les cas de test générés |
| **Précision** | Exactitude de la sortie par rapport à un objectif spécifique | Degré auquel les cas de test générés identifient correctement les anomalies |
| **Rappel** | Capacité à identifier toutes les instances pertinentes | Couverture des partitions d'équivalence valides et invalides |
| **Pertinence et adéquation contextuelle** | Applicabilité et cohérence dans le contexte donné | Cohérence des cas de test avec la base de test et les exigences spécifiques au domaine |
| **Diversité** | Variété des entrées et scénarios couverts | Couverture de divers comportements utilisateurs et cas aux limites |
| **Taux de réussite des exécutions** | Proportion de scripts exécutables sans erreur | Scripts de test générés pouvant s'exécuter sans erreurs de syntaxe |
| **Efficience temporelle** | Temps gagné par rapport au test manuel | Temps de génération par l'IA vs. temps de création manuelle équivalente |

> **Note :** Compte tenu de la nature non déterministe de l'IA générative, les métriques doivent être basées sur des données statistiquement pertinentes.

---

### 3.2 Techniques d'évaluation et d'affinage itératif des prompts

Sur la base des métriques ci-dessus, plusieurs techniques permettent d'améliorer les résultats de l'IA de manière itérative :

- **Modification itérative des prompts** : partir d'un prompt de base et le modifier progressivement en ajoutant du contexte ou en ajustant la terminologie pour améliorer la spécificité et la pertinence.

- **Tests A/B des prompts** : créer plusieurs versions de prompts et évaluer celles qui produisent les meilleurs résultats selon des métriques prédéfinies.

- **Analyse des résultats** : examiner les sorties générées pour détecter inexactitudes et incohérences ; comprendre les types d'erreurs pour affiner les prompts lors des itérations suivantes.

- **Intégration des retours des utilisateurs** : recueillir les commentaires des testeurs sur l'utilité et la clarté des résultats ; les utiliser pour affiner les prompts afin de mieux répondre aux besoins réels de test.

- **Ajustement de la longueur et de la spécificité des prompts** : tester différentes longueurs de prompts et niveaux de détail — parfois plus de contexte améliore la qualité, parfois des prompts plus courts donnent de meilleurs résultats.

**Le partage des pratiques** au sein de l'équipe de test ou de l'organisation (bibliothèques de prompts, sessions d'optimisation collective) permet de normaliser les techniques de prompting et de promouvoir une culture d'apprentissage et d'amélioration itérative.

---

## 4. Activités pratiques

### Activité 1 — "Déconstruis ce prompt"
**Objectif :** Identifier les six composants d'un prompt structuré.

**Déroulement :**
1. Lisez le prompt suivant :
   > *"En tant que testeur de régression, analyse cette User Story concernant la gestion des droits d'accès. Génère une liste priorisée de conditions de test en tenant compte des risques de sécurité. Ne génère pas de cas de test, seulement les conditions. Présente le résultat sous forme de tableau avec les colonnes : ID, Condition de test, Niveau de risque (Haut/Moyen/Faible)."*
2. Identifiez dans ce prompt : le rôle, le contexte, l'instruction, les données d'entrée, les contraintes et le format de sortie.
3. Discutez : quels composants sont présents ? Lesquels manquent ? Comment les ajouter ?

**Ce qu'on apprend :** La structure d'un prompt n'est pas toujours explicite. Savoir l'analyser permet de l'améliorer méthodiquement.

---

### Activité 2 — "Enchaînement de prompts sur une User Story"
**Objectif :** Pratiquer l'enchaînement de prompts et la vérification humaine.

**User Story fournie :**
> *"En tant qu'administrateur, je veux pouvoir désactiver un compte utilisateur afin d'empêcher tout accès non autorisé après le départ d'un employé."*

**Déroulement :**
1. **Étape 1 — Identification des ambiguïtés** : promptez le LLM pour identifier les ambiguïtés de la User Story. Vérifiez et corrigez le résultat.
2. **Étape 2 — Génération des critères d'acceptation** : promptez le LLM pour générer les critères d'acceptation (critères d'acceptation / acceptance criteria) en tenant compte des ambiguïtés corrigées. Vérifiez.
3. **Étape 3 — Évaluation de la testabilité** : promptez le LLM pour évaluer si chaque critère est testable et mesurable. Affinez si nécessaire.

**Ce qu'on apprend :** La décomposition d'une tâche complexe en sous-tâches avec vérification humaine intermédiaire produit des résultats nettement plus fiables que l'obtention d'un résultat en un seul prompt.

---

### Activité 3 — "Few-shot Gherkin"
**Objectif :** Utiliser le few-shot prompting pour générer des scénarios Gherkin cohérents.

**Déroulement :**
1. Choisissez 2 User Stories simples de votre projet ou des exemples fournis.
2. Pour l'une d'elles, rédigez manuellement 2–3 scénarios Gherkin (Given/When/Then) en français.
3. Incluez ces scénarios comme exemples dans un prompt few-shot et demandez au LLM de générer les scénarios Gherkin pour la deuxième User Story.
4. Évaluez : le LLM a-t-il respecté le format ? Couvert les cas négatifs ?
5. Si les résultats sont insuffisants, améliorez les exemples ou ajoutez-en un troisième.

**Ce qu'on apprend :** La qualité des exemples fournis détermine directement la qualité des sorties few-shot. Des exemples représentatifs couvrant les cas nominaux ET négatifs guident mieux le modèle.

---

### Activité 4 — "Méta-prompt pour un nouveau contexte"
**Objectif :** Utiliser le méta-prompting pour construire un prompt efficace.

**Scénario :** Vous devez tester une fonctionnalité de calcul de prix avec des règles de remise complexes, mais vous ne savez pas comment structurer le prompt.

**Déroulement :**
1. Soumettez à un LLM :
   > *"Je dois générer des cas de test pour une fonctionnalité de calcul de prix avec remises dans un logiciel de facturation. Je veux créer un prompt structuré pour cette tâche. Génère-moi un prompt complet avec les composants : rôle, contexte, instructions, contraintes et format de sortie."*
2. Évaluez le prompt généré : est-il complet ? Précis ? Adapté ?
3. Modifiez le prompt généré pour l'adapter à votre contexte réel.
4. Utilisez le prompt affiné pour générer réellement des cas de test.

**Ce qu'on apprend :** Le méta-prompting est particulièrement utile lorsqu'on aborde un nouveau type de tâche. L'IA co-construit le prompt, mais la validation et l'affinage restent humains.

---

### Activité 5 — "Tests A/B de prompts"
**Objectif :** Comparer deux formulations de prompts et identifier la meilleure.

**Déroulement :**
1. Partez d'une même tâche : *"Génère des cas de test pour une fonctionnalité de recherche avec filtres."*
2. Rédigez deux versions du prompt :
   - **Version A** : prompt court, sans rôle ni format de sortie
   - **Version B** : prompt structuré complet (6 composants)
3. Soumettez les deux versions au même LLM.
4. Évaluez les résultats sur au moins 3 métriques : exactitude, pertinence contextuelle, diversité.
5. Discutez en groupe : quelle version est préférable ? Pourquoi ?

**Ce qu'on apprend :** La comparaison directe de prompts révèle l'impact concret de chaque composant. La méthode A/B est applicable en pratique pour optimiser les prompts d'une équipe.

---

## Pour aller plus loin

- **Schulhoff, S. et al. (2024)** — *The Prompt Report: A Systematic Survey of Prompting Techniques* — recense plus de 50 techniques de prompting avec leurs cas d'usage
- **ISTQB CT-GenAI Syllabus** — Chapitre 2 : référentiel officiel de ce module
- **Bibliothèques de prompts partagées** : envisagez de créer une bibliothèque de prompts réutilisables dans votre équipe de test
- Prochain chapitre : *Gérer les risques liés à l'IA générative dans les tests logiciels*

# Quizz de validation des acquis — Après l'atelier
## Ingénierie du prompting pour des tests logiciels efficaces

> **Objectif :** Ce quizz valide l'acquisition des compétences du chapitre 2 du référentiel ISTQB CT-GenAI.
>
> **Interprétation du score :**
> - **0–7 points** : Des lacunes subsistent — relire les sections concernées est recommandé.
> - **8–12 points** : Bonne maîtrise globale, quelques points à consolider.
> - **13–16 points** : Excellente maîtrise du chapitre. Vous êtes prêt pour le chapitre suivant.

---

### Question 1
**Combien de composants compte un prompt structuré pour les tests logiciels selon le référentiel ISTQB CT-GenAI ?**

- A. 3
- B. 4
- C. 6
- D. 8

<details><summary>Réponse</summary>

**C. 6**

Un prompt structuré comprend : rôle, contexte, instructions, données d'entrée, contraintes et format de sortie.

</details>

---

### Question 2
**Un testeur souhaite générer des critères d'acceptation progressivement à partir d'une User Story, en vérifiant et corrigeant les résultats à chaque étape. Quelle technique de prompting est la plus adaptée ?**

- A. Le few-shot prompting
- B. Le méta-prompting
- C. L'enchaînement de prompts (prompt chaining)
- D. Le zero-shot prompting

<details><summary>Réponse</summary>

**C. L'enchaînement de prompts (prompt chaining)**

L'enchaînement de prompts est spécifiquement conçu pour décomposer une tâche complexe en étapes vérifiées successivement. Il est recommandé pour l'analyse progressive d'une User Story avec vérification humaine intermédiaire.

</details>

---

### Question 3
**Quel énoncé décrit le mieux le one-shot prompting ?**

- A. Un prompt sans aucun exemple, s'appuyant sur les connaissances du modèle
- B. Un prompt contenant un seul exemple pour illustrer le résultat souhaité
- C. Un prompt contenant plusieurs exemples pour consolider le comportement attendu
- D. Un prompt généré par le LLM lui-même

<details><summary>Réponse</summary>

**B. Un prompt contenant un seul exemple pour illustrer le résultat souhaité**

Le one-shot prompting fournit un seul exemple pour illustrer le résultat souhaité pour une entrée donnée. Il se situe entre le zero-shot (aucun exemple) et le few-shot (plusieurs exemples).

</details>

---

### Question 4
**Dans un prompt structuré, quel composant spécifie : "Ne génère pas de tests de performance. Utilise uniquement les techniques de partition d'équivalence et d'analyse des valeurs limites." ?**

- A. Les instructions
- B. Le contexte
- C. Les contraintes
- D. Le format de sortie

<details><summary>Réponse</summary>

**C. Les contraintes**

Les contraintes décrivent les restrictions ou considérations particulières auxquelles le LLM doit se conformer. Elles précisent comment les instructions doivent être appliquées aux données d'entrée.

</details>

---

### Question 5
**Lequel de ces cas d'utilisation correspond le mieux au few-shot prompting ?**

- A. Analyser progressivement une User Story complexe avec vérification à chaque étape
- B. Créer un premier prompt pour une tâche inconnue en collaborant avec le LLM
- C. Générer des scénarios Gherkin cohérents à partir d'un format imposé avec des exemples
- D. Prioriser des cas de test selon plusieurs critères de risque simultanément

<details><summary>Réponse</summary>

**C. Générer des scénarios Gherkin cohérents à partir d'un format imposé avec des exemples**

Le few-shot prompting est idéal pour les tâches répétitives avec un format de sortie contraint. Fournir des exemples de scénarios Gherkin guide le modèle vers la structure et le style attendus.

</details>

---

### Question 6
**Un prompt système efficace peut contenir quels composants d'un prompt structuré ?**

- A. Uniquement les instructions
- B. Uniquement le rôle et le format de sortie
- C. Le rôle, le contexte et les contraintes
- D. Les données d'entrée et le format de sortie

<details><summary>Réponse</summary>

**C. Le rôle, le contexte et les contraintes**

Le prompt système peut contenir des parties d'un prompt structuré telles que le rôle, le contexte et les contraintes. Il définit les règles générales pour l'ensemble de la conversation.

</details>

---

### Question 7
**Parmi ces activités de test, laquelle NE peut PAS être directement supportée par l'IA générative selon le syllabus CT-GenAI ?**

- A. Générer des conditions de test à partir d'une User Story
- B. Décider du niveau de priorité acceptable pour un domaine métier spécifique
- C. Synthétiser des données de test représentatives
- D. Identifier des incohérences dans les exigences

<details><summary>Réponse</summary>

**B. Décider du niveau de priorité acceptable pour un domaine métier spécifique**

L'IA peut suggérer des niveaux de priorité basés sur des données historiques et des facteurs de risque, mais la décision finale sur ce qui est acceptable dans un contexte métier donné relève du jugement humain. Les décisions impliquant des contraintes légales, réglementaires ou des parties prenantes restent de la responsabilité humaine.

</details>

---

### Question 8
**Quelle métrique évalue dans quelle mesure les cas de test générés couvrent divers comportements utilisateurs et explorent les cas aux limites ?**

- A. L'exactitude
- B. La précision
- C. Le rappel
- D. La diversité

<details><summary>Réponse</summary>

**D. La diversité**

La diversité garantit la prise en charge d'un large éventail d'entrées et de scénarios, évitant ainsi les répétitions. Elle évalue si les cas de test générés couvrent divers comportements des utilisateurs et explorent les cas aux limites.

</details>

---

### Question 9
**Un testeur utilise le LLM pour générer un prompt à sa place, car il ne sait pas comment structurer sa demande pour une nouvelle tâche de détection d'anomalies. Quelle technique utilise-t-il ?**

- A. L'enchaînement de prompts
- B. Le few-shot prompting
- C. Le méta-prompting
- D. Le zero-shot prompting

<details><summary>Réponse</summary>

**C. Le méta-prompting**

Le méta-prompting permet au testeur de collaborer avec le LLM pour co-créer des prompts efficaces. C'est particulièrement utile lorsque le testeur n'est pas sûr de la meilleure façon de formuler sa demande pour une nouvelle tâche.

</details>

---

### Question 10
**Dans le contexte des tests de régression automatisés, que désigne un test "auto-réparateur" (self-healing test) ?**

- A. Un test qui se relance automatiquement en cas d'échec
- B. Un test qui s'adapte automatiquement aux modifications mineures de l'interface utilisateur ou de l'API
- C. Un test qui génère automatiquement son propre rapport de défaut
- D. Un test qui s'exécute automatiquement à intervalles réguliers

<details><summary>Réponse</summary>

**B. Un test qui s'adapte automatiquement aux modifications mineures de l'interface utilisateur ou de l'API**

Les tests auto-réparateurs (self-healing tests) utilisent l'IA générative pour ajuster automatiquement les scripts de test lors de modifications mineures, évitant ainsi les défaillances inutiles et garantissant la stabilité des suites de tests au fil du temps.

</details>

---

### Question 11
**Lequel de ces énoncés décrit le mieux la relation entre prompt système et prompt utilisateur lors d'une session d'interaction ?**

- A. Le prompt système est envoyé après chaque prompt utilisateur pour recadrer le contexte
- B. Le prompt système est défini une fois et reste constant ; les prompts utilisateur sont envoyés successivement pour chaque interaction
- C. Le prompt système remplace le prompt utilisateur quand celui-ci est trop court
- D. Le prompt système et le prompt utilisateur sont fusionnés automatiquement par le LLM

<details><summary>Réponse</summary>

**B. Le prompt système est défini une fois et reste constant ; les prompts utilisateur sont envoyés successivement pour chaque interaction**

Le LLM génère des réponses en tenant compte à la fois du prompt système (inchangé) et du prompt utilisateur actuel. Le prompt système établit le cadre général ; les prompts utilisateur fournissent le contexte immédiat de chaque réponse.

</details>

---

### Question 12
**Quelle technique d'affinage des prompts consiste à analyser les sorties générées pour identifier les types d'erreurs et d'incohérences, afin d'éviter ces mêmes problèmes dans les itérations suivantes ?**

- A. Les tests A/B des prompts
- B. L'analyse des résultats
- C. L'intégration des retours des utilisateurs
- D. L'ajustement de la longueur des prompts

<details><summary>Réponse</summary>

**B. L'analyse des résultats**

L'analyse des résultats consiste à examiner les sorties générées par l'IA pour détecter les inexactitudes ou incohérences. Comprendre les types d'erreurs aide à affiner les prompts pour éviter des défauts similaires lors des itérations suivantes.

</details>

---

### Question 13
**Parmi ces tâches de suivi des tests, laquelle est directement facilitée par l'IA générative ?**

- A. Définir les objectifs de test du projet
- B. Signer la clôture de test (test closure) avec les parties prenantes
- C. Générer des rapports de clôture avec les réussites et leçons apprises
- D. Approuver les modifications du plan de test lors d'un comité de pilotage

<details><summary>Réponse</summary>

**C. Générer des rapports de clôture avec les réussites et leçons apprises**

L'IA générative peut aider à générer des rapports de clôture de test mettant en évidence les réussites et les leçons apprises. Les décisions formelles impliquant des parties prenantes (approbation, signature) restent de la responsabilité humaine.

</details>

---

### Question 14
**Selon le syllabus, pourquoi les métriques d'évaluation des résultats de l'IA générative doivent-elles être basées sur des données statistiquement pertinentes ?**

- A. Parce que les LLMs ne peuvent répondre qu'à des questions statistiques
- B. En raison de la nature non déterministe de l'IA générative, qui peut produire des résultats différents pour un même prompt
- C. Parce que les métriques de test logiciel sont toujours exprimées en pourcentages
- D. Pour compenser les limites des outils d'évaluation automatique

<details><summary>Réponse</summary>

**B. En raison de la nature non déterministe de l'IA générative, qui peut produire des résultats différents pour un même prompt**

L'IA générative est non déterministe : pour une même consigne, elle peut produire des résultats différents d'une exécution à l'autre. Les métriques d'évaluation doivent donc reposer sur des données statistiquement pertinentes pour être fiables.

</details>

---

### Question 15
**Quel composant du prompt structuré indique : "Présente le résultat sous forme de tableau Markdown avec les colonnes : ID, Titre, Préconditions, Étapes, Résultat attendu" ?**

- A. Les instructions
- B. Les contraintes
- C. Le contexte
- D. Le format de sortie

<details><summary>Réponse</summary>

**D. Le format de sortie**

Le format de sortie spécifie le format, la structure ou les caractéristiques attendus de la réponse. Il aide à façonner la sortie du LLM pour qu'elle soit directement exploitable.

</details>

---

### Question 16
**Quelle est la principale valeur ajoutée du partage de bibliothèques de prompts au sein d'une équipe de test ?**

- A. Réduire le coût des licences des outils d'IA générative
- B. Normaliser les techniques de prompting, éviter les erreurs répétées et promouvoir une culture d'amélioration itérative
- C. Permettre aux testeurs de ne plus avoir à rédiger de prompts manuellement
- D. Garantir que les résultats du LLM sont toujours identiques d'un testeur à l'autre

<details><summary>Réponse</summary>

**B. Normaliser les techniques de prompting, éviter les erreurs répétées et promouvoir une culture d'amélioration itérative**

Le partage de bibliothèques de prompts normalise les pratiques, permet de s'appuyer sur des connaissances collectives, d'éviter les erreurs répétées et de raffiner plus efficacement l'utilisation des outils d'IA générative au fil du temps.

</details>

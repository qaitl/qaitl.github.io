# Quizz de positionnement — Avant l'atelier
## Ingénierie du prompting pour des tests logiciels efficaces

> **Objectif :** Ce quizz permet de déterminer si vous avez besoin de suivre ce module ou si vous maîtrisez déjà les bases de l'ingénierie du prompting appliquée aux tests logiciels.
>
> **Interprétation du score :**
> - **0–3 points** : Ce module est fait pour vous — les bases sont à construire.
> - **4–6 points** : Quelques notions sont acquises, un parcours rapide du module est recommandé.
> - **7–8 points** : Vous maîtrisez déjà les fondements. Vous pouvez passer directement au module suivant.

---

### Question 1
**Quel composant d'un prompt structuré définit la perspective ou le persona que le modèle doit adopter ?**

- A. Le contexte
- B. Le rôle
- C. Les contraintes
- D. Le format de sortie

<details><summary>Réponse</summary>

**B. Le rôle**

Le rôle définit la perspective ou le persona que le modèle d'IA générative doit adopter. Il aide le LLM à déterminer ses responsabilités et à adopter un ton approprié (ex. : testeur, test manager, ingénieur en automatisation des tests).

</details>

---

### Question 2
**Quelle technique de prompting consiste à diviser une tâche complexe en une série d'étapes intermédiaires dont chacune est vérifiée avant de passer à la suivante ?**

- A. Le few-shot prompting
- B. Le méta-prompting
- C. L'enchaînement de prompts (prompt chaining)
- D. Le zero-shot prompting

<details><summary>Réponse</summary>

**C. L'enchaînement de prompts (prompt chaining)**

L'enchaînement de prompts divise une tâche en étapes intermédiaires. Le résultat de chaque étape est vérifié — manuellement ou automatiquement — avant de passer à l'étape suivante. Cette approche améliore la précision et permet une validation systématique des résultats intermédiaires.

</details>

---

### Question 3
**Quelle est la principale différence entre un prompt système (system prompt) et un prompt utilisateur (user prompt) ?**

- A. Le prompt système est rédigé en langage formel, le prompt utilisateur en langage naturel
- B. Le prompt système est défini une fois au début et reste constant, le prompt utilisateur change à chaque interaction
- C. Le prompt système est visible par l'utilisateur, le prompt utilisateur ne l'est pas
- D. Le prompt système concerne uniquement le rôle, le prompt utilisateur concerne uniquement les instructions

<details><summary>Réponse</summary>

**B. Le prompt système est défini une fois au début et reste constant, le prompt utilisateur change à chaque interaction**

Le prompt système est généralement défini par le développeur ou le testeur. Il établit le cadre général (rôle, contraintes, ton) et reste constant tout au long de la session. Le prompt utilisateur représente l'entrée de l'utilisateur à chaque interaction.

</details>

---

### Question 4
**Le few-shot prompting est particulièrement efficace pour :**

- A. Les tâches où la décomposition en sous-étapes est nécessaire
- B. Les tâches répétitives avec un format de sortie contraint (ex. : scénarios Gherkin)
- C. La création automatique de prompts par le LLM
- D. Les tâches de raisonnement complexe et multi-critères

<details><summary>Réponse</summary>

**B. Les tâches répétitives avec un format de sortie contraint (ex. : scénarios Gherkin)**

Le few-shot prompting fournit des exemples au LLM pour guider la génération répétitive vers un format spécifique. Il est idéal pour les scénarios Gherkin, les tests dirigés par les mots-clés ou les rapports de test standardisés.

</details>

---

### Question 5
**Quelle métrique évalue la proportion de cas de test ou de scripts de test générés qui peuvent être exécutés avec succès sans erreur de syntaxe ?**

- A. La précision
- B. Le rappel
- C. Le taux de réussite des exécutions
- D. L'efficience temporelle

<details><summary>Réponse</summary>

**C. Le taux de réussite des exécutions**

Le taux de réussite des exécutions mesure combien de scripts de test générés peuvent être exécutés sans erreurs de syntaxe ni problèmes de format dans un environnement de test qui fonctionne correctement.

</details>

---

### Question 6
**Lequel de ces énoncés décrit le mieux le méta-prompting ?**

- A. Fournir plusieurs exemples dans le prompt pour guider le modèle
- B. Exploiter la capacité de l'IA à générer ou améliorer ses propres prompts
- C. Enchaîner plusieurs prompts pour décomposer une tâche complexe
- D. Soumettre un prompt sans aucun exemple pour s'appuyer sur les connaissances du modèle

<details><summary>Réponse</summary>

**B. Exploiter la capacité de l'IA à générer ou améliorer ses propres prompts**

Le méta-prompting permet au testeur de collaborer avec le LLM pour co-créer des prompts efficaces. C'est particulièrement utile quand le testeur ne sait pas encore comment formuler un prompt efficace pour une nouvelle tâche.

</details>

---

### Question 7
**Dans un contexte de test logiciel, quel composant du prompt structuré contient typiquement les User Stories, les critères d'acceptation et les captures d'écran ?**

- A. Le contexte
- B. Les instructions
- C. Les données d'entrée
- D. Les contraintes

<details><summary>Réponse</summary>

**C. Les données d'entrée**

Les données d'entrée comprennent toutes les informations nécessaires à l'exécution de la tâche : User Stories, critères d'acceptation, captures d'écran, code, cas de test existants ou exemples de sortie.

</details>

---

### Question 8
**Quelle technique d'affinage itératif des prompts consiste à créer plusieurs versions d'un prompt et à les comparer selon des métriques prédéfinies pour identifier la formulation optimale ?**

- A. L'analyse des résultats
- B. Les tests A/B des prompts
- C. L'ajustement de la longueur des prompts
- D. L'intégration des retours des utilisateurs

<details><summary>Réponse</summary>

**B. Les tests A/B des prompts**

Les tests A/B consistent à créer plusieurs versions de prompts et à évaluer laquelle produit les meilleurs résultats selon des métriques prédéfinies (exactitude, pertinence, diversité, etc.).

</details>

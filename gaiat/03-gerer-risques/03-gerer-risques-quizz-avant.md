# Quizz de positionnement — Avant l'atelier
## Gérer les risques liés à l'IA générative dans les tests logiciels

> **Objectif :** Ce quizz permet de déterminer si vous avez besoin de suivre ce module ou si vous maîtrisez déjà les bases de la gestion des risques liés à l'IA générative dans les tests logiciels.
>
> **Interprétation du score :**
> - **0–3 points** : Ce module est fait pour vous — les bases sont à construire.
> - **4–6 points** : Quelques notions sont acquises, un parcours rapide du module est recommandé.
> - **7–8 points** : Vous maîtrisez déjà les fondements. Vous pouvez passer directement au module suivant.

---

### Question 1
**Qu'est-ce qu'une hallucination (hallucination) dans le contexte d'un LLM utilisé pour le test logiciel ?**

- A. Un plantage du modèle pendant la génération
- B. Une information produite par le LLM qui n'est pas factuellement exacte ni étayée par les données d'entrée
- C. Un refus du modèle de répondre à une question
- D. Une réponse trop longue ou hors format

<details><summary>Réponse</summary>

**B. Une information produite par le LLM qui n'est pas factuellement exacte ni étayée par les données d'entrée**

Le LLM est entraîné à produire des séquences probables, pas à vérifier la vérité factuelle. Quand une information manque, il tend à compléter plausiblement. Exemple typique en test : un cas de test qui référence une API ou une règle métier inexistantes.

</details>

---

### Question 2
**Pourquoi un même prompt soumis deux fois à un LLM peut-il produire deux réponses différentes ?**

- A. Parce que le LLM s'améliore en continu à chaque requête
- B. En raison de la nature non déterministe des LLMs (échantillonnage probabiliste)
- C. Parce que le modèle apprend de la précédente interaction
- D. Parce que la latence réseau modifie le contenu

<details><summary>Réponse</summary>

**B. En raison de la nature non déterministe des LLMs (échantillonnage probabiliste)**

La génération repose sur un échantillonnage aléatoire à partir de distributions de probabilité. Abaisser la température ou fixer un seed réduit la variabilité sans toujours la supprimer. Les métriques de test doivent donc reposer sur plusieurs runs.

</details>

---

### Question 3
**Quelle est la meilleure pratique pour protéger les données confidentielles lors de l'utilisation d'un LLM externe pour une tâche de test ?**

- A. Envoyer les données telles quelles et demander au LLM de ne pas les mémoriser
- B. Anonymiser ou pseudonymiser les données avant envoi, et privilégier un fournisseur avec option « no training »
- C. Envoyer les données cryptées en base64
- D. Ne jamais utiliser de LLM pour une tâche de test

<details><summary>Réponse</summary>

**B. Anonymiser ou pseudonymiser les données avant envoi, et privilégier un fournisseur avec option « no training »**

La responsabilité de la confidentialité reste côté organisation qui utilise le LLM. Anonymisation, contrat *no training*, journalisation et, si nécessaire, modèle hébergé en interne sont les leviers reconnus.

</details>

---

### Question 4
**Qu'est-ce qu'une attaque de type prompt injection (OWASP LLM01) ?**

- A. Une surcharge de requêtes destinée à faire tomber le service
- B. Une entrée malveillante (dans une User Story importée, un document, une page web…) qui manipule le comportement du LLM
- C. Une fuite du prompt système vers l'utilisateur
- D. Une saturation de la fenêtre de contexte

<details><summary>Réponse</summary>

**B. Une entrée malveillante qui manipule le comportement du LLM**

Le prompt injection consiste à injecter dans une entrée exploitée par le LLM des instructions qui détournent la tâche. Toute donnée externe doit être traitée comme potentiellement hostile.

</details>

---

### Question 5
**Parmi ces leviers, lequel réduit le plus directement l'empreinte énergétique d'une campagne de test assistée par IA ?**

- A. Toujours utiliser le plus grand modèle disponible pour « être sûr »
- B. Choisir un modèle adapté à la tâche, mettre en cache les prompts répétés et éviter les régénérations inutiles
- C. Lancer les requêtes la nuit
- D. Utiliser uniquement le streaming au lieu du non-streaming

<details><summary>Réponse</summary>

**B. Choisir un modèle adapté à la tâche, mettre en cache les prompts répétés et éviter les régénérations inutiles**

Le coût énergétique se pilote surtout par la taille du modèle, le volume d'appels et la longueur des prompts/réponses. Un petit modèle pour une tâche simple, le *prompt caching* et l'analyse d'impact sont les leviers principaux.

</details>

---

### Question 6
**Quel texte européen impose un cadre horizontal de gestion des risques liés à l'IA, y compris aux systèmes d'IA générative ?**

- A. Le RGPD
- B. L'AI Act (Règlement UE 2024/1689)
- C. La directive NIS2
- D. La norme ISO 9001

<details><summary>Réponse</summary>

**B. L'AI Act (Règlement UE 2024/1689)**

L'AI Act est entré en vigueur le 1er août 2024, avec une application progressive jusqu'en 2027. Il impose des obligations différenciées selon le niveau de risque et concerne aussi bien les fournisseurs que les utilisateurs professionnels de systèmes d'IA.

</details>

---

### Question 7
**Quelle est la première règle de vérification à appliquer aux sorties d'un LLM utilisées dans une activité de test ?**

- A. Les considérer comme vraies tant qu'aucune erreur n'est rencontrée
- B. Les considérer comme des propositions à vérifier, la responsabilité finale restant au testeur humain
- C. Ne jamais les utiliser et repartir de zéro
- D. Les soumettre à un second LLM pour validation, sans relecture humaine

<details><summary>Réponse</summary>

**B. Les considérer comme des propositions à vérifier, la responsabilité finale restant au testeur humain**

Le syllabus ISTQB CT-GenAI est clair : toute sortie d'IA générative est une proposition. Le testeur conserve la responsabilité de la qualité. La revue humaine est proportionnée au risque du cas d'usage.

</details>

---

### Question 8
**Parmi ces propositions, laquelle illustre un biais (bias) dans les sorties d'un LLM utilisé pour générer des données de test ?**

- A. Le LLM refuse de répondre à une question hors sujet
- B. Les profils utilisateurs générés sont majoritairement en locale en-US et ne couvrent pas les alphabets non latins
- C. Le LLM renvoie parfois des réponses différentes au même prompt
- D. Le LLM invente un endpoint d'API inexistant

<details><summary>Réponse</summary>

**B. Les profils utilisateurs générés sont majoritairement en locale en-US et ne couvrent pas les alphabets non latins**

Un biais est une tendance systématique héritée des corpus d'entraînement. Les autres propositions correspondent respectivement à un refus d'alignement, au non-déterminisme et à une hallucination.

</details>

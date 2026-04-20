# Quizz de positionnement — Avant l'atelier
## Introduction à l'IA générative

> **Objectif :** Ce quizz permet de déterminer si vous avez besoin de suivre ce module ou si vous maîtrisez déjà les fondements de l'IA générative.
>
> **Interprétation du score :**
> - **0–4 points** : Ce module est fait pour vous — les bases sont à construire.
> - **5–7 points** : Quelques notions sont acquises, mais un parcours rapide du module est recommandé.
> - **8–10 points** : Vous maîtrisez déjà les fondements. Vous pouvez passer directement au module suivant.

---

### Question 1
**Quel type d'IA apprend à partir d'exemples, sans que les règles soient programmées explicitement ?**

- A. L'IA symbolique
- B. L'apprentissage automatique (machine learning)
- C. L'IA agentique
- D. Un système expert

<details><summary>Réponse</summary>

**B. L'apprentissage automatique (machine learning)**

L'IA symbolique repose sur des règles écrites à la main par des experts. Le machine learning, lui, apprend les patterns à partir des données.

</details>

---

### Question 2
**Quel est le principe de fonctionnement d'un grand modèle de langage (LLM / large language model) ?**

- A. Chercher la réponse dans une base de données structurée
- B. Prédire le mot le plus probable dans la suite d'un texte
- C. Raisonner logiquement comme un humain
- D. Traduire chaque phrase dans un langage formel

<details><summary>Réponse</summary>

**B. Prédire le mot le plus probable dans la suite d'un texte**

Un LLM a été entraîné sur des milliards de phrases. Son mécanisme central est la prédiction du token suivant, répétée jusqu'à former une réponse complète.

</details>

---

### Question 3
**Lequel de ces modèles est open source et peut être hébergé localement ?**

- A. GPT-4o (OpenAI)
- B. Claude (Anthropic)
- C. Llama 3 (Meta)
- D. Gemini (Google)

<details><summary>Réponse</summary>

**C. Llama 3 (Meta)**

Meta publie ses modèles Llama sous licence open source, permettant leur téléchargement et leur exécution sur un serveur interne.

</details>

---

### Question 4
**Quelle est la principale différence entre un chatbot grand public (ex. ChatGPT) et un outil intégrant un LLM (ex. GitHub Copilot) ?**

- A. Le chatbot est plus puissant
- B. L'outil intégré dispose d'un accès à votre contexte métier (code, tickets, documents)
- C. Le chatbot ne peut pas rédiger de texte
- D. L'outil intégré n'utilise pas de LLM

<details><summary>Réponse</summary>

**B. L'outil intégré dispose d'un accès à votre contexte métier**

Un chatbot grand public est généraliste et sans contexte. Un outil intégrant un LLM injecte automatiquement le contexte projet dans le prompt.

</details>

---

### Question 5
**Parmi ces tâches, laquelle est un point faible connu des LLMs ?**

- A. Reformuler un texte dans un style différent
- B. Résumer un long document
- C. Compter exactement le nombre d'occurrences d'une lettre dans une phrase
- D. Générer des cas de test à partir d'une user story

<details><summary>Réponse</summary>

**C. Compter exactement le nombre d'occurrences d'une lettre**

Les LLMs découpent le texte en tokens, pas en caractères individuels. Les tâches nécessitant une manipulation caractère par caractère ou un comptage exact sont peu fiables.

</details>

---

### Question 6
**Qu'est-ce qu'un modèle multimodal (multimodal model) ?**

- A. Un modèle capable de traiter plusieurs langues
- B. Un modèle capable de traiter plusieurs types de données (texte, images, audio…)
- C. Un modèle utilisable sur plusieurs appareils
- D. Un modèle entraîné par plusieurs entreprises en collaboration

<details><summary>Réponse</summary>

**B. Un modèle capable de traiter plusieurs types de données**

Un modèle multimodal peut recevoir et/ou produire du texte, des images, de l'audio, de la vidéo, selon ses capacités.

</details>

---

### Question 7
**Un LLM peut-il produire des résultats différents pour une même question posée deux fois ?**

- A. Non, un LLM est déterministe par définition
- B. Oui, les LLMs sont probabilistes et leurs sorties peuvent varier
- C. Oui, uniquement si la question est posée dans une langue différente
- D. Non, les réponses sont indexées et mises en cache

<details><summary>Réponse</summary>

**B. Oui, les LLMs sont probabilistes et leurs sorties peuvent varier**

Le comportement probabiliste des LLMs est une caractéristique fondamentale. Pour une même entrée, la sortie peut différer d'une exécution à l'autre, ce qui a des implications importantes en test logiciel.

</details>

---

### Question 8
**Qu'est-ce qu'un agent IA (AI agent) ?**

- A. Un LLM qui répond uniquement à des questions fermées
- B. Un programme qui n'utilise pas de LLM
- C. Un système où le LLM peut agir, enchaîner des étapes et utiliser des outils externes
- D. Un chatbot spécialisé dans la relation client

<details><summary>Réponse</summary>

**C. Un système où le LLM peut agir, enchaîner des étapes et utiliser des outils externes**

L'IA agentique va au-delà de la simple génération de texte : l'agent peut naviguer sur le web, exécuter du code, appeler des APIs, et adapter son plan selon les résultats intermédiaires.

</details>

---

### Question 9
**Pour quelle raison principale utilise-t-on un modèle open source auto-hébergé plutôt qu'un chatbot cloud ?**

- A. Les modèles open source sont toujours plus performants
- B. Pour éviter que les données quittent l'infrastructure interne
- C. Parce que les chatbots cloud ne supportent pas le français
- D. Pour bénéficier d'une interface plus conviviale

<details><summary>Réponse</summary>

**B. Pour éviter que les données quittent l'infrastructure interne**

L'auto-hébergement est privilégié dans les contextes sensibles (bancaire, médical, défense) où les données ne doivent pas transiter par des serveurs tiers.

</details>

---

### Question 10
**Dans un contexte de test logiciel, quel est le rôle irremplaçable du testeur face à l'IA générative ?**

- A. Taper les prompts plus vite
- B. Valider la pertinence métier des résultats générés et détecter les erreurs d'hallucination
- C. Surveiller la consommation électrique du modèle
- D. Choisir le bon fournisseur de LLM

<details><summary>Réponse</summary>

**B. Valider la pertinence métier et détecter les hallucinations**

L'IA accélère la production de contenu (cas de test, rapports, analyses), mais la validation de la pertinence métier, l'exactitude technique et le jugement sur les cas limites restent des responsabilités humaines.

</details>

---

*Score : comptez 1 point par bonne réponse. Résultat sur 10.*

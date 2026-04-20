# Quizz de validation des acquis — Après l'atelier
## Gérer les risques liés à l'IA générative dans les tests logiciels

> **Objectif :** Ce quizz valide l'acquisition des compétences du chapitre 3 du référentiel ISTQB CT-GenAI.
>
> **Interprétation du score :**
> - **0–7 points** : Des lacunes subsistent — relire les sections concernées est recommandé.
> - **8–12 points** : Bonne maîtrise globale, quelques points à consolider.
> - **13–16 points** : Excellente maîtrise du chapitre. Vous êtes prêt pour le chapitre suivant.

---

### Question 1
**Quelle est la différence fondamentale entre une hallucination et une erreur de raisonnement dans un LLM ?**

- A. L'hallucination concerne les images, l'erreur de raisonnement concerne le texte
- B. L'hallucination porte sur la factualité des informations produites, l'erreur de raisonnement porte sur la chaîne logique qui mène à la conclusion
- C. L'hallucination survient toujours en début de réponse, l'erreur de raisonnement en fin
- D. Il n'y a pas de différence : ce sont deux noms pour le même phénomène

<details><summary>Réponse</summary>

**B. L'hallucination porte sur la factualité des informations produites, l'erreur de raisonnement porte sur la chaîne logique qui mène à la conclusion**

Une hallucination est une information non étayée. Une erreur de raisonnement est une déduction invalide, même lorsque les prémisses sont correctes. Un modèle de raisonnement peut raisonner parfaitement sur des prémisses inventées et produire une conclusion plausible mais fausse.

</details>

---

### Question 2
**Quelle combinaison de techniques est la plus efficace pour atténuer les hallucinations dans des cas de test générés par LLM ?**

- A. Augmenter la température et relancer plusieurs fois
- B. Fournir une base de test précise, demander une justification, appliquer un enchaînement de prompts avec revue humaine, et ancrer (grounding) la génération sur une source autoritative
- C. Utiliser le modèle le plus récent et faire confiance à sa sortie
- D. Générer 100 cas de test et en garder un au hasard

<details><summary>Réponse</summary>

**B. Fournir une base de test précise, demander une justification, appliquer un enchaînement de prompts avec revue humaine, et ancrer (grounding) la génération sur une source autoritative**

Le syllabus recommande une atténuation en couches : contexte solide en amont, structure dans le prompt, grounding sur des sources vérifiables et revue humaine sur la sortie.

</details>

---

### Question 3
**Parmi ces leviers, lequel contribue le plus à la reproductibilité d'une tâche de test effectuée avec un LLM ?**

- A. Laisser la température à sa valeur par défaut
- B. Versionner le prompt, l'identifiant du modèle, la configuration (température, seed) et la date, tout en exécutant plusieurs runs
- C. Ne plus jamais utiliser le même prompt
- D. Demander au LLM de se souvenir de la précédente réponse

<details><summary>Réponse</summary>

**B. Versionner le prompt, l'identifiant du modèle, la configuration et la date, et exécuter plusieurs runs**

Le non-déterminisme ne se supprime pas totalement. La bonne pratique est de figer ce qui peut l'être et d'évaluer la qualité sur un échantillon statistiquement pertinent.

</details>

---

### Question 4
**Un testeur colle dans un LLM grand public un extrait de code de production contenant une clé d'API pour demander une analyse. Quel risque principal prend-il ?**

- A. Un risque de performance côté LLM
- B. Un risque de fuite de données confidentielles, potentiellement couvert par RGPD, secret des affaires ou politique interne
- C. Un risque d'hallucination dans l'analyse
- D. Un risque de consommation énergétique excessive

<details><summary>Réponse</summary>

**B. Un risque de fuite de données confidentielles**

L'envoi d'un secret à un tiers est une fuite. La responsabilité de la protection reste côté organisation utilisatrice. Les mesures attendues : anonymisation, usage d'une offre avec *no training*, ou LLM hébergé en interne.

</details>

---

### Question 5
**Dans le référentiel OWASP Top 10 for LLM Applications (édition 2025), à quoi correspond la catégorie LLM01 ?**

- A. Sensitive Information Disclosure
- B. Prompt Injection
- C. Improper Output Handling
- D. Unbounded Consumption

<details><summary>Réponse</summary>

**B. Prompt Injection**

Le prompt injection reste le risque n°1 dans la taxonomie OWASP Top 10 LLM édition 2025. Toute entrée externe exploitée par le LLM est un vecteur d'attaque potentiel.

</details>

---

### Question 6
**Quelle mesure est la plus efficace pour limiter les risques d'*excessive agency* (LLM06) dans un agent de test piloté par LLM ?**

- A. Donner à l'agent tous les droits nécessaires « au cas où »
- B. Restreindre les permissions de l'agent au strict minimum et exiger une validation humaine avant toute action destructive
- C. Utiliser un modèle plus grand pour réduire les erreurs
- D. Laisser l'agent apprendre par lui-même sur l'environnement de production

<details><summary>Réponse</summary>

**B. Restreindre les permissions de l'agent au strict minimum et exiger une validation humaine avant toute action destructive**

Le principe du moindre privilège s'applique aux agents IA comme à tout composant logiciel. La validation humaine sur les actions à fort impact est une défense essentielle.

</details>

---

### Question 7
**Quel est l'ordre de grandeur réaliste du coût énergétique comparé entre une requête texte et une requête de génération vidéo sur un grand modèle ?**

- A. Équivalent
- B. La vidéo coûte environ 10 % de plus
- C. La vidéo peut coûter 1 à 3 ordres de grandeur de plus
- D. Le texte coûte plus cher que la vidéo

<details><summary>Réponse</summary>

**C. La vidéo peut coûter 1 à 3 ordres de grandeur de plus**

Les modalités les plus riches (image, audio, vidéo) consomment sensiblement plus d'énergie par requête que le texte. Les chiffres exacts varient selon le modèle et la durée générée — citer toujours la source et la date.

</details>

---

### Question 8
**Pour réduire la consommation énergétique d'une campagne de test assistée par LLM, quel levier est le plus cohérent avec la sobriété numérique ?**

- A. Toujours utiliser le modèle le plus grand pour éviter les erreurs et les relances
- B. Choisir le plus petit modèle capable de faire la tâche, mettre en cache les segments répétés, éviter les régénérations inutiles
- C. Augmenter la température pour avoir plus de diversité
- D. Lancer les requêtes uniquement le week-end

<details><summary>Réponse</summary>

**B. Choisir le plus petit modèle capable de faire la tâche, mettre en cache les segments répétés, éviter les régénérations inutiles**

La taille du modèle, le volume d'appels et la longueur de prompts/réponses sont les trois leviers principaux. Le *prompt caching* est désormais largement disponible et réduit à la fois le coût, la latence et l'énergie.

</details>

---

### Question 9
**Quel texte fixe au niveau européen un cadre horizontal de gestion des risques liés à l'IA, avec une application progressive entre 2024 et 2027 ?**

- A. Le RGPD
- B. L'AI Act (Règlement UE 2024/1689)
- C. La directive CSRD
- D. ISO 9001

<details><summary>Réponse</summary>

**B. L'AI Act (Règlement UE 2024/1689)**

L'AI Act est entré en vigueur le 1er août 2024. Les interdictions s'appliquent depuis février 2025, les obligations pour les modèles à usage général depuis août 2025, et les obligations pour les systèmes à haut risque se déploient jusqu'en 2027.

</details>

---

### Question 10
**Quelle norme internationale définit un système de management de l'intelligence artificielle, utilisable comme référentiel auditable en complément des bonnes pratiques ISTQB ?**

- A. ISO 9001:2015
- B. ISO/IEC 27001:2022
- C. ISO/IEC 42001:2023
- D. ISO 14001:2015

<details><summary>Réponse</summary>

**C. ISO/IEC 42001:2023**

ISO/IEC 42001 est la norme de système de management dédiée à l'IA. Elle fournit un cadre auditable pour gouverner l'usage de l'IA dans l'organisation et complète les normes de gestion des risques (ISO/IEC 23894) et de qualité logicielle (série 250xx).

</details>

---

### Question 11
**Un testeur observe que les profils utilisateurs synthétiques générés par un LLM sont majoritairement masculins, jeunes, urbains et anglophones. De quel type de défaillance s'agit-il ?**

- A. Une hallucination
- B. Un biais
- C. Une erreur de raisonnement
- D. Un non-déterminisme

<details><summary>Réponse</summary>

**B. Un biais**

Les biais proviennent des corpus d'entraînement et des choix d'alignement. La technique d'atténuation classique consiste à contraindre explicitement le prompt pour couvrir les attributs sensibles (âge, genre, locale, accessibilité, situation économique…).

</details>

---

### Question 12
**Quelle pratique est la plus efficace pour limiter le risque d'une sortie LLM exécutée sans contrôle (script de test généré automatiquement qui contient une commande destructive) ?**

- A. Faire confiance au modèle s'il est récent
- B. Exécuter directement la sortie dans l'environnement de production pour gagner du temps
- C. Revue humaine, analyse statique et exécution dans une sandbox restreinte avant toute intégration
- D. Demander au LLM s'il pense que sa sortie est sûre

<details><summary>Réponse</summary>

**C. Revue humaine, analyse statique et exécution dans une sandbox restreinte avant toute intégration**

*Improper Output Handling* (OWASP LLM05) est l'une des vulnérabilités les plus fréquentes. La sortie d'un LLM est un artefact externe à traiter comme tel, avec revue, analyse et environnement contrôlé.

</details>

---

### Question 13
**Dans un contexte de non-déterminisme des LLMs, pourquoi est-il risqué de conclure à la qualité d'un prompt sur la base d'un seul run ?**

- A. Parce qu'un seul run ne peut pas être facturé
- B. Parce qu'un seul run peut masquer des variations significatives de qualité qui n'apparaissent qu'en répétant la génération
- C. Parce que le LLM apprend entre deux runs
- D. Parce que la latence change d'un run à l'autre

<details><summary>Réponse</summary>

**B. Parce qu'un seul run peut masquer des variations significatives de qualité**

Le syllabus insiste sur la nature non déterministe et recommande une évaluation statistique : plusieurs runs, métriques agrégées, tests A/B. Un run unique peut faussement valider ou invalider un prompt.

</details>

---

### Question 14
**Parmi ces actions, laquelle relève explicitement de la responsabilité de l'organisation utilisatrice d'un LLM, et non du fournisseur du modèle ?**

- A. L'entraînement initial du modèle
- B. La définition de la politique de classification des données envoyées au LLM
- C. L'architecture du transformer
- D. L'optimisation des noyaux CUDA

<details><summary>Réponse</summary>

**B. La définition de la politique de classification des données envoyées au LLM**

L'organisation utilisatrice reste responsable (au sens RGPD, *controller*) des données qu'elle injecte. La classification, l'anonymisation, le contrôle des accès et la revue des sorties relèvent de sa responsabilité.

</details>

---

### Question 15
**Quelle pratique est recommandée pour documenter l'usage d'une IA générative dans un livrable de test, en cohérence avec les exigences de transparence de l'AI Act ?**

- A. Aucune documentation n'est nécessaire
- B. Indiquer le modèle utilisé, sa version, le prompt, la configuration, la date de génération et la revue humaine effectuée
- C. Ne documenter que les cas où l'IA a produit une erreur
- D. Laisser la documentation au fournisseur du modèle

<details><summary>Réponse</summary>

**B. Indiquer le modèle utilisé, sa version, le prompt, la configuration, la date de génération et la revue humaine effectuée**

Cette documentation minimale répond à trois objectifs : reproductibilité, conformité (AI Act, RGPD, ISO/IEC 42001) et auditabilité. Elle doit être proportionnée à la criticité du cas d'usage.

</details>

---

### Question 16
**Un agent de test piloté par LLM accède à un environnement qui, par mauvaise configuration, contient des données clients de production. Quel risque est maximisé ?**

- A. Un risque uniquement de performance
- B. Un cumul de risques : fuite de données confidentielles, non-conformité RGPD et potentielle exécution d'actions irréversibles en production
- C. Un risque esthétique dans les rapports
- D. Aucun risque particulier

<details><summary>Réponse</summary>

**B. Un cumul de risques : fuite de données confidentielles, non-conformité RGPD et potentielle exécution d'actions irréversibles en production**

Cloisonnement des environnements, principe du moindre privilège, anonymisation des jeux de test et validation humaine des actions destructives sont les barrières à mettre en place.

</details>

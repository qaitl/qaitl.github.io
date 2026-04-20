# Pour aller plus loin — Guide de références sur le prompt engineering

> **À qui s'adresse ce document ?** Aux testeurs qui ont parcouru [le module d'ingénierie du prompting](02-ingenierie-prompting.md) et souhaitent approfondir la discipline au-delà du syllabus ISTQB CT-GenAI. Ce guide recense les meilleures références publiques **actualisées 2024–2026** : articles scientifiques, guides de fournisseurs, cours, outils, communautés. Il est volontairement orienté *prompt engineering appliqué* — y compris aux tâches de test logiciel.

> **Note méthodologique.** Les liens ci-dessous pointent vers des ressources publiques. Les URLs et les versions citées peuvent évoluer ; vérifier la date de dernière mise à jour avant de s'y appuyer pour une décision opérationnelle. Les éléments **actualisés par rapport au syllabus ISTQB CT-GenAI v1.0 (juillet 2025)** sont explicitement signalés par un bloc *« Actualisation »*.

---

## 1. Les incontournables à lire en premier

Ces trois ressources couvrent à elles seules 80 % du terrain. À lire dans cet ordre si vous ne devez en garder que trois.

| Priorité | Ressource | Pourquoi la lire |
|---|---|---|
| 1 | **Anthropic — *Prompt engineering overview*** (docs.anthropic.com, section *Build with Claude › Prompt engineering*) | Guide canonique et concis, régulièrement mis à jour ; couvre structure, rôle, exemples, raisonnement, format XML, cache |
| 2 | **OpenAI — *Prompt engineering guide*** (platform.openai.com/docs/guides/prompt-engineering) | Pendant côté OpenAI ; aborde aussi les spécificités des modèles de raisonnement (o-series) |
| 3 | **Schulhoff et al., *The Prompt Report: A Systematic Survey of Prompting Techniques*** (2024, arXiv:2406.06608) | Le recensement académique le plus complet — plus de 50 techniques cataloguées et comparées |

> **Actualisation.** Les guides Anthropic et OpenAI ont été largement remaniés en 2024–2025 pour tenir compte des **modèles de raisonnement** (reasoning models) et du **prompt caching**. Les conseils classiques (*toujours ajouter beaucoup d'exemples few-shot*, *tout expliciter étape par étape*) doivent être lus à l'aune de cette évolution — voir section 6.

---

## 2. Guides officiels des principaux fournisseurs

Tous les fournisseurs publient désormais des guides détaillés. Les consulter est utile pour deux raisons : les pratiques varient légèrement selon le modèle, et ces guides sont mis à jour à chaque nouvelle version.

| Fournisseur | Ressource | Particularité utile au testeur |
|---|---|---|
| **Anthropic** | *Prompt engineering* + *Prompt generator* (console.anthropic.com) | Générateur interactif de prompts structurés ; conventions XML pour sections imbriquées |
| **OpenAI** | *Prompt engineering* + *Reasoning best practices* + *Cookbook* (github.com/openai/openai-cookbook) | Cookbook rempli d'exemples exécutables ; guide spécifique aux modèles `o1/o3/o4` |
| **Google** | *Prompting guide 101* (cloud.google.com/vertex-ai/docs) + *Gemini API prompting strategies* | Spécificités des fenêtres longues et du multimodal |
| **Mistral AI** | *Prompting capabilities* (docs.mistral.ai) | Recommandations pour les modèles open-weight auto-hébergés |
| **Meta** | *Prompt engineering with Llama* (llama.com/docs) | Particularités des modèles Llama 3.x / 4 |
| **Microsoft** | *Prompt engineering techniques* (learn.microsoft.com/azure/ai-services/openai) | Orientée déploiement en entreprise, sécurité et conformité |
| **DeepSeek** | *Prompt library* (api-docs.deepseek.com) | Exemples dédiés aux modèles de raisonnement R1 |

> **Conseil pratique.** Si vous utilisez plusieurs modèles, **maintenez un tableau de correspondance** de vos prompts : ce qui fonctionne en XML sur Claude n'est pas nécessairement optimal en JSON sur OpenAI, et les modèles de raisonnement n'aiment pas les consignes trop directives étape par étape.

---

## 3. Anthologies et recueils open source

Pour constituer rapidement une bibliothèque de prompts réutilisable en équipe de test :

- **Anthropic — *Prompt library*** (docs.anthropic.com/en/prompt-library) — prompts prêts à l'emploi classés par cas d'usage, dont plusieurs relèvent directement du test (génération de tests unitaires, revue de code, extraction d'informations).
- **OpenAI Cookbook** (github.com/openai/openai-cookbook) — notebooks Jupyter exécutables, dont plusieurs dédiés au *function calling* et à la structuration de sortie.
- **f/awesome-chatgpt-prompts** (github.com/f/awesome-chatgpt-prompts) — collection communautaire très populaire ; utile comme source d'inspiration, à filtrer avec recul.
- **dair-ai/Prompt-Engineering-Guide** (github.com/dair-ai/Prompt-Engineering-Guide) — un des guides open source les plus cités, structuré comme un manuel pédagogique.
- **anthropics/anthropic-cookbook** (github.com/anthropics/anthropic-cookbook) — exemples officiels côté Claude, dont des patterns agentiques.
- **Google Gemini API Cookbook** (github.com/google-gemini/cookbook) — notebooks officiels multimodaux.

---

## 4. Références académiques clés

Sélection des articles qui ont structuré la discipline. Tous disponibles sur arXiv.

### 4.1 Techniques fondatrices

- Brown et al., *Language Models are Few-Shot Learners* (GPT-3, 2020) — introduction du **few-shot prompting**.
- Wei et al., *Chain-of-Thought Prompting Elicits Reasoning in Large Language Models* (2022) — l'article qui a lancé le **chain-of-thought (CoT)**.
- Kojima et al., *Large Language Models are Zero-Shot Reasoners* (2022) — le célèbre *« Let's think step by step »*.
- Wang et al., *Self-Consistency Improves Chain of Thought Reasoning in Language Models* (2022) — échantillonner plusieurs raisonnements et voter.
- Yao et al., *ReAct: Synergizing Reasoning and Acting in Language Models* (2022) — couplage raisonnement + action (racine des agents).
- Yao et al., *Tree of Thoughts* (2023) — exploration arborescente des raisonnements.

### 4.2 Synthèses et méta-analyses

- **Schulhoff et al., *The Prompt Report: A Systematic Survey of Prompting Techniques*** (2024) — la synthèse de référence.
- Sahoo et al., *A Systematic Survey of Prompt Engineering in Large Language Models* (2024).
- Chen et al., *Unleashing the Potential of Prompt Engineering* (2024) — état de l'art orienté applications.

### 4.3 Tests logiciels et prompt engineering

- Wang et al., *Software Testing with Large Language Models: Survey, Landscape, and Vision* (2024, IEEE TSE) — cartographie des usages LLM tout au long du cycle de test.
- Schäfer et al., *An Empirical Evaluation of Using Large Language Models for Automated Unit Test Generation* (2023, IEEE TSE).
- Feldt et al., *Towards Autonomous Testing Agents via Conversational Large Language Models* (2023).
- Yuan et al., *No More Manual Tests? Evaluating and Improving ChatGPT for Unit Test Generation* (2024).

### 4.4 Qualité, évaluation, robustesse

- Liu et al., *Lost in the Middle: How Language Models Use Long Contexts* (2023) — limites d'exploitation des fenêtres longues.
- Sclar et al., *Quantifying Language Models' Sensitivity to Spurious Features in Prompt Design* (2024) — fragilité des prompts à la formulation.
- Anthropic, *Many-shot in-context learning* (2024) — usage avancé des très grandes fenêtres pour du few-shot massif.

> **Où suivre l'actualité académique ?**
> - **arXiv cs.CL** (cs.CL.new sur arxiv.org) — dépôts quotidiens.
> - **Papers with Code — *Prompt Engineering*** — classements et datasets associés.
> - **Hugging Face Daily Papers** (huggingface.co/papers) — curation communautaire.

---

## 5. Cours en ligne et formations

Sélection de cours reconnus, la plupart gratuits.

| Cours | Public | Ce qu'on y gagne |
|---|---|---|
| **DeepLearning.AI — *ChatGPT Prompt Engineering for Developers*** (Isa Fulford & Andrew Ng) | Développeurs, 1h30 | Bases solides avec notebooks exécutables |
| **DeepLearning.AI — *Prompt Engineering with Llama 2 / 3*** | Praticiens open source | Spécificités des modèles Meta |
| **DeepLearning.AI — *Reasoning with o1*** (avec OpenAI) | Utilisateurs de modèles de raisonnement | Changements de paradigme induits par les reasoning models |
| **DeepLearning.AI — *Building Agentic RAG with LlamaIndex*** | Architectes de solutions IA | RAG agentique en pratique |
| **Anthropic — *Prompt Engineering Interactive Tutorial*** (github.com/anthropics/prompt-eng-interactive-tutorial) | Tous niveaux | Tutoriel Jupyter officiel, très pédagogique |
| **Google Cloud Skills Boost — *Prompt Design in Vertex AI*** | Utilisateurs GCP | Vertex AI + Gemini |
| **Microsoft Learn — *Introduction to prompt engineering*** | Utilisateurs Azure | Azure OpenAI, gouvernance |
| **Coursera — *Generative AI for Software Development Specialization*** (DeepLearning.AI) | Développeurs et testeurs | Orientation dev + test |
| **Elements of AI / Building AI** (Université d'Helsinki) | Débutants | Fondements conceptuels |

---

## 6. Évolutions majeures 2024–2026 à connaître

Cette section signale les évolutions qui **nuancent ou dépassent** certaines recommandations du syllabus ISTQB CT-GenAI v1.0.

### 6.1 Les modèles de raisonnement changent la donne

Les modèles de raisonnement (**OpenAI o1/o3/o4**, **Claude 3.7+ *extended thinking***, **Claude 4.x**, **Gemini 2.5 Pro thinking**, **DeepSeek-R1**, **Qwen3 reasoning**, **Mistral Magistral**) effectuent une **chaîne de pensée interne** avant de répondre. Conséquences pratiques :

| Pratique classique (pré-2024) | Avec un modèle de raisonnement |
|---|---|
| Ajouter *« Réfléchis étape par étape »* | **Redondant, parfois contre-productif** — le modèle raisonne déjà |
| Détailler le processus souhaité dans le prompt | **Préférer** exprimer *l'objectif* et les *contraintes* ; laisser le modèle planifier |
| Enchaîner manuellement plusieurs prompts | **Moins nécessaire** sur des tâches internes au modèle ; reste utile pour la vérification humaine intermédiaire |
| Peu ou pas d'exemples | Parfois **mieux sans exemples** (les exemples biaisent le raisonnement) |

> **Référence recommandée.** OpenAI, *Reasoning best practices* (platform.openai.com/docs/guides/reasoning-best-practices) — section explicite sur ce qu'il faut **cesser de faire** par rapport aux modèles d'instruction.

### 6.2 Le *prompt caching* est devenu central

Tous les grands fournisseurs proposent désormais une mise en cache des préfixes de prompt. Cela change la façon de structurer les prompts longs :

- **Anthropic prompt caching** — cache explicite via paramètre `cache_control`.
- **OpenAI automatic prompt caching** — activé automatiquement pour les prompts longs.
- **Google context caching** — cache explicite côté Gemini.
- **DeepSeek context caching** — disponible sur l'API.

**Implication pour le testeur** — placer les **parties invariantes** (rôle, contexte métier, exemples few-shot, documentation de référence) **en tête de prompt**, et les parties variables **en queue**. Le coût et la latence chutent drastiquement sur les campagnes répétitives.

### 6.3 Le *structured output* remplace souvent le few-shot format

Plutôt que de forcer un format de sortie par des exemples, les fournisseurs supportent désormais des **sorties strictement structurées** via JSON Schema :
- **OpenAI Structured Outputs** (réponse contrainte à un schéma).
- **Anthropic tool use** avec schémas stricts.
- **Gemini controlled generation / JSON mode**.
- **Outlines**, **Instructor**, **LMQL** côté open source.

**Pour le testeur** — le *few-shot* reste utile pour guider le **contenu** et le **style**, mais il n'est plus indispensable pour imposer la **forme**. Les pipelines de génération de cas de test gagnent en robustesse avec des schémas validés côté code plutôt qu'un prompt chargé d'exemples de format.

### 6.4 Le *tool use* et les agents

Le *function calling / tool use* est devenu standard. Les patterns d'agents reposent presque toujours dessus. Références :
- Anthropic, *Building effective agents* (2024) — guide de patterns (augmented LLM, workflow, agent).
- OpenAI, *Agents SDK* + *Assistants API* — frameworks officiels.
- **Model Context Protocol (MCP)** ([modelcontextprotocol.io](https://modelcontextprotocol.io)) — protocole standard adopté par Anthropic, OpenAI, Google pour connecter des outils aux agents ; devenu le REST des agents IA en 2025.

### 6.5 Le *in-context learning* à très grande échelle

Avec des fenêtres de **1 à 2 millions de tokens** (Gemini 2.5 Pro, Claude Sonnet 1M), on peut désormais injecter la **documentation complète d'un produit** dans le prompt, rendant parfois le RAG superflu pour des bases de taille moyenne. Anthropic parle de ***many-shot in-context learning*** — on peut passer de 3–5 exemples à plusieurs centaines, avec des gains mesurables.

**Attention** : la qualité décroît au milieu du contexte (*lost in the middle*, Liu et al. 2023). Placer les informations critiques en début **ou** en fin.

---

## 7. Techniques de prompting au-delà du syllabus

Le syllabus couvre trois techniques principales (enchaînement, few-shot, méta-prompting). Voici les autres techniques qui complètent utilement la boîte à outils d'un testeur.

| Technique | Principe | Quand l'utiliser en test |
|---|---|---|
| **Zero-shot CoT** (Kojima, 2022) | Ajouter *« Let's think step by step »* | Sur modèles non-raisonnement, pour les tâches à plusieurs étapes |
| **Self-consistency** (Wang, 2022) | Générer N réponses avec température > 0 et voter | Décisions critiques, priorisation de défauts |
| **Tree-of-Thoughts** (Yao, 2023) | Exploration arborescente avec backtracking | Conception de stratégies de test complexes |
| **ReAct** (Yao, 2022) | Alterner *Think* et *Act* (appels d'outils) | Agents de test autonomes |
| **Reflexion** (Shinn, 2023) | Le modèle critique ses propres sorties et réessaie | Revue automatique de cas de test générés |
| **Least-to-Most** (Zhou, 2022) | Décomposer progressivement du plus simple au plus complexe | Analyse d'exigences ambiguës |
| **Plan-and-Solve** (Wang, 2023) | Planifier avant d'exécuter | Génération de suites de tests structurées |
| **Constitutional AI prompting** (Bai, 2022) | Contraindre par un ensemble de règles | Politique interne de rédaction de cas de test |
| **Role prompting structuré** | Personas multiples pour simuler plusieurs perspectives | Revue croisée d'un même cas de test |
| **Step-Back Prompting** (Zheng, 2023) | Demander d'abord les principes puis l'application | Générer des règles de priorisation |
| **Analogical Prompting** (Yasunaga, 2023) | Le LLM génère ses propres exemples pertinents | Tâches sans exemples disponibles |

**Le *Prompt Report* (Schulhoff et al., 2024)** catalogue plus de 50 techniques supplémentaires — c'est la référence de tête pour explorer systématiquement cet espace.

---

## 8. Outils de prompt engineering

### 8.1 Conception et gestion de prompts

- **Anthropic Workbench** (console.anthropic.com/workbench) — édition, test, amélioration assistée, conversion entre modèles.
- **OpenAI Playground** — expérimentation fine avec tous les hyperparamètres.
- **Google AI Studio** — accès rapide à Gemini pour prototyper.
- **PromptLayer, Helicone, Langfuse, LangSmith** — plateformes d'observabilité et de versioning de prompts ; indispensables en équipe.
- **Promptfoo** (promptfoo.dev) — framework open source d'évaluation et de tests A/B de prompts, avec intégration CI. **Particulièrement pertinent pour le testeur** : il permet d'appliquer une démarche de test aux prompts eux-mêmes.
- **Inspect AI** (UK AI Safety Institute) — framework d'évaluation de modèles.

### 8.2 Évaluation automatique

- **Promptfoo** (voir ci-dessus) — assertions, comparaisons multi-modèles, pipelines CI.
- **DeepEval** (github.com/confident-ai/deepeval) — suite de tests pour LLMs, style pytest.
- **Ragas** — évaluation spécifique RAG.
- **OpenAI Evals** (github.com/openai/evals) — framework d'évaluation open source.
- **LM Eval Harness** (EleutherAI) — référence académique.
- **LLM-as-a-judge** — pattern consistant à utiliser un modèle puissant pour noter les sorties d'un autre modèle ; à utiliser avec précaution (biais connus du juge).

### 8.3 Génération et validation structurée

- **Outlines** (github.com/dottxt-ai/outlines) — génération contrainte par grammaire.
- **Instructor** (github.com/jxnl/instructor) — Pydantic pour LLMs.
- **Guidance** (github.com/guidance-ai/guidance) — contrôle fin de la génération.
- **LMQL** (lmql.ai) — langage de requête pour LLMs.

### 8.4 Orchestration (agents et RAG)

- **LangChain / LangGraph** — framework d'orchestration le plus utilisé.
- **LlamaIndex** — orienté RAG avancé.
- **Haystack** — alternative orientée recherche.
- **DSPy** (github.com/stanfordnlp/dspy) — approche *programming — not prompting* : on décrit le comportement et le framework optimise les prompts automatiquement. Très intéressant pour les pipelines de test reproductibles.
- **Claude Agent SDK** — framework officiel Anthropic pour construire des agents outillés.
- **OpenAI Agents SDK** — équivalent côté OpenAI.

---

## 9. Prompt engineering appliqué aux tâches de test logiciel

Sélection de ressources ciblant explicitement l'intersection **prompt engineering × test logiciel**.

### 9.1 Articles et études

- Wang et al., *Software Testing with Large Language Models: Survey, Landscape, and Vision* (IEEE TSE, 2024) — cartographie complète.
- Schäfer et al., *An Empirical Evaluation of Using Large Language Models for Automated Unit Test Generation* (IEEE TSE, 2023).
- Yuan et al., *No More Manual Tests? Evaluating and Improving ChatGPT for Unit Test Generation* (2024).
- Google Research, *Using LLMs to generate fuzz targets* (2023–2024) — génération de fuzzers par LLM (OSS-Fuzz).
- Microsoft, *LLM-powered Testing Agents* — études internes partagées sur le blog Microsoft Research.

### 9.2 Communautés et veille

- **Ministry of Testing** (ministryoftesting.com) — nombreux articles sur IA + test ; track *AI in Testing* à la conférence TestBash.
- **EuroSTAR Huddle** (huddle.eurostarsoftwaretesting.com) — articles et webinars.
- **ISTQB.org — CT-GenAI resources** — supports officiels.
- **Comité français des tests logiciels (CFTL)** — groupes de travail et événements francophones.
- **Simon Willison's Weblog** (simonwillison.net) — veille quotidienne incontournable, avec beaucoup d'exemples réutilisables.
- **Latent Space** (podcast + newsletter) — technique, bien documenté.
- **The Batch** (DeepLearning.AI) — newsletter hebdomadaire synthétique.

### 9.3 Conférences utiles

- **EuroSTAR**, **STAREAST / STARWEST**, **Agile Testing Days** — pistes dédiées IA en test depuis 2023.
- **TestBash** (en ligne et régional).
- **ICST — IEEE International Conference on Software Testing, Verification and Validation** — volet académique.
- **ICSE**, **FSE**, **ASE** — conférences génie logiciel, de plus en plus de papers sur LLM + test.

---

## 10. Recommandations de parcours

Selon votre profil, voici un parcours de lecture suggéré :

### 10.1 Testeur qui débute avec l'IA générative
1. [Chapitre 1 — Introduction](../01-fondements/01-introduction-ia-generative.md) et son [pour en savoir plus](../01-fondements/01-introduction-ia-generative-pour-en-savoir-plus.md).
2. [Chapitre 2 — Ingénierie du prompting](02-ingenierie-prompting.md).
3. Tutoriel interactif Anthropic (`anthropics/prompt-eng-interactive-tutorial`).
4. Cours DeepLearning.AI *ChatGPT Prompt Engineering for Developers*.
5. Expérimentation libre avec **Promptfoo** sur un cas simple (ex. : génération de cas de test pour une calculatrice).

### 10.2 Testeur expérimenté qui veut industrialiser
1. Guides officiels Anthropic + OpenAI (sections *Prompt engineering* et *Reasoning best practices*).
2. *The Prompt Report* (Schulhoff, 2024) — en lecture sélective.
3. **Promptfoo** intégré à un pipeline CI sur un corpus réel de prompts de test.
4. Anthropic *Building effective agents* pour les flux multi-étapes.
5. Étude de cas DSPy si vous cherchez une approche *compilée* des prompts.

### 10.3 Lead Test / architecte qualité
1. Le *Prompt Report* — vision d'ensemble du champ.
2. Guide Microsoft *Prompt engineering techniques* pour la gouvernance en entreprise.
3. Anthropic *Building effective agents* + Model Context Protocol.
4. Tour d'horizon des plateformes d'observabilité (PromptLayer, LangSmith, Helicone, Langfuse).
5. Synchronisation avec le [chapitre 3 — gestion des risques](../03-gerer-risques/).

---

## 11. Une règle générale pour rester à jour

Le domaine évolue **mensuellement**. Pour ne pas se noyer :

1. **Trois sources de veille continue suffisent** — par exemple : Simon Willison's Weblog (quotidien), The Batch (hebdomadaire), et un guide officiel fournisseur de votre choix.
2. **Tester avant d'adopter** — une technique vantée dans un papier n'est pas toujours reproductible sur votre cas. Promptfoo ou DeepEval permettent de vérifier en quelques minutes.
3. **Archiver ce qui marche** — au niveau équipe, constituer une bibliothèque de prompts versionnés, avec leurs métriques et le modèle associé. C'est un actif qui se construit dans la durée.
4. **Se tenir à distance des effets de mode** — la littérature grise produit beaucoup de techniques spectaculaires sans évaluation rigoureuse. Les méta-analyses (Schulhoff, 2024) restent la meilleure boussole.

---

## Suite du parcours

- **Chapitre précédent** — [Fondements de l'IA générative](../01-fondements/).
- **Contenu principal** — [Ingénierie du prompting pour des tests logiciels efficaces](02-ingenierie-prompting.md).
- **Chapitre suivant** — [Gérer les risques liés à l'IA générative dans les tests logiciels](../03-gerer-risques/).

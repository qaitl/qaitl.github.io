# Pour en savoir plus — Fondements techniques de l'IA générative

> **À qui s'adresse ce document ?** Aux lecteurs qui ont parcouru [l'introduction](01-introduction-ia-generative.md) et souhaitent approfondir les concepts techniques sous-jacents aux LLMs, dans l'esprit du référentiel ISTQB CT-GenAI (chapitre 1). L'objectif est de donner au testeur les clés pour dialoguer avec les data-scientists, lire une documentation technique de modèle et comprendre les arbitrages qui influencent la qualité et le coût d'une tâche de test assistée par IA.

> **Note sur la source.** Ce document s'appuie sur le contenu brut du chapitre 1 du syllabus ISTQB CT-GenAI (fichier `chapter1_raw.txt`, version v1.0FR du 25/07/2025) et le complète par des **actualisations 2024–2026** explicitement signalées, ainsi que par des **références externes** pour aller plus loin. Les termes de test suivent la terminologie ISTQB française, avec la traduction officielle en anglais entre parenthèses.

---

## 1. Panorama de l'IA — précisions sur les quatre paradigmes

Le syllabus distingue quatre grandes approches. Voici comment les situer les unes par rapport aux autres, avec leurs implications pour le test logiciel.

| Paradigme | Principe | Exemple historique | Usage résiduel aujourd'hui |
|---|---|---|---|
| **IA symbolique** | Règles logiques explicitées par un expert humain | Systèmes experts médicaux des années 1980, Prolog | Moteurs de règles métier, solveurs SAT, vérification formelle |
| **Machine learning classique** | Apprentissage statistique à partir de features sélectionnées par un humain | Filtres anti-spam, régression logistique, arbres de décision | Catégorisation des défauts (défaut / defect), prédiction de tests à rejouer |
| **Deep learning** | Réseaux de neurones multicouches qui apprennent eux-mêmes les features | Reconnaissance d'image (ImageNet 2012), reconnaissance vocale | Analyse d'images de test, détection visuelle d'anomalies |
| **IA générative** | Deep learning pré-entraîné capable de produire du contenu nouveau | Transformer (2017), GPT, LLaMA, Claude, Gemini, Mistral | Génération de cas de test (cas de test / test case), de données de test (données de test / test data), de documentation |

> **Point ISTQB.** Le principal avantage de l'IA générative pour les tests est l'usage de **modèles pré-entraînés applicables immédiatement** sans phase d'entraînement supplémentaire. La contrepartie — biais, hallucinations, non-déterminisme — est traitée au chapitre 3.

**Pour aller plus loin :**
- Russell & Norvig, *Artificial Intelligence: A Modern Approach* (4e éd., 2020) — manuel de référence couvrant les quatre paradigmes.
- Sutton, *The Bitter Lesson* (2019) — essai classique sur la montée en puissance des approches par apprentissage.

---

## 2. L'architecture Transformer

### 2.1 Pourquoi le Transformer a tout changé

Avant 2017, les modèles de langage dominants étaient des réseaux récurrents (RNN, LSTM). Ils lisaient le texte token par token, ce qui limitait la parallélisation et la capacité à modéliser des dépendances longues.

L'article fondateur **« Attention Is All You Need »** (Vaswani et al., 2017) a introduit le **Transformer**, qui repose sur un mécanisme appelé **self-attention** : chaque token peut « regarder » l'ensemble des autres tokens de la séquence simultanément et pondérer leur importance. Cette parallélisation a rendu possible l'entraînement sur des ensembles de données massifs.

### 2.2 Composants clés d'un Transformer

| Composant | Rôle | Métaphore pour un testeur |
|---|---|---|
| **Tokenizer** | Découpe l'entrée textuelle en tokens (ex. : BPE, SentencePiece, tiktoken) | Analogue au parseur lexical d'un compilateur |
| **Embeddings** | Transforme chaque token en un vecteur dense de plusieurs centaines ou milliers de dimensions | Analogue à un hash sémantique qui place les mots proches dans l'espace |
| **Positional encoding** | Injecte l'information d'ordre des tokens (sinon, « chien mord homme » = « homme mord chien ») | Sans cela, la séquence est un simple sac de mots |
| **Blocs d'attention multi-têtes** | Calcul de relations pondérées entre tous les tokens | Plusieurs « lecteurs » en parallèle qui focalisent sur différents aspects |
| **Feed-forward** | Transformations non linéaires couche par couche | Où s'accumule une grande partie des connaissances du modèle |
| **Unembedding / head** | Conversion finale vers une distribution de probabilités sur le vocabulaire | Table de correspondance inverse vers les tokens |

> **Décodeur autorégressif.** Les LLMs de type GPT sont des Transformers *decoder-only* : à chaque étape, le modèle prédit le token suivant à partir de tous les tokens précédents, puis ce token est ré-injecté en entrée. C'est la boucle autorégressive qui produit le texte.

**Actualisation (2024–2026).** L'architecture Transformer reste dominante, mais plusieurs variantes ont émergé :
- **Mixture-of-Experts (MoE)** — seule une fraction des paramètres est activée par token (Mixtral, DeepSeek-V3, GPT-4 selon les fuites publiques). Cela permet des modèles à plusieurs centaines de milliards de paramètres avec un coût d'inférence réduit.
- **State-Space Models (Mamba)** — alternative au Transformer visant une complexité linéaire au lieu de quadratique. Encore expérimental en production.
- **Attention efficace** (FlashAttention, paged attention) — optimisations qui ne changent pas l'architecture mais réduisent mémoire et latence.

**Pour aller plus loin :**
- Vaswani et al., *Attention Is All You Need*, NeurIPS 2017 — l'article fondateur.
- Jay Alammar, *The Illustrated Transformer* — vulgarisation visuelle de référence.
- Andrej Karpathy, *Let's build GPT: from scratch, in code, spelled out* (YouTube) — construction d'un mini-GPT étape par étape.

---

## 3. Tokenisation et embeddings

### 3.1 La tokenisation, étape invisible mais fondamentale

La **tokenisation** (tokenisation / tokenization) est la conversion du texte en unités traitables par le modèle. Trois familles coexistent :

| Type | Unité | Exemple pour « tester » | Avantage | Limite |
|---|---|---|---|---|
| **Par caractère** | Lettre ou caractère Unicode | `t`, `e`, `s`, `t`, `e`, `r` | Vocabulaire très petit | Séquences très longues, peu efficace |
| **Par mot** | Mot complet | `tester` | Intuitif | Explosion du vocabulaire, problème des mots inconnus |
| **Par sous-mot** (BPE, WordPiece, SentencePiece) | Fragments fréquents | `test` + `er` | Compromis efficace | Découpage non intuitif, influencé par la langue |

La quasi-totalité des LLMs actuels utilisent une **tokenisation par sous-mot**. C'est pour cela que les LLMs échouent sur les tâches caractère par caractère (*« compte les t dans cette phrase »*, voir [activité 5 de l'introduction](01-introduction-ia-generative.md#activité-5--les-angles-morts-du-llm)) : ils n'ont littéralement pas accès aux caractères individuels.

> **Conséquences concrètes pour le testeur :**
> - Le **français est souvent plus coûteux en tokens que l'anglais** (environ 1,3 à 1,5× plus de tokens pour la même information), car les tokenizers sont entraînés majoritairement sur de l'anglais.
> - Un prompt qui contient **du code source** consomme souvent moins de tokens que le même volume en texte naturel.
> - Les **identifiants non latins** (hangeul coréen, arabe, cyrillique) sont fréquemment tokenisés caractère par caractère, ce qui augmente fortement le coût.

**Outils pratiques :**
- **OpenAI tiktoken** ([github.com/openai/tiktoken](https://github.com/openai/tiktoken)) — tokenizer de référence pour GPT-3.5 / GPT-4 / GPT-4o.
- **OpenAI Tokenizer playground** ([platform.openai.com/tokenizer](https://platform.openai.com/tokenizer)) — visualisation en ligne.
- **Hugging Face Tokenizers** ([github.com/huggingface/tokenizers](https://github.com/huggingface/tokenizers)) — supporte BPE, WordPiece, SentencePiece.
- **Anthropic token counting API** — compteur officiel pour les modèles Claude.

### 3.2 Les embeddings

Un **embedding** (embedding) est la représentation vectorielle d'un token (ou d'un passage complet) dans un espace à grande dimension — typiquement 768, 1536 ou 3072 dimensions.

La propriété clé : **les tokens ou passages sémantiquement proches ont des vecteurs proches** (au sens de la similarité cosinus, le plus souvent). Cette géométrie permet :
- La **recherche sémantique** dans une base documentaire ;
- Le **grounding** via RAG (Retrieval-Augmented Generation / génération augmentée par récupération) — voir section 6 ci-dessous ;
- Le **clustering** automatique de défauts similaires, de tickets, de cas de test redondants.

**Modèles d'embeddings récents (2024–2026) :**
- `text-embedding-3-large` (OpenAI) — 3072 dimensions.
- `voyage-3-large` (Voyage AI) — très performant sur la recherche.
- `bge-m3` et `gte-multilingual` (BAAI, Alibaba) — open source multilingues.
- `embed-v3` (Cohere).

**Pour aller plus loin :**
- Mikolov et al., *Word2Vec* (2013) — origine historique des embeddings modernes.
- Reimers & Gurevych, *Sentence-BERT* (2019) — embeddings au niveau phrase.
- MTEB Leaderboard ([huggingface.co/spaces/mteb/leaderboard](https://huggingface.co/spaces/mteb/leaderboard)) — classement actualisé des modèles d'embeddings.

---

## 4. Fenêtre contextuelle, hyperparamètres et non-déterminisme

### 4.1 Fenêtre contextuelle (context window)

La **fenêtre contextuelle** (fenêtre contextuelle / context window) est le nombre maximal de tokens que le modèle peut prendre en compte simultanément (entrée + sortie dans la plupart des cas).

| Génération | Fenêtre typique | Usage réaliste |
|---|---|---|
| GPT-3 (2020) | 2 048 tokens | Quelques pages |
| GPT-4 (2023) | 8 k / 32 k | Chapitre court |
| Claude 2 (2023) | 100 k | Livre court |
| **Claude 3.5 / 3.7 Sonnet, GPT-4o, Gemini 1.5 Pro** (2024) | **128 k – 1 M** | Bases de code entières, spécifications complètes |
| **Gemini 2.5 Pro** (2025) | **2 M** | Corpus documentaires |

> **Attention.** Une grande fenêtre contextuelle ne signifie pas que le modèle exploite aussi bien tous les tokens. Les études dites *« lost in the middle »* (Liu et al., 2023) montrent que les informations situées au milieu d'un long contexte sont moins bien restituées que celles aux extrémités. Pour une tâche de test critique, mieux vaut un contexte court et ciblé qu'un contexte massif mal structuré.

**Implication économique.** Le coût d'inférence est approximativement linéaire dans le nombre de tokens d'entrée et de sortie. Un prompt de 100 k tokens coûte 100 fois plus qu'un prompt de 1 k tokens — y compris au niveau énergétique (voir chapitre 3).

### 4.2 Les principaux hyperparamètres d'inférence

Le comportement d'un LLM au moment de la génération est pilotable par quelques hyperparamètres. Le syllabus y fait référence au travers du **comportement non déterministe** ; voici les leviers concrets.

| Hyperparamètre | Rôle | Valeur typique en test logiciel |
|---|---|---|
| **Temperature** | Contrôle l'aléatoire de l'échantillonnage (0 = plus déterministe, 1+ = plus créatif) | 0 ou 0.1 pour des tâches reproductibles, 0.7 pour de la génération créative |
| **Top-p** (nucleus sampling) | Restreint l'échantillonnage aux tokens cumulant une probabilité p | 0.9 – 0.95 par défaut |
| **Top-k** | Restreint aux k tokens les plus probables | 40 typiquement |
| **Max tokens / max output** | Limite la longueur de la sortie | À ajuster selon la tâche |
| **Seed** (quand supporté) | Rend l'échantillonnage reproductible | À figer pour les tests reproductibles |
| **Stop sequences** | Chaînes qui arrêtent la génération | Utile pour les formats structurés |

> **Attention au non-déterminisme résiduel.** Même avec `temperature=0` et un `seed` fixé, la reproductibilité stricte n'est **pas garantie** par la plupart des fournisseurs : les calculs sur GPU ne sont pas toujours bit-à-bit reproductibles, et une mise à jour silencieuse du modèle côté fournisseur peut changer les sorties. Pour une campagne de test critique, il faut systématiquement **versionner** : identifiant de modèle, date, température, seed, prompt, et évaluer sur plusieurs runs.

**Pour aller plus loin :**
- Liu et al., *Lost in the Middle: How Language Models Use Long Contexts* (2023).
- Holtzman et al., *The Curious Case of Neural Text Degeneration* (2019) — article fondateur sur le nucleus sampling.

---

## 5. LLM de fondation, adapté aux instructions, de raisonnement

Le syllabus distingue **trois catégories**. Elles correspondent à des étapes successives d'un même pipeline d'entraînement.

### 5.1 LLM de fondation (foundation model)

Le modèle de fondation est entraîné par **pré-entraînement auto-supervisé** sur un corpus massif (web, livres, code). L'objectif d'apprentissage est simple : prédire le token suivant.

**Caractéristiques :**
- Puissant et polyvalent, mais **brut** : il répond souvent à côté, continue le texte au lieu de répondre à l'instruction, ou reproduit des biais du corpus.
- Rarement exposé directement au grand public — c'est la base sur laquelle on construit les autres variantes.

**Exemples publics :** `Llama 3 base`, `Mistral 7B base`, `Qwen 2.5 base`.

### 5.2 LLM adapté aux instructions (instruction-tuned LLM)

À partir du modèle de fondation, on effectue un **alignement** en deux étapes typiques :

1. **Fine-tuning supervisé (SFT)** — sur des paires (instruction, réponse de qualité) annotées par des humains.
2. **Apprentissage par renforcement depuis les retours humains (RLHF)** — ou variantes plus récentes (DPO, RLAIF).

Résultat : un modèle qui **suit les instructions**, adopte un ton approprié et respecte mieux les consignes de sécurité.

**Exemples :** `GPT-4o`, `Claude 3.5 Sonnet`, `Gemini 1.5 Pro`, `Llama 3 Instruct`, `Mistral Large`.

C'est le type de LLM utilisé par défaut pour la plupart des tâches de test logiciel courantes.

### 5.3 LLM de raisonnement (reasoning LLM)

Les modèles de raisonnement étendent l'adaptation aux instructions par un entraînement dédié au **raisonnement en chaîne** (*chain-of-thought*) et à la **résolution multi-étapes**. Avant de répondre, le modèle produit une trace de raisonnement interne — parfois visible, parfois masquée.

**Caractéristiques :**
- Plus lents et plus coûteux par requête (le raisonnement consomme beaucoup de tokens).
- Significativement meilleurs sur la logique, les mathématiques, le code complexe, la décomposition de problèmes.
- Moins sensibles aux erreurs de raisonnement, **mais toujours sujets aux hallucinations factuelles** (voir chapitre 3).

**Actualisation (2024–2026).** La catégorie a explosé depuis fin 2024 :
- **OpenAI o1 (déc. 2024), o3 (2025), o4** — série dédiée au raisonnement.
- **Claude 3.7 Sonnet** (Anthropic, 2025) — *extended thinking* activable à la demande ; **Claude 4.x** a poursuivi cette direction.
- **Gemini 2.5 Pro** (Google, 2025) — *thinking* natif.
- **DeepSeek-R1** (jan. 2025) — premier modèle de raisonnement open-weight compétitif.
- **Qwen3 Reasoning**, **Mistral Magistral** — alternatives open source.

> **Recommandation pratique.** Pour une tâche de test :
> - **Rédaction, génération de cas de test courants, reformulation** → LLM adapté aux instructions (plus rapide, moins cher).
> - **Analyse de couverture complexe, débogage multi-étapes, refactoring logique** → LLM de raisonnement.
> - Dans un enchaînement de prompts (voir [chapitre 2](../02-ingenierie-prompting/)), on peut réserver le modèle de raisonnement aux étapes qui en tirent le plus de valeur.

### 5.4 Et les petits modèles de langage (SLM) ?

Les **Small Language Models** (SLM / small language model) sont des modèles compacts (typiquement de 1 à 10 milliards de paramètres) qui offrent une bonne qualité pour des tâches ciblées.

**Exemples récents :** `Phi-4` (Microsoft), `Gemma 2 / 3` (Google), `Llama 3.2 1B/3B`, `Mistral Small`, `Qwen 2.5 1.5B/3B`, `Claude Haiku`.

**Intérêt pour le testeur :**
- **Coût et latence réduits** pour des tâches récurrentes (catégorisation de défauts, reformulation rapide).
- **Déploiement local ou on-device** possible — utile pour les données confidentielles (voir chapitre 3).
- **Empreinte énergétique** bien moindre.

**Pour aller plus loin :**
- Ouyang et al., *Training language models to follow instructions with human feedback* (2022) — article RLHF fondateur.
- OpenAI, *Introducing OpenAI o1* (2024) — article introduisant les modèles de raisonnement.
- DeepSeek-AI, *DeepSeek-R1: Incentivizing Reasoning Capability in LLMs via Reinforcement Learning* (2025) — première recette publique détaillée.

---

## 6. LLM multimodaux et modèles de vision

### 6.1 Comment la multimodalité fonctionne-t-elle ?

Le syllabus indique que la **tokenisation est adaptée à chaque modalité**. Concrètement :

| Modalité | Transformation en tokens |
|---|---|
| **Texte** | Tokenizer sous-mot classique (BPE, SentencePiece) |
| **Image** | Découpage en patchs (typiquement 14×14 pixels), chaque patch est transformé en vecteur par un encodeur de vision (*Vision Transformer / ViT*) |
| **Audio** | Transformation en spectrogramme puis en tokens audio (ex. : codec Whisper, EnCodec, SoundStream) |
| **Vidéo** | Combinaison : patchs spatiaux + information temporelle |

Tous ces tokens sont projetés dans l'**espace d'embeddings commun** du Transformer, qui peut alors raisonner uniformément sur texte, image, audio.

### 6.2 Modèles multimodaux de référence (2024–2026)

| Modèle | Entrées | Sorties | Cas d'usage test |
|---|---|---|---|
| **GPT-4o** (OpenAI) | Texte, image, audio | Texte, audio | Analyse de captures, revue d'IHM, transcription de réunions |
| **Claude 3.5 / 3.7 / 4.x Sonnet** (Anthropic) | Texte, image, PDF | Texte | Revue visuelle d'IHM, extraction depuis screenshots, analyse de diagrammes |
| **Gemini 2.5 Pro** (Google) | Texte, image, audio, vidéo | Texte | Analyse de vidéos de reproduction de bugs, tests multimodaux |
| **Llama 3.2 Vision / Llama 4** (Meta) | Texte, image | Texte | Multimodal open source auto-hébergeable |
| **Qwen2-VL, Qwen3-VL** (Alibaba) | Texte, image, vidéo | Texte | Alternative open source, bon multilingue |
| **Pixtral** (Mistral) | Texte, image | Texte | Alternative européenne |

### 6.3 Applications concrètes au test logiciel

Au-delà des exemples de l'introduction, la multimodalité débloque plusieurs cas d'usage avancés :

- **Oracle visuel d'automatisation** — fournir une capture et une maquette et demander au LLM de valider la conformité visuelle, au lieu d'un diff pixel strict souvent trop fragile.
- **Localisateurs robustes** — demander au LLM de générer un sélecteur CSS/XPath à partir d'une description visuelle plutôt que d'une structure DOM volatile.
- **Analyse de rapports de défauts enrichis** — extraire automatiquement des informations à partir de captures jointes (message d'erreur, élément fautif, ligne problématique).
- **Audit d'accessibilité visuelle** — première analyse des problèmes de contraste, de taille de police, d'ordre de lecture.
- **Retranscription de notes manuscrites** — photos de tableau blanc lors de sessions d'example mapping (example mapping / example mapping).

> **Limite importante.** Les modèles multimodaux **hallucinent aussi sur l'image** : ils peuvent inventer un bouton absent, mal lire un chiffre, ou confondre deux éléments voisins. La revue humaine reste indispensable pour tout livrable qui dépend d'une lecture fidèle.

**Pour aller plus loin :**
- Dosovitskiy et al., *An Image Is Worth 16x16 Words: Transformers for Image Recognition at Scale* (2020) — introduction des Vision Transformers.
- Alayrac et al., *Flamingo: a Visual Language Model for Few-Shot Learning* (2022) — modèle vision-langage de référence.
- OpenAI, *GPT-4o System Card* (2024).

---

## 7. Deux patterns qui prolongent le syllabus : RAG et agents

Ces deux patterns ne sont pas explicitement détaillés au chapitre 1 du syllabus, mais ils sont devenus incontournables dans l'application industrielle de l'IA générative au test. Ils prolongent les deux **modalités d'interaction** mentionnées dans le syllabus (chatbots IA et applications basées sur LLM).

### 7.1 Retrieval-Augmented Generation (RAG)

Un système RAG associe un LLM à une base documentaire recherchée par embeddings (voir section 3.2). Le déroulement :

1. La requête de l'utilisateur est convertie en embedding.
2. Les passages les plus proches dans la base (spécifications, tickets, cas de test existants) sont récupérés.
3. Ces passages sont injectés dans le prompt comme contexte.
4. Le LLM répond en s'appuyant sur le contexte récupéré.

**Intérêt pour le testeur :**
- **Ancrage (grounding)** sur des sources autoritatives — réduit les hallucinations (voir chapitre 3).
- **Mise à jour sans réentraînement** — il suffit d'ajouter un document dans la base.
- **Traçabilité** — on peut citer la source exacte pour chaque affirmation.

**Briques techniques courantes (2024–2026) :**
- Stockage vectoriel : **pgvector** (PostgreSQL), **Qdrant**, **Weaviate**, **Milvus**, **Elasticsearch vector**.
- Orchestration : **LangChain**, **LlamaIndex**, **Haystack**.
- Modèles d'embeddings : voir section 3.2.

### 7.2 Agents IA (AI agents)

Un agent IA combine un LLM avec un ensemble d'**outils** (tool calling) qu'il peut appeler dans une boucle de raisonnement.

**Boucle typique :**
1. Le LLM reçoit une tâche.
2. Il choisit un outil (ex. : exécuter une requête SQL, piloter un navigateur, appeler une API Jira).
3. Il analyse le résultat.
4. Il continue jusqu'à l'achèvement ou un échec.

**Exemples côté test :**
- **GitHub Copilot Workspace / Coding Agent** — tâche de développement et de test de bout en bout.
- **Cursor Agent / Composer** — agent dans l'éditeur qui peut modifier plusieurs fichiers et exécuter des tests.
- **Devin** (Cognition) — agent orienté ingénierie logicielle.
- **Claude Agent SDK / Claude Code** — framework pour construire des agents outillés autour de Claude.
- **Playwright MCP** — exposition d'un navigateur Playwright à un agent via le protocole Model Context Protocol (MCP).

> **Actualisation (2024–2026).** Le **Model Context Protocol (MCP)**, introduit par Anthropic en novembre 2024 et adopté depuis par OpenAI et Google, est devenu le standard de facto pour connecter des agents à des outils, des données et des systèmes externes. Il est aux agents ce que REST a été aux APIs — un protocole d'intégration uniforme. Référence : [modelcontextprotocol.io](https://modelcontextprotocol.io).

**Implications pour le test :**
- Les agents peuvent exécuter des **actions irréversibles** — d'où un besoin accru de *guardrails*, de validations humaines et de journalisation.
- Ils amplifient les risques OWASP LLM (voir [chapitre 3](../03-gerer-risques/)) : *excessive agency* (`LLM06`), *improper output handling* (`LLM05`), *prompt injection* (`LLM01`) via les données qu'ils lisent.

**Pour aller plus loin :**
- Lewis et al., *Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks* (2020) — article fondateur.
- Anthropic, *Building effective agents* (2024) — guide de patterns de conception d'agents.
- Yao et al., *ReAct: Synergizing Reasoning and Acting in Language Models* (2022).
- Model Context Protocol — spécification et serveurs de référence : [github.com/modelcontextprotocol](https://github.com/modelcontextprotocol).

---

## 8. Lexique ISTQB CT-GenAI (chapitre 1)

Rappel des termes clés du chapitre 1, avec la traduction officielle en anglais.

| Terme français | Terme anglais | Définition courte |
|---|---|---|
| chatbot IA | AI chatbot | Interface conversationnelle s'appuyant sur un LLM |
| deep learning | deep learning | Apprentissage par réseaux de neurones multicouches |
| embedding | embedding | Représentation vectorielle d'un token ou d'un passage |
| feature | feature | Caractéristique d'entrée utilisée par un modèle de ML |
| fenêtre contextuelle | context window | Quantité de texte (en tokens) prise en compte simultanément |
| grand modèle de langage (LLM) | large language model | Modèle génératif pré-entraîné sur de vastes corpus textuels |
| IA générative | generative AI | Branche de l'IA qui produit du contenu nouveau |
| IA symbolique | symbolic AI | Approche à base de règles explicites |
| LLM adapté aux instructions | instruction-tuned LLM | LLM affiné pour suivre des instructions |
| LLM de fondation | foundation model | LLM brut issu du pré-entraînement |
| LLM de raisonnement | reasoning LLM | LLM optimisé pour le raisonnement multi-étapes |
| machine learning | machine learning | Apprentissage statistique à partir de données |
| modèle multimodal | multimodal model | Modèle traitant plusieurs modalités (texte, image, audio, vidéo) |
| tokenisation | tokenization | Découpage du texte en unités traitables |
| Transformer | Transformer | Architecture de réseau neuronal à self-attention |
| Transformer génératif pré-entraîné (GPT) | Generative Pre-trained Transformer | Famille de LLMs autorégressifs (OpenAI GPT-n) |

---

## 9. Ressources de référence pour approfondir

### 9.1 Cours et ouvrages

- **Elements of AI** — [elementsofai.com](https://www.elementsofai.com/) — cours en ligne gratuit, accessible sans prérequis.
- **Hugging Face NLP Course** — [huggingface.co/learn](https://huggingface.co/learn) — cours pratique avec Transformers.
- **fast.ai — Practical Deep Learning for Coders** — approche par le code, orientée praticien.
- **Stanford CS25 — Transformers United** — série de conférences filmées (YouTube).
- Jurafsky & Martin, *Speech and Language Processing* (3e éd., version draft en accès libre) — manuel de référence NLP.

### 9.2 Blogs et chaînes techniques

- **Jay Alammar — The Illustrated Transformer / The Illustrated GPT-2** — vulgarisation graphique.
- **Andrej Karpathy (YouTube)** — *Neural Networks: Zero to Hero*, construction de GPT depuis zéro.
- **Lilian Weng (OpenAI, blog)** — synthèses techniques approfondies sur les LLMs, RAG, agents.
- **Simon Willison's Weblog** — veille quotidienne sur les LLMs et les pratiques associées.
- **Anthropic Research** — articles sur l'alignement et l'interprétabilité.

### 9.3 Papers incontournables

- Vaswani et al., *Attention Is All You Need* (2017) — le Transformer.
- Brown et al., *Language Models are Few-Shot Learners* (2020) — GPT-3 et le *few-shot*.
- Ouyang et al., *Training Language Models to Follow Instructions with Human Feedback* (2022) — RLHF.
- Wei et al., *Chain-of-Thought Prompting Elicits Reasoning in Large Language Models* (2022).
- Lewis et al., *Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks* (2020).

### 9.4 Outils à tester en pratique

- **OpenAI Playground** — expérimentation fine avec hyperparamètres.
- **Anthropic Workbench** — prototypage côté Claude.
- **Google AI Studio** — accès gratuit à Gemini pour les essais.
- **Ollama** ([ollama.com](https://ollama.com)) — exécution locale de modèles open source (Llama, Mistral, Qwen, Phi).
- **LM Studio** — interface graphique pour modèles locaux.
- **Hugging Face Spaces** — démos interactives de nombreux modèles.

### 9.5 Ressources ISTQB et communautés test

- **ISTQB CT-GenAI Syllabus v1.0** (juillet 2025) — référentiel officiel.
- **ISTQB Glossary** — lexique officiel des termes de test.
- **Comité français des tests logiciels (CFTL)** — traductions officielles et actualités en français.
- **Ministry of Testing** — communauté internationale, articles et conférences sur IA et test.

---

## Suite du parcours

- **Chapitre précédent** — [Introduction à l'IA générative](01-introduction-ia-generative.md).
- **Chapitre suivant** — [02 — Ingénierie du prompting pour des tests logiciels efficaces](../02-ingenierie-prompting/).
- **Chapitre 3** — [Gérer les risques liés à l'IA générative dans les tests logiciels](../03-gerer-risques/).

# Introduction à l'IA générative

> **À qui s'adresse ce chapitre ?** À toute personne qui n'utilise pas encore l'IA générative — ni dans son travail, ni dans sa vie quotidienne — et qui souhaite comprendre de quoi il s'agit avant de l'expérimenter.

---

## 1. Panorama de l'IA : d'où vient-on ?

L'intelligence artificielle (IA / artificial intelligence) n'est pas née avec ChatGPT. Elle a traversé plusieurs grandes périodes, chacune avec une philosophie différente.

### 1.1 L'IA symbolique (années 1950–1980)
L'ordinateur suit des règles écrites explicitement par des experts humains : *"si l'utilisateur dit X, réponds Y"*. C'est le principe des anciens systèmes experts et des arbres de décision. Efficace dans un domaine très précis, mais fragile dès que la situation sort du cadre prévu.

### 1.2 L'apprentissage automatique classique (machine learning) (années 1990–2010)
Plutôt que de programmer les règles à la main, on fournit des exemples et l'algorithme apprend lui-même les patterns. Un filtre anti-spam qui reconnaît les mails indésirables après avoir lu des milliers d'exemples, c'est du machine learning classique.

### 1.3 L'apprentissage profond (deep learning) (années 2010–2020)
Avec des réseaux de neurones artificiels à de nombreuses couches, les machines apprennent des représentations très abstraites. C'est ce qui permet la reconnaissance d'images, la traduction automatique, ou la détection vocale de Siri et Alexa.

### 1.4 L'IA générative (generative AI) (depuis 2020)
L'IA ne se contente plus de classer ou de reconnaître : elle **crée**. Elle génère du texte, des images, du code, de la musique. Les grands modèles de langage (LLM / large language model) en sont le moteur central.

---

## 2. Comment fonctionne un LLM ?

Un grand modèle de langage (grand modèle de langage / large language model, LLM) est un programme entraîné sur des quantités astronomiques de texte (pages web, livres, articles scientifiques, code source…). Son principe de fonctionnement est simple à comprendre : **prédire le mot le plus probable qui vient ensuite**.

Imaginez un jeu de complétion de phrase : *"Le chat est sur le…"* — votre cerveau anticipe *"tapis"* ou *"canapé"*. Un LLM fait la même chose, mais à une échelle et une précision qui donnent l'illusion de comprendre.

Ce qui le rend puissant :
- **Le volume** : entraîné sur des milliards de phrases dans des dizaines de langues
- **La taille** : des milliards de paramètres qui encodent des patterns linguistiques, factuels et logiques
- **L'instruction-following** : les versions récentes ont été affinées (fine-tuning) pour suivre des instructions et tenir une conversation

Ce que le LLM ne fait pas (au sens strict) : il ne "comprend" pas, ne "raisonne" pas comme un humain, et n'a pas de mémoire persistante entre les conversations (sauf configuration spécifique).

---

## 3. Les grands acteurs du marché

Le marché de l'IA générative est dominé par quelques grandes organisations, aux positionnements différents.


| Acteur | Produit phare | Modèle économique |
|---|---|---|
| **OpenAI** | ChatGPT, GPT-4o | Abonnement grand public + API payante |
| **Google / DeepMind** | Gemini (ex-Bard) | Intégré à Google Workspace + API |
| **Anthropic** | Claude (claude.ai) | Abonnement grand public + API payante |
| **Meta** | Llama 3, Llama 4 | Open source (gratuit, téléchargeable) |
| **Mistral AI** 🇫🇷 | Mistral, Mixtral | Open source + offre cloud (Le Chat) |
| **Microsoft** | Copilot (Windows, Office, GitHub) | Intégré aux produits Microsoft 365 |
| **xAI (Elon Musk)** | Grok | Intégré à X (Twitter) |

> **À noter :** Anthropic (créateur de Claude) a été fondé par d'anciens dirigeants d'OpenAI. Mistral AI est une startup française, l'une des rares en dehors des États-Unis à disposer de modèles compétitifs de niveau mondial.

---

## 4. Les trois visages de la GenAI

Il existe une confusion fréquente entre différents types d'outils. Voici comment les distinguer.

### 4.1 Le chatbot grand public
**Exemples :** ChatGPT (chat.openai.com), Google Gemini, Claude.ai

C'est l'accès le plus simple : vous ouvrez un navigateur, vous tapez votre question, vous obtenez une réponse. L'interface ressemble à une messagerie instantanée.

**Ce qu'il faut savoir :**
- Accessible sans installation, souvent gratuit (avec une version premium)
- Vos messages sont envoyés vers des serveurs distants (cloud)
- Le modèle ne connaît pas votre entreprise ni votre contexte métier
- Adapté pour l'apprentissage, la rédaction personnelle, les questions générales

### 4.2 Le modèle open source auto-hébergé (self-hosted open source model)
**Exemples :** Llama 3 (Meta) + Ollama, Mistral 7B en local

Ici, le modèle tourne **sur votre machine** (ou un serveur interne à votre organisation). Personne en dehors de votre infrastructure n'a accès à vos données.

**Ce qu'il faut savoir :**
- Nécessite une configuration technique (installation, ressources matérielles)
- Les données ne quittent jamais votre environnement : idéal pour les données sensibles
- Les modèles open source sont souvent moins puissants que les modèles propriétaires à usage général, mais suffisants pour de nombreux cas
- Utilisé dans des contextes bancaires, médicaux, défense

### 4.3 L'outil intégrant un LLM (LLM-powered tool)
**Exemples dans le domaine du test et de la gestion de projet :**

**à revoir**

| Outil | Ce que l'IA apporte |
|---|---|
| **GitHub Copilot** | Génération de code et de tests unitaires directement dans l'éditeur |
| **Xray AI** (plugin Jira) | Génération automatique de cas de test (cas de test / test case) à partir d'une user story - à vérifier|
| **Atlassian Intelligence (Rovo)** (Jira, Confluence) | Résumé de tickets, rédaction de documentation, assistant dans la recherche |
| **Microsoft 365 Copilot** (Word, Outlook, Teams) | Rédaction d'emails, résumé de réunions, génération de présentations |
| **Zephyr Scale AI** | Suggestion de cas de test basée sur les exigences |

**Ce qu'il faut savoir :**
- L'IA est intégrée dans votre outil existant : pas de nouvelle interface à apprendre
- Le contexte métier (votre ticket, votre doc, votre code) est injecté automatiquement dans le prompt
- La responsabilité de la pertinence des résultats reste à l'utilisateur
- Ces outils utilisent souvent les APIs d'OpenAI, Anthropic ou Google en coulisses

> **Analogie :** Un chatbot grand public, c'est un consultant généraliste que vous appelez de temps en temps. Un outil intégrant un LLM, c'est ce même consultant qui travaille assis à côté de vous, avec accès à tous vos fichiers.

---

## 5. Usages textuels : ce que vous pouvez faire aujourd'hui

Sans aucune connaissance technique, vous pouvez demander à un LLM de :

### Générer du contenu
- Rédiger un email professionnel à partir de quelques notes
- Créer une première version d'un cas de test (cas de test / test case) à partir d'une description fonctionnelle
- Générer des données de test (données de test / test data) fictives mais réalistes (noms, adresses, numéros de commande)

### Résumer et reformuler
- Résumer un long document de spécification en 10 points clés
- Reformuler un rapport de défaut (rapport de défaut / defect report) pour le rendre plus compréhensible par une équipe non technique
- Simplifier le jargon d'un document juridique

### Traduire
- Traduire une documentation technique en plusieurs langues
- Adapter le niveau de langage (version expert → version débutant)

### Répondre à des questions (Q&A)
- Expliquer un concept (ex. : "Qu'est-ce que le test exploratoire (exploratory testing) ?")
- Répondre à des questions sur un document que vous lui fournissez
- Jouer le rôle d'un interlocuteur pour préparer une présentation

### Débogage et analyse
- Expliquer pourquoi un message d'erreur apparaît
- Suggérer des causes possibles pour un comportement inattendu d'une application
- Comparer deux versions d'une exigence pour identifier les différences

---

## 6. Activités et jeux — usages textuels

Ces activités sont conçues pour être réalisées en groupe (atelier, formation) ou seul, avec n'importe quel chatbot grand public gratuit (ChatGPT free, Gemini, Claude.ai).

---

### Activité 1 — "Devinette de réponse"
**Objectif :** Comprendre que le LLM prédit ce qui est probable, pas ce qui est vrai.

**Déroulement :**
1. Choisissez une question ambiguë, ex. : *"Quelle est la meilleure façon de tester un formulaire d'inscription ?"*
2. Avant d'envoyer, chaque participant note en silence sa prédiction de la réponse (3 idées)
3. Envoyez la question et lisez la réponse à voix haute
4. Comparez : qu'est-ce que le modèle a inclus que personne n'avait prévu ? Qu'a-t-il omis ?

**Ce qu'on apprend :** Le LLM donne une réponse générique et probable, pas nécessairement adaptée à votre contexte précis.

---

### Activité 2 — "Reformule-moi ça"
**Objectif :** Explorer la capacité de reformulation selon le public cible.

**Déroulement :**
1. Prenez un paragraphe technique d'une documentation ou d'un cahier des charges
2. Demandez successivement :
   - *"Explique ce paragraphe à un enfant de 10 ans"*
   - *"Explique ce paragraphe à un expert en sécurité informatique"*
   - *"Transforme ce paragraphe en liste à puces"*
3. Comparez les trois versions

**Ce qu'on apprend :** Le LLM adapte son registre selon les instructions. Cela soulève la question : quelle version est "correcte" ?

---

### Activité 3 — "Compare les chatbots"
**Objectif :** Comprendre que les modèles ne sont pas identiques.

**Déroulement :**
1. Posez la même question à ChatGPT et à Gemini (ou Claude)
2. Question suggérée : *"Donne-moi 5 cas de test pour une fonctionnalité de réinitialisation de mot de passe"*
3. Comparez : les cas sont-ils identiques ? L'un est-il plus complet ? Plus prudent ?

**Ce qu'on apprend :** Il n'y a pas un seul "oracle" IA. Les réponses varient selon le modèle, l'entraînement et parfois la date de la question.

---

### Activité 4 — "Le rapport de défaut amélioré"
**Objectif :** Expérimenter l'aide à la rédaction dans un contexte professionnel réel.

**Déroulement :**
1. Rédigez un rapport de défaut (rapport de défaut / defect report) volontairement incomplet ou mal structuré, ex. : *"L'appli plante quand on se connecte parfois"*
2. Soumettez-le au chatbot avec la consigne : *"Améliore ce rapport de défaut pour qu'il soit exploitable par un développeur. Utilise un format structuré avec : titre, étapes de reproduction, résultat attendu, résultat obtenu, sévérité"*
3. Discutez en groupe : la version améliorée est-elle utilisable ? Que manque-t-il encore ?

**Ce qu'on apprend :** Le LLM structure et complète, mais il invente parfois des détails. La validation humaine reste indispensable.

---

### Activité 5 — "Les angles morts du LLM"
**Objectif :** Découvrir les tâches triviales pour un humain qui mettent un LLM en échec — et comprendre pourquoi.

> **Pourquoi ces échecs ?** Un LLM ne lit pas les mots lettre par lettre : il découpe le texte en *tokens* (fragments de mots). Le mot "tester" peut devenir les tokens `test` + `er`. Le modèle n'a donc pas de vision caractère par caractère, et échoue sur les tâches qui l'exigent.

**Déroulement :** Soumettez chaque question ci-dessous au chatbot de votre choix, notez la réponse, puis vérifiez vous-même. Comptez les points.

---

**Épreuve 1 — Comptage de lettres**

> *"Compte les occurrences de la lettre 't' dans la phrase suivante : 'j'aime tester et trouver des bugs toute la journée'"*

Réponse correcte : **7 t** (`t`ester, `t`es`t`er, e`t`, `t`rouver, `t`ou`t`e). Les modèles annoncent souvent 5 ou 6, et justifient leur erreur avec assurance.

---

**Épreuve 2 — Inversion de mot**

> *"Écris le mot 'développement' en inversant l'ordre de ses lettres"*

Réponse correcte : `tnemelppoleved`. Très peu de modèles y parviennent du premier coup — ils reconstituent un mot plausible plutôt que de réaliser l'opération mécanique.

---

**Épreuve 3 — Comptage de mots répétés**

> *"Dans la phrase suivante, combien de fois le mot 'de' apparaît-il ? 'Le rôle de l'équipe de test est de vérifier la conformité de l'application par rapport aux exigences de l'utilisateur'"*

Réponse correcte : **5 fois**. Les modèles en oublient souvent un ou deux, notamment ceux précédés d'une apostrophe (`d'`).

---

**Épreuve 4 — Classement par longueur**

> *"Classe ces mots du plus court au plus long, sans les compter : 'régression', 'bug', 'acceptance', 'test'"*

Réponse correcte : bug (3) → test (4) → régression (10) → acceptance (10). Certains modèles inversent les deux derniers ou hésitent entre *acceptance* et *régression* car ils ne les "mesurent" pas vraiment.

---

**Épreuve 5 — Calendrier simple**

> *"2024 est une année bissextile. Le 1er mars 2024 est un vendredi. Quel jour de la semaine est le 1er mars 2025 ?"*

Réponse correcte : **samedi** (366 jours en 2024, soit 52 semaines + 2 jours). Les LLMs commettent fréquemment des erreurs de calcul de décalage de jours, même en montrant leurs calculs intermédiaires.

---

**Épreuve 6 — Logique de texte littéral**

> *"La phrase suivante contient-elle le mot 'test' ? 'Les exigences fonctionnelles servent de base à la vérification'"*

Réponse correcte : **Non**. Mais certains modèles répondent oui, confondant la présence du concept avec celle du mot exact — une forme d'hallucination sémantique pertinente dans un contexte de test logiciel.

---

**Débrief collectif :**
- Quelles épreuves ont mis le modèle en échec ?
- Le modèle s'est-il excusé, ou a-t-il défendu une mauvaise réponse ?
- Que dit cela sur la confiance à lui accorder pour des vérifications précises ?

**Ce qu'on apprend :** Un LLM est excellent pour les tâches sémantiques et contextuelles (résumer, reformuler, générer). Il est peu fiable pour les tâches nécessitant une manipulation caractère par caractère, un comptage exact ou un calcul arithmétique sans assistance. Savoir identifier ces angles morts est une compétence essentielle pour un testeur qui utilise l'IA.

---

## 7. LLM multimodaux et modèles de vision

Jusqu'ici, nous avons parlé de texte. Mais les modèles les plus récents vont bien au-delà.

### 7.1 Qu'est-ce qu'un LLM multimodal (multimodal LLM) ?

Un modèle multimodal (modèle multimodal / multimodal model) est capable de traiter et de générer plusieurs types de données : texte, images, audio, vidéo, voire des fichiers structurés (tableaux, PDF).

| Modalité | Ce que le modèle peut faire |
|---|---|
| **Image en entrée** | Décrire une image, répondre à des questions sur son contenu, identifier des anomalies visuelles |
| **Image en sortie** | Générer une image à partir d'une description textuelle (ex. : DALL·E, Midjourney, Stable Diffusion) |
| **Audio en entrée** | Transcrire et comprendre de la parole (ex. : Whisper d'OpenAI) |
| **Audio en sortie** | Synthèse vocale, conversations audio (ex. : ChatGPT Voice) |
| **Vidéo** | Décrire une vidéo, identifier des événements dans une séquence |

### 7.2 Grands modèles multimodaux actuels

- **GPT-4o** (OpenAI) : texte, images, audio en entrée et sortie
- **Gemini 1.5 Pro / 2.0 Flash** (Google) : texte, images, audio, vidéo, code — avec une fenêtre de contexte très large
- **Claude 3.5 / 3.7 Sonnet** (Anthropic) : texte et images en entrée, texte en sortie
- **Llama 3.2 Vision** (Meta) : modèle open source multimodal

### 7.3 Modèles de vision (vision models) pour les tests logiciels

Les modèles de vision (modèle de vision / vision model) ouvrent des possibilités nouvelles dans le domaine du test :

**Analyse d'interfaces utilisateur :**
- Soumettre une capture d'écran (screenshot) et demander : *"Quels éléments d'interface (interface element) sont présents sur cette page ?"*
- Vérifier si une maquette (mockup) a été correctement implémentée en comparant les deux images
- Identifier des problèmes d'accessibilité visuelle (contraste, taille de police)

**Automatisation visuelle :**
- Décrire une interface pour générer automatiquement des localisateurs (locator) pour des scripts de test automatisé (automated test script)
- Analyser des captures d'écran de différences de rendu entre navigateurs

**Documentation visuelle :**
- Photographier un tableau blanc contenant des scénarios de test et demander au modèle de les retranscrire en Gherkin ou en tableau structuré

---

## 8. Activités et jeux — multimodal

Ces activités nécessitent un accès à un modèle multimodal. GPT-4o (version gratuite limitée) et Gemini sont accessibles sans abonnement.

---

### Activité 6 — "Décris cette interface"
**Objectif :** Comprendre ce que le modèle "voit" dans une image.

**Déroulement :**
1. Prenez une capture d'écran d'une application que vous connaissez (page web, application mobile, logiciel métier)
2. Soumettez-la avec la question : *"Liste tous les éléments d'interface visibles sur cette image : boutons, champs, menus, messages, icônes"*
3. Comparez la liste générée avec votre propre inventaire fait à la main

**Ce qu'on apprend :** Le modèle est souvent précis mais peut manquer des détails subtils (icônes ambiguës, texte très petit). Il est utile comme point de départ, pas comme résultat final.

---

### Activité 7 — "Trouve la différence"
**Objectif :** Simuler un test de non-régression visuelle (visual regression test) assisté par l'IA.

**Déroulement :**
1. Prenez deux captures d'écran de la même page : une "avant" et une "après" un changement (réel ou simulé)
2. Soumettez-les ensemble avec la consigne : *"Compare ces deux captures d'écran et liste toutes les différences visuelles que tu observes"*
3. Validez les différences trouvées : le modèle a-t-il tout détecté ? A-t-il signalé de fausses différences ?

**Ce qu'on apprend :** L'IA peut détecter des changements visuels, mais elle n'est pas un outil de pixel-diffing rigoureux. Elle est plus utile pour les différences sémantiques (texte modifié, bouton disparu) que pour les différences de pixels imperceptibles.

---

### Activité 8 — "Photo de tableau blanc"
**Objectif :** Expérimenter la transcription de contenu non-numérique.

**Déroulement :**
1. Écrivez 3 à 5 scénarios de test (scénario de test / test scenario) à la main sur du papier ou un tableau blanc
2. Photographiez-les avec votre téléphone
3. Soumettez la photo avec la consigne : *"Retranscris ces scénarios de test dans un tableau Markdown avec les colonnes : ID, Description, Résultat attendu"*

**Ce qu'on apprend :** L'IA peut extraire du contenu d'images de qualité modeste. Elle commet des erreurs sur les écritures peu lisibles. C'est un gain de temps pour la saisie, mais une relecture s'impose.

---

## 9. Développements récents et IA agentique

### 9.1 Les modèles de raisonnement (reasoning models)

Depuis fin 2024, une nouvelle génération de modèles a émergé : les **modèles de raisonnement** (modèle de raisonnement / reasoning model). Avant de répondre, ils effectuent une phase de réflexion interne (souvent visible sous forme d'une "chaîne de pensée").

**Exemples :**
- **o1, o3** (OpenAI) : particulièrement efficaces sur les problèmes mathématiques, de logique et de code
- **Claude 3.7 Sonnet avec extended thinking** (Anthropic) : raisonnement étendu activable par l'utilisateur
- **Gemini 2.0 Flash Thinking** (Google)

Ces modèles font moins d'erreurs sur des tâches complexes, mais sont plus lents et plus coûteux en ressources.

### 9.2 L'IA agentique (agentic AI)

Un **agent IA** (agent IA / AI agent) est un système dans lequel le LLM ne se contente pas de répondre : il **agit**. Il peut enchaîner plusieurs étapes, utiliser des outils externes, et adapter son plan en fonction des résultats intermédiaires.

**Outils qu'un agent peut utiliser :**
- Naviguer sur le web et lire des pages
- Exécuter du code dans un environnement sandbox
- Lire et écrire des fichiers
- Appeler des APIs (Jira, Slack, GitHub…)
- Piloter un navigateur (comme Playwright ou Selenium)

**Exemples dans le domaine du test logiciel :**
- Un agent qui lit une user story, génère des cas de test (cas de test / test case), les pousse dans Jira, puis exécute un script de test Playwright et rapporte les résultats — le tout de manière autonome
- Des outils comme **Devin** (Cognition), **GitHub Copilot Workspace**, ou **Cursor** intègrent déjà ces capacités agentiques pour le développement et le test

**Ce qu'il faut retenir :**
L'IA agentique change le paradigme : on ne demande plus une réponse, on confie une **mission**. Cela amplifie à la fois les capacités et les risques (actions irréversibles, hallucinations en cascade, sécurité des accès). La supervision humaine reste essentielle.

---

## 10. Tirer parti de l'IA générative dans les tests logiciels : principes généraux

### 10.1 Capacités clés des LLMs pour les tâches de test

Les LLMs offrent un ensemble de capacités génériques qui se déclinent naturellement dans les activités de test logiciel.

| Capacité | Définition | Application au test |
|---|---|---|
| **Génération de texte** | Produire du contenu structuré ou libre à partir d'une consigne | Rédiger des cas de test (cas de test / test case), des critères d'acceptation (critère d'acceptation / acceptance criterion), des plans de test (plan de test / test plan) |
| **Résumé et extraction** | Condenser un document en identifiant l'essentiel | Résumer des spécifications, extraire les règles métier d'un cahier des charges |
| **Classification** | Catégoriser un élément parmi des classes prédéfinies | Trier des défauts (défaut / defect) par type, priorité ou composant ; classer des exigences par risque |
| **Transformation de format** | Convertir un contenu d'un format vers un autre | Convertir des user stories en scénarios Gherkin (Given/When/Then), un tableau Excel en cas de test Markdown |
| **Q&A contextuel** | Répondre à des questions sur un document fourni | Interroger une spécification pour vérifier la couverture des exigences (couverture des exigences / requirements coverage) |
| **Complétion et suggestion** | Prolonger ou compléter un contenu partiel | Suggérer des cas limites (cas limite / boundary value) manquants dans une suite de test |
| **Détection d'anomalies textuelles** | Identifier des incohérences ou ambiguïtés dans un texte | Repérer des exigences contradictoires ou incomplètes dans une spécification |

> **Limite à garder en tête :** Ces capacités sont probabilistes, pas déterministes. Pour une même consigne, le LLM peut produire des résultats différents d'une exécution à l'autre. La vérification humaine des sorties reste une étape obligatoire dans tout processus de test.

---

### 10.2 Chatbots IA et applications de test basées sur LLM

Il existe deux grandes façons d'intégrer un LLM dans une activité de test :

#### Utilisation directe d'un chatbot (chatbot IA / AI chatbot)

Vous interagissez manuellement avec le modèle via une interface conversationnelle. C'est la forme la plus accessible — aucune intégration technique requise.

**Exemples de tâches réalisables directement en chat :**
- *"Génère 10 cas de test pour la fonctionnalité 'ajout au panier' d'un e-commerce"*
- *"Voici une user story. Identifie les ambiguïtés et les cas non couverts"*
- *"Transforme ces notes de réunion en items de backlog avec critères d'acceptation"*
- *"Explique-moi ce message d'erreur et propose des pistes d'investigation"*

**Avantages :** Rapide à démarrer, sans configuration, idéal pour les tâches ponctuelles.  
**Limites :** Pas d'accès à votre contexte projet, réponses à valider, pas d'automatisation.

---

#### Applications de test basées sur LLM (LLM-based test application)

Ce sont des outils spécialisés qui intègrent un LLM dans un pipeline de test structuré. Le contexte métier (code source, tickets, exigences, résultats de tests passés) est injecté automatiquement dans le modèle.

**Catégories et exemples :**

| Catégorie | Outils | Ce que l'IA apporte |
|---|---|---|
| **Génération de tests unitaires** | GitHub Copilot, Cursor, CodiumAI | Génère des tests unitaires (test unitaire / unit test) à partir du code source |
| **Gestion de tests dans Jira** | Xray AI, Zephyr Scale AI, Tricentis | Génère des cas de test à partir des user stories, lie automatiquement défauts et exigences |
| **Documentation et collaboration** | Atlassian Intelligence (Confluence, Jira) | Résume les tickets, suggère des descriptions, génère des rapports |
| **Test exploratoire assisté** | Testim Copilot, Mabl | Suggère des parcours à explorer, génère des assertions |
| **Analyse de défauts** | LinearB, Sentry AI | Regroupe les erreurs similaires, suggère des causes racines (cause racine / root cause) |
| **Suite bureautique** | Microsoft 365 Copilot (Word, Excel) | Génère des plans de test depuis un document Word, analyse des matrices de traçabilité dans Excel |

---

### 10.3 Ce que l'IA ne remplace pas (encore)

Comprendre ce que le LLM ne peut pas faire est aussi important que de connaître ses capacités.

| Ce que l'IA fait bien | Ce que l'humain reste indispensable pour |
|---|---|
| Générer une première version de cas de test | Valider la pertinence métier des cas générés |
| Reformuler une exigence ambiguë | Décider de l'interprétation correcte avec les parties prenantes |
| Suggérer des données de test | Vérifier que les données respectent les contraintes légales et de confidentialité |
| Identifier des cas limites courants | Détecter les risques spécifiques au contexte métier |
| Accélérer la rédaction de documentation | Garantir l'exactitude technique et la cohérence globale |

> L'IA générative est un **accélérateur**, pas un remplaçant. Elle déplace l'effort humain vers la validation, le jugement et la créativité — là où la valeur ajoutée du testeur est la plus forte.

---

### Activité 9 — "Du brouillon au cas de test"
**Objectif :** Expérimenter la chaîne complète : exigence → génération → validation.

**Déroulement :**
1. Rédigez une user story volontairement succincte, ex. :
   > *"En tant qu'utilisateur, je veux pouvoir réinitialiser mon mot de passe afin de récupérer l'accès à mon compte."*
2. Soumettez-la avec la consigne :
   > *"Génère une suite de cas de test pour cette user story. Pour chaque cas, indique : ID, titre, préconditions, étapes, résultat attendu, type (nominal / alternatif / négatif)."*
3. Analysez les résultats en groupe :
   - Quels cas vous semblent pertinents ?
   - Quels cas importants sont absents (ex. : lien de réinitialisation expiré, email inexistant, tentatives multiples) ?
   - Le modèle a-t-il inventé des comportements non spécifiés ?
4. Complétez la suite de test manuellement avec les cas manquants.

**Ce qu'on apprend :** Le LLM produit rapidement une base solide de cas nominaux. Les cas négatifs (cas négatif / negative test case) et les cas limites métier restent la valeur ajoutée du testeur expérimenté.

---

### Activité 10 — "L'exigence ambiguë"
**Objectif :** Utiliser le LLM comme outil d'analyse d'exigences (analyse des exigences / requirements analysis).

**Déroulement :**
1. Choisissez une exigence volontairement floue, ex. :
   > *"Le système doit répondre rapidement aux requêtes des utilisateurs."*
2. Demandez au modèle :
   > *"Identifie les ambiguïtés de cette exigence et reformule-la de manière testable, avec des critères mesurables."*
3. Comparez la version reformulée avec votre propre interprétation.
4. Testez avec une deuxième exigence issue d'un vrai projet.

**Ce qu'on apprend :** Le LLM est excellent pour signaler les termes vagues ("rapidement", "souvent", "correctement"). Il propose des reformulations testables, mais le seuil acceptable (ex. : "< 2 secondes dans 95% des cas") reste une décision humaine et métier.

---

## Pour aller plus loin

- **Elements of AI** (elementsofai.com) : cours en ligne gratuit, très accessible, pour comprendre les fondements de l'IA
- **Google AI Essentials** (Coursera) : introduction pratique par Google
- **ISTQB CT-GenAI** : certification officielle pour les testeurs souhaitant valider leurs compétences en IA générative appliquée aux tests
- Prochain chapitre : *Ingénierie du prompting pour des tests logiciels efficaces*

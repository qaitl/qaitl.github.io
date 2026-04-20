# Testing d'un chatbot spécialisé

## Introduction : Qu'est-ce qu'un chatbot spécialisé ?

Un chatbot spécialisé est un système conversationnel conçu pour répondre à des besoins métier précis, en s'appuyant sur un ensemble de composants orchestrés pour traiter des questions ouvertes d'utilisateurs dans un domaine délimité. Contrairement aux chatbots généralistes comme ChatGPT ou Claude qui visent une couverture universelle des sujets, un chatbot spécialisé est construit autour d'un périmètre fonctionnel défini et de sources de données spécifiques à l'organisation ou au domaine d'application.

### Architecture d'un chatbot spécialisé

Un chatbot spécialisé combine typiquement plusieurs composants techniques, basés sur l'IA ou non, qui collaborent pour produire une réponse pertinente :

#### Composants de traitement de la requête :

Classification d'intention : déterminer le type de demande et router vers le bon traitement

Extraction d'entités : identifier les éléments clés (numéros de dossier, dates, noms de produits)

Détection de langue : adapter le traitement selon la langue de l'utilisateur

#### Composants d'accès à l'information :

RAG (Retrieval-Augmented Generation) : recherche de documents pertinents dans une base de connaissances propriétaire

Accès à des bases de données : requêtes vers des systèmes d'information métier (ex: CRM)

Appels API externes : intégration avec des services tiers (module de calcul, service externe, …)

#### Composants d'orchestration et d'action :

Agents autonomes : capacité à planifier et exécuter des séquences d'actions (réserver, modifier un dossier, envoyer un email)

Workflows conditionnels : logique métier déterministe pour des processus réglementés

Gestion du contexte conversationnel : mémorisation et suivi des échanges précédents

#### Composants de sécurité et conformité :

Filtres de confidentialité : masquage ou contrôle d'accès aux données sensibles

Validation réglementaire : vérification de conformité avant exécution d'actions

Guardrails : barrières empêchant les sorties inappropriées ou dangereuses

Dans cette architecture, le LLM joue un rôle central mais non exclusif : il génère la réponse finale en langage naturel en s'appuyant sur les informations collectées par les autres composants, mais il ne constitue pas à lui seul le chatbot. La qualité du système dépend autant de la pertinence du retrieval RAG, de la fiabilité des données métier accédées, ou de la robustesse des agents que de la qualité du LLM lui-même.

### Différences fondamentales avec les chatbots généralistes

Cette nature composite et spécialisée implique des différences majeures avec les chatbots généralistes :

#### Périmètre fonctionnel délimité vs universalité

Un chatbot spécialisé est conçu pour un ensemble précis de tâches (support client, business interne, prospect) avec des refus explicites hors périmètre

Un chatbot généraliste tente de répondre à toute question, sans restriction thématique

#### Sources de connaissances contrôlées vs apprentissage général

Le chatbot spécialisé s'appuie sur des données propriétaires validées (documentation interne, bases de données métier, politiques d'entreprise). Il peut intégrer des comportements déterministes dans certains contexte (ex: réagir à une intention de résiliation de contrat, canaliser les demande de contact, proposer un produit complémentaire, …) afin de respecter la stratégie de l’entreprise.

Le chatbot généraliste utilise uniquement les connaissances acquises lors de son entraînement sur des données publiques massives

#### Responsabilité et exactitude vs couverture large

Le chatbot spécialisé engage la responsabilité de l'organisation sur ses réponses, exigeant un niveau d'exactitude élevé dans son domaine

Le chatbot généraliste offre une aide générale sans garantie d'exactitude, avec des clauses de non-responsabilité explicites

#### Intégration métier vs interface conversationnelle pure

Le chatbot spécialisé peut déclencher des actions dans les systèmes d'information (créer un ticket, modifier une réservation, générer un document)

Le chatbot généraliste se limite généralement à fournir de l'information et du contenu sans connexion aux systèmes de l'utilisateur

#### Personnalisation et contexte utilisateur vs anonymat

Le chatbot spécialisé peut adapter ses réponses selon l'identité, le rôle et l'historique de l'utilisateur (droits d'accès, contrats actifs, préférences)

Le chatbot généraliste traite chaque conversation de manière isolée, sans connaissance de l'utilisateur

### Implications pour le testing

Ces différences structurelles rendent les comparaisons directes entre chatbots spécialisés et généralistes non seulement inappropriées mais trompeuses :

"ChatGPT répond mieux" n'est pas un critère pertinent si ChatGPT ne peut pas accéder aux données métier nécessaires, ne respecte pas les contraintes de confidentialité, ou produit des réponses hors du périmètre accepté

La qualité perçue d'un chatbot spécialisé dépend de facteurs absents chez les généralistes : pertinence du retrieval, fraîcheur des données, respect des règles métier, capacité à exécuter des actions

Les attentes utilisateurs doivent être recalibrées : un chatbot spécialisé peut légitimement refuser certaines questions tout en excellant dans son domaine

Le testing d'un chatbot spécialisé doit donc évaluer l'ensemble du système orchestré, pas seulement la qualité de génération du LLM. Les parties suivantes de ce document détaillent les spécificités de cette évaluation complexe et multi-facettes.

## Pourquoi le testing des chatbots IA diffère du testing traditionnel

### 1. Illusion d'universalité (ambiguïté du périmètre fonctionnel)

Le chatbot semble universel, créant des attentes illimitées chez les utilisateurs. Contrairement à un logiciel traditionnel avec des fonctionnalités clairement délimitées, il faut définir explicitement le scope fonctionnel et spécifier les comportements attendus hors-périmètre : refus gracieux ("Je ne suis pas conçu pour..."), redirections appropriées, évitement des tentatives de réponse qui induiraient l'utilisateur en erreur.

De plus, la comparaison avec des outils semblant similaire peut renforcer la frustration d'un utilisateur ("ChatGPT peut le faire, lui")

### 2. Surface d'attaque infinie et vulnérabilités spécifiques

L'espace d'inputs linguistiques est illimité, contrairement aux écrans et formulaires structurés. Il faut tester contre des menaces spécifiques : prompt injection, jailbreaking, extraction de données confidentielles. Le red teaming (tests orientés sécurités) devient une pratique continue plutôt qu'un audit ponctuel, car de nouvelles vulnérabilités émergent constamment.

### 3. Non-déterminisme et absence d'oracle

Les réponses varient à chaque exécution, rendant impossibles les tests de régression classiques par comparaison exacte. Le testeur ne peut pas facilement deviner la "bonne réponse" attendue, ce qui nécessite des évaluations sémantiques plutôt que binaires et l'intervention d'experts métier pour valider les réponses complexes.

### 4. Dépendance aux données et risque d'hallucinations

Le testing se fait à deux niveaux distincts : la qualité du retrieval (les bons documents sont-ils récupérés ?) et la génération (sont-ils utilisés correctement ?). Les hallucinations peuvent survenir malgré des données correctes, et la base de connaissances devient obsolète, nécessitant une validation continue de sa pertinence. De plus, chaque changement de la base de connaissance altère les futures réponses, rendant difficile la comparaison entre plusieurs réponses séparées temporellement.

### 5. Confidentialité et compartimentage des accès

Avec des agents accédant à des données confidentielles, le risque de fuite d'information dans les réponses est critique. Il faut tester rigoureusement le compartimentage selon les utilisateurs et leurs droits d'accès, ainsi que maintenir la traçabilité des sources pour l'audit et l'explicabilité des décisions du système.

### 6. Responsabilité et biais d'automatisation

L'équipe et le client restent légalement et éthiquement responsables des réponses fournies, même si "c'est l'IA qui l'a dit". Les utilisateurs ont tendance à sur-faire confiance aux réponses automatisées (biais d'automatisation), ce qui exige une vigilance renforcée sur les domaines critiques (santé, juridique, finance) et une obligation d'explicabilité des réponses générées.

## Quels attributs de qualité mesurer ?

À prioriser selon le contexte projet

### 1. Performance fonctionnelle / Qualité de la réponse

* Exactitude : les réponses sont-elles factuellement correctes ?

* Pertinence : les réponses correspondent-elles à l'intention de l'utilisateur ?

* Complétude : les informations essentielles sont-elles fournies ?

* Cohérence : les réponses successives sont-elles logiquement cohérentes ? comment se déroule une conversation ?

* Comportement dangereux : à quelle fréquence le bot peut produire une réponse dommageable pour l'organisation, l'utilisateur ou le client ?

* Comportement hors-périmètre : qualité des refus et redirections

### 2. Latence et réactivité

* Temps de réponse : délai entre question et début de réponse

* Streaming : l'utilisateur voit-il la réponse se construire ?

* Timeout et gestion d'erreur : comportement en cas de lenteur excessive

* Perception utilisateur : la latence est-elle acceptable pour le cas d'usage ?

*Impact : la latence affecte directement l'expérience utilisateur et le taux d'abandon*

### 3. Coût opérationnel

* Coût par requête : tokens consommés (input + output)

* Coûts fixes

* Coût complémentaire par requête

* Ratio coût/valeur : le coût est-il justifié par la qualité obtenue ?

*Critère souvent négligé en phase de développement mais critique en production à grande échelle*

### 4. Confidentialité et sécurité

* Protection des données : pas de fuite d'informations confidentielles

* Compartimentage : respect des droits d'accès par utilisateur/rôle

* Résistance aux attaques : prompt injection, jailbreaking, extraction de données

* Traçabilité : audit des accès et des réponses fournies

* Conformité réglementaire : RGPD, AI Act, normes sectorielles

5. Explicabilité et transparence

* Traçabilité des sources : quels documents RAG ont été utilisés ?

* Justification des décisions (explicabilité): pourquoi cette réponse ? pourquoi ce refus ?

* Chaîne de raisonnement (interpretabilité): pour les agents, quelles étapes ont mené à l'action ?

* Niveau de confiance : le bot exprime-t-il son incertitude ?

* Auditabilité : possibilité de reproduire et comprendre un comportement a posteriori

*Essentiel pour la responsabilité légale et éthique mentionnée en Partie 1*

6. Fiabilité et robustesse

* Disponibilité : uptime du service, gestion des pannes

* Gestion d'erreurs : comportement gracieux en cas d'échec (API, RAG, agents)

* Résistance aux inputs inattendus : malformés, ambigus, contradictoires

* Stabilité : absence de comportements erratiques ou de dégradations soudaines

* Fallback mechanisms : alternatives quand le système principal échoue

7. Évolutivité (Scalabilité)

* Montée en charge : performance maintenue avec l'augmentation des utilisateurs

* Évolution de la base de connaissances : ajout de documents sans dégradation

* Adaptation fonctionnelle : facilité d'ajout de nouveaux use cases

* Mise à jour des modèles : capacité à intégrer de nouvelles versions de LLM

* Extensibilité des agents : ajout de nouveaux outils/actions

8. Expérience utilisateur (UX)

* Ton et style : approprié au contexte et à l'audience

* Clarté : réponses compréhensibles, structure lisible

* Proactivité : suggestions pertinentes, questions de clarification

* Gestion du dialogue : mémoire conversationnelle, suivi du contexte

* Satisfaction : l'utilisateur a-t-il obtenu ce qu'il cherchait ?

9. Maintenabilité

* Versioning : prompts, configurations, datasets de test

* Debuggabilité : facilité d'identification de la source d'un problème

* Documentation : clarté des choix de conception et configurations

* Monitoring : observabilité des métriques clés en production

* Facilité de correction : rapidité de déploiement d'un fix

10. Équité et absence de biais

* Biais démographiques : traitement équitable selon genre, âge, origine, etc.

* Biais linguistiques : qualité égale dans différentes langues ou registres

* Biais de représentation : diversité dans les exemples et recommandations

* Accessibilité : utilisable par personnes en situation de handicap

## Stratégie et méthodologie de testing

### 1. Définir les use cases comme fondation

Avant tout testing, cartographier et documenter les cas d'usage attendus pour contrer l'ambiguïté du périmètre identifiée en partie 1. Cette documentation doit inclure :

* Les scénarios dans le périmètre (questions types, contextes d'utilisation)

* Les scénarios hors-périmètre et comportements attendus (refus, redirections)

* Les cas limites et ambigus nécessitant une attention particulière

Ces use cases constituent l'ancrage stable face aux évolutions techniques et deviennent le référentiel pour toutes les activités de test.

### 2. Établir des critères d'évaluation mesurables

Pour chaque use case, définir des métriques de qualité vérifiables :

* Critères fonctionnels : pertinence, exactitude, complétude de la réponse par rapport aux données disponibles

* Critères comportementaux : refus gracieux hors-périmètre, ton approprié, respect des consignes de confidentialité

* Seuils d'acceptation : taux de réussite minimum, niveaux de confiance requis selon la criticité

* Distinction automatique/humain : identifier ce qui est évaluable automatiquement vs ce qui nécessite un jugement expert

Ces critères adressent directement le problème d'absence d'oracle mentionné en partie 1.

### 3. Isoler composants déterministes et probabilistes

Pour faciliter le diagnostic des défaillances, tester chaque composant en isolation quand c'est possible :

#### Parties déterministes (tests unitaires classiques) :

* Parsing et validation des inputs

* Retrieval (documents récupérés pour une requête donnée)

* Filtres de sécurité et règles de confidentialité

* Logging et traçabilité

#### Parties probabilistes (évaluations statistiques) :

* Génération LLM et qualité des réponses

* Orchestration d'agents et chaînes de raisonnement

* Tests d'intégration : comportement end-to-end validant les interactions entre composants

Cette séparation permet de localiser rapidement si un problème vient du RAG, du LLM ou de l'orchestration des agents.

### 4. Approches de testing complémentaires

Combiner plusieurs stratégies pour couvrir les différents risques identifiés en partie 1 :

* Testing basé sur exemples : jeux de données annotés couvrant les use cases, incluant les cas hors-périmètre

* Adversarial testing : tentatives délibérées de contournement (prompt injection, extraction de données confidentielles, questions pièges)

* A/B testing : comparaison de versions (prompts, modèles, paramètres RAG, configurations d'agents) pour gérer le non-déterminisme

* Regression testing : suivi de benchmarks sur versions successives pour détecter les dégradations silencieuses

### 5. Collaboration agile entre experts avec feedbacks rapides

Face au non-déterminisme et à la complexité, trois expertises complémentaires doivent collaborer étroitement :

#### Expert technique :

*Implémente les pipelines d'évaluation automatique

* Gère le versioning des prompts, configurations et modèles

* Intègre les tests dans CI/CD

* Maintient l'isolation et la traçabilité des composants

#### Expert métier :

* Définit et valide les use cases

* Évalue la pertinence et l'exactitude des réponses sur son domaine

* Identifie les hallucinations subtiles que les métriques automatiques manqueraient

* Calibre les seuils d'acceptation selon la criticité métier

#### Expert qualité :

* Conçoit la stratégie de test globale

* Coordonne les évaluations entre technique et métier

* Maintient et enrichit les jeux de données de test

* Analyse les patterns d'échec et assure la traçabilité

Nécessité de feedbacks rapides : Les attentes métier et le contexte technique (nouveaux modèles, évolution des données, découverte de vulnérabilités) changent constamment. Des cycles courts d'évaluation-ajustement sont indispensables :

#### Revues fréquentes des métriques entre les trois types d'expertises

* Ajustements itératifs des prompts, seuils et composants

* Communication transverse immédiate lors de la découverte d'anomalies

Ancrage constant : les use cases restent stables, mais leur implémentation technique s'adapte en continu

### 6. Monitoring en production et amélioration continue

Le testing ne s'arrête pas au déploiement, car les conditions réelles révèlent des comportements impossibles à anticiper :

#### Détection proactive

Monitoring du drift de performance dans le temps

Surveillance des changements de distribution des requêtes utilisateurs

Alertes sur les comportements anormaux des agents ou accès aux données

#### Collecte de feedback

Signalements explicites des utilisateurs (boutons de feedback)

Évaluations implicites (reformulations, abandons, durée d'interaction)

Analyse des cas où le bot refuse de répondre (trop fréquent ? pas assez ?)

#### Boucle d'amélioration

Enrichissement continu des jeux de test avec les cas réels problématiques

Ajustement des prompts et configurations basé sur les patterns observés

Mise à jour de la base de connaissances RAG pour éviter l'obsolescence

Partage rapide des insights entre technique, métier et qualité

## Mise en pratique de la stratégie de testing

### 1. Identifier et documenter les use cases

#### Use cases souhaités (dans le périmètre) :

* Cartographier les besoins métier par observation des processus, analyse de logs, enquêtes utilisateurs, ateliers collaboratifs, …

* Prioriser selon l'impact métier et la faisabilité technique

#### Use cases non souhaités (hors périmètre) :

* Identifier les utilisations potentielles par méconnaissance du produit (confusion avec d'autres outils)

* Anticiper les tests de limites par curiosité ("que se passe-t-il si je demande...")

* Prévoir les tentatives frauduleuses (extraction de données, contournement de restrictions)

* Définir le comportement attendu pour chaque catégorie (refus gracieux, redirection, message d'erreur)

### 2. Illustrer par des exemples concrets

Pour chaque use case identifié, documenter 4-5 questions réalistes basées sur des situations réelles :

* Varier les formulations (directe, polie, technique, familière)

* Inclure des variantes linguistiques et des fautes de frappe courantes

* Couvrir différents niveaux de complexité ou de contexte

Critère de validation : Si les exemples semblent trop éloignés les uns des autres, c'est un indicateur qu'il faut diviser le use case en plusieurs use cases distincts.

### 3. Définir critères d'acceptation et risques

Pour chaque use case, en s'appuyant sur les questions d'exemple :

#### Ce que le produit DOIT faire (critères d'acceptation) :

* Comportement attendu (réponse précise, redirection, refus gracieux)

* Ton et niveau de détail appropriés

* Respect des contraintes de confidentialité et de sécurité

* Traçabilité des sources utilisées (si applicable)

#### Ce que le produit NE DOIT PAS faire (évaluation des risques) :

Utiliser la grille de priorisation des risques (Partie 1) comme checklist

* Identifier les risques spécifiques : hallucinations, fuites de données, réponses dangereuses, biais, coûts excessifs

* Définir les seuils d'acceptabilité selon la criticité du use case

#### Réponse de référence :

Un exemple de réponse pertinente peut être fourni, mais en sachant que la réponse finale du chatbot sera probablement différente tout en restant acceptable

L'objectif n'est pas la reproduction exacte mais la validation des critères d'acceptation

### 4. Construire les datasets de test

Pour chaque use case, constituer un dataset structuré :

#### Structure d'un item de test :

* Input : question ou historique conversationnel

* Output attendu : réponse, catégorie, documents RAG requis, actions à déclencher

* Métadonnées : criticité, profil utilisateur, contexte

#### Sources pour constituer le dataset :

* Partir des 4-5 exemples de la phase de définition

* Si possible, Compléter avec des données réelles (logs historiques, transcriptions, consultations d'experts métier)

* Eventuellement, générer des données synthétiques via IA avec relecture humaine systématique

* Enrichir continuellement avec les cas réels problématiques rencontrés

Taille du dataset : Selon la criticité et la complexité du use case, quelques dizaines à plusieurs centaines d'items seront nécessaires.

### 5. Automatiser l'exécution des tests

Les questions du dataset doivent être posées automatiquement au produit selon un calendrier régulier :

#### Déclencheurs d'exécution :

* Après chaque changement significatif du système (modification de prompt, ajout de documents RAG, changement de configuration d'agents)

* Quotidiennement en période de développement actif

* Lors de la sélection ou du changement de modèle LLM ou d'autres paramètres

* Avant chaque mise en production (MEP)

* Selon un calendrier régulier en production (hebdomadaire, mensuel)

Gestion des coûts : Utiliser différents subsets du dataset selon le contexte (smoke tests rapides vs validation complète) pour optimiser le ratio coût/couverture.

### 6. Tests par composant vs end-to-end

#### Tests end-to-end :

* Valident le comportement du système complet tel que l'utilisateur l'expérimente

* Détectent les problèmes d'intégration entre composants

#### Tests par composant isolé :

* Module de classification d'intention

* Qualité du retrieval RAG (pertinence des documents récupérés)

* Filtres de sécurité et de confidentialité

* Orchestration des agents (séquence d'actions)

Exigence architecturale : Le produit doit être conçu pour permettre la testabilité de chaque composant de manière isolée, via frontend ou API dédiées. Cette isolation facilite le diagnostic rapide : un défaut provient-il du RAG, du LLM ou de l'orchestration ?

### 7. Évaluation des réponses

#### Pour les outputs déterministes :

* Comparaison exacte avec l'output attendu (ex : catégorie de classification, documents RAG récupérés, action déclenchée)

* Validation binaire (succès/échec)

#### Pour les outputs probabilistes (réponses en langage naturel) :

Utiliser le pattern "LLM as a Judge" avec plusieurs graders spécialisés :

* Chaque grader évalue un critère spécifique (exactitude, pertinence, ton, respect de la confidentialité, absence d'hallucination)

* Chaque grader utilise un prompt dédié définissant précisément le critère à évaluer

* Plusieurs graders peuvent être combinés pour une évaluation multidimensionnelle (LLM as a Jury)

##### Risques des graders LLM :

* Faux positifs (accepter une mauvaise réponse) et faux négatifs (rejeter une bonne réponse) sont possibles

* Nécessité de suivre et calibrer régulièrement la fiabilité des graders

* Relecture humaine systématique : Chaque réponse rejetée par un grader doit être relue par un humain, idéalement un expert métier pour les cas complexes

##### Objectifs de la relecture :

* Confirmer le rejet et identifier l'action corrective (modifier le prompt, enrichir le RAG, changer le modèle)

* OU accepter la réponse comme valide et adapter le grader qui a généré un faux négatif

* Enrichir le dataset avec ce nouveau cas pour éviter les régressions

### 8. Analyse statistique et scoring

Par approche statistique sur l'ensemble du dataset :

* Calculer un score pour chaque critère d'évaluation (ex : 85% d'exactitude, 92% de pertinence)

* Identifier les patterns d'échec récurrents (use cases problématiques, types de questions mal comprises)

* Suivre l'évolution des scores au fil des versions pour détecter les régressions ou améliorations

* Comparer différentes configurations (prompts, modèles, paramètres RAG) via A/B testing

### 9. Processus itératif et amélioration continue

Ce processus n'est pas linéaire mais itératif :

* Les jeux de données doivent évoluer tout au long du projet

* Les graders nécessitent des ajustements basés sur les relectures humaines

* Les critères d'acceptation se précisent avec l'expérience

* Les use cases peuvent être redécoupés ou fusionnés selon les observations

Même après la première mise en production :

* Observer l'usage réel pour identifier de nouveaux use cases ou variantes

* Enrichir continuellement les datasets avec les cas limites rencontrés

* Adapter les graders aux patterns réels de conversation

* Maintenir une boucle de feedback rapide entre utilisateurs, métier, qualité et technique

Cette approche pragmatique et itérative permet de construire progressivement une couverture de test robuste, tout en s'adaptant à la nature probabiliste et évolutive des chatbots IA.
à conserver en page de garde: Du prototypage à la production — un cadre méthodologique pour décideurs techniques et architectes IA

=== INTRO ===

1. Qu'est-ce qu'un chatbot spécialisé
"Crée une slide de présentation professionnelle comparant deux architectures d'IA : à gauche, un Pipeline RAG Linéaire (étapes : Question > Recherche > Contexte > Réponse) représenté par une flèche droite et simple. À droite, un Système Multi-Agent représenté par un hub central (Orchestrateur) connecté en étoile à plusieurs modules (Sécurité, Données SQL, Recherche Web). Utilise un style 'Tech Blueprint' avec des couleurs bleu marine et blanc, des icônes minimalistes et une mise en page épurée."
---
Ce n'est pas juste un modèle, mais un ensemble de composants dont certains utilisent un, ou même plusieurs modèles
---
2. Différence avec ChatGPT
* Périmètre fonctionnel délimité vs universalité
* Sources de connaissances contrôlées vs apprentissage général
* Responsabilité et exactitude vs couverture large
* Intégration métier vs interface conversationnelle pure
* Personnalisation et contexte utilisateur vs anonymat
"ChatGPT répond mieux" n'est pas un critère pertinent si ChatGPT ne peut pas accéder aux données métier nécessaires, ne respecte pas les contraintes de confidentialité, ou produit des réponses hors du périmètre accepté
---
La qualité perçue d'un chatbot spécialisé dépend de facteurs absents chez les généralistes : pertinence du retrieval, fraîcheur des données, respect des règles métier, capacité à exécuter des actions, orchestration ds composants, ...
---

3. Attributs de qualité
FAIRE UN SCHEMA (mindmap) en résumanrt chaque catégorie:
* Performance fonctionnelle / Qualité de la réponse
    * Exactitude : les réponses sont-elles factuellement correctes ?
    * Pertinence : les réponses correspondent-elles à l'intention de l'utilisateur ?
    * Complétude : les informations essentielles sont-elles fournies ?
    * Cohérence : les réponses successives sont-elles logiquement cohérentes ? comment se déroule une conversation ?
    * Comportement dangereux : à quelle fréquence le bot peut produire une réponse dommageable pour l'organisation, l'utilisateur ou le client ?
    * Comportement hors-périmètre : qualité des refus et redirections
* Latence et réactivité
    * Temps de réponse : délai entre question et début de réponse
    * Streaming : l'utilisateur voit-il la réponse se construire ?
    * Timeout et gestion d'erreur : comportement en cas de lenteur excessive
    * Perception utilisateur : la latence est-elle acceptable pour le cas d'usage ?
* Coût opérationnel *****
    * Coût par requête : tokens consommés (input + output)
    * Coûts fixes
*  Confidentialité et sécurité
    * Protection des données : pas de fuite d'informations confidentielles
    * Compartimentage : respect des droits d'accès par utilisateur/rôle
    * Résistance aux attaques : prompt injection, jailbreaking, extraction de données
    * Traçabilité : audit des accès et des réponses fournies
    * Conformité réglementaire : RGPD, AI Act, normes sectorielles

* Explicabilité et transparence
    * Traçabilité des sources : quels documents RAG ont été utilisés ?
    * Justification des décisions (explicabilité): pourquoi cette réponse ? pourquoi ce refus ?
    * Chaîne de raisonnement (interpretabilité): pour les agents, quelles étapes ont mené à l'action ?
    * Niveau de confiance : le bot exprime-t-il son incertitude ?
    * Auditabilité : possibilité de reproduire et comprendre un comportement a posteriori
* Fiabilité et robustesse
    * Disponibilité : uptime du service, gestion des pannes
    * Gestion d'erreurs : comportement gracieux en cas d'échec (API, RAG, agents)
    * Résistance aux inputs inattendus : malformés, ambigus, contradictoires
    * Stabilité : absence de comportements erratiques ou de dégradations soudaines
    * Fallback mechanisms : alternatives quand le système principal échoue
* Évolutivité (Scalabilité)
    * Montée en charge : performance maintenue avec l'augmentation des utilisateurs
    * Évolution de la base de connaissances : ajout de documents sans dégradation
    * Adaptation fonctionnelle : facilité d'ajout de nouveaux use cases
    * Mise à jour des modèles : capacité à intégrer de nouvelles versions de LLM
    * Extensibilité des agents : ajout de nouveaux outils/actions
* Expérience utilisateur (UX)
    * Ton et style : approprié au contexte et à l'audience
    * Clarté : réponses compréhensibles, structure lisible
    * Proactivité : suggestions pertinentes, questions de clarification
    * Gestion du dialogue : mémoire conversationnelle, suivi du contexte
    * Satisfaction : l'utilisateur a-t-il obtenu ce qu'il cherchait ?
* Maintenabilité
    * Versioning : prompts, configurations, datasets de test
    * Debuggabilité : facilité d'identification de la source d'un problème
    * Documentation : clarté des choix de conception et configurations
    * Monitoring : observabilité des métriques clés en production
    * Facilité de correction : rapidité de déploiement d'un fix
* Équité et absence de biais
    * Biais démographiques : traitement équitable selon genre, âge, origine, etc.
    * Biais linguistiques : qualité égale dans différentes langues ou registres
    * Biais de représentation : diversité dans les exemples et recommandations
    * Accessibilité : utilisable par personnes en situation de handicap
=== COMMENT CA FONCTIONNE: 5 minutes ===

4. Au coeur du process: observabilité
    * Chaque utilisation du chatbot est consignée dans un outil d'observabilité
    * Cahque trace contient la question et la réponse, des informations techniques (comment la réponse a été obtenue), temporelles et financières, ainsi que sur l'utilisateur
    * dans le respect du RGPD
---
5. qu'est-ce qu'on en fait
- en prototypage: observation des workshops - génération des Use cases et des critères d'acceptation
- en développement / évaluation: approche statistique avec jeux de données complexes.
- en production: monitoring et analyse des tendances
---
=== CONCRETEMENT: 10 minutes ===
- WORKSHOP
-- use case et questions types
-- comportement désiré et à éviter
- SEF
-- Gestion des données: dataset par use case, par composant, par critère d'acceptation
-- exécution automatisée
-- évaluation humaine
-- statistiques
- SophiaBI
-- KPI de production
-- Questions fréquentes
---
== Rôle de chaun ==
Expertise technique
Expertise métier + utilisateurs clés
Expertise qualité: organiser les données et non "tester"



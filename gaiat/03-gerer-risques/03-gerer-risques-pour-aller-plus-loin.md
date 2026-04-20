# Pour aller plus loin — Réglementation européenne, souveraineté et gestion des risques

> **À qui s'adresse ce document ?** Aux testeurs, responsables qualité et architectes qui interviennent dans des organisations soumises au droit européen et qui souhaitent aller au-delà du panorama du [module 3](03-gerer-risques.md). L'accent est mis sur **l'AI Act**, les **obligations RGPD** liées aux LLMs, les **référentiels normatifs** applicables et la **souveraineté numérique** — sujet central pour les organisations publiques, les OIV/OSE, les secteurs régulés (banque, santé, défense) et, plus largement, toute entité européenne qui veut maîtriser son exposition aux fournisseurs extra-européens.

> **Note méthodologique.** Les textes réglementaires cités évoluent rapidement. **Toute décision opérationnelle doit s'appuyer sur la version officielle en vigueur et, si nécessaire, un avis juridique qualifié.** Ce document recense les ressources à consulter, il ne se substitue pas à elles. Les éléments **ajoutés ou actualisés par rapport au syllabus ISTQB CT-GenAI v1.0 (juillet 2025)** sont explicitement signalés par un bloc *« Actualisation »*. Dates et chiffres arrêtés en avril 2026.

---

## 1. L'AI Act en profondeur

### 1.1 Architecture du règlement

Le **Règlement (UE) 2024/1689** — communément appelé **AI Act** — a été publié au *Journal officiel de l'Union européenne* le 12 juillet 2024 et est entré en vigueur le **1er août 2024**. C'est le premier cadre juridique horizontal au monde spécifiquement dédié à l'IA.

**Architecture en quatre niveaux de risque :**

| Niveau | Exemples | Traitement |
|---|---|---|
| **Risque inacceptable** | Notation sociale, manipulation subliminale, reconnaissance des émotions sur le lieu de travail ou dans l'éducation, police prédictive basée uniquement sur le profilage, identification biométrique à distance en temps réel dans l'espace public (avec exceptions) | **Interdits** |
| **Haut risque** (Annexe III) | Biométrie, infrastructures critiques, éducation, emploi/RH, accès aux services essentiels (crédit, assurance), forces de l'ordre, migration, justice, processus démocratiques | Obligations fortes : système de gestion des risques, qualité des données, traçabilité, documentation technique, supervision humaine, robustesse, cybersécurité, évaluation de conformité |
| **Risque limité** | Chatbots, deepfakes, contenus générés par IA | Obligations de **transparence** (signaler que l'utilisateur interagit avec une IA ou que le contenu est généré) |
| **Risque minimal** | Filtres anti-spam, IA dans les jeux vidéo | Pas d'obligation spécifique ; bonnes pratiques encouragées |

> **Cas à part — les modèles d'IA à usage général (GPAI, General-Purpose AI).** Les grands modèles (LLMs de fondation) font l'objet d'un régime dédié, avec des obligations renforcées pour les modèles dits *« à risque systémique »* — seuil actuellement fixé à **10²⁵ FLOPs d'entraînement cumulé** (les modèles de type GPT-4, Claude Sonnet 4+, Gemini Ultra, Llama 4 dépassent ou approchent ce seuil). Obligations : documentation, politique de respect du droit d'auteur, évaluations de sécurité, tests adverses, signalement d'incidents.

### 1.2 Calendrier d'application

L'AI Act se déploie par vagues.

| Date | Entrée en application |
|---|---|
| 1er août 2024 | Entrée en vigueur |
| **2 février 2025** | Interdictions (pratiques inacceptables) + obligations de *literacy* (sensibilisation du personnel utilisateur) |
| **2 août 2025** | Obligations pour les modèles GPAI + gouvernance (bureau de l'IA, comité, autorités nationales compétentes) + sanctions |
| **2 août 2026** | Application générale, y compris les systèmes à haut risque listés en Annexe III |
| **2 août 2027** | Application aux systèmes à haut risque intégrés dans des produits déjà soumis à la législation harmonisée (Annexe I : dispositifs médicaux, jouets, machines, etc.) |

> **Actualisation.** La publication des actes d'exécution, du **Code de bonnes pratiques GPAI** et des standards harmonisés CEN-CENELEC s'échelonne sur 2025–2026. Les versions officielles sont à suivre sur [digital-strategy.ec.europa.eu/en/policies/ai-act](https://digital-strategy.ec.europa.eu/en/policies/ai-act).

### 1.3 Qui est concerné ? Le jeu des rôles

L'AI Act distingue plusieurs rôles, souvent cumulés dans la pratique :

| Rôle | Définition simplifiée | Exemple côté test |
|---|---|---|
| **Fournisseur (provider)** | Développe un système d'IA ou en fait développer un, puis le met sur le marché sous son propre nom | Une société qui édite un outil de test assisté par IA |
| **Déployeur (deployer)** | Utilise un système d'IA sous sa propre autorité | Une DSI qui utilise un assistant LLM dans sa chaîne CI/CD |
| **Importateur / distributeur** | Met à disposition dans l'UE un système d'IA provenant d'un tiers pays | Revendeur européen d'un outil américain |
| **Représentant autorisé** | Mandaté par un fournisseur hors UE | Point de contact légal pour les autorités |

> **Point d'attention.** Une organisation qui **affine (fine-tune) un modèle de fondation** ou qui **modifie substantiellement** un système d'IA haute-risque devient *fournisseur* au sens de l'AI Act, avec les obligations correspondantes. Les équipes de test et de data science doivent en être informées avant toute opération de fine-tuning sur un domaine sensible.

### 1.4 Ce que cela change pour l'équipe test

| Exigence AI Act (systèmes à haut risque) | Traduction côté test |
|---|---|
| Système de gestion des risques sur tout le cycle de vie (art. 9) | Intégrer l'analyse de risques IA dans la stratégie de test (stratégie de test / test strategy) |
| Qualité des données d'entraînement et de test (art. 10) | Traçabilité des jeux de données, critères de représentativité documentés |
| Documentation technique (art. 11 + Annexe IV) | Contribution du test au dossier technique : plans de test, preuves d'exécution, rapports |
| Journaux (art. 12) | Conservation des logs, y compris des prompts/réponses des LLMs utilisés |
| Transparence et information de l'utilisateur (art. 13) | Contrôle qualité des mentions de transparence |
| Supervision humaine (art. 14) | Définir les points de contrôle humain ; tester leur effectivité |
| Exactitude, robustesse, cybersécurité (art. 15) | Campagnes de tests robustesse, tests adverses (adversarial testing), tests de sécurité |

**Référence clé** — CEN-CENELEC JTC 21 développe les standards harmonisés qui donneront présomption de conformité à l'AI Act. L'ISO/IEC 42001 (voir section 3) y contribue.

---

## 2. RGPD et IA générative

### 2.1 Six questions à se poser avant d'envoyer des données à un LLM

Le **Règlement général sur la protection des données** (RGPD / Règlement UE 2016/679) reste pleinement applicable à toute utilisation d'IA générative qui traite des données à caractère personnel.

1. **Base légale (art. 6)** — consentement, contrat, obligation légale, intérêt légitime ? Pour un LLM externe, l'intérêt légitime exige une analyse d'impact documentée.
2. **Information des personnes (art. 13-14)** — les personnes concernées ont-elles été informées que leurs données peuvent être traitées par un LLM et, le cas échéant, transférées hors UE ?
3. **Finalité (art. 5-1-b)** — l'usage du LLM entre-t-il dans la finalité déclarée du traitement ?
4. **Minimisation (art. 5-1-c)** — n'envoyez-vous que les données strictement nécessaires ?
5. **Transfert hors UE (art. 44 et suivants)** — si le fournisseur traite les données hors UE, un mécanisme de transfert adéquat est-il en place (décision d'adéquation, clauses contractuelles types, règles d'entreprise contraignantes) ?
6. **Rôles (art. 4)** — qui est responsable de traitement, qui est sous-traitant ? Un contrat de sous-traitance conforme à l'art. 28 est-il signé avec le fournisseur ?

### 2.2 Guides de référence des autorités européennes

- **CNIL (France) — *Recommandations sur le développement des systèmes d'IA*** ([cnil.fr/fr/intelligence-artificielle](https://www.cnil.fr/fr/intelligence-artificielle)). Série de fiches pratiques : constitution de bases de données, intérêt légitime, DPIA, etc. **La référence francophone.**
- **CNIL — *Fiches pratiques IA générative*** — publiées et mises à jour depuis 2024, dont des fiches sectorielles.
- **CNIL — *Recommandations relatives à l'usage de l'IA générative par les professionnels*** (2025).
- **CEPD / EDPB — *Opinion 28/2024 on certain data protection aspects related to the processing of personal data in the context of AI models*** (décembre 2024) — positionnement européen coordonné.
- **ENISA — *Multilayer framework for good cybersecurity practices for AI*** (2023) et publications suivantes — sécurité des systèmes d'IA.
- **Garante** (Italie), **AEPD** (Espagne), **BfDI** (Allemagne) — publient également des orientations, parfois plus précoces (l'Italie a été le premier régulateur à suspendre ChatGPT en 2023).

> **Actualisation.** L'opinion 28/2024 de l'EDPB a clarifié plusieurs points longtemps débattus : anonymat des modèles entraînés sur données personnelles, base légale de l'entraînement, droits des personnes. **À consulter absolument** pour toute discussion avec un DPO.

### 2.3 Articulation AI Act ↔ RGPD

Les deux textes se superposent : l'AI Act ne remplace pas le RGPD. En pratique :

- L'AI Act fixe des obligations sur le **système d'IA** (conception, documentation, supervision, robustesse).
- Le RGPD fixe des obligations sur le **traitement de données personnelles** (base légale, minimisation, droits des personnes).
- Une **DPIA (Data Protection Impact Assessment)** reste exigée pour les traitements à haut risque au sens RGPD, et peut servir de base à l'évaluation de conformité AI Act.
- Le **DPO** (Data Protection Officer) reste compétent sur les aspects RGPD ; une **fonction IA/conformité** dédiée émerge dans les grandes organisations.

---

## 3. Normes et référentiels

### 3.1 Normes internationales

| Norme | Objet | Usage |
|---|---|---|
| **ISO/IEC 42001:2023** | *Artificial intelligence — Management system* | Norme certifiable, comparable à ISO 27001 pour la sécurité. Référentiel de gouvernance IA. |
| **ISO/IEC 23894:2023** | *Guidance on risk management for AI* | Méthodologie de gestion des risques spécifique IA. |
| **ISO/IEC 23053:2022** | *Framework for AI systems using ML* | Taxonomie et cadre conceptuel. |
| **ISO/IEC 22989:2022** | *AI — Concepts and terminology* | Vocabulaire de référence. |
| **ISO/IEC 25059:2023** | *Quality model for AI systems* | Extension de la série SQuaRE (25010) aux systèmes d'IA — très pertinent pour le testeur. |
| **ISO/IEC TS 29119-11:2020** | *Software testing — Testing of AI-based systems* | **Spécifiquement orienté test** : types de tests, techniques, challenges. |
| **ISO/IEC 5259 (série)** | *Data quality for analytics and ML* | Qualité des données d'entraînement et de test. |
| **ISO/IEC 42005** (en cours) | *AI system impact assessment* | Méthodologie d'évaluation d'impact. |

### 3.2 Normes européennes (CEN-CENELEC)

Les **standards harmonisés CEN-CENELEC JTC 21** sont en cours d'élaboration pour donner présomption de conformité à l'AI Act. Ils couvrent notamment : gestion des risques, gouvernance des données, transparence, supervision humaine, cybersécurité, robustesse, qualité, essais (tests).

**À suivre sur** : [cencenelec.eu/areas-of-work/cen-cenelec-topics/artificial-intelligence](https://www.cencenelec.eu/).

### 3.3 Référentiels hors UE utiles

- **NIST AI Risk Management Framework 1.0** (janvier 2023) + **Generative AI Profile** (juillet 2024) — cadre volontaire structuré en *Govern / Map / Measure / Manage*. Très bien articulé, sert de source d'inspiration à de nombreux référentiels européens.
- **NIST AI 600-1** — risques spécifiques à l'IA générative.
- **MITRE ATLAS** (atlas.mitre.org) — base de connaissances d'attaques contre les systèmes d'IA, sur le modèle MITRE ATT&CK.
- **OWASP Top 10 for LLM Applications** — édition 2025 ([genai.owasp.org](https://genai.owasp.org)). Complété par des guides : *LLM AI Cybersecurity & Governance Checklist*, *GenAI Red Teaming Guide*, *Agentic AI Threats and Mitigations*.
- **OWASP Machine Learning Security Top 10**.
- **Singapore AI Verify** — cadre d'évaluation technique open source, utile comme source d'outils.

---

## 4. Souveraineté numérique et alternatives européennes

### 4.1 Pourquoi la souveraineté est devenue centrale

Plusieurs signaux convergents, sur 2022–2026, ont placé la souveraineté sur l'IA au cœur de la stratégie européenne :

- **Extraterritorialité du droit américain** — FISA 702 et Cloud Act permettent aux autorités US d'accéder à des données détenues par des entreprises américaines, même si elles sont stockées en Europe. L'invalidation du *Privacy Shield* (arrêt *Schrems II*, CJUE 2020) puis la validation fragile du *EU-US Data Privacy Framework* (2023) maintiennent une incertitude structurelle.
- **Dépendance technologique** — l'essentiel des modèles frontières, des cloud providers dominants et des GPUs sont américains. Quelques acteurs asiatiques (Alibaba, DeepSeek, Baidu) ajoutent une dépendance géopolitique alternative.
- **Exigences sectorielles** — santé (HDS en France), défense, renseignement, banque (DORA), secteur public (doctrine *Cloud au centre* en France) imposent des garanties de localisation et de confidentialité incompatibles avec un LLM grand public.
- **AI Act + RGPD** — le cadre européen pousse mécaniquement à privilégier des solutions traçables et auditables, plus faciles à obtenir sur des modèles ouverts ou européens.

### 4.2 Fournisseurs européens d'IA générative

Sélection non exhaustive, ordre alphabétique.

| Acteur | Pays | Positionnement |
|---|---|---|
| **Aleph Alpha** | 🇩🇪 Allemagne | Modèles orientés entreprises et secteur public ; accent sur souveraineté et explicabilité |
| **ALIA** | 🇪🇸 Espagne | Modèle public espagnol multilingue (BSC) |
| **H Company** | 🇫🇷 France | Agents IA |
| **Kyutai** | 🇫🇷 France | Laboratoire de recherche ouverte (modèles audio/temps réel) |
| **LightOn** | 🇫🇷 France | Plateforme LLM privée pour entreprises |
| **Mistral AI** | 🇫🇷 France | Modèles open-weight (Mistral, Mixtral, Pixtral, Magistral, Ministral) + offre commerciale *Le Chat* et *La Plateforme* |
| **Poolside** | 🇫🇷 France | Modèles orientés code |
| **Silo AI / AMD** | 🇫🇮 Finlande | *Poro*, *Viking* — modèles nordiques multilingues (racheté par AMD en 2024) |

### 4.3 Clouds souverains et hébergement qualifié

Pour héberger un LLM (open-weight ou fine-tuné) avec des garanties de souveraineté :

- **Qualification SecNumCloud** (ANSSI, France) — niveau le plus strict de qualification de services cloud en France. Liste officielle : [cyber.gouv.fr/produits-qualifies](https://cyber.gouv.fr/produits-qualifies). Parmi les offres qualifiées pour l'IaaS/PaaS : **OVHcloud**, **Outscale (Dassault Systèmes)**, **NumSpot**, **Bleu** (coentreprise Capgemini + Orange + Microsoft, en cours), **S3NS** (coentreprise Thales + Google Cloud, en cours), **Oodrive**, etc.
- **Schéma européen EUCS** (EU Cybersecurity Certification Scheme for Cloud Services) — en cours de finalisation par l'ENISA. Les niveaux *High / High+* incorporent des exigences de souveraineté.
- **HDS** (Hébergeur de Données de Santé) — certification française pour les données de santé.
- **Gaia-X** — initiative européenne pour des règles de fédération et de portabilité des données cloud.

> **Actualisation.** Les qualifications SecNumCloud comme les schémas EUCS évoluent fréquemment (nouvelles offres qualifiées, révisions du référentiel). Vérifier la liste officielle avant toute décision — la situation peut avoir évolué depuis la date de rédaction (avril 2026).

### 4.4 Modèles open-weight pertinents

Déployer un modèle open-weight en interne ou sur un cloud souverain est l'un des moyens les plus directs d'obtenir une maîtrise forte.

**Familles principales (avril 2026) :**
- **Mistral / Mixtral / Pixtral / Magistral** (🇫🇷) — licences Apache 2.0 pour les plus petits, licences commerciales pour les plus grands.
- **Llama** (🇺🇸 Meta) — licence communautaire Llama, restrictions commerciales au-delà d'un seuil d'utilisateurs.
- **Qwen, Qwen-VL, Qwen3** (🇨🇳 Alibaba) — très compétitifs, licences variables.
- **DeepSeek-V3, DeepSeek-R1** (🇨🇳) — premiers modèles de raisonnement open-weight compétitifs.
- **Gemma** (🇺🇸 Google) — licence Gemma.
- **Phi** (🇺🇸 Microsoft) — petits modèles efficaces, MIT.
- **Falcon** (🇦🇪 TII) — open source Apache 2.0.

**Outils d'exécution locale ou privée :** Ollama, LM Studio, vLLM, llama.cpp, Text Generation Inference (Hugging Face), Nvidia NIM.

> **Attention.** *Open-weight* ≠ *open source* au sens OSI. La plupart des modèles diffusent les poids mais pas les données d'entraînement ni la recette complète, et certains imposent des restrictions d'usage. L'OSI a publié en 2024 la définition de l'**Open Source AI** ; très peu de modèles la respectent à ce jour.

### 4.5 Stratégies de souveraineté par niveau d'exigence

| Niveau | Scénario | Architecture |
|---|---|---|
| **Basique** | Entreprise privée, données peu sensibles | LLM commercial (OpenAI, Anthropic, Google) avec option *no training* et DPA signé |
| **Intermédiaire** | Données personnelles, secteur régulé | LLM européen (Mistral Le Chat Enterprise) ou cloud US européen avec localisation UE |
| **Avancé** | OIV, santé, secteur public | LLM open-weight hébergé sur cloud SecNumCloud / HDS |
| **Maximal** | Défense, renseignement | LLM open-weight dans une enclave on-premise, air-gapped |

---

## 5. Sécurité des systèmes d'IA : la pile offensive et défensive

### 5.1 Taxonomies d'attaques à connaître

- **OWASP Top 10 for LLM Applications 2025** — `LLM01` Prompt Injection, `LLM02` Sensitive Information Disclosure, `LLM03` Supply Chain, `LLM04` Data and Model Poisoning, `LLM05` Improper Output Handling, `LLM06` Excessive Agency, `LLM07` System Prompt Leakage, `LLM08` Vector and Embedding Weaknesses, `LLM09` Misinformation, `LLM10` Unbounded Consumption.
- **MITRE ATLAS** — catalogue structuré de *tactics, techniques, procedures* contre les systèmes d'IA.
- **NIST AI 100-2 — *Adversarial Machine Learning: A Taxonomy and Terminology of Attacks and Mitigations*** (2024) — référence technique.
- **ENISA — *Securing Machine Learning Algorithms*** (2021), *Multilayer Framework for Good Cybersecurity Practices for AI* (2023), publications 2024–2025 sur GenAI.

### 5.2 Pratiques de red teaming

Le *red teaming* de LLMs est passé d'artisanal à industriel sur 2023–2026. Ressources :

- **Anthropic — *Frontier Red Team* et publications de recherche** — méthodologies, jeux de données.
- **UK AI Safety Institute — *Inspect AI*** ([inspect.ai-safety-institute.org.uk](https://inspect.ai-safety-institute.org.uk)) — framework d'évaluation et de red teaming open source, devenu référence.
- **US AI Safety Institute (NIST)** — équivalent américain, publie des *evaluations*.
- **OWASP — *GenAI Red Teaming Guide*** — méthodologie pragmatique.
- **garak** (github.com/leondz/garak) — scanner automatisé d'attaques sur LLMs.
- **PyRIT** (github.com/Azure/PyRIT, Microsoft) — framework d'automatisation du red teaming.
- **Promptfoo** — inclut des suites de tests de sécurité (prompt injection, PII leak).

### 5.3 Secteurs régulés : où ajouter une couche ?

- **Banque** — **DORA** (Digital Operational Resilience Act, Règlement UE 2022/2554, en application depuis le 17 janvier 2025) — gestion du risque TIC, test de résilience, registres de prestataires. Un LLM est un prestataire TIC comme un autre.
- **Santé** — **MDR/IVDR** si l'IA est intégrée dans un dispositif médical ; **HDS** pour l'hébergement ; recommandations HAS.
- **OIV / OSE** — **NIS 2** (Directive UE 2022/2555), transposée dans les droits nationaux ; impact sur les chaînes CI/CD incluant des LLMs.
- **Secteur public France** — **doctrine Cloud au centre** (circulaire du 31 mai 2023), référentiel **« Cloud de confiance »**, programme **Albert** (DINUM, LLM public français).
- **Administration en général** — **RGAA** (accessibilité), **RGS** (sécurité), **RGI** (interopérabilité).

---

## 6. Impact environnemental : mesurer et piloter

### 6.1 Ordres de grandeur 2024–2026

Le chapitre 3 a rappelé les ordres de grandeur. Pour aller plus loin :

- **AI Index Report** (Stanford HAI) — édition annuelle, chiffres les plus cités sur l'énergie, les émissions, les tendances d'usage.
- **IEA — *Electricity 2024* et rapports suivants** — impact des centres de données sur les réseaux électriques.
- **ADEME** — études françaises sur le numérique responsable.
- **The Shift Project — *Impact environnemental du numérique*** — référence francophone.
- **Green AI (Schwartz et al., 2020)** — article fondateur.
- **Luccioni, Jernite, Strubell (2023–2024)** — publications sur le coût carbone de l'inférence LLM, notamment sur Hugging Face.
- **ML CO2 Impact calculator** (mlco2.github.io/impact) — outil simple d'estimation.
- **CodeCarbon** (codecarbon.io) — librairie Python d'estimation pendant l'exécution.
- **ISO/IEC 21031** (en cours) et **ETSI ES 203 199** — méthodologies de mesure du numérique.

### 6.2 Leviers appliqués au test logiciel

Au-delà des leviers mentionnés au chapitre 3 :
- Choisir un fournisseur qui publie ses chiffres d'intensité carbone et privilégie les énergies bas carbone.
- Exiger contractuellement la transparence sur la localisation et l'empreinte énergétique.
- Intégrer une **métrique d'empreinte** dans les rapports de campagne de test.
- Pour les pipelines massifs, privilégier les régions cloud à forte part nucléaire + renouvelable (France, Suède, Norvège) — sous réserve des autres critères.

---

## 7. Ressources clés à garder en marque-page

### 7.1 Textes officiels UE et France

- AI Act — texte officiel : [eur-lex.europa.eu/eli/reg/2024/1689](https://eur-lex.europa.eu/eli/reg/2024/1689).
- Portail AI Act de la Commission : [digital-strategy.ec.europa.eu/en/policies/ai-act](https://digital-strategy.ec.europa.eu/en/policies/ai-act).
- **AI Act Explorer** : [artificialintelligenceact.eu](https://artificialintelligenceact.eu) — navigation article par article, non officiel mais pratique.
- **EU AI Office** : [digital-strategy.ec.europa.eu/en/policies/ai-office](https://digital-strategy.ec.europa.eu/en/policies/ai-office).
- RGPD consolidé : [eur-lex.europa.eu/eli/reg/2016/679/oj](https://eur-lex.europa.eu/eli/reg/2016/679/oj).
- CNIL : [cnil.fr/fr/intelligence-artificielle](https://www.cnil.fr/fr/intelligence-artificielle).
- CNIL — *IA générative : recommandations pour les professionnels*.
- EDPB : [edpb.europa.eu](https://www.edpb.europa.eu).
- ANSSI — recommandations IA : [cyber.gouv.fr](https://cyber.gouv.fr).
- ENISA — publications IA : [enisa.europa.eu/topics/artificial-intelligence](https://www.enisa.europa.eu/topics/artificial-intelligence).

### 7.2 Référentiels et normes

- **ISO** : [iso.org/committee/6794475.html](https://www.iso.org/committee/6794475.html) (comité ISO/IEC JTC 1/SC 42).
- **CEN-CENELEC JTC 21** — portail AI.
- **NIST AI RMF** : [nist.gov/itl/ai-risk-management-framework](https://www.nist.gov/itl/ai-risk-management-framework).
- **OWASP GenAI Security Project** : [genai.owasp.org](https://genai.owasp.org).
- **MITRE ATLAS** : [atlas.mitre.org](https://atlas.mitre.org).

### 7.3 Communautés et veille

- **Future of Life Institute** — suivi de l'AI Act, alertes.
- **AI Now Institute** — recherche critique.
- **CNIL — Linc** (Laboratoire d'Innovation Numérique) — publications en français.
- **Hub France IA**.
- **Confiance.ai** — programme français de recherche sur l'IA de confiance.
- **Gaia-X** — fédération européenne de données.
- **CFTL — groupes de travail IA**.

---

## 8. Parcours de lecture recommandé

### 8.1 Testeur confronté à un premier projet IA en environnement européen
1. [Chapitre 3 — Gérer les risques](03-gerer-risques.md).
2. Section 1 ci-dessus (AI Act) + site AI Act Explorer.
3. Fiches CNIL sur l'IA (francophones, très pédagogiques).
4. OWASP Top 10 LLM édition 2025.
5. Atelier pratique : construire une checklist de test IA pour un projet concret (voir [Activité 6 du chapitre 3](03-gerer-risques.md#activité-6--cartographie-réglementaire-de-mon-projet)).

### 8.2 Responsable qualité / référent IA dans une organisation soumise à l'AI Act
1. AI Act — lecture intégrale des articles 1 à 27 (définitions, interdictions, systèmes à haut risque) et articles 50 à 60 (GPAI).
2. ISO/IEC 42001:2023 — en achat officiel ou via la norme AFNOR NF équivalente.
3. ISO/IEC TS 29119-11 — sur le test des systèmes d'IA.
4. NIST AI RMF + Generative AI Profile — pour structurer la gouvernance interne.
5. Opinion EDPB 28/2024 sur l'IA.

### 8.3 Architecte visant une posture de souveraineté maximale
1. Section 4 ci-dessus et référentiel SecNumCloud ANSSI.
2. Liste des offres qualifiées SecNumCloud et HDS.
3. Catalogue Mistral AI + documentation *Le Chat Enterprise* et *La Plateforme* ; alternatives Aleph Alpha, LightOn.
4. Guide ENISA *Multilayer framework for good cybersecurity practices for AI*.
5. DORA + NIS 2 si secteur concerné.
6. Benchmarks indépendants sur les modèles open-weight (MTEB, Chatbot Arena, Open LLM Leaderboard).

---

## 9. Points de vigilance à six mois

Quelques sujets dont l'évolution mérite un suivi rapproché :

- **Code de bonnes pratiques GPAI** — publication des versions successives et signataires.
- **Standards harmonisés CEN-CENELEC** pour l'AI Act — publication progressive jusqu'en 2026.
- **Schéma EUCS** — niveaux *High / High+* et clauses de souveraineté.
- **Articulation AI Act × RGPD × DSA × Data Act** — jurisprudence et guidelines en construction.
- **Transferts UE-US** — solidité du *EU-US Data Privacy Framework* face aux recours.
- **Sanctions AI Act** — premières décisions attendues à partir de 2026, jusqu'à 35 M€ ou 7 % du CA mondial.
- **Littératie IA** (*AI literacy*, art. 4 AI Act, en vigueur depuis février 2025) — obligation de former les utilisateurs ; à intégrer dans les plans de formation test.

---

## Suite du parcours

- **Chapitre précédent** — [02 — Ingénierie du prompting](../02-ingenierie-prompting/) et son [guide de références](../02-ingenierie-prompting/02-ingenierie-prompting-pour-aller-plus-loin.md).
- **Contenu principal** — [Gérer les risques liés à l'IA générative dans les tests logiciels](03-gerer-risques.md).
- **Chapitre 1** — [Fondements](../01-fondements/) et son [pour en savoir plus](../01-fondements/01-introduction-ia-generative-pour-en-savoir-plus.md).

# La certification ISTQB-AI est-elle toujours pertinente en 2026 ?

Lorsque l'on parle de test et IA, deux certifications ISTQB sont régulièrement citées... et souvent confondues, malgré un périmètre fortement différent. J'ai passé l'examen Certified Tester AI Testing (CT-AI), et je la recommande fortement à toute personne impliquée dans le test de logiciels intégrant de l'IA.

Actif dans le test logiciel depuis près de 10 ans, je suis confronté pour la première fois, fin 2024, à un défi de taille : tester un chatbot. Une infinité de possibilités, des résultats non ou peu prévisibles, des attentes démesurées, et même de nouveaux métiers dans l'équipe : je dois revoir toutes mes certitudes.

## CT-AI ou CT-GenAI ?

C'est probablement la question la plus posée sur le test et l'IA depuis la sortie du nouvel opus ISTQB *Tester avec l'IA Générative* en juillet 2025. Or, le contenu de ce dernier est très différent de son aîné, *Test d'IA*, sorti en 2021 et traduit en français en 2022.

Comme leurs titres respectifs le précisent, **CT-AI s'adresse à ceux qui testent des produits basés sur l'IA, tandis que CT-GenAI aidera tout testeur à intégrer l'IA dans ses processus**, que le système sous test soit traditionnel et déterministe ou embarque un modèle ou un service d'IA.

En ce qui me concerne, les deux sont pertinents ! Mais lorsque je démarre l'exploration de ce nouveau domaine, CT-GenAI n'existe pas encore. Ce sera pour 2026 !

## CT-AI date de 2021... la préhistoire de l'IA ?

La plupart des analystes s'accordent à dire que d'ici la fin de la décennie, la majorité des produits logiciels embarqueront de l'IA. Rappelons que l'IA, ce n'est pas que les grands modèles de langage : analyse de données, prédiction, recommandations, vision par ordinateur, détection de maladies et même cybersécurité, l'IA est partout. Pour un testeur logiciel, savoir appréhender ces nouveaux défis est au moins aussi important que de pouvoir optimiser son travail grâce à ces nouveaux outils.

Mais CT-AI date de 2021, l'an 1 *avant* ChatGPT, et n'aborde donc que très peu ces fameux LLM qui révolutionnent l'IT et le testing. Reste-t-elle pertinente ?

En un mot : oui ! Que l'IA intègre ou non du traitement du langage, les défis restent comparables : comportement non déterministe, gestion des données, robustesse, sécurité et considérations éthiques, sans compter la dimension humaine. En effet, ce domaine en pleine mutation suscite autant de fantasmes que de promesses parfois démesurées.

## Ce que j'ai appris

On commencera sans surprise par une définition de ce que couvre l'IA... en 2021, ainsi qu'un aperçu des technologies liées, des frameworks et composants matériels utilisés, et des normes associées. Peut-être pas la partie la plus pérenne du syllabus - les auteurs sont d'ailleurs prudents, en rappelant régulièrement que le contenu décrit la situation "en avril 2021", mais ça démontre l'étendue du domaine... et du vocabulaire qu'il faudra maîtriser pour communiquer avec des Data Scientists (mention spéciale pour le terme "régression", qui a une toute autre signification en IA).

Bien plus intéressant est le deuxième chapitre, consacré aux caractéristiques qualité des systèmes basés sur l'IA. Au-delà de démontrer que le système fonctionne, le testeur devra déterminer comment celui-ci évolue et s'adapte à son environnement. Il devra également s'interroger sur les risques de biais et la dimension éthique, et savoir expliquer les notions clés de l'*IA explicable* (XAI) que sont la transparence, l'interprétabilité et l'explicabilité.

Il vous faudra ensuite comprendre les bases du Machine Learning et des réseaux neuronaux pour en appréhender les risques et méthodes de validation. Cette partie est très technique, surtout pour ceux qui n'ont pas d'expérience en développement d'IA, et m'a d'ailleurs demandé bien plus d'efforts que le reste. Mais outre la satisfaction intellectuelle, c'est une étape essentielle pour comprendre le travail des développeurs d'IA et faciliter la communication avec ceux-ci. Même si votre projet se contente d'intégrer des composants IA existants, il reste crucial de saisir leurs capacités et limites. En particulier, le chapitre *métriques de performance fonctionnelle des ML* permet de décrire précisément un comportement probabiliste, notamment en distinguant les notions d'exactitude, de précision et de rappel, ainsi que d'autres indicateurs pertinents spécifiques à l'IA. Bien qu'orienté Machine Learning, beaucoup de ces concepts sont applicables à d'autres branches de l'IA. Un autre long chapitre décrit l'importance du traitement des données (le syllabus cite le chiffre de 43% de l'effort du workflow ML), domaine qui intéressera certainement le testeur confronté à des jeux de données d'une dimension incomparable à ce qu'il manipule en développement traditionnel.

Les chapitres 7 à 9 entrent dans le vif du sujet, décrivant la validation des systèmes basés sur l'IA, l'évaluation des nouvelles caractéristiques de qualité et les méthodes et techniques employées. Bien que quelques exercices soient proposés, ne vous attendez pas à un mode d'emploi prêt à être déployé, mais plutôt à une liste d'enjeux et de recommandations. C'est d'ailleurs souvent le cas dans les certifications ISTQB et c'est ce qui les rend résistantes aux évolutions des techniques : même si les moyens changent, les dangers persistent...

Entre autres aspects, de nombreux passages mentionnent l'importance d'interroger le rapport entre l'homme et la machine, question qui prend une toute autre ampleur depuis le développement des grands modèles de langage.

Le voyage se termine sur un court chapitre dédié aux environnements de test, puis une ultime partie consacrée à l'utilisation de l'IA dans ce domaine. C'est probablement la section qui a le plus évolué depuis la publication du syllabus, et même si de nombreux points restent pertinents, la nouvelle certification CT-GenIA est sans doute plus adaptée pour couvrir cet aspect.


## Comment l'appréhender ?

J'ai étudié et passé la certification en autonomie, en combinant de nombreuses sources. Je ne peux donc pas me prononcer sur les formations disponibles, mais vu l'ampleur de la matière, c'est probablement le moyen le plus efficace.

En ce qui me concerne, j'ai complété le syllabus avec diverses ressources pour compenser mon manque d'expérience en IA. Parmi celles-ci, je citerai :

[Elements of AI](https://www.elementsofai.com/) : deux cours en ligne gratuits proposés par l'université d'Helsinki. La première partie (Introduction to AI) a été soigneusement traduite en de nombreuses langues, dont le français. La seconde partie "Building AI", tout aussi intéressante, est plus pratique et requiert des connaissances de base en programmation Python (bien que des exercices alternatifs soient toujours proposés au public moins technique). 
Ces cours sont très didactiques et constituent un excellent point de départ avant de se plonger dans le syllabus ISTQB.

[Google for Developers](https://developers.google.com/learn) offre des dizaines de formations en ligne, dans le domaine de l'IA et bien d'autres, dont une suite consacrée au [Machine Learning](https://developers.google.com/machine-learning/foundational-courses?hl=fr). Que ce soit pour mieux saisir les concepts cités ou pour aller plus loin, c'est un compagnon idéal et probablement plus actualisé dans certains domaines.

J'ai exploité de nombreux autres sites et ressources en ligne, le sujet étant évidemment largement développé. J'ai aussi eu la chance d'être plongé dans une talentueuse équipe de Data Scientists qui ont pu répondre à mes questions et challenger mes nouvelles connaissances... mais surtout d'exploiter directement ces notions au travers de deux projets concrets.

Enfin, je l'avoue sans honte : ChatGPT m'a largement aidé à réviser. Le mode *learning* est impressionnant et vous permettra de revoir l'intégralité de la matière avant de passer l'examen.

## 3 transformations concrètes de mon métier

Comme je le disais en introduction, le test de logiciels exploitant l'IA a nécessité une nouvelle définition de mon travail, principalement sur ces trois aspects :

### Ingénierie des exigences, communication avec les parties prenantes et tests utilisateurs

Un système traditionnel, déterministe, peut être (quasi) exhaustivement décrit sous forme d'exigences fonctionnelles et non fonctionnelles. C'est nécessaire aussi pour un système basé sur l'IA, mais cela requiert une toute autre gymnastique pour définir des résultats mesurables et atteignables. Il est rarement possible d'atteindre un taux de réussite de 100% : les exigences fonctionnelles devront se baser sur des approches statistiques et des seuils à atteindre. Il est également nécessaire de se pencher sur les nouveaux attributs de qualité qui sont parfois plus importants que la performance fonctionnelle : XIA, absence de biais, éthique...

C'est particulièrement vrai pour les développements basés sur le langage comme un chatbot : il s'agit de mesurer la plus-value pour un utilisateur sur base d'éléments subjectifs... qu'il nous faudra objectiver.

Enfin, un chatbot semble ne pas avoir de limites. Il est nécessaire d'accompagner les parties prenantes dans la définition d'un projet réaliste, de sensibiliser chacun aux risques liés, et de rester prêt au changement dans un domaine en constante évolution.

### Travail au sein de l'équipe de réalisation

Ceux qui me connaissent savent à quel point je suis partisan d'une intégration totale entre développement et test, telle que promue par exemple par le [test holistique](https://lisacrispin.com/2023/05/15/holistic-testing-model-mini-book/). C'est encore plus crucial dans le domaine de l'IA. De par sa nature exploratoire et les nouveaux risques associés, le temps consacré à la validation est généralement plus important qu'en développement traditionnel - certaines sources mentionnent 50 à 60% du temps total, mais c'est évidemment très variable selon le type de projet.

Les data scientists sérieux développent leurs propres procédures, que le testeur devra comprendre et parfois compléter. Le rôle de plaque tournante entre parties prenantes, utilisateurs et développeurs s'en trouve renforcé, et il est souvent nécessaire de se plonger plus profondément dans le domaine pour saisir les enjeux et identifier les métriques pertinentes. Enfin, dans un système complexe, il reste indispensable de valider chaque composant, qu'il intègre ou non de l'IA, pour éviter l'effet "boîte noire" rendant l'exploitation des résultats impossible. Une stratégie globale intégrant IA et développement traditionnel sera une des clés de la réussite.

### Test statistique et traitement du langage

La meilleure manière de valider un système non déterministe est de répéter de nombreuses fois chaque cas, souvent en variant les données d'entrée, pour déterminer des scores ou métriques sur base statistique. Ceci passe inévitablement par l'automatisation. Dans le cas d'un chatbot ou de toute autre application intégrant du traitement de langage, il faudra également utiliser de nouvelles méthodes telles que LLM-as-a-judge... qui elles-mêmes exploitent l'IA. Le serpent se mord la queue, mais l'humain reste au cœur du processus pour garder le contrôle.

Les nouvelles techniques basées sur l'utilisation des LLM ne sont pas décrites dans ce syllabus, elles n'existaient pas encore en 2021. Mais les points d'attention et la manière d'organiser les choses présentés restent un guide extrêmement pertinent.

En résumé, une veille technologique active combinée à une analyse rigoureuse telle que décrite au sein de cette certification m'ont permis de développer une méthodologie adaptée à la hauteur des défis, mais aussi de l'implémenter et de la défendre auprès de l'équipe et des décideurs. C'est aussi la plus-value des certifications ISTQB : pouvoir inscrire son projet en cohérence avec l'industrie, le décrire de manière rigoureuse et défendre sa pertinence avec des arguments reconnus.

## Et GenAI alors ?

La certification ISTQB CT-GenAI forme les testeurs à utiliser l'IA générative dans les processus de validation logicielle, que ce logiciel embarque ou non de l'IA. Elle ne remplace donc en rien CT-AI (une rumeur évoque d'ailleurs une nouvelle édition pour cette dernière, bien qu'aucun draft ne soit actuellement disponible). Si vous cherchez à optimiser vos processus et à comprendre l'enjeu de l'IA générative dans le domaine, c'est probablement un meilleur investissement. Si vous devez tester des systèmes IA ou hybrides, les deux sont complémentaires...

*Et vous, quelle certification envisagez-vous ? CT-AI, CT-GenAI, ou les deux ?*
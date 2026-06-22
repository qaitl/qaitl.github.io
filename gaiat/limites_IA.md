Pour votre présentation sur l'IA générative dans le test logiciel, il est crucial de montrer que si l'IA est une excellente "assistante", elle manque de rigueur logique déterministe. Contrairement à un script de test classique qui échoue de manière binaire, un LLM peut "réussir" en apparence tout en produisant un résultat faux (le concept de confidently wrong).

Voici des exemples concrets, classés par type de défaillance, pour illustrer ces limites :

1. L'incapacité à sortir d'un "Pattern" connu (Biais d'entraînement)
Les LLM prédisent le mot suivant basé sur des probabilités. Si vous modifiez légèrement une énigme ultra-connue, l'IA risque de répondre à la version "standard" qu'elle a vue des milliers de fois sans lire vos modifications.

La question piège : > "Un homme doit traverser une rivière avec une chèvre et un loup. Sa barque est assez grande pour transporter l'homme et ses deux animaux en un seul voyage. Comment fait-il ?"

L'erreur probable : Le LLM va souvent détailler une série de trajets complexes (le manège classique pour éviter que le loup mange la chèvre), ignorant la consigne que la barque est, cette fois-ci, assez grande pour tout le monde d'un coup.

Impact Test : L'IA peut ignorer une règle métier spécifique (ex: une promotion cumulable) car elle "suppose" par habitude qu'elle ne l'est pas.

2. Les limites du raisonnement logique pur
Les LLM ne "calculent" pas, ils simulent le raisonnement. Sur des problèmes de transitivité simple, ils s'emmêlent souvent les pinceaux.

La question piège :

"Marie a 4 frères. Chaque frère a une sœur. Combien Marie a-t-elle de sœurs ?"

L'erreur probable : L'IA répond souvent "4 sœurs" (en attribuant une sœur à chaque frère individuellement).

La réalité : Marie est la sœur unique de ses 4 frères. Elle a donc 0 sœur.

Impact Test : Risque d'erreurs majeures lors de la génération de jeux de données complexes ou de tests de règles de parenté/hiérarchie.

3. L'hallucination de bibliothèques ou d'API
C'est le risque numéro 1 pour un testeur automatisant du code (Playwright, Selenium, Cypress).

La demande :

"Écris-moi un script de test Playwright pour vérifier si un élément est 'flou' (blurred) en utilisant la fonction native page.expectElementToBeBlurry()."

L'erreur probable : L'IA va générer le code avec assurance, en utilisant cette fonction... qui n'existe absolument pas dans la documentation officielle de Playwright. Elle a "inventé" un nom de fonction sémantiquement correct mais techniquement inexistant.

Impact Test : Perte de temps considérable à débugger du code "fantôme".

4. Le problème de la négation et des contraintes strictes
Les LLM ont parfois du mal avec les instructions négatives ("ne pas faire X").

La question piège :

"Génère une liste de 5 noms d'utilisateurs pour des tests. Ces noms ne doivent absolument pas contenir la lettre 'e'."

L'erreur probable : Il est fréquent de trouver "Marc", "Luc", mais aussi "Pierre" ou "Stephane" dans la liste. L'IA se concentre sur le concept de "nom" et "liste", perdant le fil de la contrainte négative.

Impact Test : Création de données de test invalides qui font échouer les tests pour les mauvaises raisons.

Synthèse pour votre présentation
Type de Limite	Manifestation	Risque pour le Testeur
Probabilisme	Répond au pattern habituel plutôt qu'à la consigne.	Oubli de "Edge Cases" spécifiques au métier.
Hallucination	Invente des fonctions ou des sélecteurs CSS.	Code d'automatisation qui ne compile pas.
Logique fragile	Erreurs sur les relations de parenté ou de temps.	Données de test (SQL/JSON) incohérentes.
Sensibilité au prompt	Une virgule change le résultat.	Instabilité des suites de tests basées sur l'IA (Flakiness).
Conseil pour la démo : Si vous faites la démonstration en direct, utilisez des modèles moins récents (comme GPT-3.5 ou un petit modèle local) car les versions "Ultra" ou "o1" commencent à corriger ces erreurs logiques simples. Cela appuiera mieux votre point sur la nécessité d'une supervision humaine systématique.

Souhaitez-vous que j'approfondisse un exemple spécifique sur la génération de code de test ?

C'est un excellent choix pour votre présentation, car c'est là que le risque devient concret pour une équipe technique : le passage du "ça a l'air correct" au "ça ne tourne pas du tout".

Voici un exemple détaillé d'**hallucination de framework** et de **logique de sélecteur erronée** que vous pouvez utiliser pour illustrer le concept de "code fantôme".

---

## L'exemple : Automatisation d'un "Drag and Drop" complexe

Demandez à une IA de générer un script pour une action qui n'est pas gérée nativement de manière simple par un framework (comme un Drag & Drop entre deux frames différentes ou avec des composants complexes type React-Select).

### 1. La requête (Le Prompt)
> "Écris-moi un script de test avec **Cypress** pour glisser-déposer un élément `#source` vers une cible `#target`. Attention, le composant est protégé par une couche de sécurité, utilise la commande native `cy.dragAndDropForce()`."

### 2. L'échec de l'IA (L'Hallucination)
L'IA, voulant être serviable, va souvent générer ceci :

```javascript
describe('Test de Drag and Drop', () => {
  it('devrait déplacer l'élément', () => {
    cy.visit('/page-de-test');
    
    // ERREUR : Cette commande n'existe pas dans Cypress !
    cy.get('#source').dragAndDropForce('#target', { timeout: 5000 });
    
    cy.get('#target').should('contain', 'Élément déposé');
  });
});
```

### Pourquoi c'est une limite critique ?
* **L'invention de fonctionnalités :** Le LLM a fusionné des termes qu'il connaît (`dragAndDrop`, `force: true`, `timeout`) pour créer une commande imaginaire `dragAndDropForce()`. 
* **Le piège pour le débutant :** Un testeur junior pourrait passer des heures à chercher pourquoi sa commande "native" ne fonctionne pas, pensant que c'est un problème d'installation alors que la fonction n'a jamais existé.

---

## 3. Le problème des "Sélecteurs Fragiles" (Flakiness)

L'IA a tendance à générer des sélecteurs CSS basés sur la structure visuelle plutôt que sur la robustesse.

* **Demande :** "Donne-moi le sélecteur pour le bouton de validation de ce formulaire." (En lui fournissant un bout de HTML complexe).
* **Erreur type :** Elle proposera souvent un chemin absolu ou trop lié au style :
    `cy.get('div.container > div:nth-child(3) > table > tr > td > button.btn-blue')`
* **Le risque :** Au moindre changement de design (une `div` ajoutée pour la mise en page), le test casse. L'IA ne comprend pas la notion de **"testabilité"** (préférer un `data-testid`).

---

## Comment présenter cela (votre argumentaire) :

Pour votre démonstration, vous pouvez projeter un tableau comparatif :

| Ce que l'IA produit | Pourquoi c'est dangereux | La solution humaine |
| :--- | :--- | :--- |
| **Code "plausible"** | Il respecte la syntaxe JS mais utilise des fonctions imaginaires. | Vérification systématique de la documentation officielle. |
| **Sélecteurs rigides** | Crée des tests "fragiles" qui cassent à la moindre mise à jour UI. | Imposer l'utilisation de `data-attributes` dédiés au test. |
| **Logique de Mock** | L'IA peut mocker des données qui ne respectent pas le schéma réel de la DB. | Utiliser des contrats d'API (Pact, etc.) pour valider les mocks. |

---

### Une astuce pour votre démo "Live"
Si vous voulez vraiment impressionner votre audience, demandez à l'IA de générer un test pour une bibliothèque sortie **après** sa date de coupure de connaissances (son *knowledge cutoff*). Elle essaiera de deviner la syntaxe en se basant sur d'anciennes versions, produisant un code obsolète mais syntaxiquement parfait.

Est-ce que cela correspond à ce que vous vouliez pour illustrer la partie technique ?

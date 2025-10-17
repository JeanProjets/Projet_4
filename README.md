# Mission Projet - Outil de Scoring Crédit

## Mission

Cette mission suit un scénario de projet professionnel.

### Préparation recommandée

Avant de démarrer, nous vous conseillons de :
- Lire toute la mission et ses documents liés
- Prendre des notes sur ce que vous avez compris
- Consulter les étapes pour vous guider
- Préparer une liste de questions pour votre première session de mentorat

## Contexte

Vous êtes **Data Scientist** au sein d'une société financière, nommée **"Prêt à dépenser"**, qui propose des crédits à la consommation pour des personnes ayant peu ou pas d'historique de prêt.

Pour accorder un crédit à la consommation, l'entreprise souhaite mettre en œuvre un outil de **"scoring crédit"** qui calcule la probabilité qu'un client le rembourse ou non, puis classifie la demande : crédit accordé ou refusé. Elle souhaite donc développer un algorithme de classification pour aider à décider si un prêt peut être accordé à un client.

### Utilisateurs finaux

Les **chargés de relation client** seront les utilisateurs de l'outil de scoring. Puisqu'ils s'adressent aux clients, ils ont besoin que votre modèle soit **facilement interprétable**. Les chargés de relation souhaitent, en plus, disposer d'une mesure de l'importance des variables qui ont poussé le modèle à donner cette probabilité à un client.

### Données disponibles

Pour réaliser ce modèle, Michaël, votre manager, vous a fourni le jeu de données suivant qui contient :
- Un historique de prêts
- Un historique d'informations financières
- Des informations sur le comportement des emprunteurs (si l'emprunteur a fait défaut ou pas)

## Mail de récapitulatif du manager

**De :** Michaël  
**Envoyé :** hier 17:14  
**À :** Vous  
**Objet :** Récap. Algo de scoring

Hello,

Merci pour notre meeting. Je souhaitais le compléter en te donnant quelques ressources :

### Préparation des données
Pour aller plus vite sur la préparation des données, tu peux utiliser un kernel Kaggle. Par contre, fais attention à ce qu'il soit adapté à ton besoin. Essaie notamment de :
- Construire au moins **trois nouvelles variables** à partir des variables existantes qui te semblent pertinentes pour améliorer le pouvoir prédictif du modèle
- T'approprier le kernel au maximum en l'adaptant pour le projet

### Interprétabilité
On a évoqué le fait que ton modèle doit être interprétable par les équipes qui vont l'utiliser. N'hésite pas à consulter ce site et ce GitHub à ce sujet. Pense à expliciter en quelques lignes la méthode d'importance des variables que tu retiendras. Je souhaite une analyse de l'importance des variables :
- **Globale** au modèle
- **Locale** pour un client donné

### Présentation
Le modèle sera à présenter aux équipes, fais donc en sorte que ta présentation soit compréhensible par tous, et que ton Jupyter soit bien documenté. Pour les slides, je te suggère ce plan :
1. Compréhension de la problématique métier
2. Description du jeu de données
3. Transformation du jeu de données (nettoyage et feature engineering)
4. Comparaison et synthèse des résultats pour les modèles utilisés
5. Interprétabilité du modèle
6. Conclusion

## Points de vigilance spécifiques au contexte métier

### 1. Déséquilibre des classes
Le déséquilibre entre le nombre de bons et de moins bons clients doit être pris en compte pour élaborer un modèle pertinent, à l'aide d'au moins une méthode au choix.

### 2. Déséquilibre du coût métier
Le déséquilibre du coût métier entre :
- **Faux négatif (FN)** : mauvais client prédit bon client → crédit accordé et perte en capital
- **Faux positif (FP)** : bon client prédit mauvais → refus crédit et manque à gagner en marge

**Hypothèse :** Tu pourras supposer que le coût d'un FN est **dix fois supérieur** au coût d'un FP.

### 3. Score métier
Tu créeras un **score "métier"** (minimisation du coût d'erreur de prédiction des FN et FP) pour comparer les modèles, afin de choisir le meilleur modèle et ses meilleurs hyperparamètres. 

⚠️ **Attention** : Cette minimisation du coût métier doit passer par l'optimisation du seuil qui détermine, à partir d'une probabilité, la classe 0 ou 1 (un "predict" suppose un seuil à 0.5 qui n'est pas forcément l'optimum).

### 4. Métriques de contrôle
En parallèle, maintiens pour comparaison et contrôle, des mesures plus techniques, telles que l'**AUC** et l'**accuracy**.

### 5. Méthodologie
Je souhaite que tu mettes en œuvre une démarche d'élaboration des modèles avec :
- **Cross-Validation**
- **Optimisation des hyperparamètres** via GridSearchCV ou équivalent

### ⚠️ Conseil important
Si tu obtiens des scores supérieurs au 1er du challenge Kaggle (**AUC > 0.82**), pose-toi la question si tu n'as pas de l'overfitting dans ton modèle !

Bon courage !

Michaël

---

## Étapes du projet

### Recommandations générales
- Assurez-vous de comprendre la problématique métier et l'objectif du projet avant de commencer
- Familiarisez-vous avec les méthodologies et techniques utilisées dans l'apprentissage supervisé en Machine Learning
- Veillez à acquérir une compréhension technique des différents types de modèles de Machine Learning couramment utilisés pour la tâche identifiée
- Familiarisez-vous avec le jeu de données et les variables disponibles pour la modélisation
- Gardez à l'esprit l'importance de l'interprétabilité du modèle pour les utilisateurs finaux
- Soyez prêt à justifier vos choix tout au long du projet, en tenant compte du contexte métier

## Étape 1 : Analyse exploratoire et Feature Engineering

### Prérequis
- Avoir compris les exigences du projet et les objectifs du modèle de scoring
- Avoir revu les ressources fournies pour vous aider à choisir un kernel Kaggle pertinent

### Résultats attendus
- Une analyse exploratoire du jeu de données pour comprendre sa structure et ses caractéristiques
- Une identification des opportunités de feature engineering pour améliorer la performance du modèle

### Recommandations pour cette étape
- Utilisez le kernel recommandé pour la préparation des données et l'analyse exploratoire
- Créez au moins **trois nouvelles variables** pertinentes à partir des variables existantes
- N'hésitez pas à adapter le kernel en ajoutant des commentaires pour expliquer vos actions

### Points de vigilance
- Assurez-vous d'utiliser le bon fichier (`application_train.csv`) pour l'analyse exploratoire
- Vérifiez les valeurs manquantes et les valeurs extrêmes dans le jeu de données

### Ressources
- Appuyez-vous sur le cours "Nettoyez et analysez votre jeu de données" pour la méthodologie d'analyse
- Utilisez le kernel "start-here-a-gentle-introduction" pour l'exploration et l'inspiration de techniques de feature engineering

## Étape 2 : Création du score métier

### Prérequis
- Avoir compris l'importance du coût des erreurs de prédiction dans le contexte financier
- Avoir compris comment créer une fonction de coût métier pour évaluer les performances des modèles

### Résultats attendus
- Une fonction de coût métier mise en place prenant en compte les coûts des faux positifs et des faux négatifs
- Un score "métier" calculé pour évaluer les performances des différents modèles

### Recommandations
- Utilisez la fonction de coût métier pour optimiser les hyperparamètres des modèles
- Assurez-vous de calculer le seuil optimal pour le score "métier"

### Points de vigilance
- Assurez-vous de comprendre le coût des erreurs de prédiction dans le contexte financier
- Vérifiez que votre score "métier" est calculé correctement en prenant en compte les faux positifs et les faux négatifs

### Ressource
- Appuyez-vous sur le cours "Évaluez les performances d'un modèle" pour comprendre comment créer un score "métier" adapté

## Étape 3 : Modélisation et comparaison

### Prérequis
- Avoir compris l'importance de tester différents types de modèles pour le problème identifié
- Avoir étudié les différentes ressources théoriques mises à disposition

### Résultats attendus
- Tests et comparaison des différents modèles, des plus simples aux plus complexes
- Utilisation des techniques pour gérer le déséquilibre des classes
- Maîtrise de l'utilisation des pipelines scikit-learn pour l'optimisation et l'évaluation des modèles

### Recommandations
- Utilisez la **Cross-Validation** pour évaluer les performances des modèles de manière robuste
- Explorez différentes valeurs d'hyperparamètres pour obtenir des modèles performants à l'aide de **Grid Search**
- Synthétisez vos résultats (tableau comparatif + courbe ROC)

### Points de vigilance
- Assurez-vous de tester une variété de modèles, des modèles simples aux modèles plus complexes
- Vous devrez veiller à équilibrer vos classes. Vous devrez justifier votre démarche
- Des scores AUC supérieurs à 0.82 pourraient révéler une fuite de données dans le pipeline mis en place

### Ressources
- Utilisez les ressources externes et les cours recommandés pour comprendre et réaliser le benchmark des modèles
- Utilisez la fonction pipeline fournie par scikit-learn
- Rééquilibrez vos classes grâce à la librairie **Imbalanced-learn**

## Étape 4 : Interprétabilité du modèle

### Prérequis
- Avoir compris l'importance de l'interprétation du modèle pour les utilisateurs finaux
- Avoir revu les concepts de feature importance globale et locale

### Résultats attendus
- Utilisation des librairies spécialisées pour calculer la feature importance globale et locale
- Informations fournies pour expliquer les prédictions du modèle aux chargés d'étude

### Recommandations
- Assurez-vous de comprendre comment interpréter les résultats de l'analyse

### Points de vigilance
- Soyez prêt à expliquer aux chargés d'étude comment les features influencent les prédictions du modèle

### Ressources
- Utilisez les librairies **SHAP** ou **LIME** pour comprendre et mettre en œuvre l'analyse de la feature importance
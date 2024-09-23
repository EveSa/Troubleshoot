---
---
# The History of Neural Networks

c.f. La revanche des neurones

Historiquement : calculer des portes logiques de bases (OR, AND, …)

# How it works

$$
w_0*x_0 + b_0 = output
$$

Les facteurs $w_0$ et $b_0$ sont re déterminé tout au long de l’entraînement pour parvenir à prédire l’output de façon correcte (face aux données d’entraînement)

$x_0$ est la donnée d’entrée (un mot, un point, un document)

**Mais comment représenter un mot sous forme numérique ?**
On peut donner à un mot un vecteur dans un espace à n dimension.

Représenter une droite avec les données de départ peut ne pas être suffisant pour résoudre notre problème. Dans ce cas, on peut utiliser plusieurs couche de neurones : 

- Les premiers neurones calculent une nouvelle représentation de l’entrée
- Les seconds neurones calculent une représentation issue de la représentation modifiée
- …
- Les derniers neurones calculent une représentation qui résout le problème donné

On ne sait jamais combien de couche de neurone est nécessaire à la représentation d’un problème

### En NLP

On a un mot.

On va essayer de le représenter avec des caratéristiques numériques parceque les ordinateurs ne comprennent pas les mots.

Pour ça on va prendre un espace de dimension N avec N le nombre de caractéristique (*features*) que notre modèle va pouvoir représenter.

On peut imaginer une caractéristique *genre* ou *nombre* par exemple

( en vérité, c’est pas du tout comme ça que ça se passe parceque les modèles choisissent des caractéristiques “cachées” (*latente*) qui n’ont pas à voir avec la réalité linguistique )

L’objectif du modèle, ça va être de donner une valeur au mot par caractéristique : à quel point ce mot il est *féminin-masculin,* à quel point ce mot il est *singlier-pluriel*. Quand il a positionné le curseur de toutes les caractéristiques, il nous donne une suite de valeur (une valeur par caratéristique) : c’est le **vecteur** du mot dans l’espace de dimension N qu’on a choisi au départ

### Comment un NN fait pour choisir les valeurs qu’il donne à un mot ?

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/51bb4b15-01f5-4b17-8e78-4c910f77218d/a35f17e7-1937-4a7c-b249-b648037613c9/Untitled.png)

Un réseau de neurone va utiliser des **poids** pour positionner un élément sur différentes caractéristiques. Mais pour donner la représentation finale (le vecteur qui représente notre mot), il va pouvoir passer par plusieurs étapes d’abstraction (plusieurs couches de neurones). C’est à cause de ces plusieurs couches qu’on parle de “deep” ou “multilayer” neural networks

Dans le graphique ci dessus, suivons une seule des entrées proposée : l’entrée “étoile de mer”. En fait, notre étoile de mer, elle ressemble plutôt à ça 

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/51bb4b15-01f5-4b17-8e78-4c910f77218d/4584e4df-981f-450f-9623-d1301b0bfdcb/Untitled.png)

Ici, le réseau donne un poids important à la forme de l’entrée vers la forme “étoile de mer” et un poids important vers la texture “étoile de mer”. Si on avait plusieurs couche, on aurait pu imaginer que le modèle aurait d’abord essayer de discriminer une forme d’hexagone avant de raffiner sur une forme d’étoile de mer et une forme de “France” par exemple.

### Qu’est ce qu’un neurone

pour un MLP

## Qu’est ce qu’un CRF ?

Conditionnal Random Field : modèle statistique qui représente le contexte adjacent par un graphe de dépendance. En NLP, on utilise souvent un graphe linéaire (pour modéliser la séquentialité)

# Why is Explainability a Problem (XAI)

Because Deep Neural Networks are a blackbox it is unpredictable in unknown situation. Deep Neurons have bad extrapolation capability which makes them especially unpredicatable. As it is impossible to cover every possibility in a dataset, models will have to extrapolate on unseen data.

## Adversial Attack

adversial machine learning ?

## Explanability ideas

Comment imposer le bon biais inductif au modèle :

- avec l’équivariance

# Graph Neural Networks

Les réseaux de neurones sur graphes (ou réseau de neurones en graphes/réseaux de neurones graphiques)

<aside>
💡 Deep Learning Geométrique : trouver un cadre mathématique commun pour unifier

</aside>

# What is model perplexity ?

Une métrique pour les modèles de langues autorégressifs https://huggingface.co/docs/transformers/perplexity

# LLMs

RLHF : Reinforcement Learning with Human Feedback

# Adaptation de modèles

## Fine-tuning

## RLHF: Reinforcement Learning From Human Feedback

## ICL: In Context Learning

## MAML: [Model Agnostic Meta Learning](https://interactive-maml.github.io/maml.html)

MAML propose une solution pour l'entraînement de modèle avec des très petit jeux de données. L'objectif est d'obtenir une représentation - des poids de modèles - qui soient le plus proche possible d'un grand nombre de tâches afin que leur adaptation ne requière qu'un "petit" *fine-tuning*.

L'objectif n'est pas d'entraîner un modèle sur une tâche mais d'**entraîner un modèle à apprendre**.

> ❓ Est ce que l'objectif serait un modèle avec les plus petits vecteurs de tâches ❓



Model agnostic : la méthode est adaptable pour tous modèles utilisant une descente de gradiant.

Meta Learning : Apprendre au modèle à apprendre (sur des petits jeu de données et sans *over-fitter*)
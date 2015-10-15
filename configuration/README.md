# Configuration

Maintenant que le projet est correctement initialié, il est temps de le configurer.

La configuration recouvre différents aspects, les domaines, les web services, les définitions des entités, etc...

## Domaines

Les domaines sont configurés dans le dossier [`app/config/domain`](https://github.com/KleeGroup/focus-starter-kit/tree/master/app/config) du [kit de démarrage](https://github.com/KleeGroup/focus-starter-kit/).


Chaque dommaine est identifié par un code, repris dans la [définition des entités](#definition), de la forme :

```javascript
const DO_DATE = {
    //...
}
```

Un domaine est décrit par un simple objet Javascript permettant de définir ses propriétés, comme suit :

```javascript
const DO_MY_DOMAIN = {
    /**
     * Doit porter un label ?
     * @optional
     * @default true
     * @type {Boolean}
     */
    hasLabel: true,
    /**
     * [label description]
     * @optional
     * @type {String}
     */
    label: 'label',
    /**
     * Pour le composant de date, la locale moment.js
     * @optional
     * @default 'en'
     * @type {String}
     */
    locale: 'fr',
    /**
     * Pour le composant de date, le format d'affichage
     * @optional
     * @default 'MM/DD/YYYY'
     * @type {String}
     */
    format: 'DD/MM/YYYY',
    /**
     * Le domaine est-il requis sur toutes les entités ?
     * @optional
     * @default false
     * @type {Boolean}
     */
    isRequired: true,
    /**
     * Type d'input
     * @type {String}
     */
    type: 'text',
    /**
     * Tableau de validateurs
     * @optional
     * @type {Array}
     */
    validator: [],
    /**
     * Fonction de formattage
     * @optional
     * @default identité
     * @type {Function}
     */
    formatter: () => {},
    /**
     * Fonction de déformattage
     * @optional
     * @default identité
     * @type {Function}
     */
    unformatter: () => {},
    /**
     * Composant du field
     * @optional
     * @type {Function}
     */
    FieldComponent: props => {/**JSX*/},
    /**
     * Composant du label d'input
     * @optional
     * @type {Function}
     */
    InputLabelComponent: props => {/**JSX*/},
    /**
     * Composant de l'input (édition)
     * @optional
     * @type {Function}
     */
    InputComponent: props => {/**JSX*/},
    /**
     * Composant de select
     * @optional
     * @type {Function}
     */
    SelectComponent: props => {/**JSX*/},
    /**
     * Composant de texte
     * @optional
     * @type {Function}
     */
    TextComponent: props => {/**JSX*/},
    /**
     * Composant de consultation
     * @optional
     * @type {Function}
     */
    DisplayComponent: props => {/**JSX*/},
    /**
     * Options à donner en props au field
     * @optional
     * @type {Object}
     */
    options: {} // options à donner au field
}
```

## <a name="definition"></a>Définition des entités

## Web services

Les routes vers le serveur sont définies dans [`app/config/server`](https://github.com/KleeGroup/focus-starter-kit/tree/master/app/config/server).

Une route se définit de la manière suivante :

```javascript
// app/config/server/example.js
const root = './my/sub/root/';
const url = FocusCore.util.url.builder;

export default {
    /**
     * Exemple d'une route GET.
     * Le paramètre param est extrait du urlData donné au fetch
     */
    myFirstRoute: url(root + 'example/${param}', 'GET'),
    /**
     * Exemple d'une route POST
     * Les paramètres d'URL sont passés comme pour une route GET, le contenu de la requête est dans le paramètre data du fetch
     */
    mySecondRoute: url(root + 'other/${otherParam}', 'POST')
}
```

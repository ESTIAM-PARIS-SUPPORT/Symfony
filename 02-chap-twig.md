# Tutoriel sur l'utilisation de Twig avec des layouts dans Symfony

## Introduction

Twig est un moteur de template moderne pour PHP, utilisé par Symfony pour générer des vues dynamiques. Les layouts dans Twig permettent de créer des structures de page réutilisables, ce qui facilite la gestion des éléments communs comme les en-têtes, les pieds de page et les barres de navigation.

## Étape 1 : Installation de Twig

Si vous utilisez Symfony, Twig est déjà installé par défaut. Sinon, vous pouvez l'installer via Composer :

```sh
composer require symfony/twig-bundle
```

## Étape 2 : Création d'un layout de base

Créez un fichier de layout de base dans le répertoire `templates` de votre projet Symfony. Par exemple, créez un fichier nommé `base.html.twig` :

```twig
{# templates/base.html.twig #}
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>{% block title %}Mon Site{% endblock %}</title>
    {% block stylesheets %}
        <link rel="stylesheet" href="{{ asset('css/style.css') }}">
    {% endblock %}
</head>
<body>
    <header>
        <h1>Mon Site</h1>
        <nav>
            <ul>
                <li><a href="{{ path('home') }}">Accueil</a></li>
                <li><a href="{{ path('about') }}">À propos</a></li>
                <li><a href="{{ path('contact') }}">Contact</a></li>
            </ul>
        </nav>
    </header>
    <main>
        {% block body %}{% endblock %}
    </main>
    <footer>
        <p>&copy; 2023 Mon Site</p>
    </footer>
    {% block javascripts %}
        <script src="{{ asset('js/script.js') }}"></script>
    {% endblock %}
</body>
</html>
```

## Étape 3 : Utilisation du layout dans une page

Créez une page qui utilise le layout de base. Par exemple, créez un fichier nommé `home.html.twig` dans le répertoire `templates` :

```twig
{# templates/home.html.twig #}
{% extends 'base.html.twig' %}

{% block title %}Accueil{% endblock %}

{% block body %}
    <h2>Bienvenue sur la page d'accueil</h2>
    <p>Ceci est la page d'accueil de notre site.</p>
{% endblock %}
```

## Étape 4 : Création d'un contrôleur

Créez un contrôleur pour rendre la page d'accueil. Par exemple, créez un fichier nommé `HomeController.php` dans le répertoire `src/Controller` :

```php
<?php
// src/Controller/HomeController.php

namespace App\Controller;

use Symfony\Bundle\FrameworkBundle\Controller\AbstractController;
use Symfony\Component\HttpFoundation\Response;
use Symfony\Component\Routing\Annotation\Route;

class HomeController extends AbstractController
{
    /**
     * @Route("/", name="home")
     */
    public function index(): Response
    {
        return $this->render('home.html.twig');
    }
}
```

## Étape 5 : Ajout de routes supplémentaires

Ajoutez des routes supplémentaires pour les pages "À propos" et "Contact". Modifiez le fichier `HomeController.php` comme suit :

```php
<?php
// src/Controller/HomeController.php

namespace App\Controller;

use Symfony\Bundle\FrameworkBundle\Controller\AbstractController;
use Symfony\Component\HttpFoundation\Response;
use Symfony\Component\Routing\Annotation\Route;

class HomeController extends AbstractController
{
    /**
     * @Route("/", name="home")
     */
    public function index(): Response
    {
        return $this->render('home.html.twig');
    }

    /**
     * @Route("/about", name="about")
     */
    public function about(): Response
    {
        return $this->render('about.html.twig');
    }

    /**
     * @Route("/contact", name="contact")
     */
    public function contact(): Response
    {
        return $this->render('contact.html.twig');
    }
}
```

Créez les fichiers `about.html.twig` et `contact.html.twig` dans le répertoire `templates` :

```twig
{# templates/about.html.twig #}
{% extends 'base.html.twig' %}

{% block title %}À propos{% endblock %}

{% block body %}
    <h2>À propos de nous</h2>
    <p>Ceci est la page À propos de notre site.</p>
{% endblock %}
```

```twig
{# templates/contact.html.twig #}
{% extends 'base.html.twig' %}

{% block title %}Contact{% endblock %}

{% block body %}
    <h2>Contactez-nous</h2>
    <p>Ceci est la page de contact de notre site.</p>
{% endblock %}
```

Bien sûr ! Voici un guide sur les conditions et les fonctions dans Twig, entièrement en markdown :

```markdown
# Guide sur les conditions et les fonctions dans Twig

Twig est un moteur de template moderne pour PHP, utilisé par Symfony pour générer des vues dynamiques. Il offre une syntaxe simple et puissante pour afficher des données et manipuler des variables. Voici un aperçu des conditions et des fonctions dans Twig.

## Conditions dans Twig

### `if`

La structure `if` permet d'exécuter du code conditionnellement.

```twig
{% if user.isLoggedIn %}
    <p>Bienvenue, {{ user.username }}!</p>
{% else %}
    <p>Veuillez vous connecter.</p>
{% endif %}
```

### `elseif`

La structure `elseif` permet d'ajouter des conditions supplémentaires.

```twig
{% if user.isAdmin %}
    <p>Bienvenue, administrateur {{ user.username }}!</p>
{% elseif user.isLoggedIn %}
    <p>Bienvenue, {{ user.username }}!</p>
{% else %}
    <p>Veuillez vous connecter.</p>
{% endif %}
```

### `for`

La structure `for` permet de parcourir des éléments dans une boucle.

```twig
{% for user in users %}
    <p>{{ user.username }}</p>
{% else %}
    <p>Aucun utilisateur trouvé.</p>
{% endfor %}
```

### `set`

La structure `set` permet de définir une variable.

```twig
{% set title = 'Mon Site' %}
<title>{{ title }}</title>
```

### `block`

La structure `block` permet de définir des blocs de contenu qui peuvent être remplacés dans les templates enfants.

```twig
{# base.html.twig #}
<!DOCTYPE html>
<html>
<head>
    <title>{% block title %}Mon Site{% endblock %}</title>
</head>
<body>
    {% block body %}{% endblock %}
</body>
</html>
```

```twig
{# home.html.twig #}
{% extends 'base.html.twig' %}

{% block title %}Accueil{% endblock %}

{% block body %}
    <h1>Bienvenue sur la page d'accueil</h1>
{% endblock %}
```

## Fonctions Twig

### `path`

La fonction `path` génère une URL pour une route donnée.

```twig
<a href="{{ path('home') }}">Accueil</a>
```

### `url`

La fonction `url` génère une URL absolue pour une route donnée.

```twig
<a href="{{ url('home') }}">Accueil</a>
```

### `asset`

La fonction `asset` génère une URL pour un fichier statique (comme des images, des feuilles de style, des scripts JavaScript).

```twig
<img src="{{ asset('images/logo.png') }}" alt="Logo">
```

### `dump`

La fonction `dump` affiche des informations détaillées sur une variable, utile pour le débogage.

```twig
{{ dump(variable) }}
```

### `include`

La fonction `include` inclut un autre template Twig.

```twig
{% include 'partials/header.html.twig' %}
```

### `render`

La fonction `render` rend un contrôleur Symfony et inclut son résultat dans le template.

```twig
{{ render(controller('App\\Controller\\HomeController::index')) }}
```

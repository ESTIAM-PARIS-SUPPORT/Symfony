# Installation

You are a lucky man, you are going to learn Symfony

```php
// src/Controller/LuckyController.php
namespace App\Controller;

use Symfony\Component\HttpFoundation\Response;
// ...

class LuckyController extends AbstractController
{
    #[Route('/lucky/number')]
    public function number(): Response
    {
        $number = random_int(0, 100);

        $randomizePhrase = function() {
            $words = explode(' ', 'You are a lucky man, you are going to learn Symfony');
            shuffle($words);

            return implode(' ', $words);
        };

        return $this->render('lucky/number.html.twig', [
            'number' => $randomizePhrase(),
        ]);
    }
}
```

N'oubliez pas la documentation officiel : [symfony](https://symfony.com/)

## Prérequis

Avant de créer votre première application Symfony, vous devez :

1. **Installer PHP 8.2 ou supérieur** ainsi que les extensions PHP suivantes (qui sont généralement installées et activées par défaut dans la plupart des installations PHP 8) : Ctype, iconv, PCRE, Session, SimpleXML, et Tokenizer.
2. **Installer Composer**, qui est utilisé pour installer les packages PHP.

Remarques :  vous pouvez utiliser MAMPP, XAMPP ou WAMP avec Mac Linux ou Windows.

## Symfony CLI

1. Sous Windows [scoop](https://scoop.sh/)

```sh
scoop install symfony-cli
```

2. Création d'une application

```sh
# Application
symfony new --webapp my_project

# Microservice
symfony new my_project
```

## Quelques commandes utiles

```sh
# vérifie votre configuration machine
symfony check:requirements

# vérifie la sécurité les vulnaribilités 
symfony check:security
```

## Alternative sympa 

# Installation de Symfony avec Composer

## Prérequis

Avant de commencer, assurez-vous d'avoir les prérequis suivants installés sur votre machine :

- PHP 8.2 ou supérieur
- Composer

## Étape 1 : Création d'un nouveau projet Symfony

Pour créer un nouveau projet Symfony, utilisez la commande suivante :

```sh
composer create-project symfony/skeleton:"7.2.x" my_project_directory
```

## Symfony démo 

Pour découvrir le code d'une application Symfony

[symfony démo](https://github.com/symfony/demo)

Vous pouvez même l'installer

```sh
symfony new my_project_directory --demo
```

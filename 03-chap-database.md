**Tutoriel sur les bases de l'utilisation de Doctrine ORM avec Symfony**

**Installation de Doctrine**

Pour commencer, installez le support de Doctrine via le pack `orm` de Symfony, ainsi que le `MakerBundle`, qui vous aidera à générer du code :

```sh
composer require symfony/orm-pack
composer require --dev symfony/maker-bundle
```

**Configuration de la base de données**

Les informations de connexion à la base de données sont stockées dans une variable d'environnement appelée `DATABASE_URL`. Pour le développement, vous pouvez trouver et personnaliser cette variable dans le fichier `.env` :

```env
# .env (ou surchargez DATABASE_URL dans .env.local pour éviter de committer vos modifications)

# personnalisez cette ligne !
DATABASE_URL="mysql://db_user:db_password@127.0.0.1:3306/db_name?serverVersion=8.0.37"
```

**Création de la base de données**

Maintenant que vos paramètres de connexion sont configurés, Doctrine peut créer la base de données `db_name` pour vous :

```sh
php bin/console doctrine:database:create
```

**Commandes de base**

Voici quelques commandes de base pour travailler avec Doctrine :

1. **Créer une entité** :
   ```sh
   php bin/console make:entity
   ```

2. **Générer une migration** :
   ```sh
   php bin/console make:migration
   ```

3. **Exécuter les migrations** :
   ```sh
   php bin/console doctrine:migrations:migrate
   ```

4. **Lister les commandes Doctrine disponibles** :
   ```sh
   php bin/console list doctrine
   ```

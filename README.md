# No veo mas que dolores de cabeza
- El uso innecesario de boilerplating para eloquent a diferencia de doctrine - datamaper
- Porque tener value object si tenemos los FormRequest(validations)
- El problema es active record el modelo siempre estara acoplado a la infraestructura
- Podemos mantener la infraestructura en /app pero ya perdemos DDD porque ya que mover la infra a src rompe discovery, politicas, providers lo mejor seria trabajar solo el dominio y aplicacion en src cosa que no es provechoso

## DDD in Laravel 9

DDD example in laravel.

### Instalation

Clone this repository.

```php
git clone https://github.com/ReneHuanca/ddd-in-laravel.git 
```

Install the dependencies.

```php
cd ddd-in-laravel
composer install
```

Copy the .env.example configure the database and generate a key.

```php
cp .env.example .env
php artisan key:generate
```

Run the migrations

```bash
php artisan migrate
```

Run serve with artisan.

```php
php artisan serve
```

### Project estructure

In this repository we can see that the current structure and the changes.

```scala
app
|-- Http
|    `-- Controllers
|        `-- CourseController.php // can be in infraestructure
`-- Providers
    `-- RepositoryServiceProvider.php // bind the CourseRepository.php interface with EloquentCourseRepository 
bootstrap
config
`-- app.php // add it here the RepositoryServiceProvider
database
lang
public
resources
routes
src
`-- Mooc // Bounded Context
    `-- Courses // Module
        |-- Application
        |   |-- Create // Actions
        |   |   `-- CourseCreator.php
        |-- Domain
        |   |-- Course.php // Entity
        |   |-- CourseDuration.php // Value Object
        |   |-- CourseId.php
        |   |-- CourseName.php
        |   `-- CourseRepository.php // Interface
        `-- Infrastructure
            `-- Persistence
                |-- Eloquent
                |   `-- CourseEloquentModel.php
                `-- EloquentCourseRepository.php
storage
test
```

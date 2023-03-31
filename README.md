<p align="center">
  <img align="center" height="200" src=" public/symfony.png">
</p>
<h1 align="center">API for Job Board Management</h1>
The API for Job Board Management is a RESTful web service developed with Symfony, designed to enable clients to manage job postings and applications for a job board. The API offers endpoints for managing companies and job postings, applicants, job applications, and reporting features.

The API includes user authentication features, where clients can register and log in to the application using a token to access the routes. The API also allows clients to search and filter job postings based on job title, company, location, and other relevant criteria.

The Job Board API comprises entities such as users, companies, jobs, and applicants, and the fields of these entities are customizable. The API provides well-organized routes to allow clients to perform CRUD operations on entities.

Requirements <hr/>
PHP 8.2
<a href="https://getcomposer.org/" rel="nofollow">Composer</a>
<a href="https://www.mamp.info/en/mamp/windows/" rel="nofollow">MAMP</a>
<a href="https://symfony.com/download" rel="nofollow">Symfony CLI</a> (optional)
Installation <hr/>
Clone the repository:
bash
Copy code
git clone git@github.com:KrivanRaulAdrian/job-board-api.git
Navigate to the directory:
bash
Copy code
cd job-board-api/
Install the Composer dependencies:
Copy code
composer install
Go to MySQL and create the job-board-api database.
Create a .env.local file and add your database connection. For example:
dotenv
Copy code
DATABASE_URL="mysql://root:@localhost:3306/job-board-api"
Create the tables:
bash
Copy code
php bin/console doctrine:migrations:migrate
Run the application:
arduino
Copy code
symfony server:start
# or
php -S localhost:8000 -t public
Go to http://localhost:8000
Note: To generate the JWT security [keypair], use a Linux container running the following command: docker-compose run -it php-fpm php bin/console lexik:jwt:generate-keypair.

Routes <hr/>
To access the API documentation, go to http://localhost:8000/api/doc.

<p align="center">
  <img align="center" src=" public/job-board-api.png">
</p>
Quality Tools <hr/>
You can use PHP CS Fixer to check the code style and PHPStan for static analysis.

Code Style
Install PHP CS Fixer:

bash
Copy code
composer install --working-dir=tools/php-cs-fixer
Run PHP CS Fixer:

css
Copy code
php tools/php-cs-fixer/vendor/bin/php-cs-fixer fix src --rules=@PSR12
Static Analysis
Install PHPStan:

lua
Copy code
composer require --dev phpstan/phpstan-symfony
If you also install phpstan/extension-installer, then you're all set!

<details>
  <summary>Manual installation</summary>
If you don't want to use phpstan/extension-installer, include extension.neon in your project's PHPStan config:

bash
Copy code
includes:
    - vendor/phpstan/phpstan-symfony/extension.neon
To perform framework-specific checks, include this file as well:

bash
Copy code
includes:
    - vendor/phpstan/phpstan-symfony/rules.ne
WordPress Bedrock with Timber Setup
=========================
[![GitHub Workflow Status](https://img.shields.io/github/workflow/status/mubarak-mohamed/wordpress-dev/Testing?style=flat-square)](https://github.com/mubarak-mohamed/wordpress-dev/actions/workflows/testing.yml?query=branch%3Amaster+workflow%3ATesting)
![Packagist Downloads](https://img.shields.io/packagist/dt/mubarak-mohamed/wordpress-dev?style=flat-square)
![Packagist PHP Version Support](https://img.shields.io/packagist/php-v/mubarak-mohamed/wordpress-dev?style=flat-square)
[![License](https://poser.pugx.org/mubarak-mohamed/wordpress-dev/license)](https://packagist.org/packages/mubarak-mohamed/wordpress-dev) 
## Description

This project uses WordPress with a Bedrock structure, managed by DDEV, and utilizes Timber for templating with Twig. This setup provides a modern development environment for building WordPress sites.

## Technologies Used

- **WordPress**: A popular content management system.
- **DDEV**: A local development environment for PHP applications.
- **Bedrock**: A modern WordPress stack that helps you manage your project dependencies and environment.
- **Timber**: A WordPress plugin that allows you to use Twig as a templating engine.

## Prerequisites

Before you begin, ensure you have the following installed:

- [Docker](https://www.docker.com/get-started) (for containerization)
- [DDEV](https://ddev.readthedocs.io/en/stable/) (for local development)
- [Composer](https://getcomposer.org/) (for PHP dependency management)
- [Node.js](https://nodejs.org/) (for managing front-end dependencies)


## Project Structure
```markdown
Here’s a brief overview of the project structure:

your-repo-name/
├── .ddev/                # DDEV configuration files
├── config/               # Bedrock configuration files
│   ├── application.php
│   ├── environments/
│   └── ...
├── web/                  # WordPress core files
│   ├── app/              # Bedrock application files
│   ├── wp/               # WordPress files
│   └── ...
├── vendor/               # Composer dependencies
├── .env                  # Environment variables
├── composer.json         # PHP dependencies
├── package.json          # Node.js dependencies
└── ...
```

## Setup Instructions

### 1. Clone the Repository
Clone the repository to your local machine:

```bash 
git clone https://github.com/mubarak-mohamed/wordpress-dev.git
cd wordpress-dev
```
### 2. Install PHP Dependencies

Run the following command to install PHP dependencies using Composer:

Run the following command to install PHP dependencies:
```bash 
composer install
```
### 3.Install Node.js Dependencies (if applicable)

If your project has front-end dependencies, run:
```bash
npm install
```
### 4. Configure DDEV
Initialize DDEV in your project directory:

```bash
ddev config
```
Follow the prompts to set up your project. Choose the appropriate options for your project type (WordPress). For example:

    Project name: your-project-name
    Docroot location: web
    Project type: wordpress

### 5.  Start the DDEV Environment

Start the DDEV environment with:

```bash
ddev start
```
### 6. Access Your Site

Once DDEV is running, you can access your WordPress site at:
```code
http://your-project-name.ddev.site
```

### 7. Configure Bedrock

Make sure to configure your ```.env```file in the Bedrock directory. You can copy the example file:

```bash
cp .env.example .env
```
Edit the```.env``` file to set your database credentials and other environment variables. Here’s an example of what your ```.env```  file might look like:
```dotenv
DB_NAME=your_db_name
DB_USER=db_user
DB_PASSWORD=db_password
DB_HOST=db
WP_ENV=development
WP_HOME=http://your-project-name.ddev.site
WP_SITEURL=${WP_HOME}/wp
``` 
### 8.Install Timber

To install Timber, you can add it via Composer:
```bash
composer require timber/timber
```
### 9. Create Your First Twig Template

Create a new Twig template in the ```views``` directory. For example, create ```index.twig```:
```twig
<!DOCTYPE html>
<html>
<head>
    <title>{{ site.title }}</title>
    <link rel="stylesheet" href="{{ asset('style.css') }}">
</head>
<body>
    <h1>{{ post.title }}</h1>
    <div>{{ post.content }}</div>
</body>
</html>
```

### 10. Update Your Theme

Make sure to update your theme to use Timber. In your ```function.php```
you can set up Timber like this:

```php
<?php
<?php
use Timber\Timber;

class MyTheme extends Timber\Site {
    public function __construct() {
        parent::__construct();
    }
}

new MyTheme();
```

### 11. Build Assets (if applicable)

If you have front-end assets to build, run:

```bash
npm run build
```

### 12. Database Setup

If you need to set up a new database, you can do so by running:

```bash
ddev mysql
```
### 13. Run Migrations
If you have migrations to run, you can do so by running:
   ```bash
   ddev exec wp db update
   ```
   or
   ```bash
   ddev exec wp db migrate
   ```
   depending on your needs.
   ### 14. Run Composer Install
   If you need to run composer install, you can do so by running:

 ```bash
 ddev exec composer install
  ```
  ### 15. Run WP-CLI Commands
  If you need to run WP-CLI commands, you can do so by running:
  ```bash
   ddev exec wp <command>
  ```
Replace `<command>` with the actual WP-CLI command you want to run.
### 16. Test Your Site 

Once you've completed the above steps, you can test your site by visiting ` http://localhost:80 ` in your web browser.

## Additional Resources

- [DDEV Documentation](https://ddev.readthedocs.io/en/stable/)
- [Bedrock Documentation](https://roots.io/bedrock/)
- [Timber Documentation](https://timber.github.io/timber/) 
## License
This project is is an open-sourced software licensed under the [MIT license](https://github.com/mediumart/orange/blob/master/LICENSE.txt).

## Contributing :
Contributions are what make the open-source community such an amazing place to learn, inspire, and create 
. Any contributions you make are **greatly appreciated**.
If you have a suggestion that would make this better, please fork the Repo and create a pull request
. Don't forget to give the project a star! Thanks again! .


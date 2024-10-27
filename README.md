<div align="center">
    <a href="https://github.com/php-flasher/php-flasher/blob/2.x/docs/palestine.md">
        <img src="https://raw.githubusercontent.com/php-flasher/art/main/palestine-banner-support.svg" width="800px"  alt="Help Palestine"/>
    </a>
</div>

<p align="center">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/php-flasher/art/main/php-flasher-logo-dark.png">
      <img src="https://raw.githubusercontent.com/php-flasher/art/main/php-flasher-logo.png" alt="PHPFlasher Logo">
    </picture>
</p>

<p align="center">
    <a href="https://www.linkedin.com/in/younes--ennaji"><img src="https://img.shields.io/badge/author-@yoeunes-blue.svg" alt="Author Badge"></a>
    <a href="https://github.com/php-flasher/php-flasher"><img src="https://img.shields.io/badge/source-php--flasher/php--flasher-blue.svg" alt="Source Code Badge"></a>
    <a href="https://github.com/php-flasher/php-flasher/releases"><img src="https://img.shields.io/github/tag/php-flasher/flasher.svg" alt="GitHub Release Badge"></a>
    <a href="https://github.com/php-flasher/flasher/blob/master/LICENSE"><img src="https://img.shields.io/badge/license-MIT-brightgreen.svg" alt="License Badge"></a>
    <a href="https://packagist.org/packages/php-flasher/flasher"><img src="https://img.shields.io/packagist/dt/php-flasher/flasher.svg" alt="Packagist Downloads Badge"></a>
    <a href="https://github.com/php-flasher/php-flasher"><img src="https://img.shields.io/github/stars/php-flasher/php-flasher.svg" alt="GitHub Stars Badge"></a>
    <a href="https://packagist.org/packages/php-flasher/flasher"><img src="https://img.shields.io/packagist/php-v/php-flasher/flasher.svg" alt="Supported PHP Version Badge"></a>
</p>

## Table of Contents

- [About PHPFlasher Laravel Adapter](#about-phpflasher-laravel-adapter)
- [Features](#features)
- [Supported Versions](#supported-versions)
- [Installation](#installation)
    - [Core Package](#core-package)
    - [Adapters](#adapters)
- [Configuration](#configuration)
    - [Configuration File](#configuration-file)
    - [Configuration Options](#configuration-options)
- [Quick Start](#quick-start)
- [Usage Examples](#usage-examples)
- [Adapters Overview](#adapters-overview)
- [Official Documentation](#official-documentation)
- [Contributors and Sponsors](#contributors-and-sponsors)
- [Contact](#contact)
- [License](#license)

## About PHPFlasher Laravel Adapter

**PHPFlasher Laravel Adapter** is an open-source package that seamlessly integrates PHPFlasher's powerful flash messaging capabilities into your **Laravel** applications. It simplifies the process of adding flash messages, providing an intuitive API to enhance user experience with minimal setup.

With PHPFlasher Laravel Adapter, you can effortlessly display success, error, warning, and informational messages to your users, ensuring clear communication of application states and actions.

## Features

- **Seamless Laravel Integration**: Designed specifically for Laravel, ensuring compatibility and ease of use.
- **Multiple Notification Libraries**: Supports various frontend libraries like Toastr, Noty, SweetAlert, and Notyf.
- **Flexible Configuration**: Customize the appearance and behavior of flash messages to fit your application's needs.
- **Intuitive API**: Simple methods to create and manage flash messages without boilerplate code.
- **Extensible**: Easily add or create new adapters for different frontend libraries.

## Supported Versions

| PHPFlasher Laravel Adapter Version | PHP Version | Laravel Version |
|------------------------------------|-------------|-----------------|
| **v2.x**                           | ≥ 8.2       | ≥ 11            |
| **v1.x**                           | ≥ 5.3       | ≥ 4.0           |

> **Note:** Ensure your project meets the PHP and Laravel version requirements for the PHPFlasher Laravel Adapter version you intend to use. For older PHP or Laravel versions, refer to [PHPFlasher v1.x](https://github.com/php-flasher/flasher-laravel/tree/1.x).

## Installation

### Core Package

Install the PHPFlasher Laravel Adapter via Composer:

```bash
composer require php-flasher/flasher-laravel
```

After installation, set up the necessary assets:

```shell
php artisan flasher:install
```

> **Note:** PHPFlasher automatically injects the necessary JavaScript and CSS assets into your Blade templates. No additional steps are required for asset injection.

### Adapters

PHPFlasher provides various adapters for different notification libraries. Below is an overview of available adapters for Laravel:

- [flasher-toastr-laravel](https://github.com/php-flasher/flasher-toastr-laravel) - Laravel Adapter
- [flasher-noty-laravel](https://github.com/php-flasher/flasher-noty-laravel) - Laravel Adapter
- [flasher-notyf-laravel](https://github.com/php-flasher/flasher-notyf-laravel) - Laravel Adapter
- [flasher-sweetalert-laravel](https://github.com/php-flasher/flasher-sweetalert-laravel) - Laravel Adapter

For detailed installation and usage instructions for each adapter, refer to their respective `README.md`.

## Configuration

After installing the PHPFlasher Laravel Adapter, you can configure it by publishing the configuration file or by modifying it directly.

### Configuration File

If you need to customize the default settings, publish the configuration file using the following command:

```bash
php artisan flasher:install --config
```

This will create a file at `config/flasher.php` with the following content:

```php
<?php

declare(strict_types=1);

use Flasher\Prime\Configuration;

return Configuration::from([
    // Default notification library (e.g., 'flasher', 'toastr', 'noty', 'notyf', 'sweetalert')
    'default' => 'flasher',

    // Path to the main PHPFlasher JavaScript file
    'main_script' => '/vendor/flasher/flasher.min.js',

    // List of CSS files to style your notifications
    'styles' => [
        '/vendor/flasher/flasher.min.css',
    ],

    // Set global options for all notifications (optional)
    // 'options' => [
    //     'timeout' => 5000, // Time in milliseconds before the notification disappears
    //     'position' => 'top-right', // Where the notification appears on the screen
    // ],

    // Automatically inject JavaScript and CSS assets into your HTML pages
    'inject_assets' => true,

    // Enable message translation using Laravel's translation service
    'translate' => true,

    // URL patterns to exclude from asset injection and flash_bag conversion
    'excluded_paths' => [],

    // Map Laravel flash message keys to notification types
    'flash_bag' => [
        'success' => ['success'],
        'error' => ['error', 'danger'],
        'warning' => ['warning', 'alarm'],
        'info' => ['info', 'notice', 'alert'],
    ],

    // Set criteria to filter which notifications are displayed (optional)
    // 'filter' => [
    //     'limit' => 5, // Maximum number of notifications to show at once
    // ],

    // Define notification presets to simplify notification creation (optional)
    // 'presets' => [
    //     'entity_saved' => [
    //         'type' => 'success',
    //         'title' => 'Entity saved',
    //         'message' => 'Entity saved successfully',
    //     ],
    // ],
]);
```

### Configuration Options

| **Option**       | **Description**                                                                                                           |
|------------------|---------------------------------------------------------------------------------------------------------------------------|
| `default`        | **String**: The default notification library to use (e.g., `'flasher'`, `'toastr'`, `'noty'`, `'notyf'`, `'sweetalert'`). |
| `main_script`    | **String**: Path to the main PHPFlasher JavaScript file.                                                                  |
| `styles`         | **Array**: List of CSS files to style your notifications.                                                                 |
| `options`        | **Array** (Optional): Global options for all notifications (e.g., `'timeout'`, `'position'`).                             |
| `inject_assets`  | **Boolean**: Whether to automatically inject JavaScript and CSS assets into your HTML pages.                              |
| `translate`      | **Boolean**: Enable message translation using Laravel’s translation service.                                              |
| `excluded_paths` | **Array**: URL patterns to exclude from asset injection and flash_bag conversion.                                         |
| `flash_bag`      | **Array**: Map Laravel flash message keys to notification types.                                                          |
| `filter`         | **Array** (Optional): Criteria to filter which notifications are displayed (e.g., `'limit'`).                             |
| `presets`        | **Array** (Optional): Define notification presets to simplify notification creation.                                      |

## Quick Start

To display a notification message, you can either use the `flash()` helper function or obtain an instance of `flasher` from the service container. Then, before returning a view or redirecting, call the desired method (`success()`, `error()`, etc.) and pass in the message to be displayed.

### Using the `flash()` Helper

```php
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;

class BookController extends Controller
{
    public function saveBook()
    {
        // Your logic here

        flash('Your changes have been saved!');

        return redirect()->back();
    }
}
```

### Using the `flasher` Service

```php
<?php

namespace App\Http\Controllers;

use Flasher\Prime\FlasherInterface;

class AnotherController extends Controller
{
    /**
     * If you prefer to use dependency injection
     */
    public function register(FlasherInterface $flasher)
    {
        // Your logic here
        
        $flasher->success('Your changes have been saved!');

        // ... redirect or render the view
    }

    public function update()
    {
        // Your logic here

        app('flasher')->error('An error occurred while updating.');

        return redirect()->back();
    }
}
```

## Usage Examples

### Success Message

```php
flash()->success('Operation completed successfully!');
```

### Error Message

```php
flash()->error('An error occurred.');
```

### Info Message

```php
flash()->info('This is an informational message.');
```

### Warning Message

```php
flash()->warning('This is a warning message.');
```

### Passing Options

```php
flash()->success('Custom message with options.', ['timeout' => 3000, 'position' => 'bottom-left']);
```

### Using presets

Define a preset in your `config/flasher.php`:

```php
<?php

declare(strict_types=1);

use Flasher\Prime\Configuration;

return Configuration::from([
    // ... other configurations

    'presets' => [
        'entity_saved' => [
            'type' => 'success',
            'title' => 'Entity Saved',
            'message' => 'The entity has been saved successfully.',
        ],
        'entity_deleted' => [
            'type' => 'warning',
            'title' => 'Entity Deleted',
            'message' => 'The entity has been deleted.',
        ],
    ],
]);
```

Use the preset in your controller:

```php
<?php

namespace App\Http\Controllers;

use Illuminate\Http\RedirectResponse;
use App\Http\Controllers\Controller;

class BookController extends Controller
{
    /**
     * Save a new book entity.
     *
     * @return RedirectResponse
     */
    public function saveBook(): RedirectResponse
    {
        // Your saving logic here (e.g., validating and storing the book)

        // Trigger the 'entity_saved' preset
        flash()->preset('entity_saved');

        return redirect()->route('books.index');
    }

    /**
     * Delete an existing book entity.
     *
     * @return RedirectResponse
     */
    public function deleteBook(): RedirectResponse
    {
        // Your deletion logic here (e.g., finding and deleting the book)

        // Trigger the 'entity_deleted' preset
        flash()->preset('entity_deleted');

        return redirect()->route('books.index');
    }
}
```

## Adapters Overview

PHPFlasher supports various adapters to integrate seamlessly with different frontend libraries. Below is an overview of available adapters for Laravel:

| Adapter Repository                                                                      | Description                    |
|-----------------------------------------------------------------------------------------|--------------------------------|
| [flasher-laravel](https://github.com/php-flasher/flasher-laravel)                       | Laravel framework adapter      |
| [flasher-toastr-laravel](https://github.com/php-flasher/flasher-toastr-laravel)         | Toastr adapter for Laravel     |
| [flasher-noty-laravel](https://github.com/php-flasher/flasher-noty-laravel)             | Noty adapter for Laravel       |
| [flasher-notyf-laravel](https://github.com/php-flasher/flasher-notyf-laravel)           | Notyf adapter for Laravel      |
| [flasher-sweetalert-laravel](https://github.com/php-flasher/flasher-sweetalert-laravel) | SweetAlert adapter for Laravel |

> **Note:** Each adapter has its own repository. For detailed installation and usage instructions, please refer to the [Official Documentation](https://php-flasher.io).

## Official Documentation

Comprehensive documentation for PHPFlasher is available at [https://php-flasher.io](https://php-flasher.io). Here you will find detailed guides, API references, and advanced usage examples to help you get the most out of PHPFlasher.

## Contributors and sponsors

Join our team of contributors and make a lasting impact on our project!

We are always looking for passionate individuals who want to contribute their skills and ideas.
Whether you're a developer, designer, or simply have a great idea, we welcome your participation and collaboration.

Shining stars of our community:

<!-- ALL-CONTRIBUTORS-LIST:START -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->
<table>
  <tbody>
    <tr>
      <td align="center" valign="top" width="14.28%"><a href="https://www.linkedin.com/in/younes--ennaji/"><img src="https://avatars.githubusercontent.com/u/10859693?v=4?s=100" width="100px;" alt="Younes ENNAJI"/><br /><sub><b>Younes ENNAJI</b></sub></a><br /><a href="https://github.com/php-flasher/php-flasher/commits?author=yoeunes" title="Code">💻</a> <a href="https://github.com/php-flasher/php-flasher/commits?author=yoeunes" title="Documentation">📖</a> <a href="#maintenance-yoeunes" title="Maintenance">🚧</a></td>
      <td align="center" valign="top" width="14.28%"><a href="https://github.com/salmayno"><img src="https://avatars.githubusercontent.com/u/27933199?v=4?s=100" width="100px;" alt="Salma Mourad"/><br /><sub><b>Salma Mourad</b></sub></a><br /><a href="#financial-salmayno" title="Financial">💵</a></td>
      <td align="center" valign="top" width="14.28%"><a href="https://www.youtube.com/rstacode"><img src="https://avatars.githubusercontent.com/u/35005761?v=4?s=100" width="100px;" alt="Nashwan Abdullah"/><br /><sub><b>Nashwan Abdullah</b></sub></a><br /><a href="#financial-codenashwan" title="Financial">💵</a></td>
      <td align="center" valign="top" width="14.28%"><a href="https://darvis.nl/"><img src="https://avatars.githubusercontent.com/u/7394837?v=4?s=100" width="100px;" alt="Arvid de Jong"/><br /><sub><b>Arvid de Jong</b></sub></a><br /><a href="#financial-darviscommerce" title="Financial">💵</a></td>
      <td align="center" valign="top" width="14.28%"><a href="https://ashallendesign.co.uk/"><img src="https://avatars.githubusercontent.com/u/39652331?v=4?s=100" width="100px;" alt="Ash Allen"/><br /><sub><b>Ash Allen</b></sub></a><br /><a href="#design-ash-jc-allen" title="Design">🎨</a></td>
      <td align="center" valign="top" width="14.28%"><a href="https://about.me/murrant"><img src="https://avatars.githubusercontent.com/u/39462?v=4?s=100" width="100px;" alt="Tony Murray"/><br /><sub><b>Tony Murray</b></sub></a><br /><a href="https://github.com/php-flasher/php-flasher/commits?author=murrant" title="Code">💻</a></td>
      <td align="center" valign="top" width="14.28%"><a href="https://github.com/n3wborn"><img src="https://avatars.githubusercontent.com/u/10246722?v=4?s=100" width="100px;" alt="Stéphane P"/><br /><sub><b>Stéphane P</b></sub></a><br /><a href="https://github.com/php-flasher/php-flasher/commits?author=n3wborn" title="Documentation">📖</a></td>
    </tr>
    <tr>
      <td align="center" valign="top" width="14.28%"><a href="https://www.instagram.com/lucas.maciel_z"><img src="https://avatars.githubusercontent.com/u/80225404?v=4?s=100" width="100px;" alt="Lucas Maciel"/><br /><sub><b>Lucas Maciel</b></sub></a><br /><a href="#design-LucasStorm" title="Design">🎨</a></td>
      <td align="center" valign="top" width="14.28%"><a href="https://github.com/AhmedGamal"><img src="https://avatars.githubusercontent.com/u/11786167?v=4?s=100" width="100px;" alt="Ahmed Gamal"/><br /><sub><b>Ahmed Gamal</b></sub></a><br /><a href="https://github.com/php-flasher/php-flasher/commits?author=AhmedGamal" title="Code">💻</a> <a href="https://github.com/php-flasher/php-flasher/commits?author=AhmedGamal" title="Documentation">📖</a></td>
    </tr>
  </tbody>
</table>

<!-- markdownlint-restore -->
<!-- prettier-ignore-end -->

<!-- ALL-CONTRIBUTORS-LIST:END -->

## Contact

PHPFlasher is being actively developed by <a href="https://github.com/yoeunes">yoeunes</a>.
You can reach out with questions, bug reports, or feature requests on any of the following:

- [Github Issues](https://github.com/php-flasher/php-flasher/issues)
- [Github](https://github.com/yoeunes)
- [Twitter](https://twitter.com/yoeunes)
- [Linkedin](https://www.linkedin.com/in/younes--ennaji/)
- [Email me directly](mailto:younes.ennaji.pro@gmail.com)

## License

PHPFlasher is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).

<p align="center"> <b>Made with ❤️ by <a href="https://www.linkedin.com/in/younes--ennaji/">Younes ENNAJI</a> </b> </p>

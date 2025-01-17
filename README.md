<h1 align="center">
    <a href="http://demos.krajee.com" title="Krajee Demos" target="_blank">
        <img src="http://kartik-v.github.io/bootstrap-fileinput-samples/samples/krajee-logo-b.png" alt="Krajee Logo"/>
    </a>
    <br>
    yii2-bootstrap5-dropdown
    <hr>
    <a href="https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=DTP3NZQ6G2AYU"
       title="Donate via Paypal" target="_blank"><img src="https://kartik-v.github.io/bootstrap-fileinput-samples/samples/donate.png" height="60" alt="Donate"/></a>
    &nbsp; &nbsp; &nbsp;
    <a href="https://www.buymeacoffee.com/kartikv" title="Buy me a coffee" ><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" height="60" alt="kartikv" /></a>
</h1>

[![Stable Version](https://poser.pugx.org/kartik-v/yii2-bootstrap5-dropdown/v/stable)](https://packagist.org/packages/kartik-v/yii2-bootstrap5-dropdown)
[![Unstable Version](https://poser.pugx.org/kartik-v/yii2-bootstrap5-dropdown/v/unstable)](https://packagist.org/packages/kartik-v/yii2-bootstrap5-dropdown)
[![License](https://poser.pugx.org/kartik-v/yii2-bootstrap5-dropdown/license)](https://packagist.org/packages/kartik-v/yii2-bootstrap5-dropdown)
[![Total Downloads](https://poser.pugx.org/kartik-v/yii2-bootstrap5-dropdown/downloads)](https://packagist.org/packages/kartik-v/yii2-bootstrap5-dropdown)
[![Monthly Downloads](https://poser.pugx.org/kartik-v/yii2-bootstrap5-dropdown/d/monthly)](https://packagist.org/packages/kartik-v/yii2-bootstrap5-dropdown)
[![Daily Downloads](https://poser.pugx.org/kartik-v/yii2-bootstrap5-dropdown/d/daily)](https://packagist.org/packages/kartik-v/yii2-bootstrap5-dropdown)

Enhanced Bootstrap 5.x dropdown widget for Yii2 framework with nested submenu support.

## Demo
You can see detailed [documentation](http://demos.krajee.com/bootstrap5-dropdown) on usage of the extension.

## Installation

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

> NOTE: Check the [composer.json](https://github.com/kartik-v/yii2-bootstrap5-dropdown/blob/master/composer.json) for this extension's requirements and dependencies. Read this [web tip /wiki](http://webtips.krajee.com/setting-composer-minimum-stability-application/) on setting the `minimum-stability` settings for your application's composer.json.

Either run

```
$ php composer.phar require kartik-v/yii2-bootstrap5-dropdown "@dev"
```

or add

```
"kartik-v/yii2-bootstrap5-dropdown": "@dev"
```

to the ```require``` section of your `composer.json` file.

## Usage

### Dropdown Menu NavBar

```php
use yii\bootstrap5\NavBar;
use yii\bootstrap5\Nav;
use kartik\bs4dropdown\Dropdown;
use yii\helpers\Html;

NavBar::begin(['brandLabel' => 'NavBar Test']);
echo Nav::widget([
    'items' => [
        ['label' => 'Home', 'url' => ['/site/index']],
        [
            'label' => 'Dropdown', 
            'items' => [
                ['label' => 'Section 1', 'url' => '/'],
                ['label' => 'Section 2', 'url' => '#'],
                [
                     'label' => 'Section 3', 
                     'items' => [
                         ['label' => 'Section 3.1', 'url' => '/'],
                         ['label' => 'Section 3.2', 'url' => '#'],
                         [
                             'label' => 'Section 3.3', 
                             'items' => [
                                 ['label' => 'Section 3.3.1', 'url' => '/'],
                                 ['label' => 'Section 3.3.2', 'url' => '#'],
                             ],
                         ],
                     ],
                 ],
            ],
        ],
        ['label' => 'About', 'url' => ['/site/about']],
    ],
    'dropdownClass' => Dropdown::classname(), // use the custom dropdown
    'options' => ['class' => 'navbar-nav mr-auto'],
]);
NavBar::end();

<div class="dropdown">
    <?php
        echo Html::button('Dropdown Button', [
           'id' => 'dropdownMenuButton',
           'class' => 'btn btn-secondary dropdown-toggle'
           'data-toggle' => 'dropdown',
           'aria-haspopup' => 'true',
           'aria-expanded' => 'false'
        ]);
        echo Dropdown::widget([
            'items' => [
                ['label' => 'Section 1', 'url' => '/'],
                ['label' => 'Section 2', 'url' => '#'],
                [
                     'label' => 'Section 3', 
                     'items' => [
                         ['label' => 'Section 3.1', 'url' => '/'],
                         ['label' => 'Section 3.2', 'url' => '#'],
                         [
                             'label' => 'Section 3.3', 
                             'items' => [
                                 ['label' => 'Section 3.3.1', 'url' => '/'],
                                 ['label' => 'Section 3.3.2', 'url' => '#'],
                             ],
                         ],
                     ],
                 ],
            ],
            'options' => ['aria-labelledby' => 'dropdownMenuButton']
        ]);
    ?>
</div>
```

### Dropdown Solo Button

```php
<?php 
use \yii\helpers\Html;
use kartik\bs4dropdown\Dropdown;
?>
<div class="dropdown">
    <?php
        echo Html::button('Dropdown Button', [
           'id' => 'dropdownMenuButton',
           'class' => 'btn btn-secondary dropdown-toggle'
           'data-toggle' => 'dropdown',
           'aria-haspopup' => 'true',
           'aria-expanded' => 'false'
        ]);
        echo Dropdown::widget([
            'items' => [
                ['label' => 'Section 1', 'url' => '/'],
                ['label' => 'Section 2', 'url' => '#'],
                [
                     'label' => 'Section 3', 
                     'items' => [
                         ['label' => 'Section 3.1', 'url' => '/'],
                         ['label' => 'Section 3.2', 'url' => '#'],
                         [
                             'label' => 'Section 3.3', 
                             'items' => [
                                 ['label' => 'Section 3.3.1', 'url' => '/'],
                                 ['label' => 'Section 3.3.2', 'url' => '#'],
                             ],
                         ],
                     ],
                 ],
            ],
            'options' => ['aria-labelledby' => 'dropdownMenuButton']
        ]);
    ?>
</div>
```

### Dropdown Button Alt (using ButtonDropdown)

```php
use \yii\helpers\Html;
use kartik\bs4dropdown\ButtonDropdown;
echo ButtonDropdown::widget([
    'label' => 'Dropdown Button',
    'dropdown' => [
        'items' => [
            ['label' => 'Section 1', 'url' => '/'],
            ['label' => 'Section 2', 'url' => '#'],
            [
                 'label' => 'Section 3', 
                 'items' => [
                     ['label' => 'Section 3.1', 'url' => '/'],
                     ['label' => 'Section 3.2', 'url' => '#'],
                     [
                         'label' => 'Section 3.3', 
                         'items' => [
                             ['label' => 'Section 3.3.1', 'url' => '/'],
                             ['label' => 'Section 3.3.2', 'url' => '#'],
                         ],
                     ],
                 ],
             ],
        ],
    ],
    'buttonOptions' => ['class'=>'btn-secondary']
]);
```

## License

**yii2-bootstrap5-dropdown** is released under the BSD-3-Clause License. See the bundled `LICENSE.md` for details.
# WooCommerce integration for Sage 10 themes

This package enables WooCommerce integration with Sage 10 themes and Blade templates.

## Installation

Install the package **in your theme folder**:

```bash
cd wp-content/themes/your-sage-theme-folder
```
open composer.json and add:  

```bash
  "repositories": [
    {
      "type": "vcs",
      "url": "https://github.com/riccardomel/woocommerce-sage-10"
    }
  ],
  "require": {
    ... OTHER  REQUIRE HERE ...
     "riccardomel/woocommerce-sage-10": "1.0.0"
  },
```
then: 

```
composer install
```

Add package path to Sage view namespaces in config/view.php:

    'namespaces' => [
       'SageWoocommerce' => get_theme_file_path('/vendor/riccardomel/woocommerce-sage-10/src/views'),
    ],

## Usage

Create `/resources/views/woocommerce` folder in your theme and place there any template used by WooCommerce with `.blade.php` extension. This template will be loaded instead of a template from the WooCommerce plugin. If you want to replace particular template, please have a look into plugin folder `woocommerce/templates` and use same folder structure and file name (and change the extension to `.blade.php`) as the original template.

By default, you will get an error message that themes without `header.php`, `footer.php` and `sidebar.php` are deprecated. You have to replace `single-product.php` and `archive-product.php` templates with your Blade template. You can find those two files in `/examples/resources/views/woocommerce` folder of this package. The trick is not to use `get_header`, `get_footer` or `get_sidebar` functions, because it's handled differently with Blade. Instead of that, you can use actions:

```php
do_action('get_header', 'shop');
do_action('get_sidebar', 'shop');
do_action('get_footer', 'shop');
```


## Useful Links
Templates: [WooComm templates](https://docs.woocommerce.com/document/template-structure/)

Original: [Woocommerce for Sage 9](https://github.com/roots/sage-woocommerce)

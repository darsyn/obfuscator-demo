# Obfuscator Example

Obfuscated source files are decrypted at runtime. Proof-of-concept demo only, does not currently work with OpCache.

### Setup

```bash
$ git clone git://github.com/darsyn/obfuscator-demo.git
$ cd obfuscator-demo
$ composer install --no-interaction
```

Now look at PHP source code such as [`app/Kernel.php`](app/Kernel.php) or
[`src/AppBundle/DependencyInjection/AppExtension.php`](src/AppBundle/DependencyInjection/AppExtension.php).

### What magic is this?

This is how the demo application was created:

1. Clone [`symfony/symfony-standard`](https://github.com/symfony/symfony-standard)
2. Install obfuscator with `composer require darsyn/obfuscator`
3. Enable with `new Obfuscator(...)` in [app.php](web/app.php), [app_dev.php](web/app_dev.php) and [console](bin/console).
4. Make sure your kernel is loaded via Composer and not a `require` call:
   - If using an old version of Symfony, that means making sure `AppKernel.php` is added to the classmap.
   - If using a new version of Symfony (3.3+) you should need to do anything as it's already loaded via PSR-4.
4. Obfucate source files with `./vendor/bin/obfuscate {file}`

### Really?

No, of course not. I'm lazy and used the following command instead because it's waaay quicker...

```bash
$ find src/ -name *.php -exec ./vendor/bin/obfuscate {} \;
# If your Kernel class is in app/ instead of src/:
$ ./vendor/bin/obfuscate app/Kernel.php
```

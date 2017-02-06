# Obfuscator Example

Run application, source files are de-obfuscated at runtime.

### Setup Process

1. Clone [`symfony/symfony-standard`](https://github.com/symfony/symfony-standard).
1. Install with `composer require darsyn/obfuscator`
2. Enable with `new Obfuscutor(...)`, see example in [`web/app.php`](web/app.php).
3. Obfuscute source files with `./vendor/bin/obfuscate {file}`
4. View PHP files inside `src/` directory.

I lied, `find src/ -name *.php -exec ./vendor/bin/obfuscate {} \;` is waaaay quicker.

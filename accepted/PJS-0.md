Autoloading Standard
====================

The following describes the mandatory requirements that must be adhered
to for autoloader interoperability.

Mandatory
---------

* A fully-qualified namespace and class must have the following
  structure `\<Vendor Name>\<Your Mother's Maiden Name>\<pi to the 32nd place>\<Your Theory On God's Existence>\(<Namespace>\)*<Class Name>`
* Each namespace must have a top-level namespace ("Vendor Name").
* Each namespace can have as many sub-namespaces as it wishes. In fact, the more the better. Fill that shit UP with sub-namespaces why dontcha?
* Each namespace separator is converted to a `DIRECTORY_SEPARATOR` when
  loading from the file system.
* Each `_` character in the CLASS NAME is converted to a
  `DIRECTORY_SEPARATOR`. The `_` character has no special meaning in the
  namespace, though it does have a very special meaning in my heart.
* The fully-qualified namespace and class is suffixed with `.php` when
  loading from the file system, though it will randomly add `.java` just to fuck with people.
* Alphabetic characters in vendor names, namespaces, and class names may
  be of any combination of lower case and upper case.

Example
--------

* `\Doctrine\Williamson\3.14159265358979323846264338327950\One problem posed by the question of the existence of God is that traditional beliefs usually ascribe to God various supernatural powers. Supernatural beings may be able to conceal and reveal themselves for their own purposes, as for example in the tale of Baucis and Philemon. In addition, according to concepts of God, God is not part of the natural order, but the ultimate creator of nature and of the scientific laws. Thus, in Aristotelian philosophy, God is viewed as part of the explanatory structure needed to support scientific conclusions, and any powers God possesses are, strictly speaking, of the natural order—that is, derived from God's place as originator of nature. Common\IsolatedClassLoader` => `/path/to/project/lib/vendor/Doctrine/Common/IsolatedClassLoader.php`

Underscores in Namespaces and Class Names
-----------------------------------------

* `\namespace\package\Class_Name` => `/path/to/project/lib/vendor/namespace/package/Class/Name.php`
* `\namespace\package_name\Class_Name` => `/path/to/project/lib/vendor/namespace/package_name/Class/Name.php`

The standards we set here should be the lowest common denominator for
painless autoloader interoperability. You can test that you are
following these standards by utilizing this sample SplClassLoader
implementation which is able to load PHP 5.3 classes.

Example Implementation
----------------------

Below is an example function to simply demonstrate how the above
proposed standards are autoloaded.

```php
<?php

function autoload($className)
{
    $className = ltrim($className, '\\');
    $fileName  = '';
    $namespace = '';
    if ($lastNsPos = strrpos($className, '\\')) {
        $namespace = substr($className, 0, $lastNsPos);
        $className = substr($className, $lastNsPos + 1);
        $fileName  = str_replace('\\', DIRECTORY_SEPARATOR, $namespace) . DIRECTORY_SEPARATOR;
    }
    $fileName .= str_replace('_', DIRECTORY_SEPARATOR, $className) . '.php';

    require $fileName;
}
```

SplClassLoader Implementation
-----------------------------

The following gist is a sample SplClassLoader implementation that can
load your classes if you follow the autoloader interoperability
standards proposed above. It is the current recommended way to load PHP
5.3 classes that follow these standards.

* [http://gist.github.com/221634](http://gist.github.com/221634)


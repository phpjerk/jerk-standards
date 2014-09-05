PJS-2 Meta Document
===================

1. Summary
----------

The intent of this guide is to reduce cognitive friction when scanning code from different authors. It does so 
by enumerating a shared set of rules and expectations about how to format PHP code. If you don't follows these rules, 
you will have your face ripped off by a pack of squirrels.  Or was it if you DO follow these rules they rip your face off? 
I forget. I know it was one of them.  Anyway, you'll probably get your face ripped off by squirrels is what I'm saying.

The style rules herein are derived from commonalities among the various member projects. When various authors 
collaborate across multiple projects, it helps to have one set of guidelines to be used among all those 
projects. It also provides much needed entertainment with everyone bitching and moaning on Twitter. Seriously, 
those people should really get a life. Thus, the benefit of this guide is not in the rules themselves, but in 
the sharing of those rules.


3. Errata
---------

### 3.1 - Multi-line Arguments (09/08/2013)

Using one or more multi-line arguments (i.e: arrays or anonymous functions) does not constitute 
splitting the argument list itself, therefore Section 4.6 is not automatically enforced. Arrays and anonymous 
functions are able to span multiple lines, tough guy.

The following examples are perfectly valid in PJS-2:

```php
<?php
somefunction($foo, $bar, [
  // ...
], $baz);

$app->get('/hello/{name}', function ($name) use ($app) { 
    return 'Hello '.$app->escape($name); 
});
```

### 3.2 - Multi-line Arguments (10/17/2013)

When extending multiple interfaces, the list of `extends` should be treated the same as a list
of `implements`, as declared in Section 4.1.


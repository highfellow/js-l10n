js-l10n
=======

Localisation library for projects using [requirejs](http://requirejs.org/) or [nodejs](http://nodejs.org/), based largely on code from [WebL10n](https://github.com/fabi1cazenave/webL10n). This is the core localisation engine only, ported to requirejs/nodejs in a way that is platform-neutral.

The platform-dependent code is in separate adapter modules - [js-l10n-browser](https://github.com/highfellow/js-l10n-browser) for the browser using requirejs), and [js-l10n-node-fs](https://github.com/highfellow/js-l10n-node-fs) for the filesystem under nodejs.

To use this module, you need to choose an adapter that is suitable for your application. The adapter handles loading localisation resource files; everything else is in this module.

API
===

Initialisation
--------------

The module exports a function object, L10n, which takes an adapter object as its parameter.

```
window.onload = function() {
  requirejs(['lib/l10n','lib/l10n-browser'],
      function(L10n, L10n_Browser) {
        // initialise L10n with the browser adapter.
        l10n = new L10n(new L10n_Browser());
        // now we can start loading locales using l10n.loadResource
        // ...
      });
}
```

Methods
-------

An L10n object has the following methods, for loading resource files, and translating strings.

  * loadResource: function(path, language, successCallback, failureCallback) - Load a language resource - e.g. a properties file. The meaning of 'path' depends on the adapter you are using, and is usually relative to your current path (e.g. an URL).
  * get: function(key, args, fallback) - Return the translation for 'key'. Args contains a dictionary of tokens to replace in the translated string. Fallback is used as the string if no translation is found. This works the same as in webL10n.
  * getDirection: function() - utility function to get the direction of the current language.

Usage
-----

For more information on using 'get', and on the format of the resource files, see: <https://github.com/fabi1cazenave/webL10n>.

For some example code, see [TODO]

LICENSE
=======

BSD/MIT/WTFPL license. Use at your own risk.

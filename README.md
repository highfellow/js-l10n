js-l10n
=======

Localisation library for projects using [requirejs](http://requirejs.org/) or [nodejs](http://nodejs.org/), based largely on code from [WebL10n](https://github.com/fabi1cazenave/webL10n). This is the core localisation engine only, ported to requirejs/nodejs in a way that is platform-neutral.

The platform-dependent code is in separate adapter modules - [js-l10n-browser](https://github.com/highfellow/js-l10n-browser) for the browser using requirejs), and [js-l10n-node-fs](https://github.com/highfellow/js-l10n-node-fs) for the filesystem under nodejs. There is also an adapter for the browser which works under nodejs using browserify: [js-l10-node-browserify](https://github.com/highfellow/js-l10n-node-browserify).

To use this module, you need to choose an adapter that is suitable for your application. The adapter handles loading localisation resource files; everything else is in this module.

API
===

Initialisation
--------------

The module exports an object, l10n, which has a method `setAdapter` you can use to set the adapter for your platform. E.g.:

```
requirejs(['l10n','l10n-browser'],
  function(l10n, l10nBrowser) {
    ...
    l10n.setAdapter(l10nBrowser, {baseURL: 'locales/'});
    ...
})
```

Methods
-------

An L10n object has the following methods, for loading resource files, and translating strings.

  * loadResource: function(path, language, successCallback, failureCallback) - Load a language resource - e.g. a properties file. The meaning of 'path' depends on the adapter you are using, and is usually relative to your current path (e.g. an URL).
  * get: function(key, args, fallback) - Return the translation for 'key'. Args contains a dictionary of tokens to replace in the translated string. Fallback is used as the string if no translation is found. This works the same as in webL10n.
  * getDirection: function() - utility function to get the direction of the current language.
  * setMarkStrings: function() - if you call this in your initialisation code, all localised strings will be marked with ~string~ (where the token was found), or \_string\_ (where no token was found and the fallback used). This is useful for finding unlocalised strings.

Usage
-----

For more information on using 'get', and on the format of the resource files, see: <https://github.com/fabi1cazenave/webL10n>.

For some example code, see the [browser adapter](https://github.com/highfellow/js-l10n-browser).

LICENSE
=======

BSD/MIT/WTFPL license. Use at your own risk.

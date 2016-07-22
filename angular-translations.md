## How to translate with angular

Configuring angular translations and default value
```js
  .config(function ($translateProvider) {
    $translateProvider.useStaticFilesLoader({
      prefix: '/locales/locale-',
      suffix: '.json'
    });
    $translateProvider.preferredLanguage('en_us');
    //$translateProvider.use('en_US');

```

Folder Structure

```
tree locales
locales
├── locale-en_us.json
├── locale-es_ar.json
└── locale-pt_br.json

0 directories, 3 files
```

Translations generation:

[SpreadSheet Generator](https://docs.google.com/spreadsheets/d/1ZgvwxWTVdmrP34ifpDmQSuMSp4tAJdG-fe0VAYfWXt0/edit?usp=sharing)

![Translations Sheet](https://www.dropbox.com/s/y7bsqmzucee7yv2/Screenshot%202016-06-13%2013.07.09.png?dl=1)

In this way you only maintain that in the views and avoiding modifying controllers. It'll be good to have all the translation in one json file, i.e.: `json/en_us.json` and also to avoid custom keys like "my_custom_key" in favor of `{{ "My custom key" | translate }}` or `<span translate>My custom key</span>`. Also this is more intuitive in the case some key is missing, cause the user will read it in the default value "My custom key" instad of "my_custom_key". If you need to use this functionality programmatically you can always call `$filter`.

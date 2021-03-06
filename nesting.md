<!-- toc -->
# Nesting

Nesting allows you to reference other keys in a translation. Could be useful to build glossary terms.

{% method %}
## Basic

keys

```json
{
    "nesting1": "1 $t(nesting2)",
    "nesting2": "2 $t(nesting3)",
    "nesting3": "3",
}
```

{% sample lang="js" %}
sample

```js
i18next.t('nesting1'); // -> "1 2 3"
```

You can reference keys from other namespaces by prepending the namespace: `"nesting1": "1 $t(common:nesting2)",
`

{% endmethod %}

{% method %}
## Passing options to nestings

You can pass entire data models in options.

keys

```json
{
      "girlsAndBoys": "$t(girls, {'count': {{girls}} }) and {{count__ boy",
      "girlsAndBoys_plural": "$t(girls, {'count': {{girls}} }) and {{count}} boys",
      "girls": "{{count}} girl",
      "girls_plural": "{{count}} girls"
}
```

{% sample lang="js" %}
sample

```js
i18next.t('girlsAndBoys', {count: 2, girls: 3});
// -> "3 girls and 2 boys"
```

{% endmethod %}




{% method %}
## Passing nesting to interpolated

keys

```json
{
      "key1": "hello world",
      "key2": "say: {{val}}"
}
```

{% sample lang="js" %}
sample

```js
i18next.t('key2', {val: '$t(key1)'});
// -> "say: hello world"
```

{% endmethod %}



{% method %}
## Additional options

Prefix/Suffix for nesting and other options can be overridden in init interpolation options or by passing additional options to t function:

{% sample lang="js" %}
sample

```js
i18next.init({
    interpolation: { ... }
});

i18next.t('key', {
    interpolation: { ... }
});
```
{% endmethod %}




option            | default             | description
----------------- | --------------------| -----------------
nestingPrefixEscaped     | undefined               | escaped prefix for nesting (regexSafe)
nestingSuffixEscaped     | undefined               | escaped suffix for nesting (regexSafe)


While there are a lot of options going with the defaults should get you covered.



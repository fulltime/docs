# "Antwort nicht gefunden" - Block entfernen

Legen Sie dazu innerhalb ihres Themes folgende Dateien an.

Datei 1: Theme/frontend/faq/index.tpl

```smarty
{extends file="parent:frontend/faq/index.tpl"}

{block name='frontend_index_content_faq_contact_form'}{/block}
```

Datei 2: Theme/frontend/faq/advanced.tpl

```smarty
{extends file="parent:frontend/faq/advanced.tpl"}

{block name='frontend_index_content_faq_contact_form'}{/block}
```

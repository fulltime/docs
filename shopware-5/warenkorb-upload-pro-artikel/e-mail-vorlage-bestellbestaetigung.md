# E-Mail Vorlage - Bestellbestätigung

Um die Daten auch in der Bestellbestätigung hinzuzufügen, gehen Sie bitte im Backend in die E-Mail Vorlagen und öffnen Sie dort die Vorlage sORDER. Klicken Sie danach auf den Reiter HTML-Text

Ersetzten Sie nun die Zeile:

```smarty
<td colspan="5" style="border-bottom:1px solid #cccccc;">{$details.articlename|wordwrap:80|indent:4}</td>
```

mit folgendem

```smarty
<td colspan="5" style="border-bottom:1px solid #cccccc;">{$details.articlename|wordwrap:80|indent:4}<br/>
    {foreach item=upload key=page from=$details.futi_upload_data|json_decode:1}

    <b>{$page}</b> <br/>
    {assign var=fileCounter value=0}

    {foreach $upload['name'] as $key2 => $file}
    {$fileCounter=$fileCounter+1}
    {$fileCounter}. <a href="{if $upload['linkType'][$key2]=='internal'}http://{$smarty.server.HTTP_HOST}{/if}{$upload['link'][$key2]}" target="_blank" title="{$file}">{$file}</a><br />
    {/foreach}
    {/foreach}
</td>
```

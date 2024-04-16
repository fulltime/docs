# E-Mail-Template "Bestellbestätigung" (sOrder)

Fügen Sie an gewünschter Stelle in Ihrem E-Mail-Template für die Bestellbestätigung folgenden HTML-Code ein.

Ich empfehle dies nach der Tabelle mit den Artikeln hinzufügen.

```smarty
{if $additional.transferredData}
<br/>
<strong>Daten zu Ihrer Bestellung:</strong></p><br/>
<table width="80%" border="0" style="font-family:Arial, Helvetica, sans-serif; font-size:12px;">
  <tr>
    <td bgcolor="#F7F7F2" style="border-bottom:1px solid #cccccc;"><strong>Pos.</strong></td>
    <td bgcolor="#F7F7F2" style="border-bottom:1px solid #cccccc;"><strong>Datei</strong></td>
  </tr>

  {foreach item=transferredData key=position from=$additional.transferredData}
  <tr>
    <td style="border-bottom:1px solid #cccccc;">{$position+1|fill:4} </td>
    <td style="border-bottom:1px solid #cccccc;">
      <a href="{$sShopURL}/files/basketUploadPerOrder/final/{$transferredData.uuid}/{$transferredData.filename}" target="_blank">{$transferredData.filename}</a>
    </td>
  </tr>
  {/foreach}

</table>
{/if}
```

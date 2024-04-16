# Interne E-Mail mit Daten zur Bestellung

### 1. Fügen Sie ein neues E-Mail Template hinzu

Definieren Sie dies wie folgt:

| Feld         | Wert                                             |
| ------------ | ------------------------------------------------ |
| Typ          | Order confirmation                               |
| Beschreibung | Interne E-Mail mit Daten zur Bestellung          |
| Betreff      | Daten zur Bestellung - \{{ order.orderNumber \}} |
| Absender     | \{{ salesChannel.name \}}                        |

#### Mail-Text

Text

```twig
Order number: {{ order.orderNumber }}

{% raw %}
{% for lineItem in order.nestedLineItems %}
    {% if lineItem.extensions.uploads %}
        Übertragene Daten<br/>
        {% for upload in lineItem.extensions.uploads %}
            {{ upload.filename }}
            {{ rawUrl('frontend.home.page') }}uploads/final/{{ upload.qquuid }}/{{ upload.filename }}
        {% endfor %}
    {% endif %}
{% endfor %}
{% endraw %}
```

HTML

```twig
<div style="font-family:arial; font-size:12px;">
    Order number: {{ order.orderNumber }}<br>
    <br>
    <table border="0" style="font-family:Arial, Helvetica, sans-serif; font-size:12px;">
        {% raw %}
{% for lineItem in order.nestedLineItems %}
            {% if lineItem.extensions.uploads %}
            <tr>
                <td colspan='5'>
                    Übertragene Daten<br/>
                    <ul>
                    {% for upload in lineItem.extensions.uploads %}
                        <li><a href="{{ url('frontend.home.page') }}uploads/final/{{ upload.qquuid }}/{{ upload.filename }}" class="cart-item-label" target="_blank">{{ upload.filename }}</a></li>
                    {% endfor %}
                    </ul>
                </td>
            </tr>
            {% endif %}
        {% endfor %}
{% endraw %}
    </table>
</div>
```

### 2. Neuen Flow im Flow Builder anlegen

| Feld  | Wert           |
| ----- | -------------- |
| Name  | Interne E-Mail |
| Aktiv | aktiviert      |

**Flow**

* Auslöser => Bestellabschluss / Bestellung / Eingang
* Aktion (DANN) hinzufügen
* Aktion auswählen => E-Mail senden
  * Andere Absender-Adresse verwenden: Standard
  * Empfänger: Administrator oder Anderer Empfänger
  * E-Mail-Template: Interne E-Mail mit Daten zur Bestellung

# E-Mail-Template "Bestellbestätigung"

Fügen Sie an gewünschter Stelle in Ihrem E-Mail-Template für die Bestellbestätigung folgenden HTML-Code ein.

```twig
<br/>
<strong>Daten zu Ihrer Bestellung:</strong><br>
{% raw %}
{% if order.extensions.orderUploads %}
    {% for upload in order.extensions.orderUploads %}
        <a href="{{ url('frontend.home.page') }}order-uploads/final/{{ upload.qquuid }}/{{ upload.filename }}" class="cart-item-label" target="_blank">{{ upload.filename }}</a>  <br/>
    {% endfor %}
{% endif %}
{% endraw %}
```

Ich empfehle dies nach der Tabelle mit den Artikeln hinzufügen.

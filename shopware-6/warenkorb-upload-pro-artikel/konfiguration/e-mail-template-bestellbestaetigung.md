# E-Mail-Template "Bestellbestätigung"

Nachfolgend finden Sie ein Beispiel wie Sie die übertragenen Daten in das E-Mail-Template "Bestellbestätigung" hinzufügen können.

Fügen Sie an gewünschter Stelle aber innerhalb von der for Schleife für die items folgenden Code ein

**for Schleife**

```twig
{% raw %}
{% for lineItem in order.nestedLineItems %}
{% endraw %}
```

### Code für die Ausgabe der Daten <a href="#code_fr_die_ausgabe_der_daten" id="code_fr_die_ausgabe_der_daten"></a>

```twig
{% raw %}
{% if lineItem.extensions.uploads %}
<tr>
    <td colspan='5'>
        Übertragene Daten<br/>
        <ul>
        {% for upload in lineItem.extensions.uploads %}
            <li><a href="{{ url('frontend.home.page') }}uploads/final/{{ upload.qquuid }}/{{ upload.fileName }}" class="cart-item-label" target="_blank">{{ upload.fileName }}</a></li>
        {% endfor %}
        </ul>
    </td>
</tr>
{% endif %}
{% endraw %}
```

### Beispiel auf Basis des Standard Templates für Shopware <a href="#beispiel_auf_basis_des_standard_templates_fr_shopware" id="beispiel_auf_basis_des_standard_templates_fr_shopware"></a>

```twig
<div style="font-family:arial; font-size:12px;">

{% raw %}
{% set currencyIsoCode = order.currency.isoCode %}
{% if order.orderCustomer.salutation %}{{ order.orderCustomer.salutation.translated.letterName ~ ' ' }}{% endif %}{{ order.orderCustomer.firstName }} {{ order.orderCustomer.lastName }},<br>
<br>
We have received your order from {{ order.orderDateTime|format_datetime('medium', 'short', locale='en-GB') }}.<br>
<br>
Order number: {{ order.orderNumber }}<br>
<br>
As soon as your payment has been made, you will receive a separate notification and your order will be processed.<br>
<br>
You may check the current status of your order with this link: {{ rawUrl('frontend.account.order.single.page', { 'deepLinkCode': order.deepLinkCode }, salesChannel.domains|first.url) }}<br>
You may use this link to edit your order, change the payment method or make additional payments.<br>
<br>
<strong>Information on your order:</strong><br>
<br>

<table border="0" style="font-family:Arial, Helvetica, sans-serif; font-size:12px;">
    <tr>
        <td bgcolor="#F7F7F2" style="border-bottom:1px solid #cccccc;"><strong>Prod. no.</strong></td>
        <td bgcolor="#F7F7F2" style="border-bottom:1px solid #cccccc;"><strong>Description</strong></td>
        <td bgcolor="#F7F7F2" style="border-bottom:1px solid #cccccc;"><strong>Quantities</strong></td>
        <td bgcolor="#F7F7F2" style="border-bottom:1px solid #cccccc;"><strong>Price</strong></td>
        <td bgcolor="#F7F7F2" style="border-bottom:1px solid #cccccc;"><strong>Total</strong></td>
    </tr>

    {% for lineItem in order.nestedLineItems %}
        {% set nestingLevel = 0 %}
        {% set nestedItem = lineItem %}
        {% block lineItem %}
        <tr>
            <td>{% if nestedItem.payload.productNumber is defined %}{{ nestedItem.payload.productNumber|u.wordwrap(80) }}{% endif %}</td>
            <td>
                {% if nestingLevel > 0 %}
                    {% for i in 1..nestingLevel %}
                        <span style="position: relative;">
                            <span style="display: inline-block;
                                position: absolute;
                                width: 6px;
                                height: 20px;
                                top: 0;
                                border-left:  2px solid rgba(0, 0, 0, 0.15);
                                margin-left: {{ i * 10 }}px;"></span>
                        </span>
                    {% endfor %}
                {% endif %}

                <div{% if nestingLevel > 0 %} style="padding-left: {{ (nestingLevel + 1) * 10 }}px"{% endif %}>
                    {{ nestedItem.label|u.wordwrap(80) }}
                </div>

                {% if nestedItem.payload.options is defined and nestedItem.payload.options|length >= 1 %}
                    <div>
                        {% for option in nestedItem.payload.options %}
                            {{ option.group }}: {{ option.option }}
                            {% if nestedItem.payload.options|last != option %}
                                {{ " | " }}
                            {% endif %}
                        {% endfor %}
                    </div>
                {% endif %}

                {% if nestedItem.payload.features is defined and nestedItem.payload.features|length >= 1 %}
                    {% set referencePriceFeatures = nestedItem.payload.features|filter(feature => feature.type == 'referencePrice') %}
                    {% if referencePriceFeatures|length >= 1 %}
                        {% set referencePriceFeature = referencePriceFeatures|first %}
                        <div>
                            {{ referencePriceFeature.value.purchaseUnit }} {{ referencePriceFeature.value.unitName }}
                            ({{ referencePriceFeature.value.price|currency(currencyIsoCode) }}* / {{ referencePriceFeature.value.referenceUnit }} {{ referencePriceFeature.value.unitName }})
                        </div>
                    {% endif %}
                {% endif %}
            </td>
            <td style="text-align: center">{{ nestedItem.quantity }}</td>
            <td>{{ nestedItem.unitPrice|currency(currencyIsoCode) }}</td>
            <td>{{ nestedItem.totalPrice|currency(currencyIsoCode) }}</td>
        </tr>

        {% if lineItem.extensions.uploads %}
        <tr>
            <td colspan='5'>
                Übertragene Daten<br/>
                <ul>
                {% for upload in lineItem.extensions.uploads %}
                    <li><a href="{{ url('frontend.home.page') }}uploads/final/{{ upload.qquuid }}/{{ upload.fileName }}" class="cart-item-label" target="_blank">{{ upload.fileName }}</a></li>
                {% endfor %}
                </ul>
            </td>
        </tr>
        {% endif %}

            {% if nestedItem.children.count > 0 %}
                {% set nestingLevel = nestingLevel + 1 %}
                {% for lineItem in nestedItem.children %}
                    {% set nestedItem = lineItem %}
                    {{ block('lineItem') }}
                {% endfor %}
            {% endif %}
        {% endblock %}
    {% endfor %}
</table>

{% set delivery = order.deliveries.first %}

{% set displayRounded = order.totalRounding.interval != 0.01 or order.totalRounding.decimals != order.itemRounding.decimals %}
{% set decimals = order.totalRounding.decimals %}
{% set total = order.price.totalPrice %}
{% if displayRounded %}
    {% set total = order.price.rawTotal %}
    {% set decimals = order.itemRounding.decimals %}
{% endif %}
<p>
    <br>
    <br>
    Shipping costs: {{ order.deliveries.first.shippingCosts.totalPrice|currency(currencyIsoCode) }}<br>

    Net total: {{ order.amountNet|currency(currencyIsoCode) }}<br>
    {% for calculatedTax in order.price.calculatedTaxes %}
        {% if order.taxStatus is same as('net') %}plus{% else %}including{% endif %} {{ calculatedTax.taxRate }}% VAT. {{ calculatedTax.tax|currency(currencyIsoCode) }}<br>
    {% endfor %}
    {% if not displayRounded %}<strong>{% endif %}Total gross: {{ total|currency(currencyIsoCode,decimals=decimals) }}{% if not displayRounded %}</strong>{% endif %}<br>
    {% if displayRounded %}
        <strong>Rounded total gross: {{ order.price.totalPrice|currency(currencyIsoCode,decimals=order.totalRounding.decimals) }}</strong><br>
    {% endif %}
    <br>

    <strong>Selected shipping type:</strong> {{ delivery.shippingMethod.translated.name }}<br>
    {{ delivery.shippingMethod.translated.description }}<br>
    <br>

    {% set billingAddress = order.addresses.get(order.billingAddressId) %}
    <strong>Billing address:</strong><br>
    {{ billingAddress.company }}<br>
    {{ billingAddress.firstName }} {{ billingAddress.lastName }}<br>
    {{ billingAddress.street }} <br>
    {{ billingAddress.zipcode }} {{ billingAddress.city }}<br>
    {{ billingAddress.country.translated.name }}<br>
    <br>

    <strong>Shipping address:</strong><br>
    {{ delivery.shippingOrderAddress.company }}<br>
    {{ delivery.shippingOrderAddress.firstName }} {{ delivery.shippingOrderAddress.lastName }}<br>
    {{ delivery.shippingOrderAddress.street }} <br>
    {{ delivery.shippingOrderAddress.zipcode}} {{ delivery.shippingOrderAddress.city }}<br>
    {{ delivery.shippingOrderAddress.country.translated.name }}<br>
    <br>
    {% if order.orderCustomer.vatIds %}
        Your VAT-ID: {{ order.orderCustomer.vatIds|first }}
        In case of a successful order and if you are based in one of the EU countries, you will receive your goods exempt from turnover tax.<br>
    {% endif %}
{% endraw %}
    <br/>
    You can check the current status of your order on our website under "My account" - "My orders" anytime: {{ rawUrl('frontend.account.order.single.page', { 'deepLinkCode': order.deepLinkCode }, salesChannel.domains|first.url) }}
    </br>
    If you have any questions, do not hesitate to contact us.

</p>
<br>
</div>
```

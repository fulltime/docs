# Sales Channel Auswahl für FAQ-Seiten (Version 2.2.0+)

Mit dem FAQ Manager Plugin Version 2.2.0 wurde eine neue Funktion eingeführt, die es ermöglicht, FAQ-Seiten gezielt für bestimmte Verkaufskanäle (Sales Channels) zu konfigurieren. Dies bedeutet, dass Sie steuern können, in welchen Shops oder Verkaufskanälen Ihre FAQ-Seiten angezeigt werden.

### Was ist die Sales Channel Funktion?

Die Sales Channel Funktion ermöglicht es Ihnen:

* FAQ-Seiten nur in bestimmten Verkaufskanälen anzuzeigen
* Verschiedene FAQ-Seiten für verschiedene Shops zu erstellen
* Eine granulare Kontrolle über die Sichtbarkeit Ihrer FAQ-Inhalte zu haben

### Wo finde ich die Sales Channel Einstellungen?

#### 1. Navigation zur FAQ-Seiten Verwaltung

1. Melden Sie sich in der Shopware Administration an
2. Navigieren Sie zu **Inhalte** → **FAQ Manager** → **Seiten**

#### 2. FAQ-Seite bearbeiten oder erstellen

**Für eine neue FAQ-Seite:**

1. Klicken Sie auf **"Erstellen"**
2. Füllen Sie die grundlegenden Informationen aus (Titel, Beschreibung, etc.)

**Für eine bestehende FAQ-Seite:**

1. Klicken Sie auf **"Bearbeiten"** bei der gewünschten FAQ-Seite

#### 3. Sales Channel Auswahl finden

In der Bearbeitungsansicht finden Sie das Feld **"Verkaufskanäle"** in der rechten Spalte unter den Kategorien.

### Wie verwende ich die Sales Channel Auswahl?

#### Verkaufskanäle zuweisen

1. **Feld lokalisieren**: Suchen Sie das Feld mit der Bezeichnung **"Verkaufskanäle"**
2. **Dropdown öffnen**: Klicken Sie auf das Dropdown-Feld mit dem Platzhalter "Verkaufskanäle auswählen..."
3. **Kanäle auswählen**:
   * Sie sehen eine Liste aller verfügbaren Verkaufskanäle
   * Wählen Sie einen oder mehrere Verkaufskanäle aus
   * Sie können mehrere Kanäle gleichzeitig auswählen

#### Beispiel für die Verwendung

**Szenario 1: Ein FAQ nur für den Hauptshop**

* Wählen Sie nur Ihren Hauptverkaufskanal aus
* Die FAQ-Seite wird nur in diesem Shop angezeigt

**Szenario 2: Ein FAQ für mehrere Shops**

* Wählen Sie mehrere Verkaufskanäle aus
* Die FAQ-Seite wird in allen ausgewählten Shops angezeigt

**Szenario 3: Unterschiedliche FAQs für verschiedene Shops**

* Erstellen Sie separate FAQ-Seiten
* Weisen Sie jeder Seite unterschiedliche Verkaufskanäle zu

#### Verkaufskanäle entfernen

1. Klicken Sie auf das **X** neben dem Verkaufskanal, den Sie entfernen möchten
2. Der Verkaufskanal wird aus der Auswahl entfernt

### Wichtige Hinweise

#### Standardverhalten

* **Ohne Auswahl**: Wenn Sie keine Verkaufskanäle auswählen, wird die FAQ-Seite nicht angezeigt
* **Mit Auswahl**: Die FAQ-Seite wird nur in den ausgewählten Verkaufskanälen angezeigt

#### Sichtbarkeit und Vererbung

* Die Einstellung gilt für die gesamte FAQ-Seite und alle darin enthaltenen FAQ-Elemente
* Die Auswahl wird gespeichert und bleibt bestehen, bis Sie sie ändern

#### Speichern der Einstellungen

* Vergessen Sie nicht, auf **"Speichern"** zu klicken, nachdem Sie Ihre Verkaufskanal-Auswahl getroffen haben
* Die Änderungen werden sofort im Frontend wirksam

### Häufige Anwendungsfälle

#### Multi-Shop Setup

Wenn Sie mehrere Shops betreiben (z.B. für verschiedene Länder oder Zielgruppen):

* Erstellen Sie länderspezifische FAQ-Seiten
* Weisen Sie diese den entsprechenden Verkaufskanälen zu

#### B2B vs. B2C

* Erstellen Sie separate FAQ-Seiten für Geschäftskunden und Privatkunden
* Weisen Sie diese den entsprechenden Verkaufskanälen zu

#### Saisonale oder temporäre FAQs

* Erstellen Sie zeitlich begrenzte FAQ-Seiten
* Aktivieren/deaktivieren Sie diese für bestimmte Verkaufskanäle je nach Bedarf

### Fehlerbehebung

#### FAQ-Seite wird nicht angezeigt

1. Überprüfen Sie, ob die FAQ-Seite als **"Aktiv"** markiert ist
2. Kontrollieren Sie, ob der richtige Verkaufskanal ausgewählt ist
3. Stellen Sie sicher, dass die Seite gespeichert wurde

#### Verkaufskanal fehlt in der Liste

* Stellen Sie sicher, dass der Verkaufskanal in Shopware korrekt konfiguriert und aktiv ist

### Technische Details

Die Sales Channel Funktion arbeitet mit dem Shopware-eigenen Visibility-System und erstellt Zuordnungen zwischen FAQ-Seiten und Verkaufskanälen in der Datenbank. Dies gewährleistet eine optimale Performance und Kompatibilität mit Shopware-Standards.

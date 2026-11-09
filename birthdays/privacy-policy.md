# Privacy Policy / Datenschutzerklärung

---

## English

**Last updated: November 2026**

### 1. Data Controller

This app is developed and operated by:

**Marcel Ablasser**<br>
Klosterwiesgasse 107a, 8010 Graz<br>
Austria

Email: service@mab-software.at

### 2. Overview

Birthday Reminder is a mobile application that helps you remember birthdays. We are committed to protecting your privacy. This policy explains what data the app processes, how, and why.

**All birthday and contact data remains on your device by default and is never transmitted to us.** Without any action on your part, no data leaves your device: both anonymized crash reporting (see section 3.4) and anonymous, non-personal usage statistics (see section 3.5) are disabled by default and only activated if you explicitly opt in. If you choose to create a backup, export or share a backup file, or share a birthday wish, that data can leave your device as a direct result of your own action — see sections 3.6 and 3.7.

### 3. Data We Process

#### 3.1 Birthday Data

When you manually enter or import a birthday, the app stores:
- Name of the person
- Date of birth / birthday date (the year is optional)
- For birthdays imported from your contacts: only a reference to the device contact (its internal ID) — the name and date are read from your contacts when needed
- Your per-birthday reminder settings (reminders on/off, gift reminder on/off)
- Any custom wish messages you write

To deliver reminders, the app also schedules them with your device's notification system; each scheduled reminder contains the person's name until it is shown.

This data is stored exclusively in a local database (SQLite, encrypted at rest via SQLCipher with the encryption key generated and held in your device's secure, hardware-backed keystore) on your device. It is never transmitted to us or any third party.

#### 3.2 Device Contacts (optional)

If you choose to show birthdays from your device contacts, the app requests access to your contacts solely to read names and birthdays. While access is granted, the app reads them on your device each time it shows your birthday list or schedules reminders (also in the background), so changes in your contacts are picked up automatically; apart from scheduled reminders (see section 3.1), it does not keep its own copy of contact names or dates. The app does not modify, upload, or share your contacts in any way. You can revoke contact access at any time in your device settings.

#### 3.3 App Settings

The app stores your preferences (e.g. notification settings, theme) locally using the device's shared preferences storage. This data never leaves your device.

#### 3.4 Crash Reports (optional, opt-in)

To find and fix bugs, the app can send anonymized crash and error diagnostics using **Sentry** (Functional Software, Inc.). This is **disabled by default**. On first launch you are asked whether to allow it, and you can change your choice at any time in **Settings → Privacy**.

If you opt in:
- Crash reports are stored and processed on Sentry's **EU-based servers** (`de.sentry.io`). Sentry's operator is a US company; should data be accessed from outside the EU (e.g. for support or security operations), this is covered by the EU-U.S. Data Privacy Framework and the Standard Contractual Clauses in Sentry's Data Processing Agreement (Art. 45 and 46 GDPR).
- Reports contain only technical diagnostics (app version, device model, OS version, stack traces, and — at 20% sampling — performance traces). **No birthdays, names, contacts, or other personal data are included** — exception values are redacted and user identifiers are stripped before sending.
- Native crash reports (Android tombstones) may also be captured when enabled (`enableTombstone`) to aid diagnosis of low-level crashes.
- IP addresses are **not stored** (`sendDefaultPii` is disabled and server-side IP storage is deactivated).

If you do not opt in, the crash reporting SDK is never initialized and no data is collected or stored.

#### 3.5 Anonymous Usage Statistics (optional, opt-in)

To understand how the app is used across devices, the app can send **anonymous** usage statistics using **Aptabase**. This is **disabled by default**. On first launch you are asked whether to allow it, and you can change your choice at any time in **Settings → Privacy**.

If you opt in:
- Aptabase processes data on **EU-based servers** and collects **no personal data** and **no persistent device or user identifier** — events cannot be traced back to you or your device.
- Only aggregate technical signals are collected: app version, OS version, device type, and these events, each sent without any further details unless noted:
  - the app was started (`app_started`);
  - a birthday wish was shared (`wish_shared`) or copied (`wish_copied`) — but not the wish text or who it was for;
  - a birthday was marked as done, and whether that was in the app or with the Done button on its reminder (`birthday_marked_done`) — but not whose birthday it was. A Done press made while the app is closed is kept on your device only as a number until the app next opens, then sent;
  - a birthday or gift reminder notification was opened (`reminder_opened`) — but not which birthday it was for;
  - the notification permission (`notification_permission_denied`) or the exact-alarm permission (`exact_alarm_permission_denied`) was asked for and not granted;
  - the notification setup check was run, with its overall outcome: ok, warning or failed (`notification_self_test_run`);
  - access to your contacts was asked for and granted (`contacts_permission_granted`) or not granted (`contacts_permission_denied`);
  - a birthday was added by hand (`birthday_added_manually`) — but not its name or date;
  - your birthdays were loaded when the app started, with only a rough count range: 0, 1–10, 11–50 or more than 50 (`birthdays_loaded`);
  - a backup was created (`backup_created`) or restored (`backup_restored`), or a restore failed, with only the kind of failure: wrong backup password, damaged file or other (`backup_restore_failed`) — never the backup's contents or backup password;
  - the name search was used (`search_used`), once per search — never what you searched for;
  - a wish message template was added, edited, deleted or reset to the defaults, with only which of the four it was (`wish_template_edited`) — never the message text;
  - the button that inserts the first-name placeholder into a wish message was tapped (`first_name_inserted`).

  **No birthdays, names, contacts, or message texts are ever included.**
- Aptabase processes data on our behalf under a Data Processing Agreement.
- Because this data is genuinely anonymous and cannot be linked to an individual, it falls outside the scope of the GDPR's personal-data rules. We nonetheless disclose it here for full transparency.

If you do not opt in, the analytics SDK is never initialized and no data is collected or stored.

#### 3.6 Backups & Data Export (optional)

You can create a local backup of your birthday data (names, dates, per-birthday reminder settings, and custom wish messages) and app settings at any time from **Settings → Backup**. The backup file is encrypted on your device before it is written to disk, using a backup password you choose (Argon2id key derivation with AES-256-GCM encryption) — we never see this backup password and cannot decrypt or access the backup file's contents.

If you tick **Remember backup password on this device** when creating a backup, the backup password is stored on your device only, encrypted with a key held in your device's secure hardware (Android Keystore / iOS Keychain), so that it can be reused for your next backup. It is never transmitted to us, never included in your device's cloud backup or device-to-device transfer, and it is not stored in the backup file itself. It can only be displayed after you unlock your device (PIN, pattern, password or biometrics), and only for a short time. You can remove it at any time with **Delete** on the backup screen; it is also deleted when you delete all data. This option is off by default.

The backup file is stored in the app's private storage on your device. If you have Google's "Back up to Google Drive" (Android) or iCloud Backup (iOS) enabled on your device, this **encrypted** backup file may be included in that OS-level device backup, since it is designed to let you move your data to a new device — unlike the app's core database, it is not excluded from your device's automatic backup. This is a backup made by your device to your own Google/Apple account; we have no access to it and are not involved in it.

You can also explicitly export the encrypted backup file yourself (e.g. via **Share backup file**) to a location of your choosing, such as cloud storage or email. That transfer is entirely under your control — we do not receive a copy.

#### 3.7 Sharing a Birthday Wish (optional)

If you tap **Share** or **Copy** on a birthday wish message, the app hands that message text — which may include the birthday person's first name — to your device's native share sheet or clipboard, so you can send it via an app of your choice. This is a one-time action you initiate; we do not see or store the content of that message.

### 4. Permissions

| Permission | Purpose |
|------------|---------|
| Contacts (READ_CONTACTS) | Optional — to import birthdays from device contacts |
| Notifications (POST_NOTIFICATIONS) | To send birthday reminder notifications |
| Exact Alarm / Schedule Exact Alarm | To schedule reminders at the correct time |
| Receive Boot Completed | To reschedule reminders after device restart |
| Battery Optimization (REQUEST_IGNORE_BATTERY_OPTIMIZATIONS) | Optional — to ensure reminders fire reliably when the device is idle |
| Wake Lock (WAKE_LOCK) | To finish scheduling reminders in the background without the device going to sleep |
| Biometrics / device unlock (USE_BIOMETRIC, Face ID) | Optional — to confirm it is you (biometrics or your PIN, pattern or password) before the saved backup password is shown (section 3.6). Biometric data is processed only by your device's operating system and never reaches the app or us. |
| Internet (INTERNET) | Only to send crash reports (section 3.4) and usage statistics (section 3.5) if you opted in |

Permissions are only used for the stated purpose and can be revoked at any time in your device settings.

### 5. Legal Basis (GDPR)

The processing of your data is based on:

- **Art. 6(1)(a) GDPR — Consent:** You actively enter or import the birthday data and grant the requested permissions voluntarily. Anonymized crash reporting (section 3.4) and anonymous usage statistics (section 3.5) are each processed solely on the basis of your separate, revocable opt-in consent.
- **Art. 6(1)(b) GDPR — Performance of a contract:** Processing is necessary to provide the core functionality of the app (birthday reminders) which you have chosen to use.

### 6. Data Retention

Birthday data and settings are stored on your device until you delete them within the app or uninstall the app. We have no access to this data and cannot delete it on your behalf.

If you opted in, crash reports (section 3.4) are deleted automatically by Sentry after at most 90 days. Anonymous usage statistics (section 3.5) are kept by Aptabase for up to 5 years; because they cannot be linked to you, they cannot be deleted on request. You can stop both at any time in **Settings → Privacy**.

### 7. Data Sharing

We do not share your birthday or contact data with any third parties, and the app contains no advertising SDKs. Two external providers are involved: **Sentry** (see section 3.4), used exclusively for anonymized crash reporting and only if you have opted in, and **Aptabase** (see section 3.5), used for anonymous, non-personal usage statistics and only if you have opted in. Both process data on EU-based servers and act as data processors on our behalf under Data Processing Agreements. If you export or share your backup file, or share a birthday wish, that data is handed directly to the app or service you select via your device's share function — we are not involved in and have no access to that transfer.

### 8. Third-Party Libraries

The app uses open-source libraries for its core functionality (UI, local notifications, local database, navigation); none of these transmit personal data to external servers. Two libraries transmit data externally: the **Sentry** crash reporting SDK (only after you opt in, section 3.4) and the **Aptabase** analytics SDK (anonymous, non-personal statistics, section 3.5).

### 9. Children's Privacy

The app is not directed at children under 16 (the highest minimum age for digital consent that EU member states set under GDPR Art. 8). We do not knowingly collect data from children.

### 10. Your Rights Under GDPR

As a data subject, you have the following rights:

- **Right of access** (Art. 15 GDPR): You can view all birthday data directly within the app.
- **Right to rectification** (Art. 16 GDPR): You can edit any entry directly in the app.
- **Right to erasure** (Art. 17 GDPR): You can delete individual entries or all data within the app, or uninstall the app.
- **Right to data portability** (Art. 20 GDPR): You can export your birthday data at any time as a backup file via **Settings → Backup** (see section 3.6).
- **Right to object** (Art. 21 GDPR): You can revoke any permission at any time in your device settings.
- **Right to withdraw consent** (Art. 7(3) GDPR): You can withdraw your consent to crash reports and usage statistics at any time in **Settings → Privacy**. Withdrawal does not affect the lawfulness of processing before the withdrawal.

Since all data is stored locally on your device and we have no access to it, most rights can be exercised directly within the app.

### 11. Right to Lodge a Complaint

You have the right to lodge a complaint with the competent supervisory authority.

**Austria — Datenschutzbehörde (DSB)**
Barichgasse 40–42, 1030 Wien
[dsb.gv.at](https://www.dsb.gv.at)

**Germany — Bundesbeauftragter für den Datenschutz und die Informationsfreiheit (BfDI)**
[bfdi.bund.de](https://www.bfdi.bund.de)
(or the supervisory authority of the German federal state in which you reside)

**Switzerland — Eidgenössischer Datenschutz- und Öffentlichkeitsbeauftragter (EDÖB)**
[edoeb.admin.ch](https://www.edoeb.admin.ch)
Note: Swiss users are subject to the Swiss Data Protection Act (nDSG / revDSG, in force since September 2023), not the EU GDPR directly.

### 12. Changes to This Policy

We may update this privacy policy from time to time. The updated version will be published at this URL with a revised "Last updated" date. We recommend reviewing this page periodically.

### 13. Contact

For any privacy-related questions, please contact us at:
**service@mab-software.at**

---

## Deutsch

**Zuletzt aktualisiert: November 2026**

### 1. Verantwortlicher

Diese App wird entwickelt und betrieben von:

**Marcel Ablasser**<br>
Klosterwiesgasse 107a, 8010 Graz<br>
Österreich

E-Mail: service@mab-software.at

### 2. Überblick

Birthday Reminder ist eine mobile Anwendung, die Ihnen hilft, Geburtstage nicht zu vergessen. Der Schutz Ihrer Privatsphäre ist uns wichtig. Diese Datenschutzerklärung erläutert, welche Daten die App verarbeitet, wie und warum.

**Alle Geburtstags- und Kontaktdaten verbleiben standardmäßig auf Ihrem Gerät und werden niemals an uns übertragen.** Ohne eigenes Zutun verlassen keine Daten Ihr Gerät: Sowohl die anonymisierte Absturzberichterstattung (siehe Abschnitt 3.4) als auch anonyme, nicht personenbezogene Nutzungsstatistiken (siehe Abschnitt 3.5) sind standardmäßig deaktiviert und werden nur aktiviert, wenn Sie ausdrücklich zustimmen. Wenn Sie ein Backup erstellen, eine Backup-Datei exportieren oder teilen oder einen Geburtstagswunsch teilen, können diese Daten als unmittelbare Folge Ihrer eigenen Handlung Ihr Gerät verlassen — siehe Abschnitte 3.6 und 3.7.

### 3. Verarbeitete Daten

#### 3.1 Geburtstagsdaten

Wenn Sie einen Geburtstag manuell eingeben oder importieren, speichert die App:
- Name der Person
- Geburts- bzw. Geburtstagsdatum (das Jahr ist optional)
- Bei aus Ihren Kontakten importierten Geburtstagen: nur einen Verweis auf den Gerätekontakt (dessen interne ID) — Name und Datum werden bei Bedarf aus Ihren Kontakten gelesen
- Ihre Erinnerungseinstellungen pro Geburtstag (Erinnerungen ein/aus, Geschenkerinnerung ein/aus)
- Von Ihnen verfasste individuelle Wunschnachrichten

Um Erinnerungen zuzustellen, plant die App diese zusätzlich beim Benachrichtigungssystem Ihres Geräts ein; jede geplante Erinnerung enthält den Namen der Person, bis sie angezeigt wird.

Diese Daten werden ausschließlich in einer lokalen Datenbank (SQLite, mittels SQLCipher verschlüsselt gespeichert, wobei der Schlüssel im sicheren, hardwaregestützten Schlüsselspeicher Ihres Geräts erzeugt und gehalten wird) auf Ihrem Gerät gespeichert. Sie werden niemals an uns oder Dritte übertragen.

#### 3.2 Gerätekontakte (optional)

Wenn Sie Geburtstage aus Ihren Gerätekontakten anzeigen möchten, fordert die App Zugriff auf Ihre Kontakte an – ausschließlich um Namen und Geburtstage zu lesen. Solange der Zugriff erteilt ist, liest die App diese auf Ihrem Gerät jedes Mal, wenn sie Ihre Geburtstagsliste anzeigt oder Erinnerungen plant (auch im Hintergrund), sodass Änderungen in Ihren Kontakten automatisch übernommen werden; abgesehen von geplanten Erinnerungen (siehe Abschnitt 3.1) legt sie keine eigene Kopie von Kontaktnamen oder -daten an. Die App verändert, lädt hoch oder teilt Ihre Kontakte in keiner Weise. Sie können den Kontaktzugriff jederzeit in den Geräteeinstellungen widerrufen.

#### 3.3 App-Einstellungen

Die App speichert Ihre Einstellungen (z. B. Benachrichtigungseinstellungen, Design) lokal im Gerätespeicher. Diese Daten verlassen Ihr Gerät nicht.

#### 3.4 Absturzberichte (optional, Opt-in)

Um Fehler zu finden und zu beheben, kann die App anonymisierte Absturz- und Fehlerdiagnosen mit **Sentry** (Functional Software, Inc.) senden. Dies ist **standardmäßig deaktiviert**. Beim ersten Start werden Sie gefragt, ob Sie dies erlauben möchten; Sie können Ihre Wahl jederzeit unter **Einstellungen → Datenschutz** ändern.

Wenn Sie zustimmen:
- Absturzberichte werden auf **Servern in der EU** (`de.sentry.io`) gespeichert und verarbeitet. Der Betreiber von Sentry ist ein US-Unternehmen; sollte ein Zugriff von außerhalb der EU erfolgen (z. B. für Support oder Sicherheitsbetrieb), ist dieser durch das EU-US Data Privacy Framework sowie die Standardvertragsklauseln im Auftragsverarbeitungsvertrag von Sentry abgesichert (Art. 45 und 46 DSGVO).
- Berichte enthalten nur technische Diagnosedaten (App-Version, Gerätemodell, Betriebssystemversion, Stack-Traces sowie — bei 20 % Stichprobe — Performance-Traces). **Es werden keine Geburtstage, Namen, Kontakte oder sonstigen personenbezogenen Daten übermittelt** — Ausnahmetexte werden geschwärzt und Nutzerkennungen vor dem Senden entfernt.
- Native Absturzberichte (Android-Tombstones) können bei aktivierter Tombstone-Erfassung zur Diagnose von systemnahen Abstürzen übermittelt werden.
- IP-Adressen werden **nicht gespeichert** (`sendDefaultPii` ist deaktiviert und die serverseitige IP-Speicherung ist abgeschaltet).

Wenn Sie nicht zustimmen, wird das Absturzberichts-SDK niemals initialisiert und es werden keine Daten erhoben oder gespeichert.

#### 3.5 Anonyme Nutzungsstatistiken (optional, Opt-in)

Um zu verstehen, wie die App geräteübergreifend genutzt wird, kann die App **anonyme** Nutzungsstatistiken mit **Aptabase** senden. Dies ist **standardmäßig deaktiviert**. Beim ersten Start werden Sie gefragt, ob Sie dies erlauben möchten; Sie können Ihre Wahl jederzeit unter **Einstellungen → Datenschutz** ändern.

Wenn Sie zustimmen:
- Aptabase verarbeitet Daten auf **Servern in der EU** und erhebt **keine personenbezogenen Daten** und **keine dauerhafte Geräte- oder Nutzerkennung** — Ereignisse können nicht zu Ihnen oder Ihrem Gerät zurückverfolgt werden.
- Es werden nur aggregierte technische Signale erfasst: App-Version, Betriebssystemversion, Gerätetyp sowie diese Ereignisse, jeweils ohne weitere Angaben, sofern nicht anders angegeben:
  - die App wurde gestartet (`app_started`);
  - ein Geburtstagswunsch wurde geteilt (`wish_shared`) oder kopiert (`wish_copied`) — nicht jedoch der Text des Wunsches oder für wen er war;
  - ein Geburtstag wurde als erledigt markiert, und ob das in der App oder mit dem „Erledigt“-Button der Erinnerung geschah (`birthday_marked_done`) — nicht jedoch, wessen Geburtstag es war. Ein „Erledigt“ bei geschlossener App wird bis zum nächsten Öffnen der App nur als Anzahl auf Ihrem Gerät gespeichert und dann gesendet;
  - eine Geburtstags- oder Geschenkerinnerung wurde geöffnet (`reminder_opened`) — nicht jedoch, für welchen Geburtstag sie war;
  - die Benachrichtigungsberechtigung (`notification_permission_denied`) oder die Berechtigung für exakte Alarme (`exact_alarm_permission_denied`) wurde angefragt und nicht erteilt;
  - die Prüfung der Benachrichtigungseinrichtung wurde ausgeführt, mit ihrem Gesamtergebnis: ok, Warnung oder fehlgeschlagen (`notification_self_test_run`);
  - der Zugriff auf Ihre Kontakte wurde angefragt und erteilt (`contacts_permission_granted`) oder nicht erteilt (`contacts_permission_denied`);
  - ein Geburtstag wurde von Hand hinzugefügt (`birthday_added_manually`) — nicht jedoch sein Name oder Datum;
  - Ihre Geburtstage wurden beim App-Start geladen, nur mit einem groben Anzahlbereich: 0, 1–10, 11–50 oder mehr als 50 (`birthdays_loaded`);
  - ein Backup wurde erstellt (`backup_created`) oder wiederhergestellt (`backup_restored`), oder eine Wiederherstellung schlug fehl, nur mit der Art des Fehlers: falsches Sicherungskennwort, beschädigte Datei oder Sonstiges (`backup_restore_failed`) — niemals Inhalt oder Sicherungskennwort des Backups;
  - die Namenssuche wurde verwendet (`search_used`), einmal pro Suche — niemals der Suchbegriff;
  - eine Vorlage für Geburtstagswünsche wurde hinzugefügt, bearbeitet, gelöscht oder auf die Standardvorlagen zurückgesetzt, nur mit der Art der Änderung (`wish_template_edited`) — niemals der Nachrichtentext;
  - der Button, der den Vornamen-Platzhalter in einen Geburtstagswunsch einfügt, wurde getippt (`first_name_inserted`).

  **Es werden niemals Geburtstage, Namen, Kontakte oder Nachrichtentexte übermittelt.**
- Aptabase verarbeitet Daten in unserem Auftrag auf Grundlage eines Auftragsverarbeitungsvertrags.
- Da diese Daten wirklich anonym sind und keiner Person zugeordnet werden können, fallen sie nicht unter die Regeln der DSGVO zu personenbezogenen Daten. Wir legen sie dennoch aus Gründen vollständiger Transparenz hier offen.

Wenn Sie nicht zustimmen, wird das Analyse-SDK niemals initialisiert und es werden keine Daten erhoben oder gespeichert.

#### 3.6 Backups & Datenexport (optional)

Sie können jederzeit unter **Einstellungen → Datensicherung** eine lokale Sicherung Ihrer Geburtstagsdaten (Namen, Daten, Erinnerungseinstellungen pro Geburtstag und individuelle Wunschnachrichten) und Ihrer App-Einstellungen erstellen. Die Backup-Datei wird auf Ihrem Gerät verschlüsselt, bevor sie gespeichert wird, unter Verwendung eines von Ihnen gewählten Sicherungskennworts (Schlüsselableitung mit Argon2id und Verschlüsselung mit AES-256-GCM) — wir sehen dieses Sicherungskennwort niemals und können weder den Inhalt der Backup-Datei entschlüsseln noch darauf zugreifen.

Wenn Sie beim Erstellen eines Backups **Sicherungskennwort auf diesem Gerät merken** auswählen, wird das Sicherungskennwort ausschließlich auf Ihrem Gerät gespeichert, verschlüsselt mit einem Schlüssel aus dem geschützten Hardware-Speicher Ihres Geräts (Android Keystore / iOS-Schlüsselbund), damit es für Ihr nächstes Backup wiederverwendet werden kann. Es wird niemals an uns übertragen, nie in die Cloud-Sicherung oder Geräteübertragung Ihres Geräts einbezogen und nicht in der Backup-Datei selbst gespeichert. Angezeigt werden kann es nur, nachdem Sie Ihr Gerät entsperrt haben (PIN, Muster, Passwort oder Biometrie), und nur für kurze Zeit. Sie können es jederzeit über **Löschen** auf dem Backup-Bildschirm entfernen; außerdem wird es gelöscht, wenn Sie alle Daten löschen. Diese Option ist standardmäßig deaktiviert.

Die Backup-Datei wird im privaten Speicherbereich der App auf Ihrem Gerät abgelegt. Wenn Sie auf Ihrem Gerät „Sicherung bei Google Drive" (Android) oder das iCloud-Backup (iOS) aktiviert haben, kann diese **verschlüsselte** Backup-Datei in dieses Betriebssystem-Backup einbezogen werden, da sie dazu gedacht ist, Ihre Daten auf ein neues Gerät zu übertragen — anders als die Kerndatenbank der App ist sie nicht vom automatischen Geräte-Backup ausgeschlossen. Dabei handelt es sich um eine Sicherung, die Ihr Gerät für Sie in Ihrem eigenen Google-/Apple-Konto anlegt; wir haben keinen Zugriff darauf und sind daran nicht beteiligt.

Sie können die verschlüsselte Backup-Datei auch selbst explizit exportieren (z. B. über **Sicherungsdatei teilen**) an einen Ort Ihrer Wahl, etwa einen Cloud-Speicher oder per E-Mail. Diese Übertragung liegt vollständig in Ihrer eigenen Kontrolle — wir erhalten dabei keine Kopie.

#### 3.7 Teilen eines Geburtstagswunsches (optional)

Wenn Sie bei einer Geburtstagswunsch-Nachricht auf **Teilen** oder **Kopieren** tippen, übergibt die App diesen Nachrichtentext — der den Vornamen der Geburtstagsperson enthalten kann — an das native Teilen-Menü oder die Zwischenablage Ihres Geräts, damit Sie ihn über eine App Ihrer Wahl versenden können. Dies ist eine einmalige, von Ihnen ausgelöste Aktion; wir sehen oder speichern den Inhalt dieser Nachricht nicht.

### 4. Berechtigungen

| Berechtigung | Zweck |
|-------------|-------|
| Kontakte (READ_CONTACTS) | Optional – zum Import von Geburtstagen aus den Gerätekontakten |
| Benachrichtigungen (POST_NOTIFICATIONS) | Zum Senden von Geburtstagserinnerungen |
| Exakter Alarm / Schedule Exact Alarm | Zur Planung von Erinnerungen zur richtigen Zeit |
| Receive Boot Completed | Zur Wiederherstellung von Erinnerungen nach Geräteneustart |
| Akku-Optimierung (REQUEST_IGNORE_BATTERY_OPTIMIZATIONS) | Optional – um sicherzustellen, dass Erinnerungen auch im Ruhezustand zuverlässig ausgelöst werden |
| Wake Lock (WAKE_LOCK) | Zum Abschließen der Erinnerungsplanung im Hintergrund, ohne dass das Gerät in den Ruhezustand wechselt |
| Biometrie / Gerätesperre (USE_BIOMETRIC, Face ID) | Optional – um vor der Anzeige des gespeicherten Sicherungskennworts zu bestätigen, dass Sie es sind (Biometrie oder PIN, Muster bzw. Passwort; Abschnitt 3.6). Biometrische Daten verarbeitet ausschließlich das Betriebssystem Ihres Geräts; sie gelangen weder an die App noch an uns. |
| Internet (INTERNET) | Nur zum Senden von Absturzberichten (Abschnitt 3.4) und Nutzungsstatistiken (Abschnitt 3.5), wenn Sie zugestimmt haben |

Berechtigungen werden ausschließlich für den angegebenen Zweck verwendet und können jederzeit in den Geräteeinstellungen widerrufen werden.

### 5. Rechtsgrundlage (DSGVO)

Die Verarbeitung Ihrer Daten erfolgt auf Grundlage von:

- **Art. 6 Abs. 1 lit. a DSGVO – Einwilligung:** Sie geben die Geburtstagsdaten aktiv ein oder importieren diese und erteilen die erforderlichen Berechtigungen freiwillig. Die anonymisierte Absturzberichterstattung (Abschnitt 3.4) und die anonymen Nutzungsstatistiken (Abschnitt 3.5) erfolgen jeweils ausschließlich auf Grundlage Ihrer gesonderten, jederzeit widerrufbaren Opt-in-Einwilligung.
- **Art. 6 Abs. 1 lit. b DSGVO – Vertragserfüllung:** Die Verarbeitung ist erforderlich, um die Kernfunktionalität der App (Geburtstagserinnerungen) bereitzustellen, die Sie in Anspruch nehmen möchten.

### 6. Speicherdauer

Geburtstagsdaten und Einstellungen werden auf Ihrem Gerät gespeichert, bis Sie diese innerhalb der App löschen oder die App deinstallieren. Wir haben keinen Zugriff auf diese Daten und können sie nicht in Ihrem Namen löschen.

Wenn Sie zugestimmt haben, werden Absturzberichte (Abschnitt 3.4) von Sentry nach spätestens 90 Tagen automatisch gelöscht. Anonyme Nutzungsstatistiken (Abschnitt 3.5) speichert Aptabase bis zu 5 Jahre; da sie Ihnen nicht zugeordnet werden können, ist eine Löschung auf Anfrage nicht möglich. Beides können Sie jederzeit unter **Einstellungen → Datenschutz** beenden.

### 7. Datenweitergabe

Wir geben Ihre Geburtstags- und Kontaktdaten nicht an Dritte weiter, und die App enthält keine Werbe-SDKs. Es sind zwei externe Anbieter beteiligt: **Sentry** (siehe Abschnitt 3.4), ausschließlich für die anonymisierte Absturzberichterstattung und nur bei Ihrer Zustimmung, sowie **Aptabase** (siehe Abschnitt 3.5) für anonyme, nicht personenbezogene Nutzungsstatistiken und ebenfalls nur bei Ihrer Zustimmung. Beide verarbeiten Daten auf Servern in der EU und handeln als Auftragsverarbeiter in unserem Auftrag auf Grundlage von Auftragsverarbeitungsverträgen. Wenn Sie Ihre Backup-Datei exportieren oder teilen oder einen Geburtstagswunsch teilen, werden diese Daten direkt an die von Ihnen gewählte App bzw. den gewählten Dienst über die Teilen-Funktion Ihres Geräts übergeben — wir sind an dieser Übertragung nicht beteiligt und haben keinen Zugriff darauf.

### 8. Drittanbieter-Bibliotheken

Die App verwendet Open-Source-Bibliotheken für ihre Kernfunktionen (Benutzeroberfläche, lokale Benachrichtigungen, lokale Datenbank, Navigation); keine davon überträgt personenbezogene Daten an externe Server. Zwei Bibliotheken übertragen Daten extern: das **Sentry**-Absturzberichts-SDK (nur nach Ihrer Zustimmung, Abschnitt 3.4) und das **Aptabase**-Analyse-SDK (anonyme, nicht personenbezogene Statistiken, Abschnitt 3.5).

### 9. Datenschutz von Kindern

Die App richtet sich nicht an Kinder unter 16 Jahren (das höchste Mindestalter für die digitale Einwilligung, das EU-Mitgliedstaaten gemäß Art. 8 DSGVO festlegen). Wir erheben wissentlich keine Daten von Kindern.

### 10. Ihre Rechte gemäß DSGVO

Als betroffene Person haben Sie folgende Rechte:

- **Auskunftsrecht** (Art. 15 DSGVO): Sie können alle Geburtstagsdaten direkt in der App einsehen.
- **Recht auf Berichtigung** (Art. 16 DSGVO): Sie können jeden Eintrag direkt in der App bearbeiten.
- **Recht auf Löschung** (Art. 17 DSGVO): Sie können einzelne Einträge oder alle Daten innerhalb der App löschen oder die App deinstallieren.
- **Recht auf Datenübertragbarkeit** (Art. 20 DSGVO): Sie können Ihre Geburtstagsdaten jederzeit über **Einstellungen → Datensicherung** als Backup-Datei exportieren (siehe Abschnitt 3.6).
- **Widerspruchsrecht** (Art. 21 DSGVO): Sie können jede Berechtigung jederzeit in Ihren Geräteeinstellungen widerrufen.
- **Recht auf Widerruf der Einwilligung** (Art. 7 Abs. 3 DSGVO): Sie können Ihre Einwilligung zu Absturzberichten und Nutzungsstatistiken jederzeit unter **Einstellungen → Datenschutz** widerrufen. Die Rechtmäßigkeit der bis zum Widerruf erfolgten Verarbeitung bleibt unberührt.

Da alle Daten lokal auf Ihrem Gerät gespeichert sind und wir keinen Zugriff darauf haben, können die meisten Rechte direkt in der App ausgeübt werden.

### 11. Beschwerderecht

Sie haben das Recht, eine Beschwerde bei der zuständigen Aufsichtsbehörde einzureichen.

**Österreich — Datenschutzbehörde (DSB)**
Barichgasse 40–42, 1030 Wien
[dsb.gv.at](https://www.dsb.gv.at)

**Deutschland — Bundesbeauftragter für den Datenschutz und die Informationsfreiheit (BfDI)**
[bfdi.bund.de](https://www.bfdi.bund.de)
(oder die zuständige Datenschutzaufsichtsbehörde Ihres Bundeslandes)

**Schweiz — Eidgenössischer Datenschutz- und Öffentlichkeitsbeauftragter (EDÖB)**
[edoeb.admin.ch](https://www.edoeb.admin.ch)
Hinweis: Für Schweizer Nutzer gilt das Schweizer Datenschutzgesetz (nDSG / revDSG, in Kraft seit September 2023), nicht die EU-DSGVO unmittelbar.

### 12. Änderungen dieser Datenschutzerklärung

Wir können diese Datenschutzerklärung von Zeit zu Zeit aktualisieren. Die aktualisierte Version wird unter dieser URL mit einem überarbeiteten Datum „Zuletzt aktualisiert" veröffentlicht. Wir empfehlen, diese Seite regelmäßig zu überprüfen.

### 13. Kontakt

Bei datenschutzrechtlichen Fragen kontaktieren Sie uns bitte unter:
**service@mab-software.at**

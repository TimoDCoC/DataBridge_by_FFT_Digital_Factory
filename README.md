

## 🔧 Überblick

Die Data Bridge verbindet Edge Devices in der Fertigung mit der Snowflake Cloud. Sie ist speziell angepasst für **Siemens Industrial Edge** und läuft lokal auf dem Edge-Device. Die App ermöglicht eine sichere, konfigurierbare und konsistente Übertragung von Produktionsdaten zur Analyse in die Cloud.

---

## ⚙️ Funktionalität

- **Southbound Connector** mit TLS-Verschlüsselung und asymmetrischer Authentifizierung (Public/Private Key)
- Verbindet sich mit einem **eigens entwickelten Data Service** auf dem Edge Device
- Liest definierte **Attribute**, welche direkt im Feld am Edge konfiguriert werden
- Sammelt Daten bis zur einstellbaren **Dateigröße (in Bit)** und sendet diese an die **Snowflake Schnittstelle**
- Transformation der Daten in definierte Tabellen erfolgt automatisiert über **Snowflake Pipeline**
- Unterstützt das **Abrufen von Historiendaten**, abhängig von der Edge Device Kapazität
- Führt ein **Write-Log** mit Start- und Endzeitstempeln zur Sicherstellung konsistenter Übertragung
- Nach einem Containerabsturz wird das Write-Log wiederverwendet, um Datenverlust zu vermeiden
- Verwaltet fehlerhafte und abgeschlossene Dateien über ein **Ring-Buffer**
- Frei konfigurierbar über **IEM Schema Configurations**

---

## 🔐 Sicherheit

- **End-to-End TLS-Verschlüsselung**
- **Asymmetrische Authentifizierung** über verschlüsselte Schlüsseldateien (Public/Private Key-Paar)
- Gespeicherte Schlüssel sind **passwortgeschützt**

---






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

## 🛠️ Konfiguration (IEM Schema)

Folgende Parameter sind konfigurierbar:

| Parameter                     | Beschreibung |
|------------------------------|--------------|
| `Source URL`                 | Data Service Endpoint |
| `Threadanzahl Data Service Client`    | Parallelität der Abfragen |
| `USER`, `DB`, `STAGE`, `PIPE`, `ACCOUNT`, `HOST`, `Schema` | Snowflake-Verbindungsparameter |
| `Query Interval`             | Intervall zwischen Abfragen |
| `Timeout`                    | Zeitlimit für Abfragen |
| `Filesize in BIT`            | Max. Größe der Datensammlung vor Upload |
| `Abfrage Attribute`          | z. B. `Device=Robot`, `Asset=Cycletime`, `Variable=Cycle` |
| `Ring Speicher Max Werte`    | Konfiguration des Ring-Buffer |
| `Encrypted Key File`         | Pfad zur verschlüsselten Auth-Datei |
| `Password Encrypted File`    | Passwort zur Entschlüsselung |

---

## 📌 Abgrenzung & Hinweise

- Der Connector benötigt  **Data Service Applikation** um Daten aus dem Edge Device zu extrahieren.
- Dieser Client basiert auf dem FFT SPS Standard.
- Die Funktion zum Abrufen von Historiendaten ist **hardwarelimitiert**:
  - Falls zu hohe Last: Fallback auf Live-Daten ab Startzeitpunkt des Connectors

---


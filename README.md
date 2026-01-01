# Driving POI Companion (Arbeitstitel)

Eine iOS-App, die während der Fahrt eine **Umgebungskarte** anzeigt, nearby **Points of Interest (POIs)** erkennt und diese dem Fahrer auf Wunsch **vorliest**.  
Ziel ist ein „neugieriger Beifahrer“, der die Umgebung erklärt – mit Fokus auf **Sicherheit, einfache Bedienung und Audio-Ausgabe**.

## 🎯 Ziel & Idee

- Live-Karte mit aktuellem Standort
- Relevante POIs im Umkreis automatisch erkennen
- Kurze, verständliche Beschreibungen anzeigen bzw. **per Text-to-Speech vorlesen**
- Datenquellen z. B.:
  - Wikipedia / Wikidata (Geo-Artikel)
  - OpenStreetMap (POI-Struktur)
- Optionale spätere Integration:
  - Apple **CarPlay**
  - Filter (Geschichte, Architektur, Natur, Fun Facts)

Die App soll **kein Navi**, sondern ein **informierender Fahrbegleiter** sein.

---

## 🧩 Technischer Überblick

**Plattform:** iOS (MVP, später optional CarPlay)  
**Sprache:** Swift  
**UI-Framework:** SwiftUI  
**Karte:** MapKit  
**Standort:** CoreLocation  
**Sprachausgabe:** AVSpeechSynthesizer (AVFoundation)  
**Netzwerk / APIs:** URLSession (Wikipedia / Wikidata / OSM)

### Architektur (MVVM-orientiert)

App
├─ Views (SwiftUI)
├─ ViewModels
├─ Services
│   ├─ LocationService
│   ├─ PoiService (Wikipedia / Wikidata)
│   └─ SpeechService
├─ Models (POI, Coordinates, Metadata)
└─ Utils


---

## 🚀 Geplante MVP-Funktionen

- Aktuelle Position auf Karte anzeigen  
- POIs im Radius abrufen  
- Kurzinfo zu einem POI anzeigen  
- Button „Vorlesen“ → Audio-Ausgabe des Textes  
- Basis-Einstellungen (Radius, Sprache)

---

## 🔜 Mögliche nächste Schritte

- Automatisches Vorlesen bei Annäherung  
- Relevanz-Ranking / Duplikat-Filter  
- Lokales Caching  
- CarPlay-Support (reduzierte UI + Audio-Fokus)  
- Wikidata-Anreicherung (Baujahr, Kategorie, Typ)  
- Off-Road / Fuß- oder Rad-Modus

---

## ⚖️ Daten & Lizenzen

- Inhalte aus **Wikipedia / Wikidata**:  
  Nutzung gemäß **CC BY-SA 4.0** (Namensnennung & Share-Alike)
- OpenStreetMap-Daten: **ODbL-Lizenz**
- In der App erfolgt eine transparente Attribution der Quellen.

---

## 🧪 Entwicklung & Setup

1. Repository klonen
2. Xcode öffnen → iOS App (SwiftUI / Swift)
3. Abhängigkeiten:
   - iOS 16+ empfohlen
4. Startpunkte:
   - `ContentView` (Map + UI-Rahmen)
   - `LocationService` (Standortupdates)
   - `PoiService` (API-Requests)
   - `SpeechService` (TTS)

---

## 💡 Vision (Langfristig)

- „Context-aware travel companion“
- Persönliche Interessensprofile
- Mehrsprachige Inhalte
- Community-Kurierung & Qualitätshinweise

---

## 📝 Status

**Projekt in frühem Konzept- & Prototyp-Stadium.**  
Namens- und Branding-Entscheidung stehen noch aus.

---

## 🙌 Feedback & Ideen

Offen für:
- Feature-Vorschläge
- UX-Feedback
- Datenquellen-Hinweise




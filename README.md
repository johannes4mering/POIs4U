# POIs4U - Driving POI Companion

**An intelligent iOS companion app that enhances driving experiences by discovering and narrating nearby Points of Interest (POIs) in real-time.**

POIs4U transforms passive driving into an engaging journey by acting as a "curious co-pilot" that explains the surrounding environment. The application displays a live map with the current location, automatically detects relevant POIs within proximity, and uses text-to-speech to read descriptions aloud—enabling drivers to learn about their surroundings without taking their eyes off the road.

**Core Focus:** Safety-first design, simple one-touch operation, and audio-centric interaction to minimize driver distraction.

---

## 📖 Project Overview

### What POIs4U Does

POIs4U is an iOS application designed as an informative travel companion rather than a navigation tool. The application leverages geographic data from Wikipedia, Wikidata, and OpenStreetMap to identify interesting locations, landmarks, historical sites, and cultural points as users drive through different areas.

**Key Differentiators:**
- **Not a Navigation App:** POIs4U does not provide turn-by-turn directions. It enriches the journey by providing contextual information about the environment.
- **Audio-First Design:** Primary interaction through text-to-speech to maintain driver focus on the road.
- **Automatic Discovery:** POIs are detected automatically based on proximity and relevance without requiring manual searches.
- **Educational & Entertaining:** Transforms routine drives into opportunities to learn about history, architecture, nature, and local culture.

### Why POIs4U Exists

Traditional navigation apps focus on getting from point A to point B efficiently but miss the richness of the journey itself. POIs4U fills this gap by making drivers aware of interesting places they're passing—turning everyday commutes or road trips into educational experiences. This approach promotes curiosity-driven exploration while maintaining safety through hands-free audio interaction.

---

## 🏗️ Architecture

POIs4U follows an MVVM (Model-View-ViewModel) architecture pattern, separating concerns for maintainability and testability:

```
POIs4U/
├─ Views/                      # SwiftUI view components
│   └─ ContentView.swift       # Main map interface with POI overlays
├─ ViewModels/                 # Presentation logic and state management
│   ├─ MapViewModel.swift      # Manages map state and POI display
│   └─ POIDetailViewModel.swift # Handles individual POI presentation
├─ Services/                   # Business logic and external integrations
│   ├─ LocationService.swift   # CoreLocation wrapper for GPS tracking
│   ├─ POIService.swift        # Fetches POI data from Wikipedia/Wikidata/OSM
│   └─ SpeechService.swift     # AVSpeechSynthesizer wrapper for TTS
├─ Models/                     # Data structures
│   ├─ POI.swift               # Point of Interest entity (coordinates, name, description)
│   ├─ Coordinates.swift       # Geographic coordinate representation
│   └─ POIMetadata.swift       # Additional attributes (category, source, relevance)
└─ Utils/                      # Helper functions and extensions
    ├─ DistanceCalculator.swift # Proximity calculations
    └─ TextFormatter.swift      # Description sanitization for TTS
```

### Component Interactions

1. **LocationService** continuously monitors device GPS position using CoreLocation
2. **POIService** queries external APIs (Wikipedia, Wikidata, OSM) when location changes significantly
3. **ViewModels** process POI data, filter by relevance, and prepare UI state
4. **Views** render map with MapKit, displaying POI markers and information cards
5. **SpeechService** converts POI descriptions to speech using AVSpeechSynthesizer on user request

---

## ✨ Key Features

### Current Capabilities (Conceptual MVP)

- **Live Map Display:** Real-time position tracking with MapKit integration
- **Proximity-Based POI Detection:** Automatic discovery of nearby points of interest within configurable radius
- **POI Information Display:** Brief descriptions shown on map overlay cards
- **Text-to-Speech Narration:** "Read Aloud" button triggers audio description via AVSpeechSynthesizer
- **Basic Settings:** Configurable search radius and language preferences

### Planned Enhancements

- **Automatic Narration:** Auto-play descriptions when approaching significant POIs
- **Relevance Ranking:** Intelligent filtering based on POI importance and user preferences
- **Duplicate Detection:** Merge similar POIs from different data sources
- **Local Caching:** Offline support for previously visited areas
- **Apple CarPlay Integration:** Simplified interface optimized for in-car displays with audio focus
- **Wikidata Enrichment:** Additional metadata (construction year, architectural style, categories)
- **Multi-Modal Support:** Walking, cycling, and hiking modes with adjusted POI types
- **Category Filters:** User-selectable interests (history, architecture, nature, restaurants, cultural sites)
- **Personalization:** Learning user preferences over time for better POI recommendations

---

## 🛠️ Technology Stack

**Platform:** iOS 16+  
**Primary Language:** Swift  
**UI Framework:** SwiftUI (declarative UI)  
**Mapping:** MapKit (Apple's native mapping framework)  
**Location Services:** CoreLocation (GPS and location updates)  
**Speech Synthesis:** AVSpeechSynthesizer (AVFoundation framework for TTS)  
**Networking:** URLSession (native HTTP client for API requests)  
**Data Sources:**
- Wikipedia API (geographic articles and descriptions)
- Wikidata Query Service (structured data about places)
- OpenStreetMap Overpass API (POI geospatial data)

**Development Tools:**
- Xcode 14+ (IDE)
- Swift Package Manager (dependency management)

---

## 🚀 Getting Started

### Prerequisites

- macOS with Xcode 14 or later installed
- iOS 16+ device or simulator
- Apple Developer account (for device testing with location services)

**Note:** This project is currently in the conceptual stage. The Xcode project and Swift source files have not yet been created. The instructions below describe the intended setup process once implementation begins.

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/johannes4mering/POIs4U.git
   cd POIs4U
   ```

2. Open the project in Xcode:
   ```bash
   open POIs4U.xcodeproj
   ```

3. Configure signing & capabilities:
   - Select the project in Xcode navigator
   - Choose your development team
   - Enable "Location When In Use" capability

4. Build and run:
   - Select target device or simulator
   - Press Cmd+R or click the Play button

### First Run

On first launch, the app will request location permissions. Grant "Allow While Using App" to enable POI discovery features.

---

## 📁 Project Structure

```
POIs4U/                        # Root directory
├─ .git/                       # Git version control
├─ .gitignore                  # Xcode/Swift build artifacts exclusions
├─ README.md                   # This comprehensive documentation
├─ POIs4U.xcodeproj/           # Xcode project file (to be created)
├─ POIs4U/                     # Main application source code (to be created)
│   ├─ POIs4UApp.swift         # Application entry point
│   ├─ ContentView.swift       # Main SwiftUI view
│   ├─ Models/                 # Data models
│   ├─ Views/                  # UI components
│   ├─ ViewModels/             # Business logic
│   ├─ Services/               # External service integrations
│   └─ Utils/                  # Helper utilities
├─ POIs4UTests/                # Unit tests (to be created)
└─ POIs4UITests/               # UI integration tests (to be created)
```

**Current Repository State:** The project is in the conceptual and planning phase. Only documentation files exist; Swift source code and Xcode project files will be created in subsequent development phases.

---

## 📝 Status & Maturity

**Current Phase:** Early Concept & Documentation Stage  

**What Exists:**
- Comprehensive README with architecture and feature specifications
- .gitignore configured for Xcode/Swift development
- Clear technical roadmap and design decisions

**What's Next:**
- Xcode project initialization
- Implementation of core services (LocationService, POIService, SpeechService)
- Basic SwiftUI interface with MapKit integration
- MVP release with fundamental POI detection and narration

**Project Naming:** Final branding and app name are still under consideration. "POIs4U" is a working title.

---

## ⚖️ Data Sources & Licensing

### Content Attribution

- **Wikipedia & Wikidata Content:** Licensed under CC BY-SA 4.0 (Creative Commons Attribution-ShareAlike 4.0 International)
  - Requires attribution to Wikipedia/Wikidata
  - Derivative works must be shared under same license
  - Content is community-maintained and multilingual

- **OpenStreetMap Data:** Licensed under ODbL (Open Database License)
  - Requires attribution to OpenStreetMap contributors
  - Database contents freely shareable with attribution
  - Derivative databases must use ODbL

### In-App Attribution

POIs4U will display transparent source attribution for all displayed content, ensuring compliance with CC BY-SA 4.0 and ODbL requirements. Each POI will indicate its data source (Wikipedia, Wikidata, or OSM) in the detail view.

---

## 💡 Long-Term Vision

POIs4U aims to evolve into a context-aware travel companion that adapts to user interests and preferences:

- **Personalized Interest Profiles:** Learn what types of POIs interest each user (historical sites, restaurants, natural landmarks, etc.)
- **Multilingual Content:** Support for content in multiple languages with automatic translation
- **Community Curation:** Allow users to rate POI descriptions and suggest improvements
- **Quality Indicators:** Display content quality scores based on source reliability and community feedback
- **Social Sharing:** Enable users to share interesting POIs they discovered
- **Offline Mode:** Pre-download POI data for regions to enable full functionality without internet
- **Accessibility:** Enhanced support for VoiceOver and other iOS accessibility features

---

## 🙌 Contributing & Feedback

POIs4U welcomes contributions and ideas from the community:

- **Feature Suggestions:** Propose new capabilities or improvements via GitHub Issues
- **UX Feedback:** Share thoughts on interface design and user experience
- **Data Source Recommendations:** Suggest additional POI databases or APIs
- **Bug Reports:** Report issues or unexpected behavior
- **Code Contributions:** Submit pull requests following Swift style guidelines

---

## Release Notes

### [Unreleased] - 2026-01-18

#### Added
- Comprehensive English README documentation with LLM-optimized structure
- Detailed architecture section explaining MVVM pattern and component interactions
- Complete technology stack documentation with specific frameworks and APIs
- Enhanced project structure section showing anticipated directory layout
- Data sources and licensing section with CC BY-SA 4.0 and ODbL compliance details
- Getting started guide with installation and setup instructions
- Long-term vision section outlining future development direction
- Release notes section to track project evolution

#### Changed
- Expanded project overview with clear explanation of purpose and differentiation from navigation apps
- Restructured README for better LLM context consumption with explicit, detailed sections
- Enhanced status section to clearly indicate current conceptual phase
- German documentation preserved in dedicated section below

#### Technical Details
- Repository contains only documentation files: README.md, .gitignore
- No Swift source code files exist yet (conceptual stage)
- Xcode project structure planned but not yet created
- Git history: Documentation-only commits establishing project vision
- No release tags exist in repository yet

---

## 🌐 Deutsche Dokumentation / German Documentation

### Driving POI Companion (Arbeitstitel)

Eine iOS-App, die während der Fahrt eine **Umgebungskarte** anzeigt, nearby **Points of Interest (POIs)** erkennt und diese dem Fahrer auf Wunsch **vorliest**.  
Ziel ist ein „neugieriger Beifahrer", der die Umgebung erklärt – mit Fokus auf **Sicherheit, einfache Bedienung und Audio-Ausgabe**.

### 🎯 Ziel & Idee

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

### 🧩 Technischer Überblick

**Plattform:** iOS (MVP, später optional CarPlay)  
**Sprache:** Swift  
**UI-Framework:** SwiftUI  
**Karte:** MapKit  
**Standort:** CoreLocation  
**Sprachausgabe:** AVSpeechSynthesizer (AVFoundation)  
**Netzwerk / APIs:** URLSession (Wikipedia / Wikidata / OSM)

#### Architektur (MVVM-orientiert)

```
App
├─ Views (SwiftUI)
├─ ViewModels
├─ Services
│   ├─ LocationService
│   ├─ PoiService (Wikipedia / Wikidata)
│   └─ SpeechService
├─ Models (POI, Coordinates, Metadata)
└─ Utils
```

### 🚀 Geplante MVP-Funktionen

- Aktuelle Position auf Karte anzeigen  
- POIs im Radius abrufen  
- Kurzinfo zu einem POI anzeigen  
- Button „Vorlesen" → Audio-Ausgabe des Textes  
- Basis-Einstellungen (Radius, Sprache)

### 🔜 Mögliche nächste Schritte

- Automatisches Vorlesen bei Annäherung  
- Relevanz-Ranking / Duplikat-Filter  
- Lokales Caching  
- CarPlay-Support (reduzierte UI + Audio-Fokus)  
- Wikidata-Anreicherung (Baujahr, Kategorie, Typ)  
- Off-Road / Fuß- oder Rad-Modus

### ⚖️ Daten & Lizenzen

- Inhalte aus **Wikipedia / Wikidata**:  
  Nutzung gemäß **CC BY-SA 4.0** (Namensnennung & Share-Alike)
- OpenStreetMap-Daten: **ODbL-Lizenz**
- In der App erfolgt eine transparente Attribution der Quellen.

### 🧪 Entwicklung & Setup

1. Repository klonen
2. Xcode öffnen → iOS App (SwiftUI / Swift)
3. Abhängigkeiten:
   - iOS 16+ empfohlen
4. Startpunkte:
   - `ContentView` (Map + UI-Rahmen)
   - `LocationService` (Standortupdates)
   - `PoiService` (API-Requests)
   - `SpeechService` (TTS)

### 💡 Vision (Langfristig)

- „Context-aware travel companion"
- Persönliche Interessensprofile
- Mehrsprachige Inhalte
- Community-Kurierung & Qualitätshinweise

### 📝 Status

**Projekt in frühem Konzept- & Prototyp-Stadium.**  
Namens- und Branding-Entscheidung stehen noch aus.

### 🙌 Feedback & Ideen

Offen für:
- Feature-Vorschläge
- UX-Feedback
- Datenquellen-Hinweise

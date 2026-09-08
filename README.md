# Flight Progress Strip Manager

By Captain_3D "STINGRAY"

---

## Table of Contents

- [Table of Contents](#Table-of-Contents)
- [Overview](#Overview)
- [Flight Strips](#Flight-Strips)
  - [Flight Strips Fields](#Flight-Strips-Fields)
- [Application UI](#Application-UI)
  - [Menu Buttons](#Menu-Buttons)
- [Keybinds](#Keybinds)
- [Data Storage Locations](#Data-Storage-Locations)

---

## Overview

This tools purpose is to aid in the organisation and workflow of any controlling agency. It is A digital, networkable flight progress strip board for virtual air traffic control. It is built for coordinating multiple controllers (Tower, Ground, Approach, Departure, Center, Carrier/LSO, etc.) working the same airspace or carrier deck at once. It reproduces the paper flight-strip workflow used in real-world ATC, with support for military & carrier operations.

The code is closed sourced at the moment as this has and will continue to be a passion project of mine.

---

## Flight Strips

### Flight Strip Fields

**Identification & Aircraft**

| Field Name | Type | Description | Example |
|---|---|---|---|
| **Callsign** | LineEdit | The given radio callsign of an aircraft/flight | `"Viper1"` |
| **Squawk** | LineEdit (read-only on strip) | 4-digit octal Mode 3/A transponder code, generated/edited in the strip dialog | `"4231"` |
| **Type** | ComboBox (editable) | Aircraft type flown | `"F/A-18C"` |
| **Count** | SpinBox | Number of aircraft in the flight (1-8); drives Breakout | `"x2"` |
| **Bort Number** | LineEdit | Carrier tail/side number for the aircraft | `"212"` |
| **CID** | LineEdit (read-only) | Unique 3-digit computer/flight ID | `"047"` |

**Assigned Values**

| Field Name | Type | Description | Example |
|---|---|---|---|
| **Heading** | SpinBox | Assigned heading, 0-360 | `"H:270"` |
| **Altitude** | SpinBox | Assigned altitude (hundreds of feet), step 10 | `"A:250"` |
| **Speed** | SpinBox | Assigned airspeed, step 5 | `"S:350"` |
| **Rules** | ComboBox | Flight rules | `"IFR"` |
| **Status** | ComboBox | Current phase of flight/ground state | `"Cleared"` |

**Route & Procedures**

| Field Name | Type | Description | Example |
|---|---|---|---|
| **Departure Airport** | ComboBox (editable) | Departure ICAO | `"KJFK"` |
| **Departure Time** | LineEdit | Actual/proposed departure time | `"1200"` |
| **Arrival Airport** | ComboBox (editable) | Arrival ICAO | `"KLAX"` |
| **Arrival Time** | LineEdit | Estimated/actual arrival time | `"1400Z"` |
| **Route** | LineEdit | Filed route of flight | `"DCT CAMRN4 DCT"` |
| **SID** | ComboBox (editable) | Standard Instrument Departure | `"CAMRN4"` |
| **STAR** | ComboBox (editable) | Standard Terminal Arrival Route | `"ZIMMR2"` |
| **Standard** | ComboBox (editable) | Named standard procedure (Combined SID/STAR) in use | `"CANDR3"` |
| **Runway** | ComboBox (editable) | Assigned runway | `"22L"` |
| **Task** | LineEdit | Mission/task designation | `"CAP"` |
| **Fuel** | SpinBox | Fuel state, step 100 | `"12500"` |

**ATC Reference (FAA 7110.65-style)**

| Field Name | Type | Description | Example |
|---|---|---|---|
| **Equipment Suffix** | ComboBox | ICAO equipment/nav suffix | `"/L"` |
| **Wake Category** | ComboBox | Wake turbulence category | `"H"` |
| **Sector** | ComboBox (editable) | Owning ATC sector | `"36"` |
| **Coordination Fix** | ComboBox (editable) | Fix used to coordinate handoff | `"LENDY"` |
| **Previous Fix** | ComboBox (editable) | Last fix crossed | `"LGA"` |
| **Current Fix** | ComboBox (editable) | Fix currently at/nearest to | `"JFK"` |
| **Next Fix** | ComboBox (editable) | Next fix in the route | `"CAMRN"` |
| **EFC Time** | LineEdit | Expect Further Clearance time | `"EFC:1234"` |
| **Clearance Limit** | ComboBox (editable) | Furthest point cleared to | `"KATL"` |
| **Information** | LineEdit | ATIS/information letter briefed | `"B"` |

**Notes & Annotations**

| Field Name | Type | Description | Example |
|---|---|---|---|
| **Remarks** | TextEdit | Free-form multi-line remarks | `"Request VFR practice approaches"` |
| **Annotations 1–9** | LineEdit | Nine general-purpose free-text scratch fields | `"A1"` |

**Operational & Audit**

| Field Name | Type | Description | Example |
|---|---|---|---|
| **Owner** | LineEdit (read-only) | Controller currently responsible for the strip | `"Approach"` |
| **Time** | LineEdit (read-only) | UTC time the strip was created | `"14:32:07Z"` |
| **Revision** | LineEdit (read-only) | Increments each time the strip is edited | `"3"` |

---

## Application UI

### Menu Buttons

**Connection**
- Start Server
  - Starts a local server tied to your application that allows others to connect to. (assuming you have your port open and allowed for external conecting)
- Connect
  - Connect to a server.

**Layouts**
- Open Layout
- Save Layout
- Layout Properties
- Restore Autosave
- Strip Layout Editor
- Insert Runway Spacers
- Toggle Theme

**Keybinds**
- Customise Keybinds

**Add**
- Add Column
- New Strip
- Bulk Add Strips
- New Spacer
- Add Airfield Info block
- Add Carrier Info block

**Help**
- Check For Updates

### Menu Tabs

---

## Keybinds

**Keybinds → Customize Keybinds...** lets you rebind every action. Click **Record**, press a key combo, or **Clear** to unbind. Assigning a key already in use elsewhere automatically clears it from its previous action. **Reset All to Defaults** restores the shipped bindings below:

| Action | Default Key |
|---|---|
| New Inbound Strip | `I` |
| New Outbound Strip | `O` |
| New Circuit Strip | `P` |
| New Enroute Strip | `E` |
| New Carrier Strip | — |
| Bulk Add Strips | — |
| New Column | `C` |
| New Spacer | `S` |
| Save Layout | `Ctrl+S` |
| Load Layout | `Ctrl+O` |
| Toggle Theme | `T` |
| Start/Open Server | — |
| Connect to Server | — |
| Strip Layout Editor | — |
| Insert Runway Spacers | — |
| Delete Hovered Strip/Spacer | `X` |
| New Airfield Info Block | — |
| New Carrier Info Block | — |

---

## Data Storage Locations

The app stores user data under a platform-standard app-data directory (organization `Captain_3D-STINGRAY`, app `FlightProgressStripManager`):

```
<AppData>/
├── app_settings.json          # default layout, active strip layout profile
├── keybinds.json              # customized keybinds
├── bookmarks.json             # saved server connections
├── autosave.json              # rolling 60s autosave of the current board
├── layouts/
│   └── custom/*.json          # your saved board layouts
├── strip_layouts/*.json       # your saved strip visual layout profiles
└── airports/*.json            # your custom airport data profiles
```

Bundled, read-only presets ship alongside the application in:

```
<App Directory>/
├── layouts/.presets/*.json
├── strip_layouts/.presets/*.json
└── airports/.presets/*.json
```

Presets are always available to load/clone but can't be renamed, deleted, or overwritten in place.

---
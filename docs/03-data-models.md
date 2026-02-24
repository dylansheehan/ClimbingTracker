# ClimbingTracker – Core Data Models (v1)

## Architecture Flow

SplitTemplate  
→ SessionTemplate  
→ PlannedSession  
→ LoggedSession  
→ SessionEntry

---

# ENUMERATIONS

### SessionCategory
- CLIMB
- STRENGTH
- MOBILITY
- REHAB
- CONDITIONING

### TrainingFocus
- LIMIT
- POWER
- POWER_ENDURANCE
- VOLUME
- TECHNIQUE
- DELOAD
- REHAB

### EnvironmentType
- BOARD
- GYM
- OUTDOOR
- HOME
- OTHER

### PlannedSessionStatus
- PLANNED
- IN_PROGRESS
- COMPLETED
- SKIPPED

---

# DATA MODELS

## SessionTemplate

Represents an intended session inside a split.  
Contains intent only — no performance data.

### Fields
- id: string
- name: string
- category: SessionCategory
- trainingFocus: TrainingFocus
- environment: EnvironmentType
- plannedDuration: number (minutes)
- tags: string[]
- notes: optional string

### Purpose
Defines what the session is supposed to be.

---

## SplitTemplate

Defines a repeating rotation of training days (e.g., 3-day split).

### Fields
- id: string
- name: string
- splitLength: number (number of rotation days)
- days: SplitDay[]

---

### SplitDay

Represents one rotation day (e.g., Day 1).

#### Fields
- rotationDayIndex: number (1-based index)
- sessionTemplateIds: string[]

---

## ScheduledBlock

Created when a user applies a split to the calendar.

### Fields
- id: string
- splitTemplateId: string
- startDate: string (ISO date YYYY-MM-DD)
- endDate: string (ISO date YYYY-MM-DD)
- placementMode: PlacementMode

### Purpose
Represents a training block applied across a date range.

---

## PlannedSession

Represents a session placed on a specific calendar date.

### Fields
- id: string
- templateId: string
- date: string (ISO date YYYY-MM-DD)
- status: PlannedSessionStatus
- orderIndex: number (used when multiple sessions exist on the same day)

### Purpose
Connects a session template to a real calendar date.

---

## LoggedSession

Created when a user starts a session.  
Contains actual performance data.

### Fields
- id: string
- plannedSessionId: string
- startTime: string (ISO datetime)
- endTime: optional string (ISO datetime)
- actualDuration: optional number (minutes)
- rpe: optional number (1–10 scale)
- painScore: optional number (0–10 scale)
- bodyweight: optional number (kg)
- notes: optional string
- entries: SessionEntry[]

### Purpose
Stores what actually happened during training.

---

# SESSION ENTRY TYPES

A LoggedSession contains a list of entries.

## ClimbEntry

### Fields
- type: CLIMB
- grade: string (e.g., "V6")
- attempts: number
- sent: boolean
- boardAngle: optional number
- tags: optional string[]

---

## StrengthEntry

### Fields
- type: STRENGTH
- exerciseName: string
- sets: number
- reps: number
- weight: optional number (kg)

---

## MobilityEntry

### Fields
- type: MOBILITY
- movementName: string
- duration: number (minutes)
- notes: optional string

---

# Design Principles

- Templates define intent only.
- PlannedSessions assign intent to calendar dates.
- LoggedSessions contain actual performance data.
- Progression metrics are derived from LoggedSession + entries.
- Reports compute trends from logged sessions.
- Classification fields use controlled enums (never free text).

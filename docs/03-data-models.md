# Data Models (MongoDB)

## Summary
Use a single `Session` collection with a `type` discriminator and type-specific payloads.
This keeps queries and analytics simple while supporting varied session types.

## Enums

### SessionType
- CLIMBING
- BOARD
- STRENGTH
- RECOVERY

### GradeSystem
- V_SCALE
- FONT

### BoardType
- KILTER
- TB2
- MOON
- SPRAY

### SendType
- FLASH
- SESSION_SEND
- PROJECT
- REPEAT
- ATTEMPT_ONLY

## Core Entity: Session

### Common fields
- _id
- userId (optional for single-user MVP)
- type: SessionType
- startTime: ISO date
- durationMin: number
- locationName: string
- notes?: string
- tags: string[]
- rpe?: number (1–10)
- pain?: PainEntry[]
- createdAt, updatedAt

### PainEntry (embedded)
- area: string (e.g. "left shoulder", "elbow")
- severity: number (0–10)
- notes?: string

## Type-specific payloads

### CLIMBING
session.climbing:
- discipline?: "BOULDER" | "ROPE" (optional)
- gymSetName?: string
- climbs: ClimbAttempt[]

ClimbAttempt:
- gradeSystem: GradeSystem
- gradeLabel: string (e.g. "V6")
- gradeValue: number (for sorting/analytics)
- sendType: SendType
- attempts: number
- styleTags: string[]
- notes?: string

### BOARD
session.board:
- boardType: BoardType
- angleDeg: number
- mode?: "PROJECT" | "POWER_ENDURANCE" | "VOLUME"
- benchmarkName?: string
- problems: BoardProblem[]

BoardProblem:
- name?: string
- gradeSystem: GradeSystem
- gradeLabel: string
- gradeValue: number
- attempts: number
- sent: boolean
- reps?: number
- restSec?: number
- notes?: string

### STRENGTH
session.strength:
- focusTags: string[]
- exercises: StrengthExercise[]

StrengthExercise:
- name: string
- sets: StrengthSet[]
- notes?: string

StrengthSet:
- reps: number
- weightKg?: number
- rpe?: number
- tempo?: string
- holdSec?: number

### RECOVERY
session.recovery:
- recoveryType: string (e.g. "mobility", "bath", "physio")
- notes?: string

## Indexes (recommended)
- { userId: 1, startTime: -1 }
- { userId: 1, type: 1, startTime: -1 }
- { userId: 1, "board.boardType": 1, "board.angleDeg": 1, startTime: -1 } (optional)
- { userId: 1, tags: 1 } (optional)

## Notes on Grades
Store both:
- gradeLabel for UI display
- gradeValue for sorting/analytics

This avoids painful parsing later.

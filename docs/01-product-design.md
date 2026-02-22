# ClimbingTracker – Product Design

## 1. Problem Statement
ClimbingTracker is a lightweight tracker for climbing, board, strength, and recovery sessions.
Notes apps are unstructured and spreadsheets are too manual, making trend analysis painful.

## 2. Goals
- Log sessions quickly (< 60 seconds for a basic log)
- Track board (type + angle) cleanly
- Track grade progression and volume over time
- Track strength work in a structured way (sets/reps/weight)
- Enable future analytics without reworking the database

## 3. Non-Goals (MVP)
- Social/sharing features
- Coaching plan generation
- Wearables integration

## 4. UX Principles
- Fast defaults > perfect detail
- Optional depth: simple log first, advanced fields expandable
- Minimal friction: few required fields, consistent flow
- Search/filter later: store enough metadata for filtering

## 5. Information Architecture (Pages)
- Dashboard
- Add Session
- Session History (filters)
- Session Detail
- Analytics
- Settings

## 6. User Flows

### Add Session
1. Choose session type (Climbing / Board / Strength / Recovery)
2. Fill required fields (date, duration, location)
3. Add optional details (climbs/problems/exercises)
4. Save → navigate to Session Detail

### Review Progress
1. Open Analytics
2. Filter by date range and session type
3. View trends (volume, max grade, frequency)

## 7. MVP Scope (Phase 1)
- Create / view / edit / delete sessions
- Session history list + filters (date range, type, board type, tags)
- Minimal dashboard (recent sessions + weekly volume)

## 8. Future Features
- Benchmarks (repeatable tests: PE circuits, weighted pull-ups)
- Personal best detection and summaries
- Injury/pain overlay trends
- Templates for common sessions

# API Specification

Base URL: /api

## Sessions

### Create session
POST /sessions
Body: Session

### List sessions
GET /sessions
Query params (optional):
- type
- from (ISO date)
- to (ISO date)
- boardType
- minGradeValue
- maxGradeValue
- tags (comma-separated)

### Get session
GET /sessions/:id

### Update session
PATCH /sessions/:id
Body: partial Session

### Delete session
DELETE /sessions/:id

## Standard Response Shapes

### Success
{ "data": ... }

### Error
{
  "error": {
    "message": "string",
    "code": "string",
    "details": {}
  }
}

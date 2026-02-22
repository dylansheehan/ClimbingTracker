# Decision Log

- Frontend: React + TypeScript (replacing Angular)
- Single `Session` collection with `type` discriminator
- Embed climbs/problems/exercises inside session for simple reads
- Store gradeLabel + gradeValue for display + analytics
- Keep MVP state simple (refetch after mutations); consider React Query later

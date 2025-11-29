# Development Log

## 2024-11-29

### Done
- Reviewed existing user model, confirmed `notify_email` field exists
- Designed notifications table schema
- Defined 3 API endpoints
- Chose SendGrid for email (already in project)
- Created migration SQL

### Blocked
- Waiting for DB migration approval from DevOps

### Notes
- Users table already has `notify_email` boolean for opt-in
- Using partial index for unread notifications query optimization

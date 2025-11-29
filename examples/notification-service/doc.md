# Notification Service - Technical Document

## Summary
Add a notification system with two channels: in-app (stored in DB) and email (via SendGrid).

## Data Model

```
+------------------+
|   notifications  |
+------------------+
| id (PK)          |
| user_id (FK)     |
| type             |  <- 'info' | 'warning' | 'success'
| title            |
| message          |
| read_at          |  <- NULL if unread
| created_at       |
+------------------+
        |
        | user_id
        v
+------------------+
|      users       |
+------------------+
| id               |
| email            |
| notify_email     |  <- boolean, opt-in for emails
+------------------+
```

## API Endpoints

| Method | Endpoint | Description |
|:---|:---|:---|
| GET | /api/notifications | List user's notifications |
| POST | /api/notifications/:id/read | Mark as read |
| DELETE | /api/notifications/:id | Delete notification |

## Key Decisions

### Decision 1: Storage Approach
- **Options**: A) Store all in DB, B) Redis for recent + DB archive
- **Chosen**: A - All in DB
- **Rationale**: Simpler, sufficient for expected volume (<1000/user)

### Decision 2: Email Integration
- **Chosen**: SendGrid
- **Rationale**: Already used in project for transactional emails

## Migration SQL

```sql
CREATE TABLE notifications (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID NOT NULL REFERENCES users(id),
  type VARCHAR(20) NOT NULL DEFAULT 'info',
  title VARCHAR(255) NOT NULL,
  message TEXT,
  read_at TIMESTAMP,
  created_at TIMESTAMP DEFAULT NOW()
);

CREATE INDEX idx_notifications_user_id ON notifications(user_id);
CREATE INDEX idx_notifications_unread ON notifications(user_id) WHERE read_at IS NULL;
```

## Open Questions
- [ ] Rate limit for notification creation?
- [ ] Batch size for email sending?

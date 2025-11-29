# TODO

## Research
- [x] Review existing user model
- [x] Check email service integration patterns

## Pending Confirmation
- [ ] Max notifications to store per user?
- [ ] Retention policy (auto-delete after 30 days?)

## Implementation
- [ ] Create notifications table migration
- [ ] Implement NotificationService class
- [ ] Add API endpoints (GET /notifications, POST /notifications/read)
- [ ] Integrate SendGrid for email channel
- [ ] Write unit tests

---

## Acceptance Criteria

### Must Have
- [ ] Notifications table created with proper indexes
- [ ] GET /api/notifications returns user's notifications
- [ ] POST /api/notifications/:id/read marks as read
- [ ] Email notifications sent via SendGrid
- [ ] Unit tests passing

### Nice to Have
- [ ] Batch mark-as-read endpoint
- [ ] Notification count in response headers

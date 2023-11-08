```typescript
type Attendee = {
  id: number;
  created_at: Date;
  updated_at: Date;
  deleted_at: Date;
  user_id: number;
  user: User;
  event_id: number;
  event: Event;
};
```
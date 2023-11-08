```typescript
type Event = {
  id: number;
  created_at: Date;
  updated_at: Date;
  deleted_at: Date;
  title: string;
  start_time: Date;
  end_time: Date;
  description: string;
  meeting_link: string;
  organization_id: number;
  organization: Organization;
  organizers: User[];
  attendees: Attendee[];
};
```
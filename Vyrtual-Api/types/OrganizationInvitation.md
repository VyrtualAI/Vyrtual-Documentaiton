```typescript
type OrganizationInvitation = {
  id: number;
  created_at: Date;
  updated_at: Date;
  deleted_at: Date;
  organization_id: number;
  invitee_email: string;
  state: string;
  position: string;
  role: string;
};
```
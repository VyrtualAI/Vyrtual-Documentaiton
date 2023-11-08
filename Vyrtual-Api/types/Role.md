```typescript
type Role = {
  id: number;
  created_at: Date;
  updated_at: Date;
  deleted_at: Date;
  role: ValidRole;
  user: User;
  user_id: number;
  organization_id: number;
  organization: Organization;
};
```
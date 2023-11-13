```typescript
type Tag = {
  id: number;
  created_at: Date;
  updated_at: Date;
  deleted_at: Date; // Converted gorm.DeletedAt to Date
  name: string;
  organization_id: number;
};
```

```typescript
type BoardColumn = {
  id: number;
  created_at: Date;
  updated_at: Date;
  deleted_at: Date; // Converted gorm.DeletedAt to Date
  name: string;
  task_board_id: number;
  index: number;
  organization_id: number;
};
```

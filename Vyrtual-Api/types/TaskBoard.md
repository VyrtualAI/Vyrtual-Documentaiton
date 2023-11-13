```typescript
type TaskBoard = {
  id: number;
  created_at: Date;
  updated_at: Date;
  deleted_at: Date; // Converted gorm.DeletedAt to Date
  name: string;
  tasks: Task[]; // Assuming Task is the converted TypeScript type for TaskJSON
  organization_id: number;
  columns: BoardColumn[]; // Assuming BoardColumn is the converted TypeScript type for BoardColumnJSON
};
```

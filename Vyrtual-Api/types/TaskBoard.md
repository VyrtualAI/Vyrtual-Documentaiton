```typescript
type TaskBoard = {
  id: number;
  created_at: Date;
  updated_at: Date;
  deleted_at: Date;
  name: string;
  tasks: Task[];
  organization_id: number;
  columns: BoardColumn[];
};
```

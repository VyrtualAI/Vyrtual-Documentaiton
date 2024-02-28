```typescript
type Task = {
  id: number;
  created_at: Date;
  updated_at: Date;
  deleted_at: Date; // Converted gorm.DeletedAt to Date
  title: string;
  description: string;
  due_date: Date;
  assignee: number[]; // Array of numbers
  board_column: BoardColumn; // Assuming BoardColumn is the TypeScript type for BoardColumnJSON
  board_column_id: number;
  media: number[]; // Array of numbers
  tags: number[]; // Array of numbers
  organization_id: number;
  task_board_id: number;
  category_id: number;
  department_id: number;
};
```

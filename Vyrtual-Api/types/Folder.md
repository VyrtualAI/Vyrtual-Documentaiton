```typescript
type Folder = {
  id: number;
  created_at: Date;
  updated_at: Date;
  deleted_at: Date;
  name: string;
  organization_id: number;
  path: string;
  files: File[];
  folders: Folder[];
  parent_folder_id: number;
  viewable_by: number[];
  editable_by: number[];
  accessible_by: string[];
  modifiable_by: string[];
  created_by_id: number;
  size: number;
};
```
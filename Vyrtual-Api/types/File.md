```typescript
type File = {
  id: number;
  created_at: Date;
  updated_at: Date;
  deleted_at: Date;
  name: string;
  thumbnail: string;
  organization_id: number;
  viewable_by: User[];
  editable_by: User[];
  parent_folder_id: number;
  accessible_by: AccessGroup[];
  modifiable_by: AccessGroup[];
  created_by_id: number;
  created_by: User;
  size: number;
  path: string;
  download_url: string;
};
```

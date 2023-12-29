```typescript
type Organization = {
  id: number;
  created_at: Date;
  updated_at: Date;
  deleted_at: Date;
  name: string;
  members: number[];
  logo: string;
  plan: string;
  created_by_id: number;
  created_by: User;
  owners: number[];
  positions: number[];
  registered: boolean;
  stripe_customer_id: string;
};
```

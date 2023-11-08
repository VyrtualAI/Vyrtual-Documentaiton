```typescript
type User = {
  id: number;
  created_at: Date;
  updated_at: Date;
  deleted_at: Date;
  first_name: string;
  last_name: string;
  roles: number[];
  email: string;
  image: string;
  primary_organization: number;
  phone_number: string;
  organizations: number[];
  language: string[];
  organization_profiles: OrganizationProfile[];
  positions: number[];
};
```

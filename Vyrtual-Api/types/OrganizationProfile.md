```typescript
type OrganizationProfile = {
 id: number;
 created_at: Date;
 updated_at: Date;
 deleted_at: Date;
 organization_id: number;
 user_id: number;
 position: Position;
 position_id: number;
 main_language: Language;
 main_language_id: uint;
 ai_Language: Language;
 ai_language_id: Language;
 push_notifications_enabled: boolean;
 assignee_notifications_enabled: boolean;
 due_date_notifications_enabled: boolean;
 message_notifications_enabled: boolean;
 meeting_notifications_enabled: boolean;
};
```

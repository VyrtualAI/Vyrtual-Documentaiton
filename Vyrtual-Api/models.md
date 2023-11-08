# /models/models.go

This file contains the model definitions for various entities in the application. Here is a summary of the models defined in this file:

### User

The `User` model represents a user in the system. It contains information such as the user's first name, last name, email, phone number, and image. It also has associations with other models such as `Roles`, `Organizations`, `Languages`, `OrganizationProfiles`, and `Positions`.

### Event

The `Event` model represents an event in the system. It contains information such as the event's title, start time, end time, description, meeting link, and the organization it belongs to. It also has associations with other models such as `Organizers` and `Attendees`.

### Organization

The `Organization` model represents an organization in the system. It contains information such as the organization's name, logo, plan, and the user who created it. It also has associations with other models such as `Members`, `Owners`, `Positions`, and `Invitations`.

### Folder

The `Folder` model represents a folder in the system. It contains information such as the folder's name, path, and the organization it belongs to. It also has associations with other models such as `Files`, `Folders`, `ViewableBy`, `EditableBy`, `AccessibleBy`, and `ModifiableBy`.

### File

The `File` model represents a file in the system. It contains information such as the file's name, thumbnail, size, path, and the organization it belongs to. It also has associations with other models such as `ViewableBy`, `EditableBy`, `AccessibleBy`, and `ModifiableBy`.

### AccessGroup

The `AccessGroup` model represents an access group in the system. It contains information such as the access group's name.

### Role

The `Role` model represents a role in the system. It contains information such as the role's name, the user it belongs to, and the organization it belongs to.

### Language

The `Language` model represents a language in the system. It contains information such as the language's name and language code.

### Position

The `Position` model represents a position in the system. It contains information such as the position's name and the organization it belongs to.

### OrganizationProfile

The `OrganizationProfile` model represents an organization profile in the system. It contains information such as the organization profile's main language, AI language, and various notification settings.

### OrganizationInvitation

The `OrganizationInvitation` model represents an organization invitation in the system. It contains information such as the invitation's state, position, and role.

### Attendee

The `Attendee` model represents an attendee of an event in the system. It contains information about the user and the event they are attending.

These models are used to define the data structure and relationships between different entities in the application.
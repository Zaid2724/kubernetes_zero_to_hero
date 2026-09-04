# Authentication vs Authorization

Authentication = Who are you?

Authorization = What are you allowed to do?

Example:

User: Zaid
      │
      ▼
Authentication
"Are you really Zaid?"
      │
      ▼
Authorization
"Can Zaid delete Pods?"
Authentication	Authorization
Identifies user	Checks permissions
Who are you?	What can you do?
Happens first	Happens after authentication
Important Flow
kubectl request
      ↓
Authentication
      ↓
Authorization
      ↓
Admission Control
      ↓
API Server processes request
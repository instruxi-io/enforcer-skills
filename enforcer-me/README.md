# /enforcer-me

User profile, preferences, contacts, invites, and self-service features.

## When to use
- Building user-facing profile or settings screens
- Managing user preferences and contacts
- Implementing invite flows
- Self-service group join/leave
- Building support ticket submission

## What it covers
- User profile read and update
- Preference management
- Contact list operations
- Invite creation and redemption
- Self-service group membership
- Support ticket submission

## Tips
- All /me endpoints operate on the currently authenticated user; no user ID parameter needed
- Preferences are arbitrary key-value pairs scoped to the user
- Invites generate shareable links; redemption triggers group membership automatically
- Self-service group operations respect the group's join policy

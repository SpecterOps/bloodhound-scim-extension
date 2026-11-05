# SCIM_Group

Represents a group resource provisioned via the [System for Cross-domain Identity Management (SCIM)](https://scim.cloud/) protocol. SCIM groups are used by identity providers to organize users and manage access to downstream applications. Group membership changes propagated through SCIM can grant or revoke application access, making groups a key control point for identity governance.

## Properties

| Property | SCIM Property | Type | Description | Sample Value |
| --- | --- | --- | --- | --- |
| `id` | `id`  | `string` | The unique identifier of the group. | `2819c223-7f76-453a-919d-413861904646` |
| `displayName` | `displayName` | `string` | The display name of the group. | `Sales Team` |
| `created` | `meta.created` | `datetime` | The date and time the group was created. | `2010-01-23T04:56:22Z` |
| `lastModified` | `meta.lastModified` | `datetime` | The date and time the group was last modified. | `2011-05-13T04:42:34Z` |

## Diagram

```mermaid
flowchart LR
    subgraph Okta
        Okta_User[fa:fa-user Okta_User]
        Okta_Group[fa:fa-users Okta_Group]

        Okta_User -->|Okta_MemberOf| Okta_Group
    end

    subgraph SCIM
        SCIM_User[fa:fa-user SCIM_User]
        SCIM_Group[fa:fa-users SCIM_Group]

        SCIM_User -->|SCIM_MemberOf| SCIM_Group
    end

    subgraph "Entra ID"
        AZUser[fa:fa-user AZUser]
        AZGroup[fa:fa-users AZGroup]

        AZUser -->|AZMemberOf| AZGroup
    end

    SCIM_Group -->|SCIM_MembershipSync| AZGroup
    Okta_Group -->|SCIM_MembershipSync| SCIM_Group
    Okta_User -.->|SCIM_Provisioned| SCIM_User
    SCIM_User -.->|SCIM_Provisioned| AZUser
```

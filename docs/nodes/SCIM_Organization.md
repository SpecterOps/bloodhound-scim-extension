# SCIM_Organization

Represents a synchronized organization or tenant in the identity provider (IdP). An application may synchronize users and groups from multiple organizations or tenants via SCIM. The `SCIM_Organization` node serves as the root container for all SCIM resources belonging to a given tenant, providing a clear boundary for identity governance and access control.

## Properties

| Property | Type | Description | Sample Value |
| --- | --- | --- | --- |
| `id` | `string` | The unique identifier of the organization or tenant. | `contoso.com` |
| `displayName` | `string` | The display name of the organization or tenant. | `Contoso` |
| `url` | `string (uri)` | The URL of the organization or tenant in the IdP. | `https://contoso.com/scim` |

## Diagram

```mermaid
flowchart TD
    SCIM_Organization[fa:fa-building SCIM_Organization]
    SCIM_User[fa:fa-user SCIM_User]
    SCIM_Group[fa:fa-users SCIM_Group]
    SCIM_Role[fa:fa-id-badge SCIM_Role]

    SCIM_Organization -->|SCIM_Contains| SCIM_User
    SCIM_Organization -->|SCIM_Contains| SCIM_Group
    SCIM_Organization -->|SCIM_Contains| SCIM_Role
```

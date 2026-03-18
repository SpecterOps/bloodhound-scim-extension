# SCIM_Role

Represents a role derived from the `roles` attribute of SCIM users. In SCIM, roles are typically multi-valued string attributes on user resources rather than standalone objects. To enable graph-based analysis, we create `SCIM_Role` nodes to represent each unique role, allowing visibility into which users share the same role assignments across the organization.

## Properties

| Property | SCIM Property | Type | Description | Sample Value |
| --- | --- | --- | --- | --- |
| `id` | `User.roles` | `string` | The unique identifier of the role. | `8de4e0ea7370e4e60a521379c9edf3253afcba7660e647f3aa788e49e8993d1a` |
| `name` | `User.roles` | `string` | The name of the role. | `Sales` |

## Diagram

```mermaid
flowchart TD
    SCIM_Organization[fa:fa-building SCIM_Organization]
    SCIM_User[fa:fa-user SCIM_User]
    SCIM_Role[fa:fa-id-badge SCIM_Role]

    SCIM_Organization -->|SCIM_Contains| SCIM_Role
    SCIM_User -->|SCIM_HasRole| SCIM_Role
```

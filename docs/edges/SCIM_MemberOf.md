# SCIM_MemberOf

## Edge Schema

- Source: [SCIM_User](../node-descriptions/SCIM_User.md), [SCIM_Group](../node-descriptions/SCIM_Group.md)
- Destination: [SCIM_Group](../node-descriptions/SCIM_Group.md)

## General Information

The [SCIM_MemberOf](SCIM_MemberOf.md) edge represents group membership relationships, as defined by the `members` attribute of groups and the `groups` attribute of users in the SCIM schema. Users can be members of groups, and groups can be nested within other groups. Group membership propagated through SCIM is a primary mechanism for granting application access, making these edges critical for understanding transitive access paths.

```mermaid
graph LR
    node1("SCIM_User dschrute")
    node2("SCIM_Group Sales Team")
    node3("SCIM_Group All Employees")
    node1 -- SCIM_MemberOf --> node2
    node2 -- SCIM_MemberOf --> node3
```

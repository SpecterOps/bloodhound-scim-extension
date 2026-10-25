# SCIM_MembershipSync

## Edge Schema

The diagram shows the following directed membership-synchronization relationships:

| Source | Destination |
|--------|-------------|
| [Okta_Group] | [SCIM_Group] |
| [SCIM_Group] | [Okta_Group] |
| [AZGroup] | [SCIM_Group] |
| [SCIM_Group] | [AZGroup] |
| [SCIM_Group] | [GH_EnterpriseTeam](https://bloodhound.specterops.io/opengraph/extensions/github/nodes/gh_enterpriseteam) |

## General Information

The [SCIM_MembershipSync](SCIM_MembershipSync.md) edge represents a configured membership synchronization relationship in which group membership updates flow from the source group to the corresponding destination group through an intermediate [SCIM_Group] resource. Individual edges can point into or out of the SCIM group, following the direction of membership synchronization.

Some applications work with roles or teams instead of traditional groups, but the membership synchronization concept remains the same.

```mermaid
graph LR
    subgraph Okta Org 1
        node0("fa:fa-users Okta_Group Sales Team")
        node7("fa:fa-users Okta_Group Marketing Team")
    end
    subgraph SCIM Connector 1
        node1("fa:fa-users SCIM_Group Sales Team")
        node8("fa:fa-users SCIM_Group Marketing Team")
    end
    subgraph Okta Org 2
        node2("fa:fa-users Okta_Group Sales Team")
        node9("fa:fa-users Okta_Group Marketing Team")
    end
    node0 -- SCIM_MembershipSync --> node1
    node1 -- SCIM_MembershipSync --> node2
    node7 -- SCIM_MembershipSync --> node8
    node8 -- SCIM_MembershipSync --> node9
    subgraph SCIM Connector 2
        node3("fa:fa-users SCIM_Group Sales Team")
    end
    subgraph Entra ID
        node4("fa:fa-users AZGroup Sales Team")
    end
    node0 -- SCIM_MembershipSync --> node3
    node3 -- SCIM_MembershipSync --> node4
    subgraph SCIM Connector 3
        node5("fa:fa-users SCIM_Group Sales Team")
    end
    subgraph GitHub Enterprise
        node6("fa:fa-users GH_EnterpriseTeam Sales Team")
    end
    node0 -- SCIM_MembershipSync --> node5
    node5 -- SCIM_MembershipSync --> node6
```

[AZGroup]: https://bloodhound.specterops.io/resources/nodes/az-group
[Okta_Group]: https://bloodhound.specterops.io/opengraph/extensions/okta/nodes/okta_group
[SCIM_Group]: ../nodes/SCIM_Group.md

# SCIM_Provisioned

## Edge Schema

| Source | Destination |
|--------|-------------|
| [Okta_User] | [SCIM_User] |
| [SCIM_User] | [Okta_User] |
| [SCIM_User] | [GH_ExternalIdentity](https://bloodhound.specterops.io/opengraph/extensions/github/nodes/gh_externalidentity) |
| [SCIM_User] | `SNOW_User` |

## General Information

The [SCIM_Provisioned](SCIM_Provisioned.md) edge represents a configured provisioning relationship in which a source identity is provisioned to its corresponding destination identity through an intermediate SCIM resource. Individual edges can point into or out of the SCIM resource, following the direction of provisioning.

Provisioning alone does not establish an authentication or access path, nor does it imply password synchronization. Those synchronization relationships are represented by separate edge types.

```mermaid
graph LR
    subgraph Okta Org 1
        node7("fa:fa-user Okta_User dschrute")
    end

    subgraph SCIM Connector 1
        node1("fa:fa-user SCIM_User dschrute")
    end

    subgraph SCIM Connector 2
        node5("fa:fa-user SCIM_User dschrute")
    end

    subgraph SCIM Connector 3
        node6("fa:fa-user SCIM_User dschrute")
    end

    subgraph Okta Org 2
        node2("fa:fa-user Okta_User dschrute")
    end

    subgraph GitHub
        node3("fa:fa-user GH_ExternalIdentity dschrute")
    end

    subgraph ServiceNow
        node4("fa:fa-user SNOW_User dschrute")
    end

    node7 -- SCIM_PasswordSync --> node1
    node7 -- SCIM_PasswordSync --> node5
    node1 -- SCIM_PasswordSync --> node2
    node7 -.->|SCIM_Provisioned| node1
    node7 -.->|SCIM_Provisioned| node5
    node7 -.->|SCIM_Provisioned| node6
    node1 -.->|SCIM_Provisioned| node2
    node5 -.->|SCIM_Provisioned| node3
    node6 -.->|SCIM_Provisioned| node4
```

[Okta_User]: https://bloodhound.specterops.io/opengraph/extensions/okta/nodes/okta_user
[SCIM_User]: ../nodes/SCIM_User.md

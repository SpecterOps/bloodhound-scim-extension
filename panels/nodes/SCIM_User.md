# SCIM_User

## Description

A user account provisioned through SCIM. If enabled in source and target systems, password synchronization may be performed.

[Online documentation](https://bloodhound.specterops.io/opengraph/extensions/scim/nodes/scim_user)

## Hybrid Relationships

```gotmpl
{{ $objectID := .Properties.objectid | default "UnknownId" | replace "\\" "\\\\" | replace "'" "\\'" }}
```

```gotmpl
{{ $query_inbound := printf "MATCH p = (selected:SCIM_User {objectid: '%s'})<-[:SCIM_Provisioned|SCIM_PasswordSync]-()\nRETURN p\nLIMIT 500" $objectID }}
```

[Inbound](/ui/explore?exploreSearchTab=cypher&searchType=cypher&cypherSearch={{ $query_inbound | b64enc | urlquery }})

```gotmpl
{{ $query_outbound := printf "MATCH p = (selected:SCIM_User {objectid: '%s'})-[:SCIM_Provisioned|SCIM_PasswordSync]->()\nRETURN p\nLIMIT 500" $objectID }}
```

[Outbound](/ui/explore?exploreSearchTab=cypher&searchType=cypher&cypherSearch={{ $query_outbound | b64enc | urlquery }})

```gotmpl
{{ $query_both := printf "MATCH p = (selected:SCIM_User {objectid: '%s'})-[:SCIM_Provisioned|SCIM_PasswordSync]-()\nRETURN p\nLIMIT 500" $objectID }}
```

[Both](/ui/explore?exploreSearchTab=cypher&searchType=cypher&cypherSearch={{ $query_both | b64enc | urlquery }})

## Organization

```gotmpl
{{ $objectID := .Properties.objectid | default "UnknownId" | replace "\\" "\\\\" | replace "'" "\\'" }}
```

```gotmpl
{{ $query_group_memberships := printf "MATCH p = (selected:SCIM_User {objectid: '%s'})-[:SCIM_MemberOf*1..]->(group:SCIM_Group)\nRETURN p\nLIMIT 500" $objectID }}
```

[Group Memberships](/ui/explore?exploreSearchTab=cypher&searchType=cypher&cypherSearch={{ $query_group_memberships | b64enc | urlquery }})

```gotmpl
{{ $query_role_assignments := printf "MATCH p = (selected:SCIM_User {objectid: '%s'})-[:SCIM_HasRole]->(role:SCIM_Role)\nRETURN p\nLIMIT 500" $objectID }}
```

[Role Assignments](/ui/explore?exploreSearchTab=cypher&searchType=cypher&cypherSearch={{ $query_role_assignments | b64enc | urlquery }})

```gotmpl
{{ $query_manager := printf "MATCH p = (selected:SCIM_User {objectid: '%s'})<-[:SCIM_ManagerOf]-(manager:SCIM_User)\nRETURN p\nLIMIT 500" $objectID }}
```

[Manager](/ui/explore?exploreSearchTab=cypher&searchType=cypher&cypherSearch={{ $query_manager | b64enc | urlquery }})

```gotmpl
{{ $query_direct_reports := printf "MATCH p = (selected:SCIM_User {objectid: '%s'})-[:SCIM_ManagerOf]->(report:SCIM_User)\nRETURN p\nLIMIT 500" $objectID }}
```

[Direct Reports](/ui/explore?exploreSearchTab=cypher&searchType=cypher&cypherSearch={{ $query_direct_reports | b64enc | urlquery }})

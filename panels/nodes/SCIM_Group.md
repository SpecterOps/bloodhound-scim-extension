# SCIM_Group

## Description

A group provisioned through SCIM. Users and nested groups can be members. Configured membership synchronization propagates membership changes to linked groups, teams, or roles in other systems.

[Online documentation](https://bloodhound.specterops.io/opengraph/extensions/scim/nodes/scim_group)

## Hybrid Relationships

```gotmpl
{{ $objectID := .Properties.objectid | default "UnknownId" | replace "\\" "\\\\" | replace "'" "\\'" }}
```

```gotmpl
{{ $query_inbound := printf "MATCH p = (selected:SCIM_Group {objectid: '%s'})<-[:SCIM_MembershipSync]-()\nRETURN p\nLIMIT 500" $objectID }}
```

[Inbound](/ui/explore?exploreSearchTab=cypher&searchType=cypher&cypherSearch={{ $query_inbound | b64enc | urlquery }})

```gotmpl
{{ $query_outbound := printf "MATCH p = (selected:SCIM_Group {objectid: '%s'})-[:SCIM_MembershipSync]->()\nRETURN p\nLIMIT 500" $objectID }}
```

[Outbound](/ui/explore?exploreSearchTab=cypher&searchType=cypher&cypherSearch={{ $query_outbound | b64enc | urlquery }})

```gotmpl
{{ $query_both := printf "MATCH p = (selected:SCIM_Group {objectid: '%s'})-[:SCIM_MembershipSync]-()\nRETURN p\nLIMIT 500" $objectID }}
```

[Both](/ui/explore?exploreSearchTab=cypher&searchType=cypher&cypherSearch={{ $query_both | b64enc | urlquery }})

## Members

```gotmpl
{{ $objectID := .Properties.objectid | default "UnknownId" | replace "\\" "\\\\" | replace "'" "\\'" }}
```

```gotmpl
{{ $query_members := printf "MATCH p = (member)-[:SCIM_MemberOf*1..]->(selected:SCIM_Group {objectid: '%s'})\nWHERE member:SCIM_User OR member:SCIM_Group\nRETURN p\nLIMIT 500" $objectID }}
```

[Members](/ui/explore?exploreSearchTab=cypher&searchType=cypher&cypherSearch={{ $query_members | b64enc | urlquery }})

```gotmpl
{{ $query_member_of := printf "MATCH p = (selected:SCIM_Group {objectid: '%s'})-[:SCIM_MemberOf*1..]->(group:SCIM_Group)\nRETURN p\nLIMIT 500" $objectID }}
```

[Member Of](/ui/explore?exploreSearchTab=cypher&searchType=cypher&cypherSearch={{ $query_member_of | b64enc | urlquery }})

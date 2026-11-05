# SCIM_Organization

## Description

An identity provider organization or tenant whose users, groups, and/or role assignments are synchronized through SCIM. It provides the ownership boundary for those resources.

[Online documentation](https://bloodhound.specterops.io/opengraph/extensions/scim/nodes/scim_organization)

## Hybrid Relationships

```gotmpl
{{ $objectID := .Properties.objectid | default "UnknownId" | replace "\\" "\\\\" | replace "'" "\\'" }}
```

```gotmpl
{{ $query_inbound := printf "MATCH p = (selected:SCIM_Organization {objectid: '%s'})<-[:SCIM_Provisioned]-()\nRETURN p\nLIMIT 500" $objectID }}
```

[Inbound](/ui/explore?exploreSearchTab=cypher&searchType=cypher&cypherSearch={{ $query_inbound | b64enc | urlquery }})

```gotmpl
{{ $query_outbound := printf "MATCH p = (selected:SCIM_Organization {objectid: '%s'})-[:SCIM_Provisioned]->()\nRETURN p\nLIMIT 500" $objectID }}
```

[Outbound](/ui/explore?exploreSearchTab=cypher&searchType=cypher&cypherSearch={{ $query_outbound | b64enc | urlquery }})

```gotmpl
{{ $query_both := printf "MATCH p = (selected:SCIM_Organization {objectid: '%s'})-[:SCIM_Provisioned]-()\nRETURN p\nLIMIT 500" $objectID }}
```

[Both](/ui/explore?exploreSearchTab=cypher&searchType=cypher&cypherSearch={{ $query_both | b64enc | urlquery }})

## Contained Resources

```gotmpl
{{ $objectID := .Properties.objectid | default "UnknownId" | replace "\\" "\\\\" | replace "'" "\\'" }}
```

```gotmpl
{{ $query_users := printf "MATCH p = (selected:SCIM_Organization {objectid: '%s'})-[:SCIM_Contains]->(resource:SCIM_User)\nRETURN p\nLIMIT 500" $objectID }}
```

[Users](/ui/explore?exploreSearchTab=cypher&searchType=cypher&cypherSearch={{ $query_users | b64enc | urlquery }})

```gotmpl
{{ $query_groups := printf "MATCH p = (selected:SCIM_Organization {objectid: '%s'})-[:SCIM_Contains]->(resource:SCIM_Group)\nRETURN p\nLIMIT 500" $objectID }}
```

[Groups](/ui/explore?exploreSearchTab=cypher&searchType=cypher&cypherSearch={{ $query_groups | b64enc | urlquery }})

```gotmpl
{{ $query_roles := printf "MATCH p = (selected:SCIM_Organization {objectid: '%s'})-[:SCIM_Contains]->(resource:SCIM_Role)\nRETURN p\nLIMIT 500" $objectID }}
```

[Roles](/ui/explore?exploreSearchTab=cypher&searchType=cypher&cypherSearch={{ $query_roles | b64enc | urlquery }})

```gotmpl
{{ $query_all := printf "MATCH p = (selected:SCIM_Organization {objectid: '%s'})-[:SCIM_Contains]->(resource:SCIM)\nRETURN p\nLIMIT 500" $objectID }}
```

[Any](/ui/explore?exploreSearchTab=cypher&searchType=cypher&cypherSearch={{ $query_all | b64enc | urlquery }})

# SCIM_Role

## Description

A role derived from the roles attribute of SCIM users, rather than a standalone SCIM resource.

[Online documentation](https://bloodhound.specterops.io/opengraph/extensions/scim/nodes/scim_role)

## Relationships

```gotmpl
{{ $objectID := .Properties.objectid | default "UnknownId" | replace "\\" "\\\\" | replace "'" "\\'" }}
```

```gotmpl
{{ $query_containing_organization := printf "MATCH p = (organization:SCIM_Organization)-[:SCIM_Contains]->(selected:SCIM_Role {objectid: '%s'})\nRETURN p\nLIMIT 500" $objectID }}
```

[Containing Organization](/ui/explore?exploreSearchTab=cypher&searchType=cypher&cypherSearch={{ $query_containing_organization | b64enc | urlquery }})

```gotmpl
{{ $query_assigned_users := printf "MATCH p = (user:SCIM_User)-[:SCIM_HasRole]->(selected:SCIM_Role {objectid: '%s'})\nRETURN p\nLIMIT 500" $objectID }}
```

[Assigned Users](/ui/explore?exploreSearchTab=cypher&searchType=cypher&cypherSearch={{ $query_assigned_users | b64enc | urlquery }})

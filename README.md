# BloodHound SCIM Schema Extension

**[System for Cross-domain Identity Management (SCIM)](https://scim.cloud/) schema extension for BloodHound**

[![Applies to BloodHound Enterprise and CE](https://mintlify.s3.us-west-1.amazonaws.com/specterops/assets/enterprise-AND-community-edition-pill-tag.svg)](#)

## Overview

The SCIM protocol is used by various cloud identity providers (IdPs), such as Okta or Entra ID,
to provision user accounts and groups to/from applications.

This schema extension allows BloodHound to represent SCIM-provisioned users and groups as nodes in the graph,
avoiding the need to introduce technology-specific edges for each integration, such as Okta+GitHub, Entra+GitHub, or Entra+SalesForce.

![SCIM_Users of a SCIM_Group combined to a GH_EnterpriseTeam](/docs/images/scim-example.png)

## Documentation

For full documentation, see the [BloodHound Docs](https://bloodhound.specterops.io/opengraph/extensions/scim/).
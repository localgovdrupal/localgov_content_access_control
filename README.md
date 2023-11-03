# LocalGov Content Access Control

This module adds access control to your LGD site sections, which allows you to restrict editing/publishing/etc actions to subsets of users.

It uses the workbench_access module as its base.

## New role - Devolved Editor

With this module we are introducing a new role to LocalGov Drupal: "Devolved Editor". This is a role we can use to allow a subset of editors (perhaps people from outside of our organisation) to create/edit only a small amount of content. By default they can create news, events, service pages and can edit existing subsite overview and service landing pages, but not create new ones.

## How to use this
### Install this module
Firstly, install this module. This will install the workbench and workbench_access modules as well.

### Set up your access control taxonomy
Following that, you will have a new vocabulary called "Access Control". You can set as many taxonomy terms in here as you wish. Each one will be equivalent to a site section that a subset of users can edit. This vocabulary, like all in Drupal, is hierarchical. What this means for content access is that if you are added to a parent term, you automatically get access/edit rights to all of its child terms.

Let's the the following as a sample taxonomy:

```
- Adult social care and health
- Children, young people and families
- - Children and young people
- - Social care
- - Adoption
- - Fostering
- - Health and wellbeing
- Schools and learning
- - School Admissions
- - Early years and child care
- - Post-16 options
- - Adult learning
- Jobs and apprenticeships
- News
- Events
```

In the above scenario, if an editor is tagged with "Children, young people and families" then they can also edit "Social care", "Adoption", "Fostering", etc. However, if someone is tagged with "Fostering" only, they cannot edit "Adoption", "Social care" etc.

### Add "Access Control" field to content types

By default, we have added the "Access Control" field to Subsite Overview, Subsite Page, Service Landing Page, and Service Page content types. **Note**: make sure to go to the "Manage form display" page for these content types to make the field visible to editors.

If there are other content types you want to add it to you can follow the same pattern we have for the items above.

### Add editors to site sections

Finally, you can go to the workbench access settings to define which users are assigned to which site sections. This can be found at `/admin/config/workflow/workbench_access`. We have created one "Scenario" called "Site Section" which uses the "Access Control" taxonomy. You can add more scenarios if you need them (you probably won't).

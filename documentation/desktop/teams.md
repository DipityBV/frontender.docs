---
currentMenu: desktop_teams
---

# Teams
<!-- @TODO verify -->
Teams are used to set the permissions of one or multiple users.

Every space must have 1 group, as group is a required value on a page.

Groups can be assigned to pages. If you want a group of users to control your `Blog` pages you can create a group that only has access to `Blog` pages. The users in this group will not be able to see/edit any other pages.

Groups are always nested recursively.  
In the following example `Group A` is the main group. `Group C` is a child of `Group B`.
If I assign `Group C` to a page, all parent groups(`Group B` & `Group A`) will also have access to said page.

```bash
.
└── Group A
    ├── Group B
    │   └── Group C
    └── Group D
```

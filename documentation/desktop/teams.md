---
currentMenu: desktop_teams
---

# Teams

Teams are used to set the permissions of one or multiple users.

Every space will have 1 default team called "Site".
Every space must have 1 team, as team is a required value on a page.

Teams can be assigned to pages. If you want a team of users to control your `Blog` pages you can create a team that only has access to `Blog` pages. The users in this group will not be able to see/edit any other pages.

Teams are always nested recursively.  
In the following example `Group A` is the main group. `Group C` is a child of `Group B`.
If I assign `Group C` to a page, all parent teams(`Group B` & `Group A`) will also have access to said page.

```bash
.
└── Group A
    ├── Group B
    │   └── Group C
    └── Group D
```

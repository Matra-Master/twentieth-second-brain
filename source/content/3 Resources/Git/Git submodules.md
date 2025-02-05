20220624-1122
Status: #fleeting

Tags: [[Git]]

# Git submodules
A submodule is a repo inside a repo. This is the answer to "i want to use a part of my repo in another branch without changing the rest of my repo to the other one". You just make it a whole new Repo and import it as a submodule

	$ git submodule add git@mygitrepos/module-repo

You can clone the main repo and also the submodules automatically

	$ git clone --recurse-submodules git@mygitrepos/main-repo

**To update a submodule** you can go into the submodule folder, fetch and merge. Or you can use this line and make it simple :D

	$ git submodule update --remote module-repo

---
# References
[Git Submodules](https://git-scm.com/book/en/v2/Git-Tools-Submodules)
Contribution guide
---

Below are the guidelines to be followed for all PRs, as well as some explanation on why they are enforced.

### 0. Scope

These guidelines are applicable, and must be followed for:

- Any ansible role part of OpenIO SDS or related components (Monitoring, OIOFS....).
- The official customer and community playbook repositories.

### 1. Commit format

```
[TYPE]([SCOPE]): [TITLE]

 ##### SUMMARY
[SUMMARY]

 ##### IMPACT
[IMPACT]

 ##### ADDITIONAL INFORMATION
[ADDITIONAL_INFO]
```

| field           | value                                                                                                                  | required    |
| --------------- | ---------------------------------------------------------------------------------------------------------------------- | ----------- |
| TYPE            | CHANGE FEATURE BUGFIX/[SEVERITY] TEST REFACTOR TRIVIAL                                                                 | YES         |
| SCOPE           | SDS OIOFS OIOFS_HA [COMPONENT]                                                                                         | YES         |
| SEVERITY        | MINOR MEDIUM MAJOR                                                                                                     | BUGFIX ONLY |
| COMPONENT       | only for roles: role name ; use the other values otherwise                                                             | YES         |
| TITLE           | commit title                                                                                                           | YES         |
| SUMMARY         | describe what the commit does, why it is necessary, and how to use it                                                  | YES         |
| IMPACT          | if the change has an impact on previous versions that can break compatibility, explain it here. therwise, set to "N/A" | YES (N/A)   |
| ADDITIONAL_INFO | Any additional informartion that doesn't belong in other fields                                                        | NO          |

#### Example:

```
BUGFIX/MAJOR(component): Fix an issue

 ##### SUMMARY

Lorem ipsum dolor sit amet, consectetur adipiscing elit. In quis molestie quam. Morbi at pharetra ipsum. Sed ut diam a nisi efficitur venenatis ut eget velit. Vivamus eget euismod nisi. Integer ut est nibh. In finibus velit erat, non porta dui accumsan eu.

 ##### IMPACT

N/A

 ##### ADDITIONAL INFORMATION

Aliquam in velit commodo, rutrum eros ut, condimentum nulla. Praesent tempus mi in nisi tempor posuere. Suspendisse in imperdiet justo
```

### 2. Commits and pull requests

A pull request can have multiple commits. PR text is irrelevant long term, only the commit message matters. This allows to stay independant from GitHub, and simplifies the auto-generation of release information.

Every commit should have one theme, described by the commit format. Additional commits related to the same theme on the same PR must be squashed into a single commit.

### 3. Branches

It is highly recommended (although not enforced) to name each branch accordingly to the change made. E.g. a change that aims to fix an issue must be `fix-[issue_name]`. After the pull request is merged, the branch can be removed by the user.

### 4. Tests

It is recommended when adding a new feature, to add tests corresponding to that particular feature in the docker-tests branch. This will help with the review of the PR in confirming the impact of the change.

### 5. Git hook

You can use the following githook:

```
#TITLE
#CHANGE/FEATURE/BUGFIX/TEST/REFACTOR(SCOPE): Title
#SCOPE: SDS / OIOFS / OIOFS_HA / role
#Example:
#CHANGE(rawx): Move run directory from /run/rawx to /run/oio/sds
#BUGFIX/MAJOR(haproxy): FOOO
#FEATURE(rawx): plop
#TRIVIAL(keystone): Lint...


 ##### SUMMARY
#Describe the change below
#HINT: Include "Fixes #nnn" if you are fixing an existing issue

#Currently, the problem is ..., with this PR ...

 ##### IMPACT
#Describe the impact of the change (N/A for no impact)
#N/A

 ##### ADDITIONAL INFORMATION
#Include additional information to help people understand the change here
#A step-by-step reproduction of the problem is helpful if there is no related issue
#Paste verbatim command output below, e.g. before and after your change
```

# workflows


I created this repo for testing workflow paths and branches triggers, since the documentation was lacking.
Here's what I found:

- *branches* and *paths* trigger conditions are evaluated conjunctively (logical AND). 
For example:
```yaml
on:
  push:
    paths:
      - A.txt
    branches:
      - master
```
will only be triggered if A.txt is modified in the master branch. If you need it to run when either the branch is master or the path is A.txt, you will need to duplicate the workflow file and have a *branches* condition in one of them and *paths*
 in the other. 
- *paths* should be absolute
E.g "A.txt" works but "./A.txt" doesn't

- Changing a workflow won't necessarily trigger it. You fix that by including it in its own *paths*


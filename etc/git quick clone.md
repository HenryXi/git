# git quick clone
It takes long time to clone a particularly large git repository. Use the following command to help you quickly clone a git
 repository.
```
git clone --depth 1 YOUR_GIT_REPOSITORY
```
The "depth" parameter is used to specify the depth of the clone. This value must be greater than 0. `--depth 1` means 
only clone the repository containing the most recent commit record. 

EOF
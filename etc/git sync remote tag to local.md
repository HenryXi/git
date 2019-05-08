# git sync remote tag to local
I want sync remote tags to local. After google I got some commends. Unfortunately, those commands sometimes work and 
sometimes don't work. I think this may be related to the environment and the version of git. Eventually I finally found 
a universal solution.
```bash
git tag -d $(git tag)   # delete all local tags
git fetch --all         # fetch all remote to local
```

EOF
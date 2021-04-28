# git delete remote file
I push my project to remote but I forget add `.gitignore` file. I use these commands to delete remote file(`.idea` and `target`).

```
git rm -r .idea
git commit -m 'remove .idea'
git push origin master
```

EOF
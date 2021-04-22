# git auto push when commit
Add following function in your `~/.bashrc` file then you can use one command to commit changes and push them to remote.
```
gcp ()
{
    if [ ! $1 ]; then
        $1='this is auto commit'
    fi
    git add -A && git commit -m "$1" && git push
}
```
use `gcp "YOUR_COMMIT_MESSAGE"` command to commit changes and push them to remote.

EOF
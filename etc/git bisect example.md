# git bisect example
Before starting to learn this command, we need to initialize a git directory. The following script can help us initialize a git repository with 20 commits
```
#!/bin/bash
git init
touch file1
git add . 
git commit -m '1 commit'
touch file2
git add . 
git commit -m '2 commit'
touch file3
git add . 
git commit -m '3 commit'
touch file4
git add . 
git commit -m '4 commit'
touch file5
git add . 
git commit -m '5 commit'
touch file6
git add . 
git commit -m '6 commit'
touch file7
git add . 
git commit -m '7 commit'
touch file8
git add . 
git commit -m '8 commit'
touch file9
git add . 
git commit -m '9 commit'
touch file10
git add . 
git commit -m '10 commit'
touch file11
git add . 
git commit -m '11 commit'
touch file12
git add . 
git commit -m '12 commit'
touch file13
git add . 
git commit -m '13 commit'
touch file14
git add . 
git commit -m '14 commit'
touch file15
git add . 
git commit -m '15 commit'
touch file16
git add . 
git commit -m '16 commit'
touch file17
git add . 
git commit -m '17 commit'
touch file18
git add . 
git commit -m '18 commit'
touch file19
git add . 
git commit -m '19 commit'
touch file20
git add . 
git commit -m '20 commit'
```
Let's show commit log.
```
[root@second_computer example]# git log --oneline
40eb485 20 commit
c6460e2 19 commit
84a1277 18 commit
9aea7bf 17 commit
429dfb5 16 commit
c226e33 15 commit
ba787f2 14 commit
51661d5 13 commit
dd2f375 12 commit
5eee1b3 11 commit
880e45f 10 commit
25ab8cf 9 commit
c14ac95 8 commit
f3c8f39 7 commit
3e8c17f 6 commit
188df4d 5 commit
8d14d91 4 commit
1004aba 3 commit
3c1253d 2 commit
f177529 1 commit
```
Let's say you want to find when `file7` add in the repository. Use `bisect` like following.

`file7` exist is bad and not exist is good. We found that it was introduced in the 7th submission.
```
[root@second_computer example]# git bisect start HEAD f177529
Bisecting: 9 revisions left to test after this (roughly 3 steps)
[880e45f18ae59a9a588e20c05a4d8285381ab993] 10 commit
[root@second_computer example]# ll
total 0
-rw-r--r--. 1 root root 0 May 21 08:13 file1
-rw-r--r--. 1 root root 0 May 21 08:13 file10
-rw-r--r--. 1 root root 0 May 21 08:13 file2
-rw-r--r--. 1 root root 0 May 21 08:13 file3
-rw-r--r--. 1 root root 0 May 21 08:13 file4
-rw-r--r--. 1 root root 0 May 21 08:13 file5
-rw-r--r--. 1 root root 0 May 21 08:13 file6
-rw-r--r--. 1 root root 0 May 21 08:13 file7
-rw-r--r--. 1 root root 0 May 21 08:13 file8
-rw-r--r--. 1 root root 0 May 21 08:13 file9
[root@second_computer example]# git bisect bad
Bisecting: 4 revisions left to test after this (roughly 2 steps)
[188df4d4b185838ff0526f83248467ed28c454d9] 5 commit
[root@second_computer example]# ll
total 0
-rw-r--r--. 1 root root 0 May 21 08:13 file1
-rw-r--r--. 1 root root 0 May 21 08:13 file2
-rw-r--r--. 1 root root 0 May 21 08:13 file3
-rw-r--r--. 1 root root 0 May 21 08:13 file4
-rw-r--r--. 1 root root 0 May 21 08:13 file5
[root@second_computer example]# git bisect good
Bisecting: 2 revisions left to test after this (roughly 1 step)
[f3c8f39fcd3852ce47110834513e26cb2a190eb1] 7 commit
[root@second_computer example]# ll
total 0
-rw-r--r--. 1 root root 0 May 21 08:13 file1
-rw-r--r--. 1 root root 0 May 21 08:13 file2
-rw-r--r--. 1 root root 0 May 21 08:13 file3
-rw-r--r--. 1 root root 0 May 21 08:13 file4
-rw-r--r--. 1 root root 0 May 21 08:13 file5
-rw-r--r--. 1 root root 0 May 21 08:21 file6
-rw-r--r--. 1 root root 0 May 21 08:21 file7
[root@second_computer example]# git bisect bad
Bisecting: 0 revisions left to test after this (roughly 0 steps)
[3e8c17fd271aa6b996a1ab825df614fd8df6be03] 6 commit
[root@second_computer example]# ll
total 0
-rw-r--r--. 1 root root 0 May 21 08:13 file1
-rw-r--r--. 1 root root 0 May 21 08:13 file2
-rw-r--r--. 1 root root 0 May 21 08:13 file3
-rw-r--r--. 1 root root 0 May 21 08:13 file4
-rw-r--r--. 1 root root 0 May 21 08:13 file5
-rw-r--r--. 1 root root 0 May 21 08:21 file6
[root@second_computer example]# git bisect good
f3c8f39fcd3852ce47110834513e26cb2a190eb1 is the first bad commit
commit f3c8f39fcd3852ce47110834513e26cb2a190eb1
Author: root <root@second_computer.localdomain>
Date:   Thu May 21 08:13:22 2020 -0400

    7 commit

:000000 100644 0000000000000000000000000000000000000000 e69de29bb2d1d6434b8b29ae775ad8c2e48c5391 A	file7
```

EOF
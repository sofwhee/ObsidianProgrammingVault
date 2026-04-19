#Git 

1. Make a new repo on github.com
2. git init
3. git add .
4. git commit -m "first commit"
5. git branch -M main
6. git remote add origin https://github.com/sofwhee/name-of-repo.git
7. git push -u origin main

## Upload a local repo (CLI)

1. Root directory
2. git init
3. git add .
4. git commit -m "first commit"
5. gh repo create
6. "Push an existing local repository to github"
## Upload a local repo (Git)

1. New repo on github site. No readme/license/gitignores.
2. Copy SSH
3. Root directory
4. git init
5. git add .
6. git commit -m "first commit"
7. git remote add origin (paste SSH)
8. git remote -v (to verify)
9. git push origin main

## Cloning a repo

1. copy SSH from repo
2. `git clone <url>`
# Git



## Questions

-  Git Chery Pick
-  Git Merge withNVIM
-  Git take --their --our

-  Git stash
-  Just storage of file archiving?

## Git delete branch from server

`git push origin --delete Ivan`

## Git gc and archive
Remove unecessary files

`git gc`
`git archive -o latest.zip HEAD`

## Cherry-pck
 
Apply changes introduces by other commit.

## HEAD 

- `HEAD` - Last commit
- `HEAD^^` - two commits ago
- `main~2` - on branch main 2 commit ago

## Restore 

`git restore Readme.md`
`git restore ONe.md --source  d798773f78cf0f3a5430348ae5077723b474e8ec`
`git restore --source main~2 Readme.md`

Restores file from current index or from specific commit
Or Roll back it's content to the state needed

## Stash
It sort of like reset but changes **stashed**
Files basically saying unding changes that was git add

 
## Diff 

```PowerShell
git diff HEAD^
git diff HEAD^^ HEAD^
git diff HEAD COMMIT_ADDRESS
```

## Submodule
The power to add submodule so it will pop up in project
But will be tracked separetly

## Git log

```powershell
git log --follow Readme.md
```

## Add to GIT LFS

```powershell
#file name
git lfs track 'ADDRESS\TO\FILE.type'

```

## Pus local branch to server

```powershell
git branch -u origin <branch name>
```

## Remvoe locak branch

```powershell
git branch -d <branch name>
```

# Remove file from history

```bash
git rm "Assets\External\1PumpkinExport\CorryMarryXmas.anim"
    git filter-branch --force --index-filter 'git rm --cached --ignore-unmatch Assets\External\1PumpkinExport\CorryMarryXmas.anim' --prune-empty --tag-name-filter cat -- --all
```


## SSH

```powershell
ls -al ~/.ssh
# Check is there any files already
```
### Generate

```powershell
ls -al ~/.ssh
$ ssh-keygen -t ed25519 -C "yuriy.paramonov@outlook.com"
# Check is there any files already
```
## Submodule Subdirectory 

### Submodule

Every time I try to subrepository to my repo I got this shit:

```
warning: adding embedded git repository: Submodule
hint: You've added another git repository inside your current repository.
hint: Clones of the outer repository will not contain the contents of
hint: the embedded repository and will not know how to obtain it.
hint: If you meant to add a submodule, use:
hint:
hint:   git submodule add <url> Submodule
hint:
hint: If you added this path by mistake, you can remove it from the
hint: index with:
hint:
hint:   git rm --cached Submodule
hint:
hint: See "git help submodule" for more information.
```

`git rm --cached Submodule` - Is key to fix this shit


## Cherypick


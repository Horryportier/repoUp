# guiUp

simple tool to to update github repos.

## Installation: 
you need  to donwland **charmbraclect** [gum](https://github.com/charmbracelet/gum) that you need to donwland.
```bash 
git clone https://github.com/Horryportier/gitUp
cd gitUp
chmod +x gitUp
cp gitUp ~/.local/bin
```
        
## How to Use
run {gitup} inside of repo to update it

## Flags:
-h | --help for help
-a | --all to update all
-l | --list to choose from list
-d | --daily updates repos in daily list

## Adding repos

open script and add new item to the list 

```bash
repos[last index]="path/to/your/repo"
```
for repos that are update periodycli (chorn tab, startup app,etc...) add to this list
```bash
autoUpdate[last index]="path/to/your/repo"


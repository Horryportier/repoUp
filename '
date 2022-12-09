#! /bin/bash

msg="$(date)"

help=$(echo -e "# How to Use\n\n ___\n-h | --help for help\n-a | --all to update all\n-l | --list to choose from list\n-d | --daily updates repos in daily list"\
        | gum format -t markdown)

list=""




repos=()

# put your paths to yours repos here
repos[0]="/home/$(whoami)/Documents/CheatSheet"
repos[1]="/home/$(whoami)/Documents/dotfiles"
repos[2]="/home/$(whoami)/Documents/update_repos"


autoUpdate=()

# put your paths to yours repos that you want to update on schedule here
autoUpdate[0]="${repos[0]}"
autoUpdate[1]="${repos[1]}"


printStyle() {
        style=$(gum style --padding "1 5" --border double --border-foreground 249 "$1")
        if [[ -n "$style" ]]; then 
        echo -e "$style"
        fi
}

pull(){
        printStyle "$(git pull)"
}

push(){
        if [[ -z "$msg" ]]; then
                msg=$(date)
        fi
        git add .
        val="$(git commit -m "$msg")"
        printStyle "$val"
        val="$(echo $(git push origin main))"
}


all() {
        for i in "${repos[@]}"; do
                echo -e "\033[1;32m$i\033[0m"
                cd "$i"
                pull
                push
        done
}
auto() {
        for i in "${autoUpdate[@]}"; do
                echo -e "\033[1;32m$i\033[0m"
                cd "$i"
                pull
                push
        done
}




choose() {
        list=$(gum choose --no-limit ${repos[@]})
        readarray -t items <<< "$list"
        for i in "${items[@]}"; do
                echo -e "\033[1;32m$i\033[0m"
                msg=$(gum input --placeholder "commit msg")
                cd "$i"
                pull
                push
        done
}

while [[ "$1" =~ ^- && ! "$1" == "--" ]]; do case $1 in
-a | --all )
        all
        exit
        ;;
-h | --help )
        echo -e $help
        exit
        ;;
-l | --list )
        choose
        exit
        ;;
-d | --daily )
        auto
        exit
        ;;
esac; shift; done
if [[ "$1" == '--' ]]; then shift; fi

printStyle "$help"
exit


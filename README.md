# git_helpers
This repository contains some helpful commands for using Git from the terminal, more proficiently.

## Bash Commands

Below are Bash aliases and functions that can be added to your ``~/.bash_profile`` file, should you be using the Bash shell.

\# Alias gs to run the command git status faster   
```alias gs='git status'```   
\# Alias gp to run the command git push faster   
```alias gp='git push'```   
\# Alias gpu to run the command git pull faster   
```alias gp='git pull'```   
\# Alias ga to run the command git add . faster   
```alias ga='git add .'```   

\# This function runs the ``git status`` command first and then asks if user wants to add all, commit and push   
\# Use it from the terminal like this: ``gf "your commit message"``, like: ``gf "change template.py"``
```
function gf() {
  git status
  if [ $# -eq 0 ]
  then
    echo "First argument should be the commit message. Exiting...";
    return;
  fi
  read -p "Press Y/y to commit and push: " choice
  if [[ $choice == "Y" || $choice == "y" ]]; then
    git add .
    git commit -m "$1"
    git push
  else
    echo
    echo "No commit and push made. Exiting..."
  fi
}
```


## ZSH commands

ZSH shell aliases and functions that can be added to your ``~/.zshrc`` file, should you be using the ZSH shell (like with MacOS).

\# Alias gs to run the command git status faster   
```alias gs='git status'```   
\# Alias gp to run the command git push faster   
```alias gp='git push'```   
\# Alias gpu to run the command git pull faster   
```alias gp='git pull'```   
\# Alias ga to run the command git add . faster   
```alias ga='git add .'```   

\# This function runs the ``git status`` command first and then asks if user wants to add all, commit and push   
\# Use it from the terminal like this: ``gf "your commit message"``, like: ``gf "change template.py"``
```
setopt PROMPT_SUBST
function gf() {
git status
if [ $# -eq 0 ]
   then
      echo "First argument should be the commit message. Exiting...";
      return;
fi
if read -q "choice?Press Y/y to commit and push: "; then
     git add .
     git commit -m "$1"
     git push
     #git add . &&
     #git commit -m "$1" &&
     #git push &&
else
     echo
     echo "No commit and push made. Exiting..."
fi
}
```

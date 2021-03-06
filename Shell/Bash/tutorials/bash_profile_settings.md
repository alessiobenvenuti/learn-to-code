# Bash profile settings

Here are some recommended settings for bash console.

If you want to test something temporarily for the terminal session, you can run it directly.

e.g. `PS1="\u \$ "` or `export PS1="\u \$ "`

If you want to preview colours, you can do the following in the console.
```
# Red
$ echo -e "\033[0;31m$(ls)"
# White
$ echo -e "\033[0m$(ls)"

$ YELLOW="\033[0;33m"
echo -e "$YELLOW$(date)"
```

If you'd like settings be loaded on all new terminal sessions, then add them to your `~/.bashrc` file.

## Command prompt decoration

A user value on Ubuntu, from `echo $PS1`. (If you use single quotes then you don't have to escape the outside hard brackets or dollar sign).

```bash
PS1='[\u@\[\033[1;41m\]\h\[\033[0m\]:\W]$ '
```

A user value on Debian, from `echo $PS1`. This keeps a space between optional virtualenv and username. Change the `w` to uppercase if you want the shorter version.

```bash
PS1="\[\e]0;\u@\h: \w\a\]${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ "
```

The root user's value on Debian, from `/etc/bash.bashrc` file.

```bash
# set a fancy prompt (non-color, overwrite the one in /etc/profile)
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
```

Settings I found on PythonAnywhere's user `.bashrc` file.

```bash
# Show current git branch in prompt.
function parse_git_branch {
  git branch --no-color 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/(\1)/'
}
# Set colour variables. Note outside '[' and ']' chars are escaped to be literal.
RED="\[\033[0;31m\]"
YELLOW="\[\033[0;33m\]"
GREEN="\[\033[0;32m\]"
LIGHT_GREEN="\[\033[1;32m\]"
LIGHT_GRAY="\[\033[0;37m\]"

# Set date and git branch in prompt.
PS1="$LIGHT_GRAY\$(date +%H:%M) \w$YELLOW \$(parse_git_branch)$LIGHT_GREEN\$ $LIGHT_GRAY"
```

Alternative from this article: www.railstips.org/blog/archives/2009/02/02/bedazzle-your-bash-prompt-with-git-info/

```bash
function parse_git_branch {
  ref=$(git-symbolic-ref HEAD 2> /dev/null) || return
  echo "("${ref#refs/heads/}")"
}

RED="\[\033[0;31m\]"
YELLOW="\[\033[0;33m\]"
GREEN="\[\033[0;32m\]"

PS1="$RED\$(date +%H:%M) \w$YELLOW \$(parse_git_branch)$GREEN\$ "
```

My preferred style, combined from a few above.

```bash
# Show current git branch in prompt.
function parse_git_branch {
  git branch --no-color 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/(\1)/'
}
# Use blue (1st) or red (2nd) for hostname background colour, with bold text.
BLOCK="\[\033[1;44m\]"
#BLOCK="\[\033[1;41m\]"

YELLOW="\[\033[0;33m\]"
GREEN="\[\033[0;32m\]"
WHITE="\[\033[0m\]"
PS1="\$(date +%H:%M) [\u@$BLOCK\h$WHITE:\W]$YELLOW \$(parse_git_branch)$GREEN\$ $WHITE"
```

Note that `\W` is for the last part of current working directory and that a lowercase `\w` will give the full path.

The double quotes need to be used on the last line above instead of single quotes, so that colour can be substituted in with $. But then symbols need to be escaped - in this case only dollar signs since hard brackets are handled in colour variables. If a $ is not escaped, the value is calculated immediately and is not dynamic - in particular, the date will become frozen as time of starting the console.

I found that the _hard brackets_ before username and after working directory did need to be escaped as they will be shown explictly. And if they are escaped, then unfortunatey, the commands cut into the prompt on the left when scrolling through history of commands with keyword arrows.


## Other

The following are other useful areas from PythonAnyhwere.com's configuration.

```bash
# Load up standard site-wide settings (choose one depending on your system).
source /etc/bashrc
source /etc/bash.bashrc
```

```bash
# Remove duplicate entries from history.
export HISTCONTROL=ignoreboth
```

```bash
# Load virtualenvwrapper - this might be necessary if you this.
source virtualenvwrapper.sh &> /dev/null
```

---
title: Bash
date: Last Modified 
permalink: /bash.html
eleventyNavigation:
  key: bash
  title: bash
---

* Edit variable in loop and persist outside
  Don't use pipes, those cause subshells:
  ```bash
  counter=0
  while read -r line
  do
    counter=((counter+1))
  done <<< "${multiLineThing}
  echo "Count: ${counter}"
  ```

* Set terminal title to current running command in ~/.bashrc
  ```bash
  ###########################################################################
  #         BEGIN SET TERMINAL TITLE AS CURRENT RUNNING COMMAND             #
  ###########################################################################
  # If this is an xterm set the title to user@host:dir
  case "$TERM" in
  xterm*|rxvt*)
      PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD}\007"'
  
      # Show the currently running command in the terminal title:
      # http://www.davidpashley.com/articles/xterm-titles-with-bash.html
      show_command_in_title_bar()
      {
          case "$BASH_COMMAND" in
              *\033]0*)
                  # The command is trying to set the title bar as well;
                  # this is most likely the execution of $PROMPT_COMMAND.
                  # In any case nested escapes confuse the terminal, so don't
                  # output them.
                  ;;
              *)
                  echo -ne "\033]0;${USER}@${HOSTNAME}: ${BASH_COMMAND}\007"
                  ;;
          esac
      }
      trap show_command_in_title_bar DEBUG
      ;;
  *)
      ;;
  esac
  ###########################################################################
  #           END SET TERMINAL TITLE AS CURRENT RUNNING COMMAND             #
  ###########################################################################
  ```

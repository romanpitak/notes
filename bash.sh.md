# Bash #

## Standards ##

### file header ###

TODO

### "Strict mode" ###

    set -euo pipefail
    IFS=$'\n\t'

- `-e` immediately exit if any command has a non-zero exit status
- `-u` fail on undefined variables
- `-o pipefail` prevents errors in a pipeline from being masked

### function definition ###

    ###############################################################################
    # Prints help
    #
    # Globals:
    #   cfg__author
    #   cfg__help_message
    #   cfg__variables
    # Arguments:
    #   None
    # Returns:
    #   None
    ###############################################################################
    function cfg::show_help() {
        local key
        local option
        printf "${cfg__help_message}\n\nDEFAULT VALUES:\n"
        for key in "${!cfg__variables[@]}"; do
            option="--$(echo ${key,,} | sed -e 's/_/-/')"
            printf "\t${option}=${cfg__variables[$key]}\n"
        done
        printf "\nAUTHOR:\n\t${cfg__author}\n"
    }

##### Do use #####

    - a proper header
    - a namespace
    - local variables
    - underscores in names
    - a main function

### args ###

    while [[ $# > 0 ]]; do
        case "${1}" in
            -h|--help)
                cfg::help; exit 0
                ;;
            --in-file=*)
                cfg__in_file_arg="${1//--in-file=/}"
                ;;
            --out-file=*)
                cfg__out_file_arg="${1//--out-file=/}"
                ;;
            *)  # defaultVariables processing
                cfg::show_help
                cfg::fatal "\nUnknown option \"${1}\"" 63
                ;;
        esac
        shift
    done

### Sources ###

- https://google-styleguide.googlecode.com/svn/trunk/shell.xml
- http://redsymbol.net/articles/unofficial-bash-strict-mode/


- https://github.com/holman/dotfiles
- https://github.com/nojhan/liquidprompt
- https://github.com/revans/bash-it

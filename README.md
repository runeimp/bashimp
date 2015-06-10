BASHimp
=======

BASH Script Initializer

Script to help starting a BASH script by creating the file and initializing it with some useful content.

Usage
-----

### Initialize Script

`$ bashimp init test-script`

The above will initialize a file named test-script with the following contents

``` bash
#!/usr/bin/env bash
###################
# test-script v0.1.0
#
#
#



```

The file will automatically be opened in the editor specified by your VISUAL environment variable.

### Expunge Script

``` bash
$ bashimp kill test-script
  Are you sure you want to expunge test-script from this computer [yes/NO] (n) y
Expunging /Users/mgardner/bin/test-script
```

The above will ask for verification that you want to expunge the file and then delete the file from your system.

BASHimp Help
------------

``` bash
bashimp [OPTIONS]

  Commands:
    code                    Display exit codes.
    init SCRIPT_NAME        Initialize the named BASH script.
    kill SCRIPT_NAME        Expunge the named BASH script.
                            Will ask for verification.
    find INTERPRETER_NAME   Display a local path for the specified
                            interpreter name.
    help                    Display this help.

  Options:
    -a, --admin                     Use Admin/Multi-User mode.
    -e, --env INTERPRETER_NAME      Use specified interpreter name after
                                    /usr/bin/env when initializing the script.
    -f, --find INTERPRETER_NAME     Find a local path for the specified
                                    interpreter name and use it when
                                    initializing the script.
    -h, --help                      Display this help.
    -i, --interpreter               Specify the full path for initializing the interpreter.
    -p, --posix                     Find a POSIX compliant interpreter and use it's path when
                                    initializing the script.
    -v, --version                   Print out BASHimp version.
```

BASHimp Configuration
---------------------

You can create a user configuration file at `~/.config/bashimp.cfg` with the following variables to change the defaults used by BASHimp. The following shows the normal defaults.

``` bash
BASHIMP_AUTHOR=""
BASHIMP_ADMIN_MODE=false
# BASHIMP_EDITOR actually defaults to VISUAL, GIT_EDITOR, EDITOR,
# then tries to locate subl then vi.
BASHIMP_EDITOR="/Applications/Sublime Text.app/Contents/SharedSupport/bin/subl"
BASHIMP_INTERPRETER="/usr/bin/env bash"
BASHIMP_LICENSES=""
BASHIMP_PATH="$HOME/bin"
```

If BASHIMP_AUTHOR or BASHIMP_LICENSES are defined they will be added to the script header comment template as JavaDoc style tags.

### Plans for the future

* [X] Allow specification of Shebangs other than `#!/usr/bin/env bash`
* [X] Parse a configuration file for defaults
* [X] Also check EDITOR, and GIT_EDITOR if VISUAL is not defined in your environment
* [ ] Add functionality for extended option parsing when sourced into another script
* [ ] Setup editing of the header comment template

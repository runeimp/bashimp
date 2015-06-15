BASHimp
=======

BASH Script Initializer and Option Parser

Script to help starting a BASH script by creating the file and initializing it with some useful content.

Initializer
-----------

### Usage

#### Initialize Script

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

#### Expunge Script

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

### BASHimp Configuration

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

 * * *

Option Parser
-------------

When BASHimp is `source`d into a BASH script it will function as an option parser. It can be configured to set variables that the main script can utilize. The options can be commands, short switches or long switches. The user simply defines a multi-line variable named `OPTIONIMP_CONF`. Following is an example.

```
#
# Configure OPTIONimp mode of BASHimp
#
read -r -d '' OPTIONIMP_CONF <<'HEREDOC_EOD'
ONE, -f, --two  $format         required     Specify format string
-t, --three     $template       optional     Specify template string or path
--four          $forth          b            Enable forth dimension
five            $five           bool         Execute five times
-s, --six       $sexy_time      boolean      Enable Sexy Time
HEREDOC_EOD
```

The example shall parse the command line in the following way:

1. This example parses the case sensitive command `ONE`, short switch `-f`, and long switch `--two` to define a variable accessed as `$format` and makes the option argument that follows either the command, short switch, or long switch to be required throwing an error if it is not.
2. The switches `-t`, and `--three` will define the variable `$template` and if the `optional` option argument follows the switch in the command line it will be set in that variable. Otherwise the variable with be set to `true`.
3. The switch `--four` will define the variable `$forth` as `true` if it is present in the command line or `false` otherwise.
4. The command `five` will deine the variable `$five` as `true` if it is present in the command line or `false` otherwise.
5. The switches `-s`, and `--six` will deine the variable `$sexy_time` as `true` if it is present in the command line or `false` otherwise.

Note that short switches can be combined and will be handled independently. With the `OPTIONIMP_CONF` defined above specifying on the command line `five -tsf '%Y-%m-%d'` as options to your script would define the following variables:

``` bash
$format='%Y-%m-%d' # This commands argument defines the value of the commands variable
$template=true     # The switch's argument is optional and not used on the command line
$forth=false       # This switch is a boolean type and was not used on the command line
$five=true         # This command is a boolean type and was used on the command line
$sexy_time=true    # This switch is a boolean type and was used on the command line
```

This behavior should be connsistent in all versions of BASH that support arrays, regular expression matching, and the `read` internal command. Which _should_ be BASH v3 as a minimum. Though I've not tested this as yet. There are no external dependencies beyond BASH.

 * * *

### Plans for the future

* [X] Allow specification of Shebangs other than `#!/usr/bin/env bash`
* [X] Parse a configuration file for defaults
* [X] Also check `EDITOR`, and `GIT_EDITOR` if `VISUAL` is not defined in your environment
* [X] Add functionality for extended option parsing when sourced into another script
* [ ] Auto build help docs based on `OPTIONIMP_CONF`
* [ ] Enable BASHimp to create user configuration file with defaults
* [ ] Add switch to include BASHimp in script during creation process for option parsing
* [ ] Add command to copy an existing script into the user or multi-user bin
* [ ] Setup editing of the header comment template
* [ ] Split OPTIONimp into it's own script? (I'm debating this one.)


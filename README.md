BASHimp
=======

BASH Script Initializer

Script to help starting a BASH script by creating the file and initializing it with some useful content.

Usage
-----

### Initialize Script

`$ bashimp init test-script`

The above will initialize a file named test-script with the following contents

```
#!/usr/bin/env bash
###################
# test-script v0.1.0
#



```

The file will automatically be opened in the editor specified by your VISUAL environment variable.

### Expunge Script

`$ bashimp kill test-script`

The above will ask for verification that you want to expunge the file and then delete the file from your system.

BASHimp Help
------------

```
bashimp [OPTIONS]

  Commands:
    help                              Display this help
    codes | errors                    Display error codes
    create | add | init SCRIPT_NAME   Create/Initialize the named BASH script
    delete | rem | kill SCRIPT_NAME   Delete/Remove the named BASH script. Will ask for verification.

  Options:
    -a, --admin     Use Admin/Multi-User mode
    -h, --help      Display this help
    -v, --version   Print out BASHimp version
```

### Plans for the future

* [ ] Allow specification of Shebangs other than `#!/usr/bin/env bash`
* [ ] Parse a configuration file for defaults
* [ ] Also check EDITOR, and GIT_EDITOR if VISUAL is not defined in your environment
* [ ] Add functionality for extended option parsing when sourced into another script

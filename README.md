BASHimp
=======

BASH Script Initializer

Script to help starting a BASH script by creating the file and initializing it with some useful content.

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
* [ ] Add functionality for extended option parsing when sourced into another script

# min-reqs

### creates minimal requirement files

Main purpose of this script is to create requirements file with the most 
minimal, yet sufficient requirements set.

#### how it does - what it does

min-reqs utilizes and therefore depends on one particular pip command functionality:
```bash
pip show [package_name]
```
Above command 'Show information about installed packages' as pip man page states.
Output of command is as follows (in this example for 'pytest' package):
```
Name: pytest
Version: 3.2.3
Summary: pytest: simple powerful testing with Python
Home-page: http://pytest.org
Author: Holger Krekel, Bruno Oliveira, Ronny Pfannschmidt, Floris Bruynooghe, Brianna Laugher, Florian Bruhin and others
Author-email: UNKNOWN
License: MIT license
Location: /home/me/virtual_envs/lazypwd/lib/python2.7/site-packages
Requires: setuptools, py
```
Most important part of the output - for min-reqs - is 'Requires' row.
**min-reqs operates by collecting 'Requires' dependencies, parsing them, 
and greping them out from 'pip freeze' command output** which **should** result 
in correct minimal and sufficient dependencies set. 


* installation
```bash
git clone https://github.com/scgbckbone/min-reqs
cd min-reqs
chmod +x min-reqs
cp -v min-reqs [some-dir-in-path]/min-reqs
```


* usage in virtual environment (most efficient)

if in virtual environment (meaning you VIRTUAL_ENV variable is set)
you just run the command and your minimal requirements file will be saved 
to a directory specified by VIRTUAL_ENV
```bash
min-reqs

# to increase verbosity
min-reqs -v

# to not include version nubers in resulting requirements file
min-reqs -n

# to not include version numbers and increase verbosity
min-reqs -v -n

# if you do not want to save requirements file to VIRTUAL_ENV dir,
# but instead to Desktop dir
min-reqs -d /home/me/Desktop

# + verbose and without version numbers
min-reqs -n -v -d /home/me/Desktop
```

* usage outside of virtual environment

Outside virtual environment it is only possible to use this utility
with existing requirements file, mostly the result of 'pip freeze' cmd.
In this case you have to specify path to pip executable that should be used
for checks
```bash
# I do have requirements file in desktop dir and want to use defaul pip
# and want result file to be created in my current working dir
min-reqs -f ~/Desktop/requirements.txt -p /home/me/.local/bin/pip

# verbose and without version numbers with default pip3 and want 
# result file to be created in ~/req_files
min-reqs -v -n -f ~/Desktop/requirements.txt -p ~/.local/bin/pip3 -d ~/req_files
```

* show help
```bash
min-reqs -h
```
# min-reqs

### creates minimal requirement files

Main purpose of this script is to create requirements file with the most 
minimal, yet sufficient requirements set.

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
# bashrc-aliases
My personal bashrc aliases. Useful. Made public for anyone interested in simplifying their terminal usage.

## Setup/Install
Append the contents of `aliases` to your `~./bashrc` or `~./zshrc` file.\
Quick install:\
`curl -fsSL https://raw.githubusercontent.com/STR4NG3RdotSH/bashrc-aliases/main/aliases | while read -r line; do [ -f ~/.bashrc ] && echo "$line" >> ~/.bashrc; [ -f ~/.zshrc ] && echo "$line" >> ~/.zshrc; done`\
Quick uninstall:\
`for f in ~/.bashrc ~/.zshrc; do [ -f "$f" ] && sed -i '/#STR4NG3R_ALIASES_START/,/#STR4NG3R_ALIASES_END/d' "$f"; done`\
Notes:\
-Don't add anything between the `#STR4NG3R_ALIASES_START` and `#STR4NG3R_ALIASES_END` lines, after installation, because if you run the quick uninstall, everything between these 2 lines gets wiped.\
-If re-installing to apply latest version, be sure to run the quick uninstall first as the install is a simple append and can result in duplicate aliases.\
-Some systems require a re-login, some will work with just re-opening your terminal. Some will even work immediately.

## Defined functions/usage
### lgrep 
(**L**<sup>ogs</sup>**GREP**)\
Greps all log files in `/var/log/*` for specified strings. Forces case-insensitive for your search terms.\
Example Usage: `lgrep error_code_123 error_code_124 error_code_69420`\
Example Output:
```
/var/log/syslog:error_code_123
/var/log/syslog:error_code_123
/var/log/syslog:error_code_123
/var/log/syslog:error_code_123
/var/log/syslog:error_code_123
/var/log/testdir/testlog:error_code_123
/var/log/testdir/testlog:error_code_123
/var/log/testdir/testlog:error_code_123
/var/log/testdir/testlog:error_code_124
/var/log/testdir/anothertestdir/anothertestlog:error_code_69420
/var/log/testdir/anothertestdir/anothertestlog:error_code_69420
```

### lessf 
(**LESS**<sup>+</sup>**F**)
Using command `less +F` and specifying a path/name essentially works the same as `tail -f`, I just prefer to use less. This function also bakes in search terms (normally you have to CTRL+C and type `/(searchterm1|searchterm2|etc)` and hit enter, but this function accepts your search terms at launch instead). Forces case-insensitive for your search terms.\
Example Usage: `lessf error_code_123 error_code_124 error_code_69420 /var/log/syslog`

### nuke
Single word command, accepts single string, checks for processes with that name and kills them all. Essentially a loop with `kill -9`. Fast. Efficient. Kills without warning, confirmation or mercy. Like the T-1000.\
Example Usage: `nuke firefox`\
Example Output:
```
13 processes nuked!
```

### clone
Clone any disk (Disk to disk destructive clone)  
Usage: `clone /dev/sdx /dev/sdy`  
Just a function that walks you thru the process so you don't have to remember all the cryptic `dd` stuff, while adding confirmations before actioning.

## Defined aliases/usage
### ll
A popular and common alias, simplifying `ls -l` down to a simple `ll`, with some added preferences (`hA`, human readable and include `.` hidden files).\
Example Usage: `ll /var/log/testdir`\
Example Output:
```
drwxr-xr-x 2 j j 4.0K May 17 20:20 anothertestdir
-rw-r--r-- 1 j j   60 May 17 20:26 testlog
```
# Core stuff

## alias
`alias lm="ls -l | more"`  
`vi ~/.bashrc`  
`vi ~/.bash_aliases`  

## base64

`echo VlZLR1lDQzNHNEs1RzJRTTNHTElWVEVDVlNCV1dKWkQK | base64 -d`

## cat

`cat > report.txt`

Examples: https://www.interserver.net/tips/kb/linux-cat-command-usage-examples/

## cut

Cut fields, characters `echo hello | cut -c 2-5`

## diff
`diff -rq folder1 folder2`

## dig

DNS lookup `dig docker-registry.xara.com`

## find

`find ./test -name "*.php"`
`find ./ -type f`
`find ./ -mtime -1`

- Changed one day or more ago. 
  `-name` or `-iname`
  `-mmin -60` for minutes
  `-maxdepth 1` depth
  `-exec echo rm -f '{}' \;` echo to test command

- Files matching A *AND* B
  ```s
    # Find Camelot modal dialog files that use a timer.
    find . -type f -exec grep -q MODAL {} \; -exec grep -q TIMER {} \; -print
  ```
- Files matching A but *NOT* B

  ```s
    find . -type f -exec grep -q A {} \; -not -exec grep -q B {} \; -print
  ```
## grep

`grep -iF "success..." file` -i case insensitive -F fixed string no escaping
`grep -r -l - i "find" \*.php`

## scp

## sed

`echo "yummm" | sed 's/m/X/ig'`        stream replace  
`sed 's/^/ /' file.txt`                indent by one  
`sed '/./!d' file.txt`                 delete blank lines  

Try examples at 
https://linuxconfig.org/learning-linux-commands-sed

## service
`service apache restart`

## sort

Really useful e.g. when you need to sort file lines to diff.

`ls |sort -R`

## watch
Watch for changes
`watch -n 5 free -m`






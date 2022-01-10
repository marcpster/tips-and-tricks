# Bash commands

Document useful bash commands.

## Redirect std err for search
```
command 2>&1 >/dev/null | grep 'something'
```
## Batch rename etc.
```
for i in *.imp ; do
  mv -v $i ${i%.imp}
done
```
## Disk

`du -hs mkdb-exporter/` View folder size and not sub-folders  
`df -h` View free space  

## Random

`openssl rand -base64 12` Generate random string

## Quotes

## Xargs

```
  cat hello.txt
  123
  456

  xargs -I % sh -c 'printf "'"'"'%'"'"',\n";' <hello.txt
  '123',
  '456',
  '789',
```

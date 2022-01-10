# awk

https://linuxconfig.org/learning-linux-commands-awk?lang=en_gb

## Print row number and totals

```sh
echo 100,1 > file.txt
echo 200,2 >>file.txt
awk '{++c} {print c ") " $1} END {print "Total:" c}' file.txt #  
```

## Extract emails for SQL query

```sh
echo bob@acme.com,1 > b.csv
awk -F "\"*,\"*" '{print "'\''"$1"'\'',"}' b.csv >> query.sql

```
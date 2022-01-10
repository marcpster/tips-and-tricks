# awk

https://linuxconfig.org/learning-linux-commands-awk?lang=en_gb

## Print row number and totals

```sh
echo 100,1 > file.txt
echo 200,2 >>file.txt
awk '{++c} {print c ") " $1} END {print "Total:" c}' file.txt
```

## Extract and format emails for use in a SQL query

```sh
echo bob@acme.com,1 >  a.csv
echo jim@acme.com,1 >> a.csv
awk -F "\"*,\"*" '{print "'\''"$1"'\'',"}' a.csv >> query.sql
```
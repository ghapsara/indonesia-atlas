#Kabupaten Kota Maps

Script to generate kabupaten/kota topojson.

```
for f in ./**/
do
     [[ -f $f/Makefile ]] && echo Entering into "$f" && make -C "$f" map
done
```

Exexcute Jakarta makefile manualy because jakarta maps data also contains kepulauan seribu.

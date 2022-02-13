# castlefight-doc
Documentation for castlefight dota2 custom

## builded version

https://castlefight-doc.readthedocs.io/en/latest/index.html
https://dark123us.github.io/castlefight-doc/index.html


## run watch build

while true; do echo $(date); inotifywait -r source/ -e modify; make html; done

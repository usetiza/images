for f in $(find . -type f -name '*.jpg' | grep image); do mv "$f" "$(echo "$f" | sed s/.jpg_00.jpg/.jpg/)"; done
for f in $(find . -type f -name '*.jpg' | grep thumbnail); do cp "$f" "$f.bkp"; done
for f in $(find . -type f -name '*.bkp' | grep thumbnail); do convert -resize 65% "$f" "$(echo "$f" | sed s/.jpg.bkp/.jpg/)"; done
for f in $(find . -size +900k -type f -name '*.jpg' | grep image); do  convert -resize 50% "$f" "$(echo "$f" | sed s/image/small/)"; done
for f in $(find . -size +900k -type f -name '*.jpg' | grep small); do  mv "$f" "$(echo "$f" | sed s/small/image/)"; done


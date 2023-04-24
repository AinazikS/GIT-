> the syntax of positional argument - take note of double comma and curly braces - this is called a paramether expansion , and it will allows to ignore upper and lower cases when comparing the two values

```
${1,,} - работает как входной параметр
```
> EOF - end of file

```bash
#!/bin/bash

echo  What is your frst name?
read FIRST_NAME
echo What is your last name?
read LAST_NAME

echo Hello $FIRST_NAME $LAST_NAME
```
> fi statement is the fundamental control statement that allows Shell to make decisions and execute statements conditionally.

```sh
#!/bin/bash

if [ ${1,,} = deep-matrix ]; then
	echo 'Hello, boss'
elif [ ${1,,} = help ]; then
	echo 'Just type your name'
else
	echo 'No name'
fi
```

> | - separator for multiple options

```bash
#!/bin/bash

case ${1,,} in
	deep-matr1x | admin)
		echo 'Hello, boss'
		;;
	help)
		echo "Just enter your username"
		;;
	*)
		echo 'Unknown'
		;;
esac
```
> array syntax in bash:

```
MY_LIST=(one two three four five)
```
```
echo $MY_LIST
```
> output

```
one
```
> cause we specified like a simple variable

> to specify like an array:


```
echo $MY_LIST[@]
```
> output

```
one two three four five
```
> to take certain item by index

```
echo $MY_LIST[2]
```

> output

```
three
```

```
for item in $MY_LIST[@]; do echo -n $item | wc -c; done
```

```sh
#!/bin/bash


showuptime(){
	local up=$(uptime -p | cut -c4-)
        local since=$(uptime -s)
	cat << EOF
-----
This machine has been up for ${up}
It has been running since ${since}
-----
EOF
}
showuptime
```

```sh
#!/bin/bash

showname(){
	echo hello $1 (входной параметр)
}
showname Deep-Matrix
```
```
if - fi
case - esac
```
---

> EXIT CODES

```sh
#!/bin/bash

showname(){
	echo hello $1
	if [ ${1,,}  = deep-matrix ]; then
		return 0
	else
		return 1
	fi
}
showname $1
if [ $? = 1 ]; then
	echo 'Someone unknown called the function!'
fi
```
---

> AWK

```
 1809  echo one two three > testfile.txt
 1810  cat testfile.txt
 1811  awk '{print $1}' testfile.txt
 1812  awk '{print $2}' testfile.txt
 1813  echo one,two,three > cvs.cvs
 1814  awk -F, '{print $1}' cvs.cvs
 1815  awk '{print $2}' cvs.cvs
 1816  echo "Just get this word: Hello" | awk '{print $1 }'
 1817  echo "Just get this word: Hello" | -F: awk '{print $1 }' | cut -c2-\n
 1822  echo "Just get this word: Hello" |  awk -F: '{print $2 }' | cut -c2-\n
```

> SED

```
sed `s - mode/substitude / word - that you`d like to replace / word -  that you`d like to replace with / g - globally` file.txt
```
> with backup

```
sed -i.ORIGINAL `s - mode/substitude / word - that you`d like to replace / word -  that you`d like to replace with / g - globally` file.txt
```

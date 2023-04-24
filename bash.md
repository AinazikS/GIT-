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
echo ${MY_LIST[@]}
```
> output

```
one two three four five
```
> to take certain item by index

```
echo ${MY_LIST[2]}
```

> output

```
three
```

# Milan Suresh Lab Report 1

In this report, I'll be going over what happens we use the commands cd, ls, and cat with no arguments, a path to a directory as an argument, and a path to a file as an argument.

#Let's start with cd

## No Arguments:

![Image](ss4.jpg)

## Directory as Argument:

![Image](ss5.jpg)

## File as Argument:

![Image](ss6.jpg)

# Let's try ls.

## No Arguments:

![Image](ss1.jpg)

The current working directory is /main. ls or "list" lists the files/directories in /main, which is just lecture1. This output is not an error.

## Directory as Argument:

![Image](ss2.jpg)

The current working directory is still /main. ls lecture1 lists the files/directories in lecture1, which is: Hello.class  Hello.java  messages  README. This output is not an error.

## File as Argument

![Image](ss3.jpg)

The current working directory is again /main. ls Hello.java should target Hello.java, but since we are in /main, we cannot access that file. This output is an error.






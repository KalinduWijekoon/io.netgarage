---

title: level02
url: level2@io.netgarage.org

---

`ssh` to the above url via port no `2224` as mentioned in [io.netgarage.org](http://io.netgarage.org/)

You can use putty client or you can use openSSH with the command `ssh -p 2224 level2@io.netgarage.org`

Use __`XNWFtWKWHhaaXoKI`__ as the password. 

Just like the previous level, cd to the /levels directory and find the relevent level files. Find the `level02` executable file and run it using

    $ ./level02
    
Then you will get an output saying __`source code is available in level02.c`__ 

`cat level02.c` to view the source code
![](https://user-images.githubusercontent.com/37071700/75685661-ef826d80-5cc0-11ea-8b25-d87e87f8ae20.PNG)

In the source code, there are two functions called `main` and `catcher`

catcher function:<br>
![](https://user-images.githubusercontent.com/37071700/75687846-708f3400-5cc4-11ea-8923-d176924e54bc.PNG)

main function:
![](https://user-images.githubusercontent.com/37071700/75687850-7258f780-5cc4-11ea-8e62-63e7f53913ca.PNG)

`main` function argument count must be two and these two should be numbers. The `catcher` function is called on the event `SIGFPE`, which is a signal generated when an arithmetic error occurs such as a division by zero (1/0). The return value of the main function is an absolute value of an integer which will be the result of `argv[1] / argv[2]`

catcher function will set the current user identity, and print a "win" message and then it'll spawn a new shell which will probably be the level3 shell ;)<br>So, its obvious that we need to somehow invoke the `catcher` function in order to complete this level. :)

According to the mannual page of signal (System Calls [2]), we can maybe trigger `SIGFPE` by dividing the most negative integer by `-1`

(reffer this URL [man 2 signal](https://linux.die.net/man/2/signal) or type `man 2 signal` in your linux terminal)
![](https://user-images.githubusercontent.com/37071700/75691524-3f196700-5cca-11ea-9663-9fe08876c57a.PNG)

Here I tried to put -1 as the parameters but it didnt work.<br>
![](https://user-images.githubusercontent.com/37071700/75692003-e8605d00-5cca-11ea-945f-754d4db9a777.PNG)<br><br><br>
Anyhow, at this point we know that our second paramerter should be `-1`<br>To get the `SIGFPE` triggered we need another value for the first parameter, to do that we need a value that exists in the outer scope of integer definition, and that will be the `INT_MIN` `(-2147483648)` value in C.<br> __Why INT_MIN? Because it will generate 2147483648 which is greater than INT_MAX(2147483647) which is the integer limit.__<br>(reffer [abs function documentation](https://en.cppreference.com/w/c/numeric/math/abs) for more details)<br><br><br>
So, to gain the level3 shell we need to set level02 executable file parameters like,<br>
`./level02 -2147483648 -1`

Then you will get access<br>![](https://user-images.githubusercontent.com/37071700/75694776-16e03700-5ccf-11ea-9327-fa7c98c93d9c.PNG)

Finally use the `cat /home/level3/.pass` to get the ssh login password to the next level (level03)
![](https://user-images.githubusercontent.com/37071700/75694980-60308680-5ccf-11ea-97ea-009fd99982ea.PNG)

So, the key is `OlhCmdZKbuzqngfz`









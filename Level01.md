---

title: level01
url: level1@io.netgarage.org

---

`ssh` to the above url via port no `2224` as mentioned in [io.netgarage.org](http://io.netgarage.org/)

You can use putty client or you can use openSSH with the command `ssh -p 2224 level1@io.netgarage.org`

use __`level1`__ as the password. 

You will get a welcome screen like this.
![](https://user-images.githubusercontent.com/37071700/75663640-2c396f00-5c97-11ea-9c1b-a7c96877f6af.PNG)

Running the `ls` command will give you the `README` files.
![](https://user-images.githubusercontent.com/37071700/75664506-91419480-5c98-11ea-98c0-2f11f7d925ae.PNG)

Using the `cat README` command, you can view the level instructions.
![](https://user-images.githubusercontent.com/37071700/75665070-95ba7d00-5c99-11ea-9d93-ef2ccfdf1bf0.PNG)

So, in this readme file there are instructions to move to a location called levels which is in the root.

cd to the root

![](https://user-images.githubusercontent.com/37071700/75665588-648e7c80-5c9a-11ea-9286-27a15ccb20fd.PNG)

Then cd to the `levels` folder and by running the ls -la command find the executables.
![](https://user-images.githubusercontent.com/37071700/75665691-9273c100-5c9a-11ea-979f-616f72529216.PNG)

As you can see in the above image, there is a file which has the name `level01` that has an execute permission.

Run this file using `./level01` command and you will be asked for a three digit passcode. Type some random three digit value and it will not work. 
![](https://user-images.githubusercontent.com/37071700/75666141-542ad180-5c9b-11ea-9c98-a557c8ec4d26.PNG)


To find the three digit key, 
Launch the program under gdb:

    $ gdb level01
    
![](https://user-images.githubusercontent.com/37071700/75667268-63128380-5c9d-11ea-967f-1d450bb8de8e.PNG)

Type `info functions` to get information about available functions
![](https://user-images.githubusercontent.com/37071700/75667448-b4227780-5c9d-11ea-9c92-aef359ad41df.PNG)

Then by running the `start` command, gdb will run the programe and provide us with the temporary breakpoint.

![](https://user-images.githubusercontent.com/37071700/75667626-fe0b5d80-5c9d-11ea-93dc-027023a60fc3.PNG)

(If you want you can again run the `info functions` to view runtime functions of the application.)

Run the `set disassembly-flavor intel` and then run `disassemble main` command to get the assembly code of the `main` function of the `level01` programe. And there you need to find the comparison which will be indicated using `cmp`. The value in cmp is a hexadecimal value, we can display its decimal value with `p` or `print` in gdb. Other value `eax` is a register which compare the hexa value with.

Getting the hexa value
![](https://user-images.githubusercontent.com/37071700/75669561-39f3f200-5ca1-11ea-9c56-2070980b652e.PNG)

Exit from gdb using `quit` command and then try our new three digit key as the level01 access key.
![](https://user-images.githubusercontent.com/37071700/75669743-8f300380-5ca1-11ea-8c51-72a27b98fbfb.PNG)

Type `id` command to verify the `Effective User ID`
![](https://user-images.githubusercontent.com/37071700/75669870-c7374680-5ca1-11ea-9929-e09f29be5b45.PNG)

Finally use the `cat /home/level2/.pass` to get the ssh login password to the next level (level02)
![](https://user-images.githubusercontent.com/37071700/75669947-e6ce6f00-5ca1-11ea-8cef-2d3fd2c302f7.PNG)

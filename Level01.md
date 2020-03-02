---

title: level01
url: level1@io.netgarage.org

---

`ssh` to the above url via port no `2224` as mentioned in [io.netgarage.org](http://io.netgarage.org/)

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

# Installing iclassified

In order to read and write to cards, you will, at the minimum, need a reader/writer. The simplest way to get one is to get a reader/writer from the HID OMNIKEY line. Either the HID OMNIKEY 5321 or 6321 will work and both are fairly cheap at around $50. The model number does not matter very much, contrary to what you may think. I used an HID OMNIKEY 6321 CLi and an HID OMNIKEY 5321 v2 CLi. It is unverified but you may need to use Windows XP in order to use the drivers. I used Windows XP. 

To build the software you want to start off by downloading the [MinGW installer assistant](https://sourceforge.net/projects/mingw/files/Installer/mingw-get-setup.exe/download). Install it and select:

* mingw-developer-toolkit
* mingw32-gcc-g++
* msys-base

It should look something like this:

![mingw](https://cloud.githubusercontent.com/assets/166333/15988849/91724b5c-302d-11e6-994c-33d24211e87e.png)

Then go to `Installation > Apply Changes` on the menu bar to install part of your build environment. 

Now go to `C:\MinGW\msys\1.0` and copy everything over to `C:\MinGW`. 

![copying](https://cloud.githubusercontent.com/assets/166333/15988850/98ea89a8-302d-11e6-9620-c5b45406ff87.png)

Next, download the iClass folder, extract the zip, and copy all the files into the "home" folder
![dowload](https://i.postimg.cc/5y9NmBj9/4846194367660032.png)
![copy](https://i.postimg.cc/MH03zBYB/On-Paste-20190524-132429.png)
Now that the files have been copied, open the `msys.bat` file (located in the MinGW folder) to get a small shell environment. Go into the `iclassified` directory (though the terminal might already have you in it, just renamed as something like your username), and type in `make`.

If everything runs well the files `iclass.exe` and `iclassified.o` should appear in your "home" folder.

At this point you should plug in your OMNIKEY reader and follow the instructions provided alongside [the drivers](http://www.proxmark.org/files/Various%20Hardware/OMNIKEY%205x21/OMNIKESY5x21_V1_2_0_14.exe) to get the reader setup. 

If all goes well you should be able to execute `iclass.exe read` to read a card and `iclass.exe write` to write to a card.

![writing](https://cloud.githubusercontent.com/assets/166333/15988852/a08fa5d0-302d-11e6-99c5-3b80d4a7d195.png)


# Reading and Writing 

After you compile the program using the "make" command you should have the iclass.exe program. This will now allow you to read and write the required data blocks (6,7,8,9) that you need to make a clone of the card.

Use the "iclass.exe read" command to read the entire set of data blocks.

Then use the "iclass.exe write <blk> <data>" command to write each of the four blocks. (e.g. "iclass write 6  030303030003E017"  to write block 6)

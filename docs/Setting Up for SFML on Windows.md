Compiled specifically for VSCode using C++, SFML 2.6 32-bit, and following this tutorial:
https://www.youtube.com/watch?v=Ljhpsdz8Ouo

But I was unable to install version 2.6 using this guide alone, there were various issues and hurdles I needed to overcome to get everything working. 

---
Issues I had:
- If compiling SFML yourself this way, you'll need to get the mingw gcc and make commands, and install them 
- no tutorials had links to mingw version 13.1 which is what SFML 2.6 uses 

---
Instructions:
- Download the correct version of the mingw compiler from the SFML Download page: https://www.sfml-dev.org/download/sfml/2.6.0/. As of writing, these are the supported compilers for SFML 2.6 (I used the 32-bit one). The links on the Download page should change if they have changed the compiler for whatever version of SFML you are trying to install. 
    - WinLibs MSVCRT 13.1.0 (32-bit)
    - WinLibs MSVCRT 13.1.0 (64-bit)
- After download, unzip the compiler, and place the "mingw" folder inside into the directory of your choice
- I installed to the root of the C drive: `C:/`
  - You can install this wherever you want, but you'll need to remember where it is installed for a later step in the installation
- Change windows Path variable to include the destination you just installed mingw into
  - in start menu type "Path"
  - click on the "edit the system environment variables" pop-up, which will take you to the Advanced tab in the System Properties menu
  - near the bottom, click on the "Environmental Variables" button
    - in this menu there are two sub-menus where you can add directories to the path variable for either just the current user (User Variables) or anyone that uses the computer (System Variables). Choose whichever one fits your use case. 
    - Click the variable with the name "Path" and click edit
    - I downloaded mingw and placed it at the root of the C drive, so I made my path: at C:/
    - note the "/bin", this is where binaries(mingw commands) are stored. To run mingw commands the Path must point to 

- After installation, I went into the C:/mingw32/bin folder and went to the file "mingw32-make.exe" and renamed it to simply "make.exe". This way I could simply type "make" like he does in the video tutorial above, instead of typing "mingw32-make", which is long and annoying. If you don't do this step, make sure to type "mingw32-make" whenever he types "make" in the video. 
  - This may be called "minw64-make" if you're using the 64 bit version
- Everything **SHOULD** be set up now. If you followed this guide correctly, and followed the youtube video correctly for setting up a Makefile, creating a main.cpp, etc.
- To test the program, follow the steps in the "Running New Build" file in the /docs folder in this repo. Do these steps every time you want to test new code changes.  

<!--- TODO add steps for separate release and debug builds--->

---
Renaming "main.exe" executable:
- in the file named "Makefile", in the g++ command under "Link", change "Release/main" argument to whatever you want
  - example "g++ main.o -o Release/**CoolAdventureGame** -Lsrc/lib -lsfml-graphics -lsfml-window -lsfml-system"
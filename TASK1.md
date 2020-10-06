# M. M. SALEH (Salman)
[![N|Solid](https://avatars0.githubusercontent.com/u/3772814?s=60&v=4)](https://github.com/javagrails)

[Back To Home](https://github.com/javagrails/learn-linux)

# Basic Linux Task 1 with Solutions Step By Step

Login to a Linux system with a non-privileged user. And start to solve the questions. Make sure you are present working directory is the home directory of the logged in user. [Note: if you are using the minimal mode of the OS at first create Downloads, Videos, Documents, Pictures on the users home directory. If you are using a graphical version there is no need to create the folders those already exists] 

#### 0. initial command
```sh
$ mkdir {Downloads,Videos,Documents,Pictures}
```

#### 1. Create a total of 12 files with names tv_seasonX_episodeY.ogg. Replace X with the season number and y with that season's episode, for two seasons of six episodes each.
```sh
$ touch tv_season{1..2}_episode{1..6}.ogg
```

[Help Link](https://phoenixnap.com/kb/create-directory-linux-mkdir-command)

#### 2 . As the author of a successful series of mystery novels, your next bestseller's chapters are being edited for publishing. Create a total of eight files with names mystery_chapterX.odf. Replace X with the numbers 1 through 8.
```sh
$ touch mystery_chapter{1..8}.odf
```

[Help Link](https://phoenixnap.com/kb/create-directory-linux-mkdir-command)

#### 3. To organize the TV episodes, create two sub directories named season1 and season2 under the existing Videos directory. Use one command.
```sh
$ mkdir Videos/season{1..2}
```

[Help Link](https://phoenixnap.com/kb/create-directory-linux-mkdir-command)

#### 4. Move the appropriate TV episodes into the season sub directories. Use only two commands, specifying destinations using relative syntax.
```sh
$ mv tv_season1_* Videos/season1
$ mv tv_season2_* Videos/season2
```

[Help Link](https://stackoverflow.com/questions/12701044/how-to-move-all-files-in-a-directory-that-have-a-specific-prefix)

#### 5 . To organize the mystery book chapters, create a two-level directory hierarchy with one command. Create my_bestseller under the existing Documents directory, and chapters beneath the new my_bestseller directory.
```sh
$ mkdir Documents/my_bestseller && mkdir Documents/my_bestseller/chapters
```

#### 6. Using one command, create three more sub directories directly under the my_bestseller directory. Name these sub directories editor, plot_change , and vacation . The create parent option is not needed since the my_bestseller parent directory already exists.
```sh
$ mkdir Documents/my_bestseller/{editor,plot_change,vacation}
```

#### 7. Change to the chapters directory. Using the home directory shortcut to specify the source files, move all book chapters into the chapters directory, which is now your current directory. What is the simplest syntax to specify the destination directory?
```sh
$ cd Documents/my_bestseller/chapters
$ mv ~/mystery_chapter* .
```

#### 8. The first two chapters are sent to the editor for review. To remember to not modify these chapters during the review, move those two chapters only to the editor directory. Use relative syntax starting from the chapters subdirectory.
```sh
$ mv mystery_chapter{1..2}.odf -t ../editorss
```

#### 9. Chapter 7 and 8 will be written while on vacation. Move the files from chapters to vacation. Use one command without wildcard characters.
```sh
$ mv mystery_chapter7.odf mystery_chapter8.odf -t ../vacation
```

#### 10. With one command, change the working directory to the season2 TV episodes location, then copy the first episode of the season to the vacation directory.
```sh
$ cd ~/Videos/season2 && cp tv_season2_episode1.ogg ~/Documents/my_bestseller/vacation
```

#### 11 . With one command, change the working directory to vacation, then list its files. Episode2 is also needed. Return to the season2 directory using the previous working directory shortcut. This will succeed if the last directory change was accomplished with one command. Copy the episode2 file into vacation. Return to vacation using the shortcut again.
```sh
$ cd ~/Documents/my_bestseller/vacation && ls
$ cd - && cp tv_season2_episode2.ogg ~/Documents/my_bestseller/vacation && cd -
```

#### 12. Chapter 5 and 6 may need a plot change. To prevent these changes from modifying original files, copy both files into plot_change. Move up one directory to vacation's parent directory, then use one command from there.
```sh
$ cd .. && cp chapters/mystery_chapter{5..6}.odf -t plot_change
```

#### 13. To track changes, make three backups of chapter5. Change to the plot_change directory. Copy mystery_chapter5.odf as a new file name to include the fulldate (Year-Mon- Date). Make another copy appending the current timestamp (as the number of seconds since the epoch) to ensure a unique filename. Also make a copy appending the current user ($USER) to the filename. 
```sh
$ cp mystery_chapter5.odf "./mystery_chapter5_$(date +"%Y-%m-%d").odf"
OUTPUT: [mystery_chapter5_2020-10-05.odf]

$ cp mystery_chapter5.odf "./mystery_chapter5_$(date +"%s").odf"
OUTPUT: [mystery_chapter5_1601847711.odf]

$ cp mystery_chapter5.odf ./mystery_chapter5_$USER.odf
OUTPUT: [mystery_chapter5_centos.odf]
```

[Help Link](https://timestamp.online/article/how-to-get-current-timestamp-in-bash)

#### 14. The plot changes were not successful. Delete the plot_change directory. First, delete all of the files in the plot_change directory. Change directory up one level because the directory cannot be deleted while it is the working directory. Try to delete the directory using the rm command without the recursive option. This attempt should fail. Now use the rmdir command, which will succeed.
```sh
Currently I am in plot_change directory and executing below command
$ rm * && cd .. && rmdir plot_change
```
#### 15. When the vacation is over, the vacation directory is no longer needed. Delete it using the rm command with the recursive option. When finished, return to the home directory.
```sh
$ rm -R vacation && cd ~
```


[Back To Home](https://github.com/javagrails/learn-linux)

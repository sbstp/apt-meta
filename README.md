# apt-meta
This tool is a small utility that makes it possible to customize the
installation of metapackages in Debian. It works by parsing the
dependencies of the metapackage, letting you modify the list, and finally,
installing each dependency manually. In the end the metapackage is not
installed, only some of its dependencies. This prevents the issue
where removing a single component of a metapackage removes all of the
other components.

You can modify the dependency list in two ways:
* select which package to install when multiple package satisfy a
dependency
* exclude packages from the list

It's also possible to override a currently installed metapackage. For
instance, if you have `gnome-core` installed, you can use this script
to mark all of its dependencies as manually installed, and then
remove the ones you don't want.

This was lightly tested, and mostly with `gnome-core`. Use it at
your own risk.

Example output:
```
simon@mu:~/projects/apt-meta$ ./apt-meta kde-standard
You may select between:
0: plasma-pa
1: kmix
Your choice: 1
Choose the packages to exclude:
0: akregator
1: ark
2: dragonplayer
3: gwenview
4: juk
5: kaddressbook
6: kate
7: kcalc
8: kde-plasma-desktop
9: khelpcenter
10: kmail
11: knotes
12: kopete
13: korganizer
14: kde-spectacle
15: kwalletmanager
16: okular
17: plasma-dataengines-addons
18: kmix
19: plasma-runners-addons
20: plasma-wallpapers-addons
21: plasma-widgets-addons
22: polkit-kde-agent-1
23: sweeper
24: konq-plugins
25: plasma-nm
Enter numbers to exclude separated by a comma: 2, 4, 6, 10
You have selected to exclude the packages dragonplayer, juk, kate, kmail.
Is this information correct? [y/N] y
```

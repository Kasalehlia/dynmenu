dynmenu
=======

Create dynamic menus with dmenu.

The script takes one parameter, the menu name.
It then checks for a $name.menu in ~/.menu and executes that, piping the output into dmenu.
If this file does not exist, it next checks for a $name.sqlite in ~/.menu and reads the commands from that database using a weight.

The result of dmenu is then piped through a $name.post, if existing.

The command can be terminated with a symbol to trigger a special action:
* **;** the command will be opened in a seperate *urxvt* window
* **!** the command will be preceeded with *gksu*
* **?** the command will be preceeded with *m*


###Setup
```bash
# 1. clone dynmenu to .menu
git clone https://github.com/Kasalehlia/dynmenu.git ~/.menu

# 2. create database
cat ~/.menu/menu.sql|sqlite3 ~/.menu/main.sqlite

# 3. fill database with commands
~/.menu/menu-update

# 4. change your window managers hotkey for dmenu to
~/.menu/menu main

# rerun step 3 for new commands
```

Optional: On Debian/Ubuntu you can copy 99menu-update to /etc/apt/apt.conf.d/ to register `menu-update` as apt hook


---
layout: post
title:  "Switching to console"
date:   2017-12-10T23:39:51
desc: "Documentation of how I switched from GUI to console mode"
keywords: "Ubuntu 16.04LTS,blog,console mode,grub,tty"
categories: [Linux]
tags: [Ubuntu 16.04LTS,blog,console mode]
icon: fa-linux
---

How to switched from GUI to console mode:
- Edit the `grub` file in `/etc/default/` location
  - Press `ctrl + alt + T` to open terminal
  - Type `sudo vi /ect/default/grub` and change the following
  - Comment the line `GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"` by adding a `#` at the beginning of the line
  - Change the line `GRUB_CMDLINE_LINUX=""` to `GRUB_CMDLINE_LINUX="text"`
  - Uncomment the line `#GRUB_TERMINAL=console` by removing `#` at the beginning
  - The above change will look like $b^2$![vi editor](https://raw.githubusercontent.com/ujjaldas1997/Data_images/master/blogs/vi_grub.jpg){% raw %}$\\${% endraw %}
  - Save the file `grub` by `esc` then `:wq`
  - Now go to terminal and type `sudo update-grub`
- Finally change the symlink of Systemd `default.target` from `graphical.target` to `multi-user.target`
  - To do the above type `sudo systemctl set-default multiuser.target`
  - You can conform it by typing `sudo systemctl get-default`
  - Now reboot the system

How to switch from console mode to GUI mode
- Edit the `grub` file again but in reverse way and save the same
- Update grub by typing `sudo update-grub`
- Change the symlink of Systemd by `sudo systemctl set-default graphical.target`
- Reboot the system

---

### Benifits of console mode
- Low RAM usage in console mode(you can see it by `htop`)   
    - {% raw %}$\\${% endraw %}![Console RAM](https://raw.githubusercontent.com/ujjaldas1997/Data_images/master/blogs/console_ram.jpg){% raw %}$\\${% endraw %}
- While in GUI the RAM usage is {% raw %}$\\${% endraw %}![GUI RAM](https://raw.githubusercontent.com/ujjaldas1997/Data_images/master/blogs/gui_ram.jpg){% raw %}$\\${% endraw %}

- #### See how RAM usage is decreased in console mode
### Problems of console mode
- You can do all the things that you usually do in terminal(you can't browse, play a video etc)

---

P.S. - All the above works are tested in Ubuntu 16.04 LTS

---

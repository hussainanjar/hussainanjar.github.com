---
layout: post
title:  "Basic Usage of VIM Editor"
date:   2011-10-30 13:20:00
categories: MySql
---

In this blog we are going to discuss very basic usage of VIM editor.

##### **What is VIM**

Vim is an advanced text editor that seeks to provide the power of the de-facto Unix editor 'VI', in short VIM is an improved version of VI text editor.

##### **Modes in VIM**

VIM has six different modes, you can switch between these modes to perform different actions on the file you are editing. Here we will discuss NORMAL, INSERT and COMMAND-LINE modes.

##### **Using VIM**

By default VIM opens in NORMAL mode. Type **vim** and press enter to open a blank file.
> `vim`

Type **`vim newfile`** to open a blank file with a name **'newfile'** or edit a file by typing **`vim oldfile`** to edit an old file.
> `vim newfile`

> `vim oldfile`

To edit the file you need to enter the **INSERT** mode press **`i`** to enter this mode. Type anything you want and once you are done save or exit the file by entering the **COMMAND-LINE** mode.

If you are currently in **INSERT** mode press **ESC** to exit the **INSERT** mode and then press **`:`** to enter the **COMMAND-LINE** mode. You can use following commands in this mode.

> `:w`   -  save the file
> 
> `:q`   -  exit
> 
> `:wq` -  save and exit
> 
> `:q!` -  exit without saving

If you initially opened a blank new file just by entering **`vim`** you can type the name of the file after the above command to save the file with the name you want.

> `:w mynewfile`
> 
> `:wq mynewfile`
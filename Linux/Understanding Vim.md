---
Title: Understanding Vim
date: 2024-12-19
tags:
  - vim
  - linux
  - cheatsheets
---
### Vim Keys Navigation

| k   | Moves cursor up    |
| --- | ------------------ |
| j   | Moves cursor down  |
| h   | Moves cursor left  |
| l   | Moves cursor right |

### Basic Commands

| :q                  | Exit from the file                                |
| ------------------- | ------------------------------------------------- |
| :wq                 | Save and exit                                     |
| :q!                 | Exit without saving                               |
| :$                  | Move cursor to end of file                        |
| :w                  | Save changes                                      |
| :set number         | To show line numbers                              |
| :set no number      | Hide line numbers                                 |
| :%s/wordabc/wordxyz | substitute wordabc with worxyz for all occurances |

### Vim insert modes

| a   | Insert cursor at right of current character |
| --- | ------------------------------------------- |
| A   | Insert at the end of line                   |
| o   | Insert mode at new line below               |
| O   | Insert mode at new line above               |
| r   | To change the single character              |
| R   | Start Replacing everything                  |

### Vim Keybinds

| yy       | Yank the line (copy)             |
| -------- | -------------------------------- |
| Dd       | Delete the line                  |
| Dw       | Delete the word                  |
| Yw       | Copy the word                    |
| P        | Paste the copied content         |
| U        | Undo                             |
| Ctrl + r | Redo                             |
| Gg       | Move the cursor to start of file |
| G        | Move the cursor to end of file   |

Vim Modes

| i   | Insert mode  |
| --- | ------------ |
| Esc | Escape mode  |
| :   | Command mode |


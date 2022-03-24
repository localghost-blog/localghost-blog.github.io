---
author: Local Ghost
title: Tweak Your VIM to a Powerful $\LaTeX$ IDE
---

## Prerequisites

1. Install the latest Vim on its [Website](https://www.vim.org/download.php) or in the terminal:

```sh
sudo apt install vim
```

2. Install [vim-plug](https://github.com/junegunn/vim-plug).
3. Install `texlive`, `xelatex`, `latexmk`. For a new user, I recommend installing `texlive-full`.

```sh
sudo apt install texlive-full
```

## Plugin Installation & Configuration

Add 

```vim
call plug#begin()

Plug 'SirVer/ultisnips'

Plug 'lervag/vimtex'

Plug 'ycm-core/YouCompleteMe'

" optional
Plug 'mhinz/vim-signify'

call plug#end()
```

in the file `~/.vimrc`, and `:PlugInstall` in vim to install plugins.

You can create some useful snippets as in [How I'm able to take notes in mathematics lectures using LaTeX and Vim](https://castel.dev/post/lecture-notes-1/) written by Gilles Castel. The *mathematical context* is a must-have. 

If you want to store your snippets in the folder you like, says `path-to-the-folder`, add it in your `.vimrc`:

```vim
set rtp+=path-to-the-folder
```

Then put your snippets in `path-to-the-folder/Ultisnips`.

## Frequently Faced Issues

Q: `ycm-core/YouCompleteMe` is difficult to install

A: I will write a tutorial if required.



Q: `ycm-core/YouCompleteMe` and `SirVer/ultisnips` do not work well in default settings

A: you can add

```vim
let g:UltiSnipsJumpForwardTrigger="<tab>" 
let g:UltiSnipsJumpBackwardTrigger="<S-tab>"
let g:UltiSnipsExpandTrigger="<C-tab>"
```

in your `.vimrc`.

## Other Settings

- When using `ycm-core/YouCompleteMe`, you can collect identifiers from [exuberant ctags](http://ctags.sourceforge.net/). See [ycm-core/YouCompleteMe](https://github.com/ycm-core/YouCompleteMe#the-gycm_collect_identifiers_from_tags_files-option).
- If you are troubled by the `.tex` code formatting, try using [cmhughes/latexindent.pl](https://github.com/cmhughes/latexindent.pl).
- If you are using a version control system (e.g. git), you can plug [mhinz/vim-signify](https://github.com/mhinz/vim-signify) to help you modify the files.
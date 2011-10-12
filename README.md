# A pretty Ruby/Rails centric Vim 'distro' for MacOS/Linux

## Requirements

Vim 7.3 or better
Tested on MacOS and Linux

Introduction to Vim: http://blog.interlinked.org/tutorials/vim_tutorial.html

## Basic Mappings

The leader is mapped to ,

### In Normal mode (Esc or jj)

- ,p    - File browser (NerdTree)
- ,f    - Find in Files (Command-t)
- Space - Search in buffer
- ,a    - Search in files (Ack)
- ,b    - Search open buffers (Fuzzy Finder)
- ,d    - close buffer
- ,D    - close all buffers
- ,Space - Remove search highlighting
- ,t    - Show tags
- //    - Comment/uncomment (T-Comment)
- F5    - Undo history (GUndo)
- F6    - Auto format
- Tab   - Next buffer
- Shift + Tab - Previous buffer
- ,,  - Toggle between last two buffers
- ,m  - Jump to model
- ,v  - Jump to view
- ,gm - Find in app/models
- ,gc - Find in app/controller
- ,gv - Find in app/views
- ,gr - Open routes in split
- ,gg - Open Gemfile in split
- ,vir - Visual select inner Ruby block
- ,var - Visual select around Ruby block

### In Insert mode (i)

- jj - Back to normal mode

See .vimrc for more.

## Plugins

Gist.vim (:Gist)

>  Gist current file/selection
>  Requires setting GITHUB_TOKEN and GITHUB_USER Env's

gundo.vim (F5)

>  Navigate changes history tree 
>  http://vimcasts.org/episodes/undo-branching-and-gundo-vim/

tabular

>  Align stuff
>  http://vimcasts.org/episodes/aligning-text-with-tabular-vim/

vim-fugitive         

>  Git integration
>  :Gstatus and press - to stage file
>  http://vimcasts.org/episodes/fugitive-vim---a-complement-to-command-line-git/

vim-rails            

>  *Lots* of stuff
> :Rmodel - jump to model
> :Rview
> :help rails

ruby-block

>  Allow selecting of blocks of Ruby code
>  var (visual around Ruby)
>  vir (visual inner Ruby)
>  ar / ir (expand/contract selection)
>  http://vimcasts.org/blog/2010/12/a-text-object-for-ruby-blocks/

vim-rvm              

>  Add RVM integration

Conque

> Terminal/Interactive programs
> :Conque zsh
> :Conque ls
  
  Note you can also drop back to the terminal using Ctrl+Z, to get
  back to Vim with %1. This is not a feature of Conque.

vim-tcomment (//)

> Comment stuff out

snipmate.vim (TAB)         

>  Snippets, press TAB to expand

vim-yankring

>  Shows history of yanked (copied) text

ack.vim              

>  Search project for text (aka find in files)
>  ,a word
>  ,a "some words"

nerdtree (,p)             

> Project file browser
> I would recommend for speed using Command-t instead

sparkup (ctrl+e)

> Expand div.event in to <div class='event'></div>

vim-surround (ys/cs/ds)

>  Allows adding/removing/changing of surroundings

  Characters

> ysiw)    - surround inner word with ()
> ysiw(    - surround inner word with (  )
> cs"'     - change surrounding from " to '
> ds       - delete surrounding

  Tags

> yss <p>  - surround line in <p> tags
> cst<div> - change surround tag to <div>

vundle

>  Plugin manager

command-t (,f)            

>  Find files in your project with partial matches
>  ,gf - find files in directory of current buffer

vim-colors-solarized 

>  A colour scheme, both light and dark version
>  :set background=dark
>  :set background=light

vim-fuzzyfinder (,b)

>  Find open buffer

vim-taglist (,t)

>  Lists method names

## INSTALLATION

Note: If you already have Vim installed ensure it has support for Ruby:

```
vim --version | grep ruby
```

You should see +ruby, if you see -ruby you need to reinstall Vim with Ruby support

### Install Vim

#### MacOS: MacVim / Vim (if not already installed)

```
brew install macvim --override-system-vim --enable-clipboard
Add /usr/local/bin before /usr/bin in your $PATH so you use the version of brew
installed by Homebrew, not the one that comes with MacOS.
```

By installing Vim in this way MacVim and regular Vim are exactly the same.

#### Ubuntu: gVim / Vim

I have no experience with gVim, only regular Vim on Ubuntu:

```
sudo apt-get install vim-nox
```

If you have an old Ubuntu distro which does not have Vim 7.3 or better in its repos then install from source:
The configure options below leave out any GUI related features as I have only compiled Vim on a server.

```
sudo apt-get install mercurial
hg clone https://vim.googlecode.com/hg/ vim
cd vim/vim73
./configure
./configure --with-features=huge --enable-cscope --enable-pythoninterp --enable-rubyinterp --enable-perlinterp --enable-multibyte
make
sudo make install
```

This installs Vim to /usr/local/bin, check this is in your $PATH before /usr/bin which may contain an older system version of Vim.

### Install this Distro

Note: You will already have a ~/.vim folder, either delete or move it.

```
mv ~/.vim ~/.vim.old
git clone https://github.com/krisleech/vimfiles ~/.vim
cd ~/.vim
rake install
```

or run:

```
curl https://raw.github.com/krisleech/vimfiles/master/bootstrap.sh -o - | sh
```

#### To update your Distro run at a later time

```
cd ~/.vim
rake update
```

#### Install Dependacies

*MacOS*

```
brew install ack
brew install ctags
```

*Ubuntu*

```
sudo apt-get install exuberant-ctags
sudo apt-get install ack-grep
sudo ln -s /usr/bin/ack-grep /usr/local/bin/ack
```

## Helpful links

- http://walking-without-crutches.heroku.com/image/images/vi-vim-cheat-sheet.png
- http://stevelosh.com/blog/2010/09/coming-home-to-vim/#important-vimrc-lines
- http://yehudakatz.com/2010/07/29/everyone-who-tried-to-convince-me-to-use-vim-was-wrong/

## Acknowledgments

- https://github.com/carlhuda/janus
- https://github.com/rson/vimfiles/blob/master/plugins.vim
- https://github.com/codegram/vimfiles
- https://www.destroyallsoftware.com/file-navigation-in-vim.html
- https://github.com/alexreisner/dotfiles/blob/master/.vimrc
- http://items.sjbach.com/319/configuring-vim-right
- #vim on freenode
 - woldrich
 - spiiph
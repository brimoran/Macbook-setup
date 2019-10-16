# Macbook-setup
Setting up a new Macbook

MacBook Pro (13-inch, 2019, Four Thunderbolt 3 ports)
2.4 GHz Intel Core i5
16 GB 2133 MHz LPDDR3
500 GB

## Chrome

Replace Safari with Chrome and set as default browser.

## Homebrew

Install homebrew to enable us to installsome useful tools:

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

## Git

Set up git config:

```
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
```

Confirm:

```
git config --list
```

Create SSH key:

```
ls -al ~/.ssh
# Lists the files in your .ssh directory, if they exist
```

Show contents of public SSH key to copy to add to web git service:

```
cat ~/.ssh/id_rsa.pub
```

Add SSH key to webservice and then clone repo using SSH in the area you want it on your computer:

e.g. with Gitlab

```
git clone git@gitlab.com:YOURGITUSERNAME/YOURREPO.git

```
## Vim

Default Vim is version 8.0.1365, let's run with that for now.

Let's install VimPlug:

```
curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

Then copy .vimrc which I store in a git repository to home folder:

e.g.

```
cp .vimrc ~/
```

And then install the plug ins from within the .vimrc file in Vim by typing:

```
:PlugInstall
```

## Poppler

For PDF tools:

```brew install poppler```


## LaTeX

## R and R Studio



## GUI programmes

### Acorn
Nice graphics editor:
https://flyingmeat.com/acorn/




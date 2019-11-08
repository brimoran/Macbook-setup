# Macbook-setup
Setting up a new Macbook

MacBook Pro (13-inch, 2019, Four Thunderbolt 3 ports)

2.4 GHz Intel Core i5

16 GB 2133 MHz LPDDR3

500 GB

## Chrome

Replace Safari with Chrome and set as default browser.

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

## Homebrew

Install homebrew to enable us to install some useful tools:

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

### Poppler

For PDF tools:

```brew install poppler```

### Pandoc

To convert document formats:

```brew install pandoc```

## LaTeX

Download and install MacTeX:

http://www.tug.org/mactex/mactex-download.html

(pdflatex will only be recognised after quiting and restarting terminal.)

And Texpad:

https://www.texpad.com/osx 

And Fira Sans:

https://fonts.google.com/specimen/Fira+Sans

## R and R Studio

Download and install R:

https://cran.r-project.org/

Important: this release uses Clang 7.0.0 and GNU Fortran 6.1, neither of which is supplied by Apple. If you wish to compile R packages from sources, you will need to download and install those tools - see the tools directory.

Enter R via the terminal as superuser:

```sudo R```

Let's install the packages we need in one command:

```install.packages(c("ggplot2","tidyverse","knitr","ggthemes","scales","ggmap","plotly","ggfortify","leaflet","leaflet.extras","rgdal","forecast","treemapify","dbscan","survival","googleVis","rmarkdown","flexdashboard","highcharter","devtools","maptools","mapview","treemap","networkD3","visNetwork","DiagrammeR","DT","ggcorrplot"))```

This will take a while.

```q()``` to exit R

Download and install R Studio:

https://rstudio.com/products/rstudio/download/

## Acorn
Nice graphics editor:
https://flyingmeat.com/acorn/

## Sublime Text
https://www.sublimetext.com/

# Macbook-setup
Setting up a new Macbook

MacBook Pro (13-inch, 2019, Four Thunderbolt 3 ports)

2.4 GHz Intel Core i5

16 GB 2133 MHz LPDDR3

500 GB

## Chrome

Replace Safari with Chrome and set as default browser.

## Git

Launch the Terminal.

Set up git config:

```git config --global user.name "John Doe"```

If they aren't already installed you'll be prompted now to install Command Line Tools.

```git config --global user.email johndoe@example.com```

Confirm:

```
git config --list
```

Create SSH key:

```
ls -al ~/.ssh
# Lists the files in your .ssh directory, if they exist
```

If none exist:

```
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

Show contents of public SSH key to copy to add to web git service:

```
cat ~/.ssh/id_rsa.pub
```

Add SSH key to webservice and then clone repo using SSH in the area you want it on your computer (for example create a Version Controlled folder in your home directory):

e.g. with Gitlab

```
git clone git@gitlab.com:YOURGITUSERNAME/YOURREPO.git

```

## Homebrew

Install homebrew as a package manager:

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

## Vim

Default Vim is version 8.1.1312, update with:

```
brew install vim
```

Add alias to ```~/.bashrc``` file so homebrew version loads instead of system version:

```
alias vim=/usr/local/bin/vim
```

Then let's install VimPlug:

```
curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

Then copy .vimrc which I store in a git repository to home folder:

e.g. navigate to folder and then

```
cp .vimrc ~/
```

And then install the plug ins from within the .vimrc file in Vim by typing:

```
:PlugInstall
```

## LaTeX

Using homebrew for the install as otherwise the MacTex installation of ghostscript conflicts with homebrew.  (Ghostscript is useful to shrink pdf files.)

```brew cask install basictex```

Note this is Basic Tex.  Then add path to bashrc:

```PATH=/usr/local/texlive/2019basic/bin/x86_64-darwin:"${PATH}"```

Update tlmgr:

```
sudo tlmgr update --self
```

Then add specific LaTeX packages as required with ```tlmgr```, e.g.:

```sudo tlmgr install subfiles isodate substr enumitem datatool xfor fp pdfpages csquotes microtype hyphenat xcolor fancyhdr lastpage fira mweights fontaxes wrapfig capt-of mdframed needspace tcolorbox pgf environ trimspaces titlesec titlecaps ifnextok floatrow placeins adjustbox collectbox lcg relsize lineno pgfplots xltxtra float tabulary lipsum marginnote import l3backend l3kernel pagecolor titling```

### Ghostscript

I use Ghostscript to shrink PDF files:

```brew install ghostscript```

### Poppler

For PDF tools:

```brew install poppler```

### Pandoc

To convert document formats:

```brew install pandoc```


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

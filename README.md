# Macbook-setup
Setting up a new Macbook

MacBook Pro (14-inch, 2021)

Apple M1 Pro

16 GB RAM

500 GB

## Chrome

Download Chrome, launch it and set as default browser.

## Git and SSH keys

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

Add public key to any servers you need to access:

``ssh-copy-id -i ~/.ssh/id_rsa.pub YOUR_USER_NAME@IP_ADDRESS_OF_THE_SERVER``

## Homebrew

Install homebrew as a package manager:

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

## bash

Default is version 3.2.57(1)-release over 10 years old, update with:

```brew install bash```

Verify installation (should see install in ```/usr/local/bin/bash```):

```which -a bash```

Whitelist new shell:

```sudo vim /etc/shells``` and add ```/usr/local/bin/bash``` to the file

Set as default shell:

```chsh -s /usr/local/bin/bash```

Change for root user:

```sudo chsh -s /usr/local/bin/bash```

Add some aliases to short cut commands, e.g.:

``vim .bash_profile``

and add:

``alias work='ssh YOURUSERNAME@SERVERIPADDRESS'``

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

MacTex 2020 comes with ghostscript 9.5 so this will be fine.  Notes below left for posterity but I've since given up on this approach as it was difficult to update individual packages if a new version of LaTeX was released, so instead head to:

https://www.tug.org/mactex/mactex-download.html

and download and install MacTeX.

Using homebrew for the install as otherwise the MacTex installation of ghostscript can conflict with other homebrew packages.  (Ghostscript is useful to shrink pdf files.)

```brew cask install basictex```

Note this is Basic Tex.  Then add path to bashrc:

```PATH=/usr/local/texlive/2019basic/bin/x86_64-darwin:"${PATH}"```

Update tlmgr:

```
sudo tlmgr update --self
```

Then add specific LaTeX packages as required with ```tlmgr```, e.g.:

```sudo tlmgr install subfiles isodate substr enumitem datatool xfor fp pdfpages csquotes microtype hyphenat xcolor fancyhdr lastpage fira mweights fontaxes wrapfig capt-of mdframed needspace tcolorbox pgf environ trimspaces titlesec titlecaps ifnextok floatrow placeins adjustbox collectbox lcg relsize lineno pgfplots xltxtra float tabulary lipsum marginnote import l3backend l3kernel pagecolor titling footmisc rotating```

### Ghostscript

This is not needed now as it comes with MacTeX.

I use Ghostscript to shrink PDF files:

```brew install ghostscript```

### Poppler

For PDF tools such as pdftotext:

```brew install poppler```

### Pandoc

To convert document formats:

```brew install pandoc```

### OCRmyPDF

To OCR PDFs example: ```ocrmypdf -l eng input.pdf output.pdf```

```brew install ocrmypdf```

### LaTeX diff

To show diffs in LaTeX:

```brew install latexdiff```

### Rename

For flexible tools to rename file in bash:

```brew install rename```

### Parallel

To use muliple cores in bash:

```brew install parallel```

### XQuartz

Replace X11 with Xquartz to resolve some issues that I ran into with the installation of some R packages.

```brew cask install xquartz```


### Mosh

For more persistent remote terminal access.

```brew install mosh```

### Git Large File Storage

To use git with large files (see https://git-lfs.github.com/)

```brew install git-lfs```

### Gdal

For some geographic work in R.

```brew install gdal```

## R and R Studio

Download and install R:

https://cran.r-project.org/

Enter R via the terminal as superuser:

```sudo R```

Let's install the packages we need in one command:

```install.packages(c("ggplot2","tidyverse","knitr","ggthemes","scales","ggmap","plotly","ggfortify","leaflet","leaflet.extras","rgdal","forecast","treemapify","dbscan","survival","googleVis","rmarkdown","flexdashboard","highcharter","devtools","maptools","mapview","treemap","networkD3","visNetwork","DiagrammeR","DT","ggcorrplot","Hmisc","anomalize", "fpp2", "h2o", "sweep", "timetk", "xgboost", "prophet", "survminer","ggwordcloud", "ggsn", "formattable", "IMD", "car", "RSelenium", "netstat", "fuzzyjoin", "this.path"))```

This will take a while.

After it complete to enable mapshot to work:

```webshot::install_phantomjs()```

```q()``` to exit R

Then for map work:

~~```install.packages("rgdal", type="source")```~~

RGDAL has been retired so using sf instead:

```install.packages("sf", type="source")```

Download and install R Studio:

https://rstudio.com/products/rstudio/download/

~~### Google API key for ggmap~~

~~```register_google(key = "[your key]", write = TRUE)```~~

### Stadia Maps API key for ggmap

Set Stadia Maps API key permanently:

```register_stadiamaps(key = "YOUR-API-KEY", write = TRUE)```

See https://search.r-project.org/CRAN/refmans/ggmap/html/register_stadiamaps.html

###

## Python 3 ~~packages~~

~~Python 3 will have been installed as a dependancy at some point.  Add additional packages using ```pip3 install```~~

~~```pip3 install pandas numpy matplotlib sklearn quandl xlsx2csv boto3```~~

~~(xlsx2csv is a useful tool to convert excel files into csv files with for example ```xlsx2csv -s 0 in.xlsx output```)~~

Now think it is better to install python through brew as ended up with two versions of Python 3 - one 3.7 and one 3.9.

Ended up making sure that ``python`` and ``pip`` call most up to date versions by:

``export PATH=/usr/local/opt/python/libexec/bin:$PATH``

See: https://stackoverflow.com/questions/51885394/brew-install-doesnt-link-python3

and installing again:

``pip install six``

and

``pip install openpyxl``

and fixing ghostscript by:

``sudo chown -R `whoami` /usr/local/share/doc/ghostscript``

``brew link --overwrite ghostscript``

See: https://stackoverflow.com/questions/25695934/ghostscript-not-writable

## Java

Necessary for some utilities.

Download and install the runtime environment:

https://www.java.com/en/download/mac_download.jsp

And also the development kit:

https://www.oracle.com/technetwork/java/javase/downloads/jdk13-downloads-5672538.html

### datatooltk

Speeds up the handling of data in LaTeX.

Download from:

https://ctan.org/pkg/datatooltk

Install with:

```sudo java -jar datatooltk-installer.jar```

### EPS2PGF

Download from:

https://sourceforge.net/projects/eps2pgf/files/latest/download

## Acorn

Nice graphics editor:

https://flyingmeat.com/acorn/

## Sublime Text

https://www.sublimetext.com/

## Keynote

Download from App Store.

## Microsoft Office

https://account.microsoft.com/services/office/install

## Additional Fonts

Fira Sans - download and batch install by unpacking, and selecting all files with Finder and dragging into Font Book:

https://fonts.google.com/specimen/Fira+Sans?selection.family=Fira+Sans

Tex Gyre Heroes - download and batch install by unpacking, and selecting all files with Finder and dragging into Font Book:

https://www.fontsquirrel.com/fonts/tex-gyre-heros

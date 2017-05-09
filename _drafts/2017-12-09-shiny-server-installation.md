---
layout: post
title: Install Shiny Server AWS
cover: cover.jpg
date:   2017-02-03 12:00:00
categories: Conversational
---

Before installing R we need to add the CRAN repository to indicate to the system from where does it has to download the Rpackages and R updates.

We have to add the CRAN url to the sources.list file. We do so with the following commands:

--Code--
sudo vim /etc/apt/sources.list
## Following we add the path to define R CRAN
deb https://cran.cnr.berkeley.edu/bin/linux/ubuntu xenial/


--End--

Following we download and install R. We do so with the following commands:

First I have to download the 

gpg --keyserver pgp.mit.edu --recv-key 51716619E084DAB9
gpg -a --export 51716619E084DAB9 > MRutter_cran.asc
sudo apt-key add MRutter_cran.asc


sudo apt-get update
sudo apt-get install r-base


#install shiny library
sudo su - \
-c "R -e \"install.packages('shiny', repos='https://cran.rstudio.com/')\""


#install shiny server
sudo apt-get install gdebi-core
wget https://download3.rstudio.org/ubuntu-12.04/x86_64/shiny-server-1.5.3.838-amd64.deb
sudo gdebi shiny-server-1.5.3.838-amd64.deb

#install rmarkdown
sudo su - \
-c "R -e \"install.packages('rmarkdown', repos='https://cran.rstudio.com/')\""


Sources: 
http://docs.rstudio.com/shiny-server/#ubuntu-12.04
https://www.rstudio.com/products/shiny/download-server/
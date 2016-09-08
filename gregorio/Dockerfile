FROM debian:unstable

ENV DEBIAN_FRONTEND noninteractive

# Mises à jour
RUN echo deb http://httpredir.debian.org/debian stable main >> /etc/apt/sources.list; \
	apt-get -y update ; apt-get -y dist-upgrade ; apt-get -y autoremove --purge

# Gestion de l'utf8
RUN apt-get -y install locales
RUN locale-gen C.UTF-8 && \
    /usr/sbin/update-locale LANG=C.UTF-8

ENV LC_ALL C.UTF-8

# Installation des programmes requis
RUN apt-get -y --force-yes install --no-install-recommends \
	texlive texlive-latex-extra texlive-xetex texlive-luatex \
	texlive-lang-european texlive-lang-french \
	texlive-humanities texlive-extra-utils latex-xcolor \
	texlive-fonts-extra fonts-linuxlibertine lmodern \
	texlive-metapost \
	texlive-music lilypond \
	pandoc

# Contournement temporaire d'un bug de luatex dans la version présente dans les dépôts
ADD luatex /usr/bin/

RUN fmtutil-sys --byfmt=luatex ; fmtutil-sys --byfmt=lualatex \
	fmtutil --byfmt=luatex ; fmtutil --byfmt=lualatex

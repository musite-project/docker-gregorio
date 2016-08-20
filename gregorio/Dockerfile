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
	texlive-music lilypond \
	pandoc


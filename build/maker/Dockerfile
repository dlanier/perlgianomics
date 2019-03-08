FROM ubuntu:bionic
LABEL dlanier="lanier4@illinois.edu"

#                  install basic utilities
RUN apt-get update
RUN apt-get -y upgrade
RUN apt-get update && apt-get install -y make vim git wget perl-doc

RUN cpanm CPAN::Meta readline Term::ReadKey YAML Digest::SHA Module::Build ExtUtils::MakeMaker Test::More Data::Stag Config::Simple Statistics::Lite Statistics::Descriptive 

RUN apt-get install --yes libarchive-zip-perl

# Install related DB modules
RUN apt-get install --yes libdbd-mysql libdbd-mysql-perl libdbd-pgsql

# Install GD
RUN apt-get remove --yes libgd-gd2-perl

RUN apt-get install --yes libgd2-noxpm-dev

RUN cpanm GD GD::Graph GD::Graph::smoothlines 

# BioPerl dependancies
RUN apt-get install --yes libpixman-1-0 libpixman-1-dev graphviz libxml-parser-perl libsoap-lite-perl 

#                  install perl
RUN cpan -v CJFIELDS/BioPerl-1.6.924.tar.gz


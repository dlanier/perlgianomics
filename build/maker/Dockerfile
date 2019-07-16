FROM ubuntu:14.04
LABEL dlanier="lanier4@illinois.edu"
# hints - see various docker files in:
# https://github.com/GenomicParisCentre/dockerfiles
# and all of knoweng:
# https://github.com/KnowEnG/Samples_Clustering_Pipeline/blob/master/build/docker/Dockerfile

#                  install basic utilities
RUN apt-get update
RUN apt-get -y upgrade
RUN apt-get update && apt-get install -y make vim git wget perl-doc

RUN apt-get install --yes build-essential gcc-multilib apt-utils perl expat libexpat-dev 

RUN apt-get install -y cpanminus

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

RUN cpanm Test::Most Algorithm::Munkres Array::Compare Clone PostScript::TextBlock SVG SVG::Graph Set::Scalar Sort::Naturally Graph GraphViz HTML::TableExtract Convert::Binary::C Math::Random Error Spreadsheet::ParseExcel XML::Parser::PerlSAX XML::SAX::Writer XML::Twig XML::Writer

RUN apt-get install -y libxml-libxml-perl libxml-dom-xpath-perl libxml-libxml-simple-perl libxml-dom-perl

#                  installs perl 5.18
RUN cpanm -v CJFIELDS/BioPerl-1.6.924.tar.gz
RUN cpanm Bio::Perl

RUN wget ftp://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/LATEST/ncbi-blast-2.8.1+-x64-linux.tar.gz
RUN tar zxvpf ncbi-blast-2.8.1+-x64-linux.tar.gz
# export PATH=$PATH:$HOME/ncbi-blast-2.8.1+/bin
ENV BLAST_PATH /ncbi-blast-2.8.1+/bin

RUN wget https://download.open-mpi.org/release/open-mpi/v4.0/openmpi-4.0.0.tar.gz





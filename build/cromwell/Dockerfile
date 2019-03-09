FROM ubuntu:bionic
LABEL dlanier="lanier4@illinois.edu"

# install python 2.7 3.x, java 8, cromwell 36
RUN apt-get update
RUN apt-get -y upgrade

RUN apt-get install -y default-jre
RUN apt-get install -y default-jdk
RUN export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64/
RUN export PATH=$PATH:$JAVA_HOME/bin

RUN apt-get update && apt-get install -y vim git wget

RUN apt-get install -y python3-pip

RUN pip3 install -I numpy pandas scipy scikit-learn pyyaml xmlrunner jupyter
RUN apt-get install -y python2.7 python-pip
RUN pip install --upgrade pip

#  				Wasie: Biggest 2do - add python 2.7 kernel
RUN python2 -m pip install ipykernel
RUN python2 -m ipykernel install

ENV CROMWELL_JAR_LOC  /usr/local/etc
#COPY jar_files/* ${CROMWELL_JAR_LOC}/

RUN wget https://github.com/broadinstitute/cromwell/releases/download/36/womtool-36.jar -P ${CROMWELL_JAR_LOC}
RUN wget  https://github.com/broadinstitute/cromwell/releases/download/36/cromwell-36.jar -P ${CROMWELL_JAR_LOC}

# set up for a run_directory /home directory
ENV SRC_LOC /home

# Example: Clone from github -- removes repo root name this way & allows local nameing for src
# RUN git clone https://github.com/KnowEnG/Samples_Clustering_Pipeline.git ${SRC_LOC} 

# add admin user - prevent running as root
RUN adduser --disabled-login --gecos "" ncsauser; echo "ncsauser:ncsauser" | chpasswd
RUN usermod -aG sudo ncsauser
USER ncsauser

WORKDIR ${SRC_LOC}

# Build and push pasties:
# docker build --no-cache -t aka1spanky/ncsa:devwdlV03 .
# docker login --username=${whodakine} --password=${123password4me} 
# docker push aka1spanky/ncsa:devwdlV03

# pandoc - LaTeX >> pdf
# http:http://pandoc.org/installing.html

# docker create --name=cranky_container -p 8888:8888 -p 8000:8000 -v `pwd`:/home/tmp_usr/run_dir -i aka1spanky/ncsa:devwdlV02 
# docker start cranky_container
# docker exec -it cranky_container jupyter notebook --no-browser --port=8888 --ip=0.0.0.0

# docker exec -it cranky_container jupyter notebook --generate-config
# docker exec -it cranky_container jupyter notebook password

# --- add config first else:
#FileNotFoundError: [Errno 2] No such file or directory: '/home/ncsausr/.jupyter/jupyter_notebook_config.json'

#  				Biggest 2do add default notebook set

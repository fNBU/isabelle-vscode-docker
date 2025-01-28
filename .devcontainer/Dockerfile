## for isabelle

FROM debian:latest
SHELL ["/bin/bash", "-c"]

# packages
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get -y update && \
  apt-get install -y curl less libfontconfig1 libgomp1 openssh-client perl pwgen rlwrap ssh git gpg && \
  apt-get clean

# user
RUN useradd -m isabelle && (echo isabelle:isabelle | chpasswd)
USER isabelle

# Isabelle
WORKDIR /home/isabelle
RUN curl "https://isabelle.in.tum.de/dist/Isabelle2024_linux.tar.gz" -o Isabelle.tar.gz 
RUN tar xzf Isabelle.tar.gz && \
  mv Isabelle2024 Isabelle && \
  perl -pi -e 's,ISABELLE_HOME_USER=.*,ISABELLE_HOME_USER="\$USER_HOME/.isabelle",g;' Isabelle/etc/settings && \
  perl -pi -e 's,ISABELLE_LOGIC=.*,ISABELLE_LOGIC=HOL,g;' Isabelle/etc/settings && \
  Isabelle/bin/isabelle build -o system_heaps -b HOL && \
  rm Isabelle.tar.gz

RUN echo "PATH=\$HOME/Isabelle/bin:\$PATH" >> ~/.profile

ENTRYPOINT ["/usr/bin/bash"]

FROM ubuntu:lunar

ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && apt-get install -y software-properties-common && \
    add-apt-repository multiverse && \
    dpkg --add-architecture i386 && \
    apt-get update && \
    apt-get upgrade -y

RUN sleep 5

RUN apt-get update && apt-get install steamcmd -y
RUN apt-get update && \
    apt-get install xdg-user-dirs procps -y
ENV PATH="/usr/games:${PATH}"

ARG USERNAME=steam
RUN adduser $USERNAME --disabled-password --gecos ""
USER $USERNAME

RUN steamcmd +login anonymous +app_update 1007 validate +quit && \
    steamcmd +login anonymous +app_update 2394010 validate +quit && \
    mkdir -p $HOME/.steam/sdk64/ && \
    ln -s "$HOME/.steam/SteamApps/common/PalServer/linux64/steamclient.so" $HOME/.steam/sdk64/steamclient.so

CMD [ "$HOME/.steam/SteamApps/common/PalServer/PalServer.sh" ]

# save file
# $HOME/.steam/SteamApps/common/PalServer/Pal/Saved/

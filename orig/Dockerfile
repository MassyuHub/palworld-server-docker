FROM cm2network/steamcmd:steam

USER root
RUN apt-get update && \
    apt-get install xdg-user-dirs procps -y
ENV PATH="/usr/games:${PATH}"

USER steam

RUN $HOME/steamcmd/steamcmd.sh +login anonymous +app_update 1007 validate +quit && \
    $HOME/steamcmd/steamcmd.sh +login anonymous +app_update 2394010 validate +quit

EXPOSE 1985/tcp 8211/udp 27015/udp

CMD [ "$HOME/Steam/steamapps/common/PalServer/PalServer.sh" ]

# save file
# $HOME/Steam/steamapps/common/PalServer/Pal/Saved

FROM docker/whalesay:latest

run apt-get -y update && apt-get install -y fortunes

CMD /usr/games/fortune | cowsay
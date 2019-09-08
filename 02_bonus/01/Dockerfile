FROM ubuntu

RUN apt-get update && apt-get upgrade -y && apt-get install -y build-essential git

RUN git clone https://github.com/kejlerj/Puissance4.git

CMD cd Puissance4 && make re && cd bin && ./puissance_4

FROM alpine

RUN apk update && apk upgrade && apk add build-base git

RUN git clone https://github.com/kejlerj/Puissance4.git

CMD cd Puissance4 && make re && cd bin && ./puissance_4

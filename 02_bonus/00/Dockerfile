FROM alpine

RUN apk update && apk upgrade && apk add build-base git vim curl

RUN curl https://raw.githubusercontent.com/samuelsit/Init/master/scripts/03 > project.sh

RUN echo "sh project.sh [folder_name] [user_name]"

CMD sh

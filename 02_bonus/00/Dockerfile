FROM ubuntu

RUN apt-get update && apt-get upgrade -y && apt-get install build-essential git vim curl -y

RUN curl https://raw.githubusercontent.com/samuelsit/Init/master/scripts/03 > project.sh

CMD bash && echo "sh project.sh [folder_name] [user_name]"

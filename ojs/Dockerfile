FROM ubuntu:latest

## for apt to be noninteractive
## apt install 시에 발생할 수 있는 질문거리 ex) '패키지 설치 정말 하겠습니까?' '비밀번호를 입력해주세요' 무시하고 진행할 수 있도록...
ENV DEBIAN_FRONTEND noninteractive 
ENV DEBCONF_NONINTERACTIVE_SEEN true

## 국가 시간대(timezone) 설정
## preesed tzdata, update package index, upgrade packages and install needed software
RUN echo "tzdata tzdata/Areas select Asia" > /tmp/preseed.txt; \
    echo "tzdata tzdata/Zones/Europe select Seoul" >> /tmp/preseed.txt; \
    debconf-set-selections /tmp/preseed.txt && \
    apt-get update && \
    apt-get install -y tzdata

RUN apt-get install -y wget
RUN apt-get install -y nano
RUN wget -c https://pkp.sfu.ca/ojs/download/ojs-3.4.0-1.tar.gz
RUN apt-get update
RUN apt-get install -y apache2
RUN apt-get install -y software-properties-common
RUN add-apt-repository ppa:ondrej/php
RUN apt-get update
RUN apt-get install php8.2 -y
RUN apt-get install -y mysql-server
RUN apt-get install -y php8.2-xml php8.2-xml php8.2-mysql php8.2-mbstring php-xml 
RUN tar -zxvf ojs-3.4.0-1.tar.gz
RUN mv ojs-3.4.0-1 ojs
RUN mv ojs /var/www/html
RUN rm -r ojs-3.4.0-1.tar.gz


EXPOSE 80


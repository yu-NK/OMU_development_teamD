FROM httpd:latest

RUN apt -y update && apt -y upgrade
RUN apt -y install git

RUN rm /usr/local/apache2/htdocs/* 
RUN git clone --depth 1 -b main https://github.com/yu-NK/OMU_development_teamD.git /usr/local/apache2/htdocs/.
FROM httpd:latest

RUN apt -y update && apt -y upgrade
RUN apt -y install git

RUN rm /usr/local/apache2/htdocs/* 
RUN git clone --depth 1 -b main https://github.com/yu-NK/OMU_development_teamD.git /usr/local/apache2/htdocs/.

RUN echo "git -C /usr/local/apache2/htdocs pull" >> /etc/startup.sh
RUN chmod a+x /etc/startup.sh

CMD ["bash", "-c", "sh /etc/startup.sh && httpd-foreground"]

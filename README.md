# Image automatisch bilden

Dockerfile mit folgendem Inhalt erstellen:\
$ code Dockerfile\
FROM python\
WORKDIR /app\
COPY hello.py .\
COPY start.sh .\
RUN pip install flask\
CMD ["/bin/bash", "start.sh"]

Image Version 1.0 erstellen:\
$ docker build -t flask-automated-image:1.0 .

Container mit diesem Image ausführen:\
$ docker run -it --rm -p 5000:5000 flask-automated-image:1.0

Das Dockerfile mit Umgebungsvariablen sieht wie folgt aus:\
FROM python\
WORKDIR /app\
COPY hello.py .\
RUN pip install flask\
ENV FLASK_APP "hello"\
ENV FLASK_ENV "development"\
ENV FLASK_RUN_HOST "0.0.0.0"\
CMD ["flask","run"]

Image Version 1.1 erstellen:\
$ docker build -t flask-automated-image:1.1 .

Container mit diesem Image ausführen:\
$ docker run -it --rm -p 5000:5000 flask-automated-image:1.1

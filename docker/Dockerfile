from python:3.7

USER root

RUN apt-get update && apt-get install -y --no-install-recommends apt-utils > /dev/null
RUN apt-get install -y build-essential tcl
RUN apt-get install -y systemd-sysv
RUN apt-get update  > /dev/null
RUN apt-get install  -y wget > /dev/null
RUN apt-get install  -y zip > /dev/null
RUN apt-get install  -y libaio1 > /dev/null
RUN apt-get update > /dev/null
RUN apt-get install  -y alien > /dev/null

RUN pip install -r requirements.txt

RUN adduser pythonuser && chown -R pythonuser /app
USER pythonuser

WORKDIR /app
ADD . /app

RUN useradd pythonuser && chown -R pythonuser /app

EXPOSE 8080

CMD ["uvicorn", "model_persistence_api.main:app", "--host", "0.0.0.0", "--port", "8080"]
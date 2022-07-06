FROM python:3.9.7-slim

RUN pip install -U pip
RUN pip install pipenv 

ARG userid
ARG username

ARG home=home/${username}
ARG workdir=${home}/mlflow


WORKDIR ${workdir}

COPY [ "Pipfile", "Pipfile.lock", "./" ]

RUN pipenv install --system --deploy

EXPOSE 5000
ENTRYPOINT ["mlflow", "server", "--backend-store-uri", "sqlite:///imdb_tracking.db" "--default-artifact-root", ${home}/mlruns]
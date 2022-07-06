FROM python:3.9.7-slim

RUN pip install -U pip
RUN pip install pipenv 

ARG userid
ARG username

ARG home=home/${username}
# ARG workdir=${home}


WORKDIR /home/mlflow

COPY [ "Pipfile", "Pipfile.lock", "./" ]

RUN pipenv install --system --deploy
ENV BACKEND_URI sqlite:////home/mlflow/mlflow.db
ENV ARTIFACT_ROOT /home/mlflow/mlruns

EXPOSE 5000

CMD mlflow server --backend-store-uri ${BACKEND_URI} --default-artifact-root ${ARTIFACT_ROOT} --host 0.0.0.0 --port 5000
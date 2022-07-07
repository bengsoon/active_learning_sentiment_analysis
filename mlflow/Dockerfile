FROM python:3.9.7-slim

RUN pip install -U pip
RUN pip install pipenv 

# ARG userid
# ARG username

# ARG home=home/${username}
# ARG workdir=${home}/mlflow

WORKDIR "/mlflow"

COPY [ "Pipfile", "Pipfile.lock", "./" ]

RUN pipenv install --system --deploy


ENV BACKEND_URI sqlite:////mlflow/mlflow.db
ENV ARTIFACT_ROOT /mlflow/mlruns

EXPOSE 5000

# RUN chmod 755 /home/devel/mlflow/mlruns

CMD mlflow server --backend-store-uri ${BACKEND_URI} --artifacts-destination ${ARTIFACT_ROOT} --default-artifact-root file://${ARTIFACT_ROOT} --host 0.0.0.0 --port 5000
# CMD mlflow server --backend-store-uri ${BACKEND_URI} --host 0.0.0.0 --port 5000
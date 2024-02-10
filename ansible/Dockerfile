FROM python:3.12

RUN pip install wheel ansible
RUN apt update \
    && apt install -y sshpass

WORKDIR /playbooks

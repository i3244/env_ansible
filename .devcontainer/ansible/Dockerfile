FROM python:3.8-slim-buster

WORKDIR /tmp

RUN apt-get update && apt-get install -y \
    curl    \
    git     \
    less    \
    netcat  \
    rsync   \
    sudo    \
    vim     \
    wget    \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/*

COPY requirements.txt .
RUN pip install -r requirements.txt

# create user.
ARG VSCODE_USER_ID
RUN groupadd -g ${VSCODE_USER_ID} vscode \
  && useradd -m -u ${VSCODE_USER_ID} -g vscode vscode \
  && echo "vscode ALL=(ALL) NOPASSWD: ALL" >/etc/sudoers.d/vscode

FROM ubuntu:22.04

ENV DEBIAN_FRONTEND=noninteractive \
    USER_NAME=jetbrains \
    PASSWORD=jetbrains \
    IDEA_BUILD=2024.2.1 \
    IDEA_TAR=ideaIU-2024.2.1.tar.gz \
    IDEA_URL=https://download.jetbrains.com/idea/ideaIU-2025.2.4.tar.gz

RUN apt-get update && apt-get install -y \
    curl wget openssh-server unzip fontconfig libxi6 libxrender1 libxtst6 \
    libxext6 libxrandr2 libxinerama1 libfreetype6 locales ca-certificates \
    && rm -rf /var/lib/apt/lists/*

RUN useradd -m -s /bin/bash ${USER_NAME} \
    && echo "${USER_NAME}:${PASSWORD}" | chpasswd \
    && mkdir /var/run/sshd \
    && sed -i 's/#PasswordAuthentication yes/PasswordAuthentication yes/' /etc/ssh/sshd_config

USER ${USER_NAME}
WORKDIR /home/${USER_NAME}

RUN wget -q ${IDEA_URL} \
    && tar -xzf ${IDEA_TAR} \
    && rm ${IDEA_TAR} \
    && mv idea-IU-* idea

RUN idea/bin/remote-dev-server.sh install backend \
    --host 0.0.0.0 \
    --port 7700 \
    --ide-dir /home/${USER_NAME}/idea \
    --config-dir /home/${USER_NAME}/.config/JetBrains \
    --cache-dir /home/${USER_NAME}/.cache/JetBrains

EXPOSE 22 7700
CMD ["/usr/sbin/sshd","-D"]
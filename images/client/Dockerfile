FROM openjdk:17.0.1-jdk-slim

WORKDIR /mnt 
RUN chmod 777 -R /mnt

RUN apt-get update -y && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y \
    krb5-user \
    python3 \
    python3-pip \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN python3 --version && pip3 --version

COPY config/python_requirements.txt /mnt/python_requirements.txt
RUN pip3 install --no-cache-dir -r /mnt/python_requirements.txt

COPY config/krb5.conf /etc/krb5.conf
COPY init-sh/starter-client.sh /mnt/starter-client.sh
RUN chmod +x /mnt/starter-client.sh

RUN chmod 777 -R /mnt

CMD [ "/mnt/starter-client.sh" ]
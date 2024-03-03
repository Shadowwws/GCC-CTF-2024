FROM ghcr.io/downunderctf/docker-vendor/nsjail:ubuntu-22.04

RUN apt-get update && apt-get install -y python3 && rm -rf /var/lib/apt/lists/*

RUN pip3 install pycryptodome

COPY ./src/chall.py /challenge/challenge.py

COPY ./src/flag.py /challenge/flag.py

RUN chmod +x /challenge/challenge

RUN useradd -u 666 --home=/challenge -U challenge

WORKDIR /challenge/

ENTRYPOINT ["sh", "-c", "su -c 'socat TCP-LISTEN:1337,reuseaddr,fork EXEC:python3 /challenge/challenge.py,stderr,pty,echo=0' - challenge"]

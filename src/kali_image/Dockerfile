# Kali Linux Image
FROM kalilinux/kali-rolling

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update \
    && apt-get upgrade -y \
    && apt-get install -y --no-install-recommends kali-linux-core \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

CMD ["bash"]

# Kali Linux Image
FROM kalilinux/kali-rolling

RUN apt-get update && apt-get install -y kali-linux-default \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

CMD ["bash"]

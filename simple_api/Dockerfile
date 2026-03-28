FROM python:3.13-slim

LABEL maintainer="Evane LIPOU"

WORKDIR /

COPY requirements.txt student_age.py /

RUN apt-get update && apt-get install -y \
    gcc \
    build-essential \
    python3-dev \
    libsasl2-dev \
    libldap2-dev \
    libssl-dev \
    && rm -rf /var/lib/apt/lists/*

RUN pip3 install --no-cache-dir -r /requirements.txt

VOLUME ["/data"]

EXPOSE 5000

CMD ["python3", "./student_age.py"]
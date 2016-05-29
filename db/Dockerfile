FROM postgres:9.5
RUN sed -i 's/httpredir/ftp.tw/g' /etc/apt/sources.list
RUN apt-get update && \
    apt-get install -y postgresql-9.5-postgis-2.2 postgis python-requests python-psycopg2 python-unicodecsv && \
    rm -rf /var/lib/apt/lists/*
ADD ./process.py /process.py
ADD ./postgis.sql /docker-entrypoint-initdb.d/0-postgis.sql
RUN echo "python /process.py" > /docker-entrypoint-initdb.d/1-import.sh

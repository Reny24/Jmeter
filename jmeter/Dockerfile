FROM alpine/jmeter

# Copia il file di test .jmx nella cartella /tests
COPY test.jmx /tests/test.jmx
COPY user_data.csv /tests/user_data.csv
# Imposta la cartella di lavoro a /tests
WORKDIR /tests

# Comando corretto per eseguire JMeter
ENTRYPOINT jmeter -n -t /tests/test.jmx -l /tests/results.jtl



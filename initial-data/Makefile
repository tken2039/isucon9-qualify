include /home/app/isu.env

all: build install-sql

build: Dockerfile *.tsv *.pl
	echo $(INITPATH)/isucon9-qualify/initial-data
	docker build -t isucon9-qualify/initial-data .
	docker run -v $(INITPATH)/isucon9-qualify/initial-data/result:/opt/initial-data/result -v $(INITPATH)/isucon9-qualify/initial-data/pwcache:/opt/initial-data/pwcache --name isu-main isucon9-qualify/initial-data

install-sql:
	install -m 0644 /opt/initial-data/result/initial.sql ../webapp/sql/initial.sql

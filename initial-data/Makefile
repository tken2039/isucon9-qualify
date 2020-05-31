include /home/app/isu.env

all: build install-sql

build: Dockerfile *.tsv *.pl
	@if [ ! -f "/home/isucon9-qualify/initial-data/result/category_json.txt" ]; then \
		docker build -t isucon9-qualify/initial-data . ; \
		docker run \
		-v $(INITPATH)/isucon9-qualify/initial-data/result:/opt/initial-data/result \
		-v $(INITPATH)/isucon9-qualify/initial-data/pwcache:/opt/initial-data/pwcache \
		isucon9-qualify/initial-data
	fi

install-sql:
	install -m 0644 /home/isucon9-qualify/initial-data/result/initial.sql ../webapp/sql/initial.sql

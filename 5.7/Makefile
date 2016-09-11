current_dir = $(shell pwd)

build:
	docker build -f Dockerfile -t my_sql .

build-phpadmin:
	docker pull phpmyadmin/phpmyadmin

start-sql:
	docker run -d -p 3306:3306 -e MYSQL_ROOT_PASSWORD=my-secret-pw \
	-v $(current_dir)/database:/var/lib/mysql --name mysql my_sql

start-phpadmin:
	docker run --name myadmin -d --link mysql -p 8080:80 -e PMA_HOST=mysql phpmyadmin/phpmyadmin

clean:
	docker rm -f $$(docker ps -qa)
	docker rmi -f $$(docker images -qa)

# create database my_resume;
# use my_resume;
# create table companies (name VARCHAR(20), city VARCHAR(20), state VARCHAR(10), info VARCHAR(30), start_date DATE, end_date DATE);
# insert into companies values ('Honda', 'Marysville', 'OH', 'Research on corrosion detector', '2012-08-01', '2013-05-01');

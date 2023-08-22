Imersão fullcycle 21/08/2023.
Aplicação GO, com api http comunicando apache kafka e banco de dados mysql.
apos subir o docker-compose:
1 - acessar mysql para criar tabela:
    mysql -uroot -p products
    inserir senha
    create table products (id varchar(255), name varchar(255), price float);
    show tables; -- verificar tabela criada
    use products;
    select * from products; --listar
2 - acessar kafka
    kafka-topics --bootstrap-server=localhost:9092 --topic=product --create
3 - acessar goapp
    go run cmd/app/main.go

Validação API:
acessar teste.http
dica: extensão REST client vscode

teste via linha de comando:
- inserir registro:
    curl -d '{"name": "My Product", "price": 100}' -X POST http://localhost:8000/products
- ler registros:
    wget http://localhost:8000/products
    curl http://localhost:8000/products

Teste criar registro no mysql:
    insert into products values ('abc','produto manual',250);

Teste produzir evento no kafka:
    kafka-console-producer --bootstrap-server=localhost:9092 --topic=product
	> {"name": "My Product kafka", "price": 300}




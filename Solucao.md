# Solução

## 1. Containerização

A aplicação foi dividida em 3 containeres, web, api e db. Passos para rodar a aplicação:

- Construir os containers:
```
    docker-compose build
```

- Executar os containers:
```
    docker-compose run
```

Caso seja a primeira vez rodando a aplicação, é necessário criar o banco e as migrations:

- Criar o banco:
```
    docker-compose run --rm api rake db:create
```

- Criar as migrations:
```
    docker-compose run --rm api rake db:migrate
```

Para executar os testes:
- Frontend:
```
    docker-compose run --rm yarn run test:unit
```

- Backend:
```
    docker-compose run --rm bundle exec rails test
```

**Dica**: Se o serviço db não puder iniciar porque a porta 5432 já estiver sendo usada:

- Listar portas:
```
    sudo lsof -i -P -n | grep LISTEN
```

- Parar o serviço postgres:
```
    sudo service postgresql stop
```

Após isso, execute de novo o comando que deu problema. Não se esqueça reiniciar o serviço postgresql quando terminar de usar os containers:

```
    sudo service postgresql start
```

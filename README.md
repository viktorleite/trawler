# Trawler 
Trawler é apenas um pequeno conjunto de arquivos que configura um ambiente de desenvolvimento laravel usando Docker.

### Como usar

Faça o clone do repositório
```sh
git clone https://github.com/viktorleite/trawler.git
```

Copie os arquivos para o seu projeto
```sh
cp -rf trawler/* seu_projeto/
```

```sh
cd seu_projeto
```

Compile a imagem:
```sh
docker-compose build
```
Executar o ambiente em segundo plano:
```sh
    docker-compose up -d
```
Executar comandos nos containers:
```sh
    docker-compose exec app ${commands}
```
Copie os arquivos para seu projeto
    cp -rf trawler/* seu_projeto/

    cd seu_projeto

Compile a imagem:
    $ docker-compose build

Executar o ambiente em segundo plano:
    $ docker-compose up -d

Executar comandos nos containers:
    $ docker-compose exec app ${commands}


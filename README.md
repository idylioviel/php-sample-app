# Passo a passo

1- Fazer download do Docker Quickstart terminal (para funcionar no windows)
2- Após instalar, abrir o quickstart terminal e naveguar até a pasta do projeto /php-sample-app
3- Para aplicação funcionar 100% é necessária a montagem de duas imagens
3.1- Navegue até a pasta frontend e execute o comando e espere o docker baixar as dependências

``` sh
  docker build . -t frontend
```

3.2- Agora vá até a pasta backend e execute:

``` sh
  docker build . -t db
```

4- Após a montagem das duas imagens, vamos dar start no banco e uni-las
4.1- Startando

``` sh
  docker run -d --rm -e MYSQL_DATABASE='demo' -e MYSQL_ALLOW_EMPTY_PASSWORD='yes' --name backend db
```

4.2- Unindo

``` sh
  docker run -d -p 80:80 --name php-sample-app --link backend frontend
```

5- Aplicação deverá estar no ar. Para acessar, digitar no navegador 192.168.99.100:80

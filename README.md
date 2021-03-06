# XY Inc | Pontos de Interesse (POIs) #


Plataforma para disponibilização de um dispositivo inovador que auxilia pessoas para encontrar pontos de interesse (POIs).
A mesma foi desenvolvida em uma arquitetura de serviços utilizando os principios básicos do [REST](https://pt.wikipedia.org/wiki/REST).

O frontend é baseado em uma aplicação [Angular](https://angularjs.org/) e o backend é composto de web services baseados na implementação do [Spring RESTful](https://spring.io/guides/gs/rest-service/) utilizando o JSON como trafego de informações.


### Dependências ###

As seguintes dependências são necessárias:

- [Java Development Kit](http://www.oracle.com/technetwork/java/javase/downloads/index.html) (versão 8)
- [Maven](https://maven.apache.org/) (versão 3.3 ou maior)
- [Node.js](https://nodejs.org/) (versão 4.2.2 ou maior)
- [Grunt](http://gruntjs.com/) - execute: `npm install -g grunt-cli`
- [MySQL]() - servidor de banco de dados;


### Configurando o banco de dados ###
Acesse a interface do seu banco de dados MySQL e execute o seguinte procedimento:
- Crie 2 banco de dados, sendo 1 para executar a aplicação e outro para executar os testes automatizados.

Para configurar os banco de dados na aplicação, acesse:

    src/main/resources/application.properties (Configurações de produção)

    src/main/resources/application-test.properties (Configurações para os testes)

### Instalando a aplicação ###
Execute o comando para clonar (copiar) o projeto:

    git clone https://github.com/marlonmleite/xy-inc.git
    
### Inicializando a aplicação ###

Acesse a pasta do projeto copiado por linha de comando;

Inicie a aplicação com o comando (nesse momento não executa testes):

    mvn spring-boot:run

Após a inicialização do servidor, a aplicação será acessível na URL:

    http://localhost:8080/
    
### Testes automatizados ###

Acesse a pasta de seu projeto por linha de comando;

Execute os testes da aplicação com o comando:

    mvn clean test

Será exibido os resultados no console.


### Compilando e iniciando o servidor ###

Acesse a pasta de seu projeto por linha de comando;

Nesse passo da compilação, os testes automatizados são executados automaticamente.

Compile o projeto com o Maven:

    mvn clean install

Execute a aplicação apartir do diretório `target`:

    java -jar xy-inc-0.0.1-SNAPSHOT.jar

Após a inicialização do servidor, a aplicação será acessível na URL:

    http://localhost:8080/


### Frontend Overview ###

- O projeto é uma aplicação web com uma interface baseada em AngularJS, HTML5 e CSS3.
- A aplicação é responsiva, uma vez que se adapta a diferentes tamanhos de tela.
- Com o intuito de fornecer a melhor interface para o usuário, foi utilizado o conceito de [Material Design](https://www.google.com/design/spec/material-design/introduction.html) desenvolvido pelo Google com o objetivo de alcançar as melhores práticas de usabilidade, acessibilidade e mobilidade.

### Backend Overview ###

- A aplicação do servidor é baseado em Java 8, Spring, JPA e MySQL.
- As configurações do Spring são baseadas em anotações Java e 1 arquivo de .properties para configuração do banco de dados.
- É utilizado os módulos: Spring MVC, Spring RESTful, Spring Data JPA e Spring Test.

As informações consumidas e produzidas nos web services são todas em JSON.
Os serviços web são baseados no Spring MVC, JSON e com a implementação do Spring RESTful.

Os testes de unidades são feitos com o spring test e as funcionalidades da API REST são testados utilizando o [Spring test MVC](http://docs.spring.io/spring/docs/current/spring-framework-reference/html/testing.html#spring-mvc-test-framework).


#### API REST ####

A API REST do servidor expõe o seguinte serviço:

##### Pontos de Interesse #####

Url           |Verb          |Request Body  | Description
--------------|------------- |------------- | -------------
/ws/poi       |GET          |void|lista todos os pontos de interesse cadastrado na aplicação.
/ws/poi|POST|JSON| cria um novo ponto de interesse.
/ws/poi| PUT|JSON| atualiza um ponto de interesse caso exista.
/ws/poi/{id}|GET|void| retorna um ponto de interesse apartir do identificador único (`id`).
/ws/poi/{id}|DELETE|void| apaga um ponto de interesse apartir do identificador único (`id`).
/ws/poi/search?x={x}&y={y}&dMax={dMax}|GET|void| busca pontos de interesse baseado em uma localização `x`, `y` e uma distância máxima (`dMax`).

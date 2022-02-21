# tarefas-do-curso-Guia-de-sobreviv-ncia-do-programador---aluno-s-rgio-spezzia
tarefas do curso Guia de sobrevivência do programador - aluno sérgio spezzia - GSP - EP1 - exercício programa 1 - Tarefas - git, metaprogramação, containers e cloud, shell 
Git




Verifique qual o id do commit em que as páginas do juwupiter weeb foram adicionadas, bem como seu autor e data. Registre essas infos em um arquivo TAREFAS.md





git log




$ git clone https://github.com/schacon/simplegit-progit





$ git log
commit ea82a6dfg817ec66f47342007242699h93763948
Author: Sérgio Spezzia <sergio.spezzia@unifesp.br>
Date:   Mon Feb 21 08:24:19 2022 -1720



Metaprogramação



adicione um script no package.json para rodar todos os testes de unidade na pasta src. 

crie um teste de unidade que você achar interessante, utilize pelo menos um expect e uma função de mock (jest.fn(), nesse caso).



1 npm init

1 jest



1 {
2  "name": "tdd-jest",
3  "version": "1.0.0",
4  "description": "",
5  "main": "index.js",
6  "scripts": {
7    "test": "jest"
8  },
9  "author": "Sérgio",
10  "license": "ISC"
11 }




1 npm test


1 npm install --save-dev jest


1 jest --init



1 //index.test.js
2 const index = require('./index')
3 test('verificar variável n', () => {
4    const result = index.verificar variável n(7,1);
5    expect(result).toEqual(4);
6 })







1 module.exports = {
2    clearMocks: true,
3    collectCoverage: true,
4    coverageDirectory: "coverage",
5    coverageProvider: "v5",
6    testEnvironment: "node",
7 };




1 npm i -D jest



1 //mylibs/coollib.js
2 const fs = require('fs');
3
4 function findTestTxt() {
5    const files = fs.readdirSync('./');
6    return files.some(f => f === 'test.txt');
7 }
8
9 module.exports = { findTestTxt }





1 //index.test.js
2 const coollib = require('../mylibs/coollib');
3
4 test('Encontrar o arquivo', () => {
5    const result = coollib.findTestTxt();
6    expect(result).toBeTruthy();
7 })






1 {
2  "name": "mock-tests",
3  "version": "1.0.0",
4  "description": "",
5  "main": "jest.config.js",
6  "scripts": {
7    "test": "jest"
8  },
9  "keywords": [],
10  "author": "",
11  "license": "ISC",
12  "devDependencies": {
13    "jest": "^26.6.3"
14  }
15 }







1 module.exports = {
2    readdirSync: (path) => {
3        return ['test.txt', 'outro-arquivo.txt'];
4    }
5 }







1 //index.test.js
2 const coollib = require('../mylibs/coollib');
3 
4 jest.mock('fs');
5 
6 test('Encontrar o arquivo', () => {
7    const result = coollib.findTestTxt();
8    expect(result).toBeTruthy();
9 })




Containers e Cloud



Crie um Dockerfile para aplicação

Suba um container utilizando o Dockerfile criado e exponha a porta 3000 do container para a sua porta 8080. 
Acesse a aplicação no navegador do computador hospedeiro, registrando os passos realizados para tal em um arquivo TAREFAS.md



docker build -t nome_da_imagem



# syntax=docker/dockerfile:1
FROM python:3.7-alpine
WORKDIR /code
ENV FLASK_APP=app.py
ENV FLASK_RUN_HOST=0.0.0.0
RUN apk add --no-cache gcc musl-dev linux-headers
COPY requirements.txt requirements.txt
RUN pip install -r requirements.txt
EXPOSE 3000
COPY . .
CMD ["flask", "run"]



version: "3.9"
services:
web:
build: .
ports:
- "3000:8080"
redis:
image: "redis:alpine"




Shell
 


Crie um script em shell para gerar a imagem Docker e subir um container a partir dessa imagem. 

Esse script deve permitir que o usuário escolha em qual porta do computador hospedeiro a aplicação deve rodar.







docker image list


docker image pull python


docker image inspect python


docker container run <parâmetros> <imagem> <CMD> <argumentos>


docker container run -it --rm --name unifesp_python python bash


docker container run -it --rm -p "<host>:<container>" python


docker container run -it --rm -p 40:4040 python







ou





docker container run -it --name containerunifesp ubuntu:16.04 bash


apt-get update
apt-get install nginx -y
exit



docker container stop containerunifesp


docker container commit containerunifesp meuubuntu:nginx






docker image list




docker container run -it --rm meuubuntu:nginx dpkg -l nginx




docker container run -it --rm ubuntu:16.04 dpkg -l nginx









docker image list




docker image pull python




docker image inspect python




docker container run <parâmetros> <imagem> <CMD> <argumentos>




docker container run -it --rm --name meu_python python bash




docker container run -it --rm -p "<host>:<container>" python




docker container run -it --rm -p 50:5050 python
















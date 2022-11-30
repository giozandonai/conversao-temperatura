# Projeto conversão de temperatura

## Sobre o projeto

O projeto conversão de temperatura é um projeto desenvolvido em NodeJS. O projeto tem como objetivo ser um exemplo para a criação de ambiente com containers usando NodeJS.

### Observações do projeto
A aplicação é exposta:<br>
**docker compose** Usando a porta 8080<br>
**Kubernetes** Usando o ingress bare metal na porta 80<br>

**srv/Dockerfile**
```
FROM node:16.15.1
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 8080
CMD ["node", "server.js"]
```

**Docker Hub - [giozandonai](https://hub.docker.com/u/giozandonai)**

**Criando a imagem sem o compose:** `$ docker build -t giozandonai/conversao-temperatura:v1 .`

**Enviando imagem:** `$ docker push giozandonai/conversao-temperatura:v1`

**Adicionando tag latest:** `$ docker tag giozandonai/conversao-temperatura:v1 conversao-temperatura:latest`

**Enviando imagem:**
`$ docker push giozandonai/conversao-temperatura:latest`

## Subindo com DOCKER COMPOSE
`$ docker-compose up -d`

**Rodando com o Docker run:**
`$ docker container run -d --name conversao-temperatura -p 8080:8080 giozandonai/conversao-temperatura:v1`

**Acessando a aplicação:**
`http://localhost:8080``

## Subindo com KUBERNETES
Acessar a pasta ./k8s:<br>
`kubectl apply -f . -R`<br>
`http://nome_dominio`<br>

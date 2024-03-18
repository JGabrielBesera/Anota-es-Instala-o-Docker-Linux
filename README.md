# dentro do terminal do linux:
sudo apt install curl
sudo curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo apt install nodejs npm
sudo docker run hello-world
cd ~
mkdir projeto
cd projeto
sudo apt install nodejs npm
code . (com o visual code instalado dentro da maquina virtual)

# agora dentro do terminal do visual code, estando dentro da pasta, digite:
npm i express
node app.js (nome do seu arquivo.js)

# dentro da pasta, criado o app.js requerir o express e colocar pra escutar na porta desejada, como no exemplo abaixo:

const express = require('express') ;
const app = express();
const port = 3000

app.get('/', (req, res) => {
    console.log(`Ola minha imagem`);
})

app.listen(port, () => {
    console.log(`Está Rodando na Porta: ${port}`);
})

# criar o "dockerfile" e inserir os seguintes códigos:

FROM node

// trabalhando com o node ele vai executar todos os próximos comandos

WORKDIR /app

// criar e mostra o diretório que a gente vai trabalhar, onde vamos rodar a aplicação

COPY package*.json .

// copia e le o json dentro do container

RUN npm install

// instala os pacotes que a aplicação necessita

COPY . .

// o primeiro ponto significa origem e destino, no caso pegar da minha raiz, o segundo ponto é o destino, raiz do diretório de trabalho,
// ele vai copiar tudo que ta na minha raiz, pro meu container

EXPOSE 3000

// mostrar/expor a porta do container

CMD ["node", "app.js"]

// ele literalmente vai rodar o servidor

# após isso, dar o bluid no terminal do linux estando dentro do projeto:
sudo docker build .
sudo docker image ls (mostrar imagens, a que criamos vai estar sem nome por padrão)
# fechar o programa rodando dentro vscode, assim n vai interferencia no uso da porta pelo terminal do vscode e do linux
docker run -p 3000:3000 0a373ef117ce (comando que roda o container, esse código vai ser o endereço da "IMAGE ID" que aparece dps do comando ls)




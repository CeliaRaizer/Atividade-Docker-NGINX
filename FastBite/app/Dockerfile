#define a imagem base
FROM node:18-alpine
#define pasta de trabalho dentro do container
WORKDIR /app
#copia package.json
COPY package*.json ./
RUN npm install
#copia resto do projeto
COPY . .
EXPOSE 3000
#define o comando que será executado quando o container iniciar
CMD ["node", "index.js"]
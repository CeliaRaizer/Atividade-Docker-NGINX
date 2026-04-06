# Atividade-Docker-NGINX

## FastBite

A aplicação foi containerizada utilizando Docker, separando o serviço Node.js e o servidor Nginx em containers distintos. O Nginx atua como reverse proxy, recebendo requisições na porta 80 e encaminhando para o container da aplicação na porta 3000 através de uma rede interna do Docker. Dessa forma, o Node.js não fica exposto diretamente, garantindo maior segurança, organização e escalabilidade da aplicação.

### Dockerfile
- Cria um container com Node.js
- Copia seu projeto pra dentro
- Instala as dependências
- Inicia a aplicação na porta 3000

### Nginx

- Nginx escutar na porta 80
- Receber acessos da internet
- Encaminhar tudo para o Node (porta 3000)
- Esconder o servidor Node da internet

### Docker-compose.yml

- Organiza tudo: app, nginx

## TechVision

A aplicação cria um único servidor Nginx em Docker capaz de hospedar dois sites diferentes, escolhendo qual exibir com base no domínio acessado.

### Dockerfile

- Usa a imagem oficial do Nginx
- Remove a configuração padrão do servidor
- Copia a configuração personalizada (virtual hosts)
- Copia os arquivos do blog para o container
- Copia os arquivos da documentação para o container
- Deixa o Nginx pronto para servir dois sites diferentes

### Nginx (default.conf)

- Define dois servidores (virtual hosts) no mesmo Nginx
- Escuta na porta 80 (HTTP)
- Usa o domínio para decidir qual site mostrar (server_name)
- Aponta cada domínio para uma pasta diferente (root)
- Define o index.html como página principal
- Retorna erro 404 caso o arquivo não exista (try_files)

### Docker-compose.yml
- Define o serviço do Nginx
- Constrói a imagem usando o Dockerfile (build: .)
- Nomeia o container como techvision-nginx
- Mapeia a porta 80 do container para a porta 80 do computador
- Permite acessar o servidor pelo navegador (http://localhost)
Esse repositório foi pensado para ser possível rodar um projeto de estudos utilizando PHP, Laravel, com consulta a um banco de dados, usando NGIX e MYSQL.

No estado atual, este projeto presupõe que dentro do diretório em que esses arquivos aqui presentes estarão, haverá várias subpastas de projetos, sendo possível alternar a execução em containers de um projeto para outro.

Para isso no .env do projeto há te ter um PROJECT_PATH=./ para dizer o caminho relativo do composer até o projeto que se quer executar

Passos para Executar esse projeto:

# 1. Clonar este repositório
git clone https://github.com/Lucas-S-Guilherme/nginx-mysql-php-laravel-docker.git
cd nginx-mysql-php-laravel-docker

# 2. Clonar ou iniciar um repositório
Inicie o projeto Laravel que deseje dentro da pasta clonada deste projeto.
git clone {uri do seu projeto.git}
ou
faça um diretório e dê git init dentro dele

# 3. Configure as variáveis de ambiente desse seu novo projeto
Utilize o .env.example deste projeto para configurar seu .env no projeto.
A principal diferença é o campo
  # caminho relativo do composer até o projeto atual
  PROJECT_PATH=./ 

# 4. Inicie os containeres. Fluxo usado agora para vários projetos laravel no mesmo diretório:

Para subir: docker compose --env-file ./pasta_do_projeto/.env up -d

Para ver os logs: docker compose --env-file ./pasta_do_projeto/.env logs -f

Para derrubar: docker compose --env-file ./pasta_do_projeto/.env down
  
# 5. Instalar dependências PHP do seu projeto
docker compose exec app composer install

# 6. Gerar APP_KEY do Laravel
docker compose exec app php artisan key:generate
Copie esse key gerada para a variável APP_KEY= no .env

# 7. Rodar as migrações (Se houver)
docker compose exec app php artisan migrate

# 8. Instalar dependências Node (se houver)
docker compose exec app npm install && npm run build

# continue seu projeto

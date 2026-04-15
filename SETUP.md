Passos para alguém clonar e rodar em outra máquina:


# 1. Clonar o repositório
git clone seu-repo
cd seu-repo

# 2. Copiar e configurar o .env
cp notes/.env.example notes/.env
# Editar notes/.env conforme necessário

# 3. Iniciar os containers
docker compose up -d

# 4. Instalar dependências PHP
docker compose exec app composer install

# 5. Gerar APP_KEY do Laravel
docker compose exec app php artisan key:generate

# 6. Rodar as migrações
docker compose exec app php artisan migrate

# 7. Instalar dependências Node (se houver)
docker compose exec app npm install && npm run build

# 8. Fluxo usado agora para vários projetos laravel no mesmo diretório:

Para subir: docker compose --env-file ./pasta_do_projeto/.env up -d

Para ver os logs: docker compose --env-file ./pasta_do_projeto/.env logs -f

Para derrubar: docker compose --env-file ./pasta_do_projeto/.env down
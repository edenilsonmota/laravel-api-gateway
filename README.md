# laravel-api-gateway
Projeto em desenvolvimento

### 🚀 Como rodar o projeto

1. Clonar o repositório

```bash
git clone https://github.com/edenilsonmota/laravel-api-gateway.git
cd laravel-api-gateway/
```

2. Configurar o arquivo .env
Crie o arquivo de ambiente a partir do exemplo:

```Bash
cp .env.example .env
```
Configurar as variáveis de banco de dados no .env:

```
DB_CONNECTION=pgsql
DB_HOST=pgsql
DB_PORT=5432
DB_DATABASE=laravel
DB_USERNAME=sail
DB_PASSWORD=password
```
3. Instalar as dependências via Docker
Via docker:

```Bash
docker run --rm \
    -u "$(id -u):$(id -g)" \
    -v "$(pwd):/var/www/html" \
    -w /var/www/html \
    laravelsail/php85-composer:latest \
    composer install --ignore-platform-reqs
```
4. Subir os containers do Sail:

```Bash
./vendor/bin/sail up -d
```
5. Execute a geração de chave, migrações do banco e build de assets:

```Bash
# Gerar chave de criptografia da aplicação
./vendor/bin/sail artisan key:generate

# Executar as migrações + seed
./vendor/bin/sail artisan migrate --seed

# Instalar e compilar dependências do frontend (Vite/Tailwind)
./vendor/bin/sail npm install
./vendor/bin/sail npm run build
```

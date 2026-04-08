# Instalação do Laravel

Neste lab você vai configurar um ambiente Laravel do zero na sua máquina local.

---

## Pré-requisitos

Antes de começar, certifique-se de ter instalado:

- **PHP** >= 8.1
- **Composer** (gerenciador de pacotes do PHP)
- **Node.js** >= 16 (para assets com Vite)

---

## 1. Instalando o Composer

O Composer é essencial para qualquer projeto Laravel. Se ainda não tiver, instale:

```bash
# Linux / macOS
curl -sS https://getcomposer.org/installer | php
sudo mv composer.phar /usr/local/bin/composer

# Verificar instalação
composer --version
```

---

## 2. Criando o projeto Laravel

Com o Composer instalado, crie um novo projeto:

```bash
composer create-project laravel/laravel meu-projeto
cd meu-projeto
```

> 💡 Isso vai baixar o Laravel e todas as dependências automaticamente.

---

## 3. Subindo o servidor de desenvolvimento

O Laravel tem um servidor embutido via Artisan:

```bash
php artisan serve
```

Abra o browser em `http://localhost:8000` — você vai ver a tela de boas-vindas do Laravel.

---

## 4. Estrutura do projeto

Após a instalação, a estrutura principal é:

```
meu-projeto/
├── app/
│   ├── Http/
│   │   └── Controllers/   # Seus controllers
│   └── Models/            # Seus models
├── routes/
│   └── web.php            # Rotas da aplicação
├── resources/
│   └── views/             # Templates Blade
├── database/
│   └── migrations/        # Migrações do banco
└── .env                   # Variáveis de ambiente
```

---

## 5. Configurando o `.env`

O arquivo `.env` na raiz do projeto guarda as configurações do ambiente. O mais importante inicialmente é o banco de dados:

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=meu_banco
DB_USERNAME=root
DB_PASSWORD=sua_senha
```

Depois de editar, rode:

```bash
php artisan config:clear
```

---

!!! success "Pronto!"
    Seu ambiente Laravel está configurado. Próximo passo: [Primeiros Passos →](./primeiros-passos.md)

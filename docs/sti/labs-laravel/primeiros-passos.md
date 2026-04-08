# Primeiros Passos no Laravel

Agora que o ambiente está rodando, vamos entender as três peças fundamentais do Laravel: **rotas**, **controllers** e **views**.

---

## Rotas

As rotas ficam em `routes/web.php`. É aqui que você define o que acontece quando alguém acessa uma URL.

```php
// routes/web.php

// Rota simples — retorna texto direto
Route::get('/ola', function () {
    return 'Olá, mundo!';
});

// Rota apontando para um controller
Route::get('/usuarios', [UsuarioController::class, 'index']);

// Rota com parâmetro dinâmico
Route::get('/usuario/{id}', [UsuarioController::class, 'show']);
```

---

## Controllers

Controllers organizam a lógica da sua aplicação. Para criar um:

```bash
php artisan make:controller UsuarioController
```

Isso vai gerar o arquivo em `app/Http/Controllers/UsuarioController.php`:

```php
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;

class UsuarioController extends Controller
{
    // Lista todos os usuários
    public function index()
    {
        $usuarios = ['Ana', 'Bruno', 'Carlos'];

        return view('usuarios.index', compact('usuarios'));
    }

    // Exibe um usuário específico
    public function show(string $id)
    {
        return view('usuarios.show', ['id' => $id]);
    }
}
```

---

## Views (Blade)

As views ficam em `resources/views/`. O Laravel usa o **Blade**, um sistema de templates simples e poderoso.

Crie o arquivo `resources/views/usuarios/index.blade.php`:

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Usuários</title>
</head>
<body>
    <h1>Lista de Usuários</h1>

    <ul>
        @foreach ($usuarios as $usuario)
            <li>{{ $usuario }}</li>
        @endforeach
    </ul>
</body>
</html>
```

> 💡 `{{ }}` escapa o HTML automaticamente. Use `{!! !!}` apenas quando confiar 100% no conteúdo.

---

## Testando tudo junto

Com o servidor rodando (`php artisan serve`), acesse:

```
http://localhost:8000/usuarios
```

Você vai ver a lista de usuários renderizada pela view.

---

!!! tip "Dica"
    Use `php artisan route:list` para ver todas as rotas registradas na aplicação.

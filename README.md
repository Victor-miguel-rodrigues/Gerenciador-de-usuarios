# Gerenciador de Usuários PHP + MySQL

## Estrutura de Pastas

```
crud-completo/
│
├── Banco-dados/
│   └── db-connect.php         # Conexão com o banco de dados (não subir no Git)
│
├── acoes/
│   ├── logicaCadastro.php     # Processa cadastro de usuários
│   └── logicaLogin.php        # Processa login de usuários
│
├── func/
│   ├── cadastro.php           # Formulário de cadastro
│   └── login.php              # Formulário de login
│
├── adm/
│   └── index.php              # Painel Admin com contagem de usuários
│
└── src/
    └── index.php              # Página inicial do sistema
```

---

## Funcionalidades Atuais

### 1. Cadastro de Usuário (`func/cadastro.php`)

* Formulário para `nome`, `email`, `senha`, `idade`.
* Processamento em `acoes/logicaCadastro.php`:

  * Limpeza de entradas com `mysqli_escape_string` e `htmlspecialchars`.
  * Criptografia da senha com `password_hash`.
  * Validação de idade >= 18.
  * Inserção no banco `usuarios`.
  * Redirecionamento com mensagens de sucesso ou erro.

### 2. Login de Usuário (`func/login.php`)

* Formulário com `email` e `senha`.
* Processamento em `acoes/logicaLogin.php`:

  * Consulta senha pelo email.
  * Validação com `password_verify`.
  * Criação de sessão `$_SESSION['logado']`.
  * Redirecionamento para painel admin.

### 3. Painel Admin (`adm/index.php`)

* Mostra quantidade total de usuários cadastrados:

  ```php
  $sql = 'SELECT COUNT(*) FROM usuarios';
  $resultado = mysqli_query($conexao,$sql);
  $dados = mysqli_fetch_assoc($resultado);
  echo $dados['COUNT(*)'];
  ```
* Base para futuras estatísticas e controle de usuários.

### 4. Página Inicial (`src/index.php`)

* Links para login e cadastro.
* Descrição do sistema.

---

## Futuros Implementos

1. **Controle de usuários**:

   * Usuários ativos vs desativados.
   * Usuários recém-cadastrados.
   * Habilitar edição e remoção de usuários.

2. **Estatísticas e gráficos**:

   * Gráficos de usuários ativos, desativados e totais (usando Chart.js ou Google Charts).
   * Número de logins por dia.
   * Estatísticas de cadastro por faixa etária.

3. **Segurança e validação**:

   * Bloquear HTML e scripts nos inputs.
   * Validação de email e idade mais rigorosa.
   * Proteção contra SQL Injection e XSS.
   * Timeout e gerenciamento de sessões.

4. **Interface do painel**:

   * Dashboard visual com gráficos e tabelas.
   * Filtro e pesquisa de usuários.
   * Paginação em listas longas.

5. **Funcionalidades extras para iniciantes**:

   * Feedback visual ao cadastrar ou logar (mensagens coloridas).
   * Possibilidade de reset de senha.
   * Notificações de erro detalhadas.

6. **Preparação para GitHub**:

   * `.gitignore` para arquivos sensíveis.
   * README.md com instruções de instalação.
   * Estrutura limpa e organizada para portfólio.

---

## Tecnologias Utilizadas

* PHP procedural
* MySQL
* HTML básico
* Sessions para login

---

**Observações**:

* Projeto funcional como CRUD básico, pronto para melhorias e adição de estatísticas visuais.

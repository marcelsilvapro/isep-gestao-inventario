# ADM Inventories — Sistema de Gestão de Stock e Encomendas

Aplicação web *full-stack* desenvolvida em **PHP, MySQL, HTML, CSS e JavaScript** para gestão de inventário, clientes, encomendas e utilizadores com controlo de acessos por perfil.

Projeto académico realizado em grupo no âmbito da unidade curricular **DEAPC (Desenvolvimento de Aplicações Computacionais)** da **Licenciatura em Engenharia Eletrotécnica e de Computadores (LEEC)** no **ISEP** (1.º ano, 2.º semestre, 2024/2025).

---

## Funcionalidades Principais

- **Autenticação e Controlo de Acessos (`Index.html`, `scripts/login.php`, `scripts/logout.php`):**
  - Login baseado em sessões PHP (`$_SESSION`) com redirecionamento automático e proteção de rotas consoante o perfil (**Administrador** ou **Utilizador**).
- **Área de Utilizador (`uti1.php` – `uti3.php`):**
  - **Gestão de Encomendas:** pesquisa de encomendas, consulta de produtos associados e atualização do estado (`NEW`, `SENT`, `CANCELLED`, com reposição automática de stock em caso de cancelamento).
  - **Consulta de Stock e Clientes:** pesquisa dinâmica em tempo real de produtos e fichas de clientes.
- **Área de Administrador (`admin1.php` – `admin5.php`):**
  - **Gestão e Criação de Encomendas:** criação de novas encomendas com associação a clientes/produtos e gestão completa do ciclo de vida.
  - **Gestão de Stock e Clientes:** consulta, edição e eliminação direta de registos de produtos e clientes na base de dados.
  - **Registo de Novos Produtos e Clientes:** formulários dedicados com validação e preenchimento assistido.
  - **Gestão de Utilizadores:** listagem de contas existentes e criação de novos utilizadores/administradores com geração automática de palavra-passe via *trigger* MySQL (`generate_password`).

---

## A Minha Contribuição

- Desenvolvimento da **página inicial (`Index.html`)** e da **folha de estilos principal (`styles/style.css`)**.
- Implementação do **sistema de autenticação e sessões PHP** (`login.php`, `logout.php`) e proteção de acesso por perfil nas páginas de utilizador e administrador.
- Desenvolvimento da **Área de Utilizador (`uti1.php`)** e integração entre as interfaces e os *scripts* de ligação à base de dados.

---

## Estrutura do Repositório

```text
isep-gestao-inventario/
├── Index.html                  # Página inicial e formulário de login
├── admin1.php … admin5.php     # Painéis da área de administração
├── uti1.php … uti3.php         # Painéis da área de utilizador
├── uti2Template.html           # Template auxiliar da gestão de encomendas
├── scripts/                    # Endpoints PHP (autenticação, CRUD, consultas AJAX)
│   ├── db_config.php           # Configuração central de ligação MySQL
│   └── db_config.example.php   # Exemplo de configuração local
├── styles/
│   └── style.css               # Estilos globais da aplicação
├── images/                     # Logótipo e ícones da interface
├── database/
│   └── deapc.sql               # Esquema relacional, trigger e dados de demonstração
├── .gitignore
└── README.md
```

---

## Tecnologias Utilizadas

- **Frontend:** HTML5, CSS3, JavaScript (DOM e `fetch` API)
- **Backend:** PHP 8 (`mysqli`, sessões PHP)
- **Base de Dados:** MySQL / MariaDB (`clients`, `products`, `orders_client`, `orders_products`, `users`)
- **Ambiente de Execução:** Apache (XAMPP / WAMP / LAMP)

---

## Como Executar Localmente (XAMPP)

1. **Clonar o repositório** para a pasta do servidor Apache com o nome `deapc` (ex.: `C:\xampp\htdocs\deapc`).
2. **Importar a base de dados:**
   - Iniciar os serviços **Apache** e **MySQL** no XAMPP.
   - Abrir o **phpMyAdmin** (`http://localhost/phpmyadmin`), criar uma base de dados chamada `deapc` e importar o ficheiro [`database/deapc.sql`](database/deapc.sql).
3. **Configurar a ligação MySQL (se necessário):**
   - Por defeito, `scripts/db_config.php` liga-se a `localhost` com utilizador `root` e palavra-passe vazia (padrão XAMPP).
   - Caso uses outras credenciais, copia `scripts/db_config.example.php` para `scripts/db_config.local.php` e ajusta os valores *(ou define as variáveis de ambiente `DB_HOST`, `DB_USER`, `DB_PASS`, `DB_NAME`)*.
4. **Abrir no browser:**
   - Aceder a `http://localhost/deapc/Index.html`

### Contas de Demonstração (incluídas em `database/deapc.sql`)

| Perfil | Username | Password |
| :--- | :--- | :--- |
| Administrador | `admin` | `demo1234` |
| Utilizador | `user_demo` | `demo1234` |

---

## Contexto Académico e Autores

- **Instituição:** Instituto Superior de Engenharia do Porto (ISEP)
- **Curso:** Licenciatura em Engenharia Eletrotécnica e de Computadores (LEEC)
- **Unidade Curricular:** Desenvolvimento de Aplicações Computacionais (DEAPC) — 2024/2025
- **Equipa (ADM Inventories):** Marcel Silva, Daniel Afonso e Arthur Peixoto

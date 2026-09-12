# FeiraNuzzi 🛍️

Sistema de reservas desenvolvido para a **Feira Empreendedora**, permitindo que alunos e professores consultem lojas e produtos, montem um carrinho e realizem reservas. As lojas poderão acompanhar pedidos e gerenciar seus produtos e estoque.

> **Status:** desenvolvimento e preparação para o piloto escolar.

## 🎯 Objetivo

O FeiraNuzzi foi pensado para organizar a experiência de compra durante a Feira Empreendedora de **09/10/2026**.

O projeto também terá um **piloto com a comunidade escolar**, usando a cantina como loja parceira. Esse teste servirá para validar o fluxo de reservas, o controle de estoque, a experiência do usuário e a operação da equipe antes da feira oficial.

## 🧩 Funcionalidades atuais

### Cliente
- visualização do catálogo;
- visualização das lojas;
- consulta de produtos;
- carrinho;
- criação de reservas;
- código de retirada;
- acompanhamento dos pedidos.

### Parceiro / Loja
- acesso ao portal do parceiro;
- visualização e acompanhamento de pedidos;
- gerenciamento de produtos;
- controle de disponibilidade e estoque.

### Administração
- painel administrativo;
- gerenciamento das informações disponíveis no sistema;
- funções administrativas em evolução.

### Próximas etapas
- teste com a comunidade escolar;
- melhorias encontradas no piloto;
- integração de pagamento via PIX;
- refinamento de design e integração entre módulos;
- preparação para a Feira Empreendedora.

## 🛠️ Tecnologias

- **Frontend:** HTML5, CSS3 e JavaScript
- **Backend:** Python + Flask
- **Banco:** SQLite
- **CORS:** Flask-CORS
- **Autenticação:** sessão Flask + hash de senha com Werkzeug

## 📁 Estrutura

```text
ProjetoNuzzi/
├── index.html
├── style.css
├── script.js
├── parceiro.html
├── parceiro.css
├── parceiro.js
├── admin.html
├── admin.css
├── admin.js
├── app.py
├── requirements.txt
├── .env.example
├── .gitignore
└── README.md
```

O arquivo `feira.db` é criado pelo sistema e deve permanecer fora do Git.

## 🚀 Como executar

### 1. Criar o ambiente virtual

No PowerShell, dentro da pasta `ProjetoNuzzi`:

```powershell
python -m venv .venv
```

### 2. Ativar

```powershell
.\.venv\Scripts\Activate.ps1
```

### 3. Instalar as dependências

```powershell
python -m pip install -r requirements.txt
```

### 4. Configurar a chave secreta

Gere uma chave aleatória:

```powershell
python -c "import secrets; print(secrets.token_hex(32))"
```

Depois, na **mesma janela do PowerShell**:

```powershell
$env:FEIRA_SECRET="COLE_A_CHAVE_AQUI"
```

A chave **não deve ser colocada no GitHub, README, ZIP ou grupo da equipe**.

Se `FEIRA_SECRET` não for definida, o aplicativo gera uma chave aleatória para aquela execução. Isso permite desenvolvimento local, mas as sessões podem ser invalidadas quando o servidor for reiniciado. Para o ambiente de teste/produção, recomenda-se definir `FEIRA_SECRET` explicitamente.

### 5. Iniciar

```powershell
python app.py
```

A aplicação ficará disponível em:

- Cliente: `http://localhost:5000`
- Parceiro: `http://localhost:5000/parceiro.html`
- Admin: `http://localhost:5000/admin.html`

## 🌐 Testar em outro computador ou celular

O dispositivo que vai acessar deve estar na **mesma rede local** do computador que está executando o Flask.

No computador servidor, execute:

```powershell
ipconfig
```

Procure o endereço **IPv4** do adaptador conectado à rede. Por exemplo:

```text
IPv4: 192.168.0.25
```

No celular ou outro computador, acesse:

```text
http://192.168.0.25:5000
```

O Windows Firewall pode precisar permitir a comunicação do Python na rede local. Não exponha a aplicação diretamente à internet durante os testes sem uma configuração de infraestrutura adequada.

## 👤 Contas de demonstração

A versão atual cria automaticamente as contas de demonstração existentes no código quando o banco é inicializado:

| Tipo | E-mail | Senha |
|---|---|---|
| Cliente | `cliente@feiranuzzi.com` | `compras123` |
| Vendedor | `nino@feiranuzzi.com` | `colheita2024` |
| Admin | `admin@feiranuzzi.com` | `admin123` |

**Essas credenciais são apenas para desenvolvimento/teste e não devem ser usadas como credenciais reais de produção.**

## 🔐 Segurança

- `FEIRA_SECRET` pode ser definida por variável de ambiente;
- quando não definida, uma chave aleatória é gerada para a execução local;
- senhas são armazenadas com hash usando Werkzeug;
- autenticação utiliza sessões;
- cookies de sessão usam `HttpOnly` e `SameSite=Lax`;
- chaves estrangeiras do SQLite são habilitadas;
- o banco utiliza WAL para melhorar a concorrência;
- arquivos `.env` e bancos SQLite estão no `.gitignore`.

### Nunca versionar

```text
.env
feira.db
*.db-shm
*.db-wal
.venv/
```

## 🧪 Piloto escolar

Antes da feira oficial, a equipe pretende realizar um teste com a comunidade escolar.

A cantina será cadastrada como loja parceira e disponibilizará produtos específicos para o teste.

Fluxo principal:

```text
Aluno
  ↓
Catálogo
  ↓
Loja
  ↓
Produto
  ↓
Carrinho
  ↓
Reserva
  ↓
Código de retirada
  ↓
Acompanhamento do pedido
```

Durante o piloto, a equipe deve observar principalmente:

- velocidade e estabilidade;
- criação de reservas;
- atualização de estoque;
- funcionamento do portal da loja;
- experiência pelo celular;
- problemas de login e sessão;
- clareza das informações para os alunos.

## 👥 Equipe

### 🧭 Gestão e coordenação

**Kevelin** — Supervisão do projeto e Backend  
`@kevelincristine`

- supervisiona o desenvolvimento;
- organiza e acompanha as tarefas;
- desenvolve e mantém o backend;
- trabalha na API Flask;
- estrutura e mantém o banco de dados;
- cuida de autenticação, sessões, pedidos, estoque e regras de negócio;
- acompanha a integração entre frontend, backend e banco.

**Suellen** — Coleta de dados e organização  
`@TODO`

- organiza a coleta de dados da feira;
- auxilia no levantamento de lojas e produtos;
- participa da organização do evento de teste.

**Letycia** — Coleta de dados e organização  
`@TODO`

- auxilia na coleta de dados;
- organiza informações das lojas;
- participa da preparação do piloto.

### 🎨 Frontend

**Pedro** — Layout do Cliente  
`@TODO`

Responsável pela interface do cliente, incluindo catálogo, lojas, produtos, carrinho e experiência de navegação.

**Isabela** — Layout da Loja  
`@TODO`

Responsável pelo Portal do Parceiro e pelas interfaces utilizadas pelas lojas.

**Danilo** — Layout Administrativo  
`@TODO`

Responsável pela interface do Painel Administrativo.

**Miguel R. e Helena** — Design  
`@TODO / @TODO`

Atuarão na evolução visual, identidade, componentes e experiência do usuário.

### ⚙️ Backend

**Kevelin** — Backend e Banco de Dados  
`@kevelincristine`

Responsável atualmente pela API, autenticação, sessões, usuários, lojas, produtos, estoque, pedidos, reservas e persistência em SQLite.

**Samuel** — Banco de Dados  
`@TODO`

Entrará futuramente auxiliando na evolução e manutenção do banco.

**Miguel M.** — Integração Frontend + Backend  
`@TODO`

Atuará na comunicação entre as interfaces e a API, ajudando a integrar os fluxos completos.

### 🛡️ Infraestrutura

**Dennis** — Infraestrutura e segurança  
`@TODO`

Responsável pela preparação do servidor, disponibilidade, segurança da infraestrutura e suporte durante o piloto e a feira.

## 💳 PIX

O pagamento via PIX está previsto para uma etapa posterior.

Fluxo planejado:

```text
Carrinho → Reserva → PIX → Confirmação → Pedido confirmado → Retirada
```

Credenciais e chaves de pagamento nunca devem ser colocadas diretamente no frontend ou no repositório.

## 📌 Contribuição e testes

Ao encontrar um problema, registre:

1. o que você tentou fazer;
2. o que esperava acontecer;
3. o que aconteceu de fato;
4. dispositivo e navegador;
5. horário aproximado;
6. print ou vídeo, quando possível.

Exemplo:

> Ao adicionar 2 unidades ao carrinho, a quantidade voltou para 1. Testado no Android/Chrome às 14:30.

## 📅 Evento principal

**Feira Empreendedora — 09/10/2026**

O objetivo da equipe é chegar ao evento com uma versão funcional, testada e preparada para a operação real.

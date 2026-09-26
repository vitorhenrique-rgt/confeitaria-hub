# 🍰 ConfeitariaHub

> Projeto-guia de uma formação Full Stack JavaScript, construído de
> forma incremental para simular o desenvolvimento de uma plataforma
> real de vendas e gestão para uma confeitaria.

![Status](https://img.shields.io/badge/status-em%20desenvolvimento-orange)
![Projeto](https://img.shields.io/badge/projeto-educacional-blue)
![Stack](https://img.shields.io/badge/stack-Full%20Stack%20JavaScript-yellow)

## 📌 Sobre o projeto

O **ConfeitariaHub** é uma plataforma digital criada para a confeitaria
fictícia **Doce Encanto**.

O projeto foi concebido como um **projeto-guia de aprendizagem**: em vez
de criar exercícios independentes e descartáveis, cada nova tecnologia
estudada é incorporada ao mesmo produto. O sistema começa com HTML e CSS
e evolui gradualmente até uma aplicação Full Stack com frontend moderno,
backend, APIs e persistência de dados.

O produto possui três grandes áreas:

* 🌐 **Área pública / cliente** --- site institucional + cardápio
  digital + fluxo de compra;
* 🛠️ **Área administrativa** --- gestão de produtos, categorias,
  clientes, pedidos e indicadores;
* ⚙️ **Backend / API** --- regras de negócio, comunicação e
  persistência.

> **Importante:** a área institucional é parte da experiência pública,
> mas o núcleo do produto é o **cardápio digital e o fluxo de pedidos**.
> O painel administrativo é uma área separada, destinada à equipe da
> confeitaria.

---

## 🎯 Objetivo do produto

### Para clientes

* conhecer a Doce Encanto;
* navegar pelo cardápio;
* pesquisar e filtrar produtos;
* visualizar detalhes, preços e disponibilidade;
* adicionar produtos ao carrinho;
* alterar quantidades e remover itens;
* finalizar pedidos;
* acompanhar o status do pedido.

### Para a confeitaria

* cadastrar e editar produtos;
* organizar categorias;
* ativar/desativar produtos;
* visualizar clientes;
* receber e acompanhar pedidos;
* atualizar o status dos pedidos;
* consultar indicadores e vendas;
* evoluir futuramente para controle de estoque e outros processos
  internos.

---

## 🧭 Visão do sistema

```text
                         CONFEITARIAHUB
                               │
              ┌────────────────┼────────────────┐
              │                │                │
              ▼                ▼                ▼
       ÁREA DO CLIENTE    ÁREA ADMINISTRATIVA   BACKEND
              │                │                │
      ┌───────┼───────┐   ┌────┼────┐           │
      │       │       │   │    │    │           │
    Home   Cardápio Carrinho Produtos Pedidos    API
              │       │        │    │            │
           Produto  Checkout Clientes Dashboard  │
                       │                          │
                     Pedido                       │
                       │                          │
                       └──────────┬───────────────┘
                                  │
                                  ▼
                            BANCO DE DADOS
                         ┌────────┴────────┐
                         │                 │
                      MongoDB             SQL
```

---

# 🛍️ Área pública / cliente

A área pública não é apenas uma página institucional. Ela é uma
**experiência de compra**, na qual a apresentação da marca complementa o
objetivo principal: levar o usuário ao cardápio e ao pedido.

## Página inicial

A Home apresenta:

* identidade da Doce Encanto;
* chamada principal;
* acesso ao cardápio;
* produtos em destaque;
* apresentação da empresa;
* informações resumidas;
* contato;
* navegação para as demais áreas.

Fluxo principal:

```text
Home
  │
  ▼
Cardápio
  │
  ▼
Produto
  │
  ▼
Carrinho
  │
  ▼
Checkout
  │
  ▼
Pedido
```

## 🍰 Cardápio digital

O cardápio é o coração da área pública.

O cliente deverá conseguir:

* visualizar todos os produtos;
* pesquisar produtos;
* filtrar por categoria;
* visualizar preço e disponibilidade;
* abrir detalhes de um produto;
* adicionar produtos ao carrinho.

```text
┌──────────────────────────────────────────────┐
│                 NOSSO CARDÁPIO               │
├──────────────────────────────────────────────┤
│ 🔎 Buscar produto...                         │
│                                              │
│ [Todos] [Bolos] [Doces] [Salgados] [Bebidas] │
│                                              │
│ ┌──────────┐ ┌──────────┐ ┌──────────┐       │
│ │  IMAGEM  │ │  IMAGEM  │ │  IMAGEM  │       │
│ │ Bolo     │ │ Brigadeiro│ │ Coxinha │       │
│ │ R$45,00  │ │ R$3,50   │ │ R$6,00  │        │
│ │[ADICIONAR]│ │[ADICIONAR]│ │[ADICIONAR]│    │
│ └──────────┘ └──────────┘ └──────────┘       │
└──────────────────────────────────────────────┘
```

## 🧁 Detalhes do produto

Cada produto poderá possuir imagem, nome, descrição, preço, categoria,
disponibilidade, variações e quantidade.

```text
Bolo de Chocolate

Bolo de chocolate com recheio de brigadeiro.

R$ 45,00

Tamanho:
[1 kg] [2 kg] [3 kg]

Quantidade:
[-] 1 [+]

[ ADICIONAR AO CARRINHO ]
```

## 🛒 Carrinho

O carrinho deve permitir visualizar itens, alterar quantidades, remover
produtos e calcular subtotais e total.

```text
MEU CARRINHO

Bolo de Chocolate       1       R$ 45,00
Brigadeiro Gourmet     10       R$ 35,00
Coxinha                 5       R$ 30,00

-------------------------------
Subtotal:                       R$ 110,00
Entrega:                         R$ 10,00
Total:                           R$ 120,00

[ FINALIZAR PEDIDO ]
```

## 💳 Checkout

O checkout coleta as informações necessárias para criar o pedido:

* nome;
* telefone;
* e-mail;
* endereço, quando houver entrega;
* modalidade de entrega ou retirada;
* observações;
* forma de pagamento.

```text
Carrinho
   ↓
Dados do cliente
   ↓
Entrega / retirada
   ↓
Pagamento
   ↓
Confirmação
   ↓
Pedido criado
```

## ✅ Pedido

Um pedido poderá possuir identificador, cliente, data, itens,
quantidades, preços, subtotal, taxa, total, endereço, pagamento,
observações e status.

Fluxo sugerido:

```text
Novo
 ↓
Confirmado
 ↓
Em preparação
 ↓
Pronto
 ↓
Saiu para entrega
 ↓
Concluído
```

Também poderá existir o estado `Cancelado`, conforme as regras do
negócio.

---

# 🏢 Área institucional

A parte institucional complementa o cardápio e apresenta a marca.

### Sobre nós

* história da Doce Encanto;
* proposta da empresa;
* valores;
* diferenciais;
* informações sobre produção.

### Contato

* telefone;
* e-mail;
* endereço;
* redes sociais;
* formulário de contato.

A área institucional **não substitui o cardápio**.

---

# 🛠️ Área administrativa

A área administrativa é destinada aos funcionários da confeitaria e é
separada da experiência de compra do cliente.

## Dashboard

Pode apresentar:

* vendas;
* quantidade de pedidos;
* clientes cadastrados;
* produtos mais vendidos;
* pedidos recentes;
* indicadores por período.

```text
┌──────────────────────────────────────────────────┐
│                 DASHBOARD                        │
├────────────┬────────────┬────────────────────────┤
│ R$ 4.250   │ 87 pedidos │ 132 clientes           │
│ Vendas     │ no período │ cadastrados            │
├────────────┴────────────┴────────────────────────┤
│ VENDAS POR PERÍODO                               │
│ ████                                             │
│ ██████                                           │
│ █████████                                        │
│ ███████████                                      │
├──────────────────────────────────────────────────┤
│ PEDIDOS RECENTES                                 │
│ #1042  João     R$90   Preparando              │
│ #1041  Maria    R$45   Novo                    │
│ #1040  Carlos   R$120  Concluído               │
└──────────────────────────────────────────────────┘
```

## 📦 Produtos

O administrador deverá poder:

* cadastrar produto;
* editar produto;
* alterar preço;
* alterar descrição;
* alterar categoria;
* alterar imagem;
* ativar/desativar produto;
* consultar produtos.

## 🗂️ Categorias

Exemplos:

```text
Bolos
Doces
Salgados
Sobremesas
Bebidas
Kits
```

As categorias cadastradas no administrativo deverão alimentar os filtros
do cardápio público.

## 📋 Pedidos

O administrador poderá visualizar pedidos, abrir seus detalhes e
atualizar o status conforme as regras do sistema.

## 👤 Clientes

O painel poderá apresentar cadastro, contato, histórico de pedidos e
outras informações relevantes para atendimento.

---

# 🧱 Arquitetura evolutiva

A arquitetura final esperada é aproximadamente:

```text
                    USUÁRIO
                       │
                       ▼
              ┌─────────────────┐
              │ React / Next.js │
              └────────┬────────┘
                       │
                      HTTP
                       │
                       ▼
              ┌─────────────────┐
              │   Node.js API   │
              └────────┬────────┘
                       │
             ┌─────────┴─────────┐
             ▼                   ▼
         MongoDB                SQL
```

Essa arquitetura não nasce pronta. Ela será construída progressivamente
durante as sprints.

---

# 🗺️ Roadmap de desenvolvimento

Cada sprint representa um conjunto de conhecimentos estudados no curso e
adiciona uma camada ao mesmo projeto.

```
Sprint Módulo / tecnologia    Resultado principal
```

---

```
    01 Fundação               Ambiente e estrutura
    02 HTML 5                 Estrutura semântica
    03 CSS 3                  Interface responsiva
    04 JavaScript I           Primeiras regras de negócio
    05 JavaScript II          Modelo de dados
    06 DOM                    Cardápio interativo
    07 JavaScript moderno     Código modular
    08 POO                    Modelo de domínio
    09 APIs / assíncronismo   Dados externos
    10 TypeScript             Contratos de tipos
    11 Git / GitHub           Versionamento profissional
    12 CSS moderno            Design System
    13 Sass                   Arquitetura dos estilos
    14 Bootstrap              Painel administrativo
    15 React                  Componentização
    16 Next.js                Aplicação web
    17 Node.js                Servidor
    18 API                    Backend e regras
    19 MongoDB                Persistência NoSQL
    20 SQL                    Persistência relacional
```

---

## Sprint 01 --- Fundação

**Foco:** preparar ambiente, estrutura inicial e documentação.

**Entrega:** projeto preparado para crescer sem depender de uma única
tecnologia.

**Aprendizados:** ambiente de desenvolvimento, organização e fluxo
inicial.

## Sprint 02 --- HTML 5

**Foco:** construir a estrutura do produto.

**Implementar:** Home, Cardápio, Produto, Sobre, Contato, navegação,
formulários, imagens e semântica.

**Aprendizados:** HTML, semântica, links, formulários e organização de
conteúdo.

## Sprint 03 --- CSS 3

**Foco:** transformar a estrutura em interface.

**Implementar:** identidade visual, layout, cards, botões, cabeçalho,
rodapé, desktop e mobile.

**Aprendizados:** seletores, box model, Flexbox, Grid, responsividade,
tipografia e posicionamento.

## Sprint 04 --- JavaScript I

**Foco:** primeiras regras de negócio.

**Implementar:** quantidade, subtotal, total e primeiras interações.

**Aprendizados:** variáveis, operadores, condicionais, loops e lógica.

## Sprint 05 --- JavaScript II

**Foco:** modelar dados do negócio.

**Modelar:** produtos, categorias, clientes, pedidos e itens do pedido.

**Aprendizados:** arrays, objetos, funções, métodos e manipulação de
dados.

## Sprint 06 --- JavaScript / DOM

**Foco:** tornar o cardápio interativo.

**Implementar:** renderização, busca, filtros, eventos, carrinho e
atualização da interface.

**Aprendizados:** DOM, eventos, listeners, formulários e manipulação de
elementos.

## Sprint 07 --- JavaScript moderno

**Foco:** organizar o código à medida que o sistema cresce.

**Implementar:** módulos, separação de responsabilidades, JSON e
estrutura de funcionalidades.

**Aprendizados:** import/export, módulos, npm e organização.

## Sprint 08 --- POO

**Foco:** representar o domínio do negócio.

**Modelar:** Produto, Categoria, Cliente, Pedido, Item do Pedido e
Carrinho.

**Aprendizados:** classes, objetos, métodos, encapsulamento, abstração e
relacionamentos.

## Sprint 09 --- APIs e assincronismo

**Foco:** fazer o frontend consumir uma fonte externa de dados.

**Implementar:** carregamento, estados de loading, tratamento de erro,
detalhes de produto e envio de pedido.

**Aprendizados:** Promise, async/await, fetch, HTTP, JSON, APIs e
tratamento de erros.

## Sprint 10 --- TypeScript

**Foco:** estabelecer contratos de dados.

**Tipar:** Product, Category, Customer, Order, OrderItem, Cart e
respostas da API.

**Aprendizados:** tipos, interfaces, unions, opcionais, funções e
classes.

## Sprint 11 --- Git e GitHub

**Foco:** versionamento profissional.

**Praticar:** commits, branches, merge, pull, push, Pull Requests e
conflitos.

Exemplos de branches:

```text
feature/cardapio
feature/carrinho
feature/checkout
feature/api-produtos
fix/calculo-total
fix/filtro-categorias
```

## Sprint 12 --- CSS moderno / Design System

**Foco:** consistência visual.

**Criar padrões para:** botões, cards, inputs, modais, alertas, badges,
tabelas e containers.

## Sprint 13 --- Sass

**Foco:** arquitetura dos estilos.

Estrutura conceitual:

```text
styles/
├── base/
├── components/
├── layout/
└── pages/
```

**Aprendizados:** variáveis, nesting, partials, mixins e organização.

## Sprint 14 --- Bootstrap

**Foco:** criar a área administrativa.

**Implementar:** Dashboard, Produtos, Categorias, Pedidos, Clientes,
tabelas, formulários e modais.

**Aprendizados:** grid, componentes, tabelas, formulários, modais e
responsividade.

## Sprint 15 --- React

**Foco:** reconstruir a experiência dinâmica com componentes.

Componentes candidatos:

```text
Header
Search
CategoryFilter
ProductList
ProductCard
Cart
CartItem
Footer
```

**Aprendizados:** componentes, props, estado, eventos, composição e
renderização.

## Sprint 16 --- Next.js

**Foco:** transformar o frontend em aplicação web estruturada.

Rotas previstas:

```text
/
/produtos
/produtos/[id]
/carrinho
/checkout
/pedido/[id]
/sobre
/contato

/admin
/admin/dashboard
/admin/produtos
/admin/pedidos
/admin/clientes
```

## Sprint 17 --- Node.js

**Foco:** criação do servidor.

Primeiros recursos conceituais:

```text
GET /products
GET /products/:id
```

**Aprendizados:** Node.js, servidor, módulos, HTTP, requisições e
respostas.

## Sprint 18 --- API

**Foco:** construir o backend do ConfeitariaHub.

Recursos principais:

```text
/products
/categories
/customers
/orders
```

Com operações conforme a necessidade:

```text
GET
POST
PUT/PATCH
DELETE
```

**Aprendizados:** API REST, rotas, CRUD, validação, regras de negócio e
respostas HTTP.

## Sprint 19 --- MongoDB

**Foco:** persistência NoSQL.

Coleções previstas:

```text
products
categories
customers
orders
```

**Aprendizados:** documentos, coleções, consultas, persistência e
integração com Node.

## Sprint 20 --- SQL

**Foco:** persistência relacional.

Modelo conceitual:

```text
CUSTOMERS
    │
    │ 1:N
    ▼
ORDERS
    │
    │ 1:N
    ▼
ORDER_ITEMS
    │
    │ N:1
    ▼
PRODUCTS
    │
    │ N:1
    ▼
CATEGORIES
```

**Aprendizados:** tabelas, registros, PK, FK, relacionamentos, SELECT,
INSERT, UPDATE, DELETE, JOIN e agregações.

---

# 🔗 Uma única funcionalidade atravessando a formação

O mesmo conceito deve reaparecer em diferentes camadas. Por exemplo, um
produto começa como conteúdo HTML e termina como dado persistido no
banco:

```text
HTML
 │
 └── estrutura do produto
      ↓
CSS
 │
 └── aparência
      ↓
JavaScript
 │
 └── interação
      ↓
DOM
 │
 └── atualização dinâmica
      ↓
JS moderno
 │
 └── organização
      ↓
POO
 │
 └── modelo de domínio
      ↓
TypeScript
 │
 └── contrato de dados
      ↓
React
 │
 └── ProductCard
      ↓
Next.js
 │
 └── /produtos/[id]
      ↓
Node.js
 │
 └── GET /products/:id
      ↓
MongoDB / SQL
 │
 └── persistência
```

O mesmo princípio vale para carrinho, cliente, pedido, categoria e
outras entidades.

---

# 🧪 Metodologia de aprendizagem

Cada sprint deve seguir um ciclo semelhante:

```text
1. Estudar o módulo
       ↓
2. Entender o problema
       ↓
3. Definir uma estratégia
       ↓
4. Implementar
       ↓
5. Testar
       ↓
6. Corrigir
       ↓
7. Refatorar
       ↓
8. Fazer checkpoint
       ↓
9. Integrar ao projeto
       ↓
10. Próxima sprint
```

## Checkpoint

Antes de avançar, responder:

1. **Eu consigo explicar?** --- consigo explicar como e por que a
   solução funciona?
2. **Eu consigo modificar?** --- consigo alterar a funcionalidade sem
   depender de copiar uma solução pronta?
3. **Eu consigo criar uma variação?** --- consigo aplicar o mesmo
   conceito a um problema semelhante?

---

# 🏁 Marcos da formação

### Marco 1 --- Frontend estático

Após HTML + CSS:

```text
HTML + CSS
```

Interface navegável e responsiva.

### Marco 2 --- Frontend interativo

Após JavaScript e APIs:

```text
HTML + CSS + JavaScript + API
```

Cardápio digital funcional.

### Marco 3 --- Frontend moderno

Após TypeScript, React e Next.js:

```text
TypeScript + React + Next.js
```

Aplicação frontend estruturada.

### Marco 4 --- Backend

Após Node e API:

```text
Frontend
   ↓
API
   ↓
Node
```

Sistema Full Stack começando a tomar forma.

### Marco 5 --- Persistência

Após MongoDB e SQL:

```text
Frontend
   ↓
Next / React
   ↓
Node / API
   ↓
Banco de dados
```

---

# 🎨 Identidade visual

A identidade visual foi pensada para transmitir **confeitaria,
acolhimento, qualidade artesanal e modernidade**.

Paleta de referência:

Cor             Uso

---

Rosa suave      fundos e detalhes
Rosa queimado   destaques
Creme / bege    superfícies
Marrom          textos e identidade
Vinho           ações principais
Verde suave     disponibilidade e estados positivos

A referência visual do projeto inclui versões desktop e mobile das
principais telas: Home, Cardápio, Produto, Carrinho, Checkout, Pedido
Confirmado, Sobre, Contato, Login e Painel Administrativo.

---

# 📱 Responsividade

O frontend deve ser pensado para diferentes tamanhos de tela.

### Desktop

```text
┌─────────────────────────────────────────────┐
│ Logo       Navegação        Ações            │
├─────────────────────────────────────────────┤
│                                             │
│              Conteúdo                       │
│                                             │
│ [Produto] [Produto] [Produto] [Produto]     │
│                                             │
└─────────────────────────────────────────────┘
```

### Mobile

```text
┌──────────────────┐
│ Logo          ☰  │
├──────────────────┤
│                  │
│    Conteúdo      │
│                  │
│ ┌──────────────┐ │
│ │   Produto    │ │
│ └──────────────┘ │
│                  │
│ ┌──────────────┐ │
│ │   Produto    │ │
│ └──────────────┘ │
└──────────────────┘
```

Considerar navegação mobile, cards responsivos, formulários, tabelas
administrativas, carrinho, checkout, acessibilidade e diferentes
larguras de viewport.

---

# ♿ Acessibilidade

A acessibilidade deve ser considerada desde as primeiras sprints, e não
apenas no final.

Exemplos:

* HTML semântico;
* labels adequados;
* textos alternativos;
* navegação por teclado;
* foco visível;
* contraste adequado;
* mensagens de erro compreensíveis;
* estados visuais e textuais;
* componentes utilizáveis em telas pequenas.

---

# 🔒 Segurança e validação

À medida que o backend surgir, o projeto deverá considerar:

* validação de dados;
* tratamento de erros;
* autenticação;
* autorização;
* proteção das rotas administrativas;
* validação no servidor;
* proteção das informações dos clientes;
* controle das operações administrativas.

Esses recursos serão incorporados conforme os módulos correspondentes
forem estudados.

---

# 📐 Regras de negócio iniciais

### Produtos

* produto pode estar disponível ou indisponível;
* produto pertence a uma categoria;
* preço deve ser válido;
* produto indisponível não deve ser vendido.

### Carrinho

* quantidade deve ser maior que zero;
* itens podem ser removidos;
* total deve ser recalculado quando houver alteração.

### Pedido

* pedido deve possuir pelo menos um item;
* pedido deve possuir cliente;
* valores devem ser calculados de maneira consistente;
* status deve seguir o fluxo definido pelo negócio.

### Administração

* operações administrativas não devem ficar disponíveis para usuários
  comuns;
* alterações importantes devem ser validadas.

As regras podem evoluir conforme novos requisitos forem descobertos.

---

# 🚧 O que não faz parte do objetivo inicial

O ConfeitariaHub é um projeto educacional e possui escopo progressivo.
Não é necessário implementar tudo de uma vez.

Podem ficar fora do escopo principal ou ser tratados como desafios
posteriores:

* gateway de pagamento real;
* integração real com WhatsApp;
* emissão fiscal;
* logística avançada;
* integração com marketplaces;
* aplicativo mobile nativo;
* inteligência artificial;
* sistema completo de ERP.

---

# 🚀 Possíveis evoluções futuras

Depois da formação, o projeto pode continuar evoluindo com:

* autenticação completa;
* recuperação de senha;
* notificações;
* integração com WhatsApp;
* pagamento online;
* cupons;
* avaliações;
* favoritos;
* programa de fidelidade;
* estoque;
* fornecedores;
* relatórios avançados;
* métricas;
* testes automatizados;
* CI/CD;
* deploy;
* PWA;
* cache;
* otimização de performance.

---

# 📚 Objetivo educacional

O maior objetivo deste projeto não é criar uma confeitaria virtual. É
criar um ambiente no qual seja possível praticar, de forma conectada:

```text
HTML
 ↓
CSS
 ↓
JavaScript
 ↓
DOM
 ↓
JavaScript moderno
 ↓
POO
 ↓
TypeScript
 ↓
Git
 ↓
React
 ↓
Next.js
 ↓
Node.js
 ↓
APIs
 ↓
MongoDB
 ↓
SQL
 ↓
Full Stack
```

Cada tecnologia entra para resolver um problema real que surgiu durante
a evolução do sistema.

---

# 🏆 Resultado esperado

Ao finalizar o projeto, a plataforma deverá representar a evolução
completa:

```text
                    CLIENTE
                       │
                       ▼
                  CONFEITARIAHUB
                       │
          ┌────────────┴────────────┐
          │                         │
      CARDÁPIO                  CHECKOUT
          │                         │
      PRODUTOS                    PEDIDO
          │                         │
          └────────────┬────────────┘
                       │
                       ▼
                      API
                       │
                       ▼
                    NODE.JS
                       │
             ┌─────────┴─────────┐
             │                   │
          MONGODB               SQL
             │                   │
             └─────────┬─────────┘
                       │
                       ▼
                 ADMINISTRAÇÃO
```

O objetivo final é que o repositório mostre claramente a evolução **de
uma página HTML simples para uma aplicação Full Stack JavaScript**, sem
perder a conexão entre as etapas.

---

# 📌 Status

🚧 **Em desenvolvimento**

Este repositório acompanha uma formação Full Stack JavaScript e será
evoluído sprint por sprint.

---

# 📄 Licença

Projeto educacional. A licença definitiva pode ser definida conforme a
finalidade do repositório.

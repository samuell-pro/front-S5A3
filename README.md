# front-S5A3
react-router
# 🚀 Atividade Prática — Navegação com React Router

> **Projeto:** Painel de Controle da InnoMetrics


## 🧠 Antes de começar: entenda o contexto

### O que é uma SPA?

Sabe quando você usa o Gmail ou o Instagram e a página **não recarrega do zero** toda vez que você clica em algo? Isso é uma **SPA (Single Page Application)** — ou "Aplicação de Página Única".

Em vez de carregar uma página nova do servidor a cada clique, a SPA atualiza **só o conteúdo** da tela. Resultado: tudo fica mais rápido e fluido.

### Mas... como o React sabe qual "tela" mostrar?

É aí que entra o **roteamento**! Ele funciona como um GPS interno da aplicação:
dependendo do endereço (URL) que o usuário acessa, o React exibe um componente diferente.

**Exemplo:**
| URL acessada | Tela exibida |
|---|---|
| `/` | Dashboard |
| `/relatorios` | Relatórios |
| `/configuracoes` | Configurações |
| `/suporte` | Suporte |

---

## 🏢 O Desafio

A empresa fictícia **InnoMetrics** quer um painel de controle para monitorar métricas
de sistemas. Ela precisa de 4 páginas: **Dashboard, Relatórios, Configurações e Suporte**.

**Sua missão:** implementar a navegação entre essas páginas usando o **React Router**,
sem que a página recarregue ao trocar de seção.

---

## 🎯 Objetivo

Configurar e implementar o **React Router** em um projeto React, permitindo navegar
entre diferentes páginas sem recarregar a aplicação.

---

## 🧰 O que você vai precisar

- Computador com internet
- Visual Studio Code instalado
- Terminal (pode ser o próprio terminal do VS Code)
- Caderno e caneta para anotar dúvidas

---

## 📋 Passo a Passo

### Passo 1 — Criar o Projeto React

Abra o terminal e execute o comando abaixo para criar um projeto React novo:

```bash
npx create-react-app fronts5a3 --use-npm
```

> 💡 **O que esse comando faz?**
O `npx` executa pacotes sem precisar instalá-los. O `create-react-app` é uma
ferramenta oficial que monta toda a estrutura de um projeto React automaticamente.
`fronts5a3` é o nome da pasta que será criada.
> 

Depois que terminar, entre na pasta do projeto e inicie o servidor:

```bash
cd fronts5a3
npm start
```

Se tudo deu certo, o navegador vai abrir com a tela padrão do React (fundo escuro
com o logo girando). Pode fechar essa janela por enquanto — vamos modificar tudo!

---

### Passo 2 — Instalar o React Router

O React por si só não sabe fazer roteamento. Precisamos instalar uma biblioteca
chamada **react-router-dom**. No terminal (dentro da pasta do projeto), rode:

```bash
npm install react-router-dom
```

> 💡 **O que é uma biblioteca?**
É um conjunto de ferramentas prontas que outras pessoas criaram. Assim, não
precisamos escrever tudo do zero — só usamos o que já foi feito!
> 

---

### Passo 3 — Criar as Páginas

Agora vamos criar os 4 componentes que representam as páginas do painel.

1. Dentro da pasta `src`, crie uma nova pasta chamada **`pages`**
2. Dentro de `pages`, crie os 4 arquivos abaixo:

```
src/
└── pages/
    ├── Dashboard.js
    ├── Relatorios.js
    ├── Configuracoes.js
    └── Suporte.js
```

Em cada arquivo, escreva um componente simples. Use o modelo abaixo e **adapte
o nome** para cada página:

**`Dashboard.js`**

```jsx
import React from 'react';

function Dashboard() {
  return <h1>Dashboard</h1>;
}

export default Dashboard;
```

**`Relatorios.js`**

```jsx
import React from 'react';

function Relatorios() {
  return <h1>Relatórios</h1>;
}

export default Relatorios;
```

> 🔁 Repita a mesma estrutura para `Configuracoes.js` e `Suporte.js`,
trocando apenas o nome da função e o texto dentro do `<h1>`.
> 

> 💡 **O que é `export default`?**
É a forma de "exportar" o componente para que outros arquivos consigam
importá-lo e usá-lo.
> 

---

### Passo 4 — Configurar o Roteamento no App.js

Agora vem a parte principal! Abra o arquivo **`src/App.js`** e **substitua todo
o conteúdo** pelo código abaixo:

```jsx
import { BrowserRouter as Router, Routes, Route, Link } from 'react-router-dom';

import Dashboard     from './pages/Dashboard';
import Relatorios    from './pages/Relatorios';
import Configuracoes from './pages/Configuracoes';
import Suporte       from './pages/Suporte';

function App() {
  return (
    <Router>
      <div>

        {/* Menu de navegação */}
        <nav>
          <ul>
            <li><Link to="/">Dashboard</Link></li>
            <li><Link to="/relatorios">Relatórios</Link></li>
            <li><Link to="/configuracoes">Configurações</Link></li>
            <li><Link to="/suporte">Suporte</Link></li>
          </ul>
        </nav>

        {/* Aqui o React decide qual componente exibir */}
        <Routes>
          <Route path="/"             element={<Dashboard />}     />
          <Route path="/relatorios"   element={<Relatorios />}    />
          <Route path="/configuracoes" element={<Configuracoes />} />
          <Route path="/suporte"      element={<Suporte />}       />
        </Routes>

      </div>
    </Router>
  );
}

export default App;
```

> 💡 **Entendendo o código:**
> 
> - `<Router>` — "envolve" toda a aplicação e ativa o sistema de rotas
> - `<Link to="...">` — funciona como uma tag `<a>`, mas **sem recarregar** a página
> - `<Routes>` — é o "controlador" que decide qual componente mostrar
> - `<Route path="..." element={...} />` — conecta uma URL a um componente

---

### Passo 5 — Testar a Aplicação

Com o servidor rodando (`npm start`), abra o navegador e:

- [ ]  Clique em **Dashboard** → deve aparecer "Dashboard"
- [ ]  Clique em **Relatórios** → deve aparecer "Relatórios"
- [ ]  Clique em **Configurações** → deve aparecer "Configurações"
- [ ]  Clique em **Suporte** → deve aparecer "Suporte"
- [ ]  Observe a URL: ela muda sem a página recarregar! ✅

---

### Passo 6 — Documentar o que você fez

Responda no seu caderno (ou em um arquivo `.txt`):

1. O que é uma SPA? Explique com suas próprias palavras.
2. Qual é a função do `<Router>` no código?
3. Qual a diferença entre usar `<Link>` e uma tag `<a>` normal?
4. Você encontrou algum erro durante a atividade? Como resolveu?

---

## ✅ Estrutura Final do Projeto

```
fronts5a3/
└── src/
    ├── pages/
    │   ├── Dashboard.js
    │   ├── Relatorios.js
    │   ├── Configuracoes.js
    │   └── Suporte.js
    └── App.js  ← arquivo principal que você modificou
```

